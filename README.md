# Azure-IoT-Hub-receiving-ESP32-Telemetry-using-DHT11
In this project I sent DHT 11 Sensor data to Azure IOT hub using ESP32.
 This project demonstrates sending temperature and humidity data from an ESP32 microcontroller to Azure IoT Hub using MQTT, with a DHT11 sensor as the data source.
The ESP32 reads sensor values periodically and publishes them as JSON telemetry messages to Azure IoT Hub, where they can be monitored, stored, or processed further.

# Features

ESP32 Wi-Fi connectivity

DHT11 temperature & humidity sensor

Secure telemetry upload to Azure IoT Hub

JSON-formatted messages

MQTT-based communication

Serial monitor debugging support

# Hardware Requirements

ESP32 Development Board

DHT11 Temperature & Humidity Sensor

10kΩ Pull-up Resistor

Breadboard & Jumper Wires

Wi-Fi connection

# Sensor Wiring

![Sensor Wiring](https://github.com/shivaninja/Azure-IoT-Hub-ESP32-Telemetry-using-DHT11/blob/db915b107484a7036e9b3ce685543c631a5fc944/Wiring%20Diagram/pic.png)

DHT11 Pin	Connection

Pin 1	3.3V (ESP32)

Pin 2	GPIO (any digital pin) + 10kΩ pull-up

Pin 4	GND

### Note: Do NOT power DHT11 with 5V when using ESP32. Use 3.3V only.

# Block Diagram
```
----------------------
|    DHT11 Sensor    |
|--------------------|
| Temperature        |
| Humidity           |
----------+-----------
          |
          | (GPIO)
          v
----------+-----------
|        ESP32       |
|--------------------|
| - DHT Library      |
| - WiFi Stack       |
| - MQTT Client      |
| - JSON Formatter   |
----------+-----------
          |
          | (Wi-Fi / MQTT)
          v
----------+-----------
|   Azure IoT Hub    |
|--------------------|
| - Device Registry  |
| - Message Ingest   |
| - Cloud Routing    |
----------+-----------
          |
          | (Monitoring / Processing)
          v
----------------------
| Azure Tools        |
|--------------------|
| - IoT Explorer     |
| - Stream Analytics |
| - Storage / Apps   |
----------------------

```

# Software Requirements

Arduino IDE

ESP32 Board Package

Required Libraries:

WiFi.h

DHT sensor library

AzureIotHub

Esp32MQTTClient
You can use the below code for including libraries in code
```
#include <WiFi.h>
#include "DHT.h"
#include "AzureIotHub.h"
#include "Esp32MQTTClient.h"
#define INTERVAL 2000
#define DEVICE_ID "ESP32DEVICELIVE"
#define MESSAGE_MAX_LEN 256
#define DHTPIN 4
#define DHTTYPE DHT11
```

# Azure IoT Hub Setup (Overview)

Create an Azure IoT Hub

Register a device inside the IoT Hub

Copy the Device Connection String

Paste it into the firmware code

Use Azure Portal / Azure IoT Explorer to monitor telemetry

# Telemetry Format
```
Data is sent as a JSON payload:

{
  "deviceId": "ESP32DEVICELIVE",
  "messageId": 1,
  "Temperature": 27.5,
  "Humidity": 62.0
}
```

# Transmission Interval

Sensor data is sent every 2 seconds

Configurable using:

#define INTERVAL 2000

# How to Run

Clone this repository

Open the .ino file in Arduino IDE

Update:

Wi-Fi SSID & Password

Azure IoT Hub connection string

Select correct ESP32 board & COM port

Upload the code

Open Serial Monitor (115200 baud)

# Serial Monitor Output Example
```
Connecting...
WiFi connected
IP address: 192.168.1.12
{"deviceId":"ESP32DEVICELIVE","messageId":1,"Temperature":28.00,"Humidity":60.00}
Send Confirmation Callback finished.
```

# Author

Shiva Goud
