# ModbusKit

**ModbusKit** is a Swift package that implements the Modbus protocol, allowing you to easily communicate with Modbus-compatible devices over TCP in your iOS, macOS.

## Features

- **Modbus TCP**: Communicate with Modbus servers over TCP/IP.
- **Client Implementation**: Modbus client (Master) implementation for interacting with Modbus devices.
- **Support for all function codes**: Including reading/writing coils, discrete inputs, input registers, and holding registers.
- **Cross-Platform**: Works on iOS and macOS
- **Easy to Use**: Swift-friendly API with clear documentation and examples.

## Installation

### Swift Package Manager

To integrate **ModbusKit** into your project using Swift Package Manager, add the following to your `Package.swift`:

```swift
dependencies: [
    .package(url: "https://github.com/schneim/ModbusKit.git", from: "1.0.0")
]


Then run swift package update in your project directory.

Usage

Modbus TCP Client

import ModbusKit

// Create a Modbus TCP client
let client = ModbusTCPClient(host: "192.168.1.100", port: 502)

do {
    // Connect to the Modbus server
    try client.connect()

    // Read holding registers (function code 03)
    let response = try client.readHoldingRegisters(address: 0x10, quantity: 2)
    print("Received data: \(response)")

    // Write a value to a coil (function code 05)
    try client.writeSingleCoil(address: 0x01, value: true)

    // Disconnect when done
    client.disconnect()
} catch {
    print("Modbus error: \(error)")
}


Documentation

Detailed documentation is available in the Docs/ folder and in-line within the code.

Contributions

We welcome contributions! If you’d like to add new features, fix bugs, or improve the documentation, feel free to fork the repository and submit a pull request. Please make sure to follow the code style and include unit tests for any new functionality.

License

ModbusKit is licensed under the MIT License. See the LICENSE file for more details.
