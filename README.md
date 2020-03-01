# ESP32-MA-Multitask
Arduino ESP32 Client for Machine Advisor, the Digital Service for machines by Schneider Electric

The library provides a simple integration to Machine Advisor from Arduino environment using a ESP32 SoC. It has a powerful and simple logging system, with a configurable comunications buffer and with the option to execute it in a separated task and in a dedicated core.

- Uses Microsoft Esp32MQTTClient library (ESP32 Azure IoT). (https://github.com/VSChina/ESP32_AzureIoT_Arduino)
- Buffering, multitasking and multi core is managed by FreeRtos thas is already included in Arduino libraries for ESP32.

In the examples, the time is got with a NTP client, but other sources, like Real time clock, can be used.

- NTPClient (https://github.com/arduino-libraries/NTPClient)

## EcoStruxure™ Machine Advisor

EcoStruxure Machine Advisor is the new digital cloud-based services platform. It enables machine builders to provide new services to machine operators for each installed machine in any production site worldwide.

It provides features like:

- Leverage the power and security of Schneider Electric’s private MS Azure Cloud
- Complete online documention repository
- Access your machine data anytime and anywhere uniquely from your laptop or mobile device
- Plan and register onsite interventions of your serial machines in less than 5 minutes
- Use your own gateway to send data from your machine (compatible with multi-vendor control systems and compatible with architectures without control system)
- Can’t connect your machine to the cloud? No problem: upload your data directly to EcoStruxure™ Machine Advisor via a .csv file!
- Start and stop anytime to upload your machine data to EcoStruxure™ Machine Advisor
- Make EcoStruxure™ Machine Advisor your own digital services platform and provide digital services to your customers for any installed machine from everywhere

You can register for a free trial account here:

- https://machine-advisor.schneider-electric.com/welcome

### Logging configuration

The variables to be logged are registered in the setup, and all the rest is done automatically calling the update method. The variables should be always INT.

Example: machineLog.registerVar("voltage", &volt, 5000, 20, 30000);

- "voltage": Name of the variable that will appear in Machine Advisor
- &volt: Memory address of global variable volt.
- 5000: Minimum sampling period in ms, in the example 5s. If set to 0, or very small, should be combined with a threshold.
- 20: (Optional) Threshold. The variable only will be logged if the change is bigger than the threshold.
- 30000: (Optional) Maximum sampling period in ms. If the variable has not been sampled in the last 30s, it is sampled unconditionally.

### Conection configuration

To configure the library, some conection information should be copied from Machine Advisor.

In the example, three strings should be provided:

- machineSend.setConnexionString(**MACHINEBROKERURL**, **MACHINECLIENTID**, **MACHINEPASSWORD**);

![Conection image](Conection.png)

### TODO List

- [ ] Add logging system to SD to make the off-line buffer much bigger
- [ ] Add deep-sleep/wake-up to reduce battery consumtion
- [ ] Document the class methods using std documentation system
- [ ] Create a Platformio Library
- [ ] Be able to download the data in JSON
- [ ] Create a GraphQL connector
- [ ] Add basic filtering to the signals (Use external library)


## Author
Xavi Armengol
