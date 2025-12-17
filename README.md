BSK Notus Modbus Integration

This repository contains my research, findings, and implementation for integrating and controlling a BSK Notus unit using the Modbus protocol.

The goal of this project is to document how the BSK Notus communicates over Modbus and to provide a practical reference for reading data and sending control commands programmatically.

DEFAULT COMMUNICATION SETTINGS FOR MODBUS:

##################

Baud rate: 115200
Data bits: 8
Parity: None
Stop bits: 1

##################

EXAMPLE FROM configuration.yaml:

modbus:
  - name: modbus_hub
    type: serial
    method: rtu
    port: /dev/ttyUSB1
    baudrate: 115200
    stopbits: 1
    bytesize: 8
    parity: N
    timeout: 1

    sensors:

      - name: "Notus Reg 0 Device State"
        slave: 1
        address: 0
        input_type: holding
        data_type: uint16

      - name: "Notus Reg 1 Aspirator Fan Speed"
        slave: 1
        address: 1
        input_type: holding
        data_type: uint16
        unit_of_measurement: "%"

      - name: "Notus Reg 2 Ventilator Fan Speed"
        slave: 1
        address: 2
        input_type: holding
        data_type: uint16
        unit_of_measurement: "%"

      - name: "Notus Reg 3 Target Temperature"
        slave: 1
        address: 3
        input_type: holding
        data_type: uint16
        scale: 0.1
        precision: 1
        unit_of_measurement: "°C"

      - name: "Notus Reg 4 Auto Mode"
        slave: 1
        address: 4
        input_type: holding
        data_type: uint16
