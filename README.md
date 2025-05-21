# Flow_Battery_Controls

Author: Robert Thomas
Date: May 2, 2025

This is a starting point for the control system demo we’re planning to show at the December expo. It’s based on the design schematic and sets up a basic state machine for charging, discharging, and fault handling. Nothing has been tested yet, and the sensor inputs are just simulated through analog reads.

# What It Does:

Picks between charging, discharging, and fault states based on voltage and temperature

Turns relays on/off depending on the state

Lights up an LED if a fault is detected

Reads analog values from A0 and A2 (for voltage and temp) and maps them to a realistic range

# Pin Setup:

| Function           | Pin | Notes                              |
| ------------------ | --- | ---------------------------------- |
| Charge Relay       | D5  | Turns on during charging           |
| Grid Relay         | D6  | Turns on during discharging        |
| Fault LED          | D13 | On if voltage/temp is out of range |
| Voltage Sensor Sim | A0  | Mapped to 0–15V                    |
| Current Sensor     | A1  | Not used right now                 |
| Temp Sensor Sim    | A2  | Mapped to 0–100°C                  |


# States

CHARGING: If voltage < 11.8V

DISCHARGING: If voltage is between 11.8V and 12.6V

FAULT: If voltage < 10.5V, > 12.6V, or temp > 50°C

Each state disables or enables the correct relays and sets the fault LED if needed.
