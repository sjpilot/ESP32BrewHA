# ESP32BrewHA
ESP32 Beer Brewing with ESPHome+Home Assistant

# ESPHome Dashboard
Here is an example dashboard from earlier prototype hardware
![Home Assistant Dashboard](/HA/Dash.png)
![History](/HA/History.png)

# PCB
The following PCB can be ordered from [JLCPCB.com](https://jlcpcb.com/) (or any other prototyping PCB company) using the files in the [PCB](/PCB) folder.
![PCB](/PCB/3D_PCB_2024-01-04.png)

# Schematic
This is the schematic built using [EasyEDA Pro](https://pro.easyeda.com/), project is in the [/EasyEDA Pro Project](/EasyEDA%20Pro%20Project) folder.
[PDF of the schematic can be viewed here](/Schematic/SCH_esp32%20brewpiless_2024-01-04.pdf)

# Q & A
What sensors does this board support?
Dallas DS18B20B & RTD PT100 via a MAX31865 (change some coponent values to use PT1000)

Why is there USB-C & Programming header?
Previous prototype only used the Programming header with an ESP-PROG so USB-C was added untested and might not work. UPDATE: USB-C does not work, programming header does. refer issues.

What is the ATECC608A security chip for?
Nothing, ESPHome does not currently support it. It is for my future & personal projects, eg Azure/AWS IOT using certificates etc.

What enclosure is this sized for?
Gainta G214MF is the OEM part number rebadged by an Australian reseller. It is available globally from https://www.xonelec.com/mpn/gainta/g214mf for example.

Connections?
AC 240V is the main input via P29.
The board can be powered via 5V DC alternatively using the VCC connector P28. Leave F21 empty if using DC power.
The relay outputs K1-3 are powered via P29 if F22 is installed or dry contacts if fuse empty.
P31-P33 are 5V outputs, noting the input PSU is only 1A max shared with ESP32, relay coils, etc.
DS18B20 is for the Dallas DS18B20, Red +, Yellow Sig, Black -.
RTD is for a 2 wire PT100 as found on some homebrewing equipment such as DigiBoil.

Issues:
During testing of a previous prototype approx 1 in 10 values of the DS18B20 had a CRC error while two sensors were connected (1m wire). R12 may need to be decreased for additional sensors / wire length.
USB-C does not work (see Github issues)

Notes:
When tuning PID loop, you may notice overshoot where the temperature keeps rising even after the element turns off. This is probably because the temperature sensor isn't making efficient contact with the thermowell so there's some delay before it heats to the liquid it's measuring.
USB net is incorrectly labelled U27 instead of U11
I have never used the RTD, ATEC & USB functions before and are completely untested.

Enclosure:
Board mounting - M3 5mm & 6mm length screws ordered.
M4 screws to mount the enclosure, use either self tappers or nut & bolts.
