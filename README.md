# Marlin 3D Printer Firmware

![GitHub](https://img.shields.io/github/license/marlinfirmware/marlin.svg)

<img align="right" width=175 src="buildroot/share/pixmaps/logo/marlin-250.png" />

Additional documentation can be found at the [Marlin Home Page](https://marlinfw.org/).
Please test this firmware and let us know if it misbehaves in any way. Volunteers are standing by!

## Marlin 2.0 Bugfix Branch for Ender 3 Pro with BTT SKR Mini E3 V2.0 and BLTouch

## Printer specific changes
These changes are based on the Ender 3 [example configuration](https://github.com/MarlinFirmware/Configurations/commits/import-2.0.x/config/examples/Creality/Ender-3/BigTreeTech%20SKR%20Mini%20E3%202.0).  
* Use probe for Z homing/don't use Z endstop
* Set Z probe pin to PC14 (SKR probe pin)
* Use BLTouch
* Nozzle to probe offset. Using [Petsfang](https://www.thingiverse.com/thing:2759439) right side BLTouch mount
* Auto biliner bed leveling
* Safe Z homing for probe
* Swapped enslosure fan and hot end fan wiring on board: Disable enslosure fan
* Set hot end fan to pin E0_AUTO_FAN_PIN FAN1_PIN

## Cura Start G-Code
    M190 S{material_bed_temperature_layer_0} ;Wait for bed to reach temp before proceeding
    G28 ; Home all axes
    G29 ; Auto level bed
    M109 S{material_print_temperature_layer_0} ;Wait for extruder to reach temp before proceeding  

## Z-Offset
Instructions:
1. G28 - Home printer
2. M851 Z0 - Reset Z-Offset
3. M500 - Store setting to eeprom
4. M501 - Set active parameters
5. M503 - Display Active Parameters
6. G28 Z - Home Z Axis
7. G1 F60 Z0 - Move nozzle to true 0 offset
8. M211 S0 - Disable soft endstops
9. Move nozzle towards to set desired height
10. Note Z on the printer display
11. M851 Z X.XX (X.XX is Z offset noted from previous step. This can be negative)
12. M211 S1 - Enable Soft Endstops
13. M500 - Save settings to Eeprom
14. M501 - Set Active Parameters
15. M503 - display current settings

## License

Marlin is published under the [GPL license](/LICENSE) because we believe in open development. The GPL comes with both rights and obligations. Whether you use Marlin firmware as the driver for your open or closed-source product, you must keep Marlin open, and you must provide your compatible Marlin source code to end users upon request. The most straightforward way to comply with the Marlin license is to make a fork of Marlin on Github, perform your modifications, and direct users to your modified fork.

While we can't prevent the use of this code in products (3D printers, CNC, etc.) that are closed source or crippled by a patent, we would prefer that you choose another firmware or, better yet, make your own.
