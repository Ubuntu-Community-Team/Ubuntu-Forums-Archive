---
title: "lmsensors snmp doesn't work after dist-upgrade"
date: 2010-05-05
forum: Server Platforms
---

### Post by batsi on 2010-05-05
Hello altogehter,

I have a small problem with lmsensors and snmp since I upgraded my small server from 9.10 to 10.04.

I use cacti to monitor my servers usage, disk space as well as temps and fans.
This was running very fine before the upgrade, but now I don't get data anymore from lmsensors.
It seems that SNMP doesn't give this information as before. (Cacti log says: "*No sensor data was returned from SNMP*")

**sensors **give the following output:

```

w83627dhg-isa-0290
Adapter: ISA adapter
Vcore:       +1.12 V  (min =  +0.00 V, max =  +1.74 V)
AVCC:        +3.41 V  (min =  +2.98 V, max =  +3.63 V)
VCC:         +3.41 V  (min =  +2.98 V, max =  +3.63 V)
3VSB:        +3.49 V  (min =  +2.98 V, max =  +3.63 V)
Vbat:        +3.31 V  (min =  +2.70 V, max =  +3.30 V)   ALARM
Case Fan:   1140 RPM  (min =  852 RPM, div = 16)
CPU Fan:     948 RPM  (min =  852 RPM, div = 16)
Sys Temp:    +32.0°C  (high = +55.0°C, hyst = +50.0°C)  sensor = thermistor
CPU Temp:    +31.0°C  (high = +55.0°C, hyst = +50.0°C)  sensor = thermistor
AUX Temp:    +44.5°C  (high = +55.0°C, hyst = +50.0°C)  sensor = thermistor
```but the output of **snmpwalk -v1 -c public localhost lmsensors** is just this:
```

LM-SENSORS-MIB::lmVoltSensorsIndex.1 = INTEGER: 0
LM-SENSORS-MIB::lmVoltSensorsIndex.2 = INTEGER: 1
LM-SENSORS-MIB::lmVoltSensorsIndex.3 = INTEGER: 2
LM-SENSORS-MIB::lmVoltSensorsIndex.4 = INTEGER: 3
LM-SENSORS-MIB::lmVoltSensorsDevice.1 = STRING: Vcore
LM-SENSORS-MIB::lmVoltSensorsDevice.2 = STRING: Vcore
LM-SENSORS-MIB::lmVoltSensorsDevice.3 = STRING: Vcore
LM-SENSORS-MIB::lmVoltSensorsDevice.4 = STRING: Vcore
LM-SENSORS-MIB::lmVoltSensorsValue.1 = Gauge32: 1120
LM-SENSORS-MIB::lmVoltSensorsValue.2 = Gauge32: 0
LM-SENSORS-MIB::lmVoltSensorsValue.3 = Gauge32: 1744
LM-SENSORS-MIB::lmVoltSensorsValue.4 = Gauge32: 0
```and that's a bit few.

Does anyone have an idea if this is a bug or if this is a feature in course of the release upgrade?
Is this a problem in snmpd/MIBs or in lmsensors?
Or am I just to stupid to configure everything as before?

---

### Post by 8Kuula on 2010-05-16
sensors
```
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.17 V  (min =  +0.85 V, max =  +1.60 V)
 +3.3 Voltage:      +3.26 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:        +4.97 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:      +12.15 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:      878 RPM  (min =  600 RPM)
CHASSIS1 FAN Speed:   0 RPM  (min =  600 RPM)
CHASSIS2 FAN Speed:   0 RPM  (min =  600 RPM)
POWER FAN Speed:      0 RPM  (min =  600 RPM)
CPU Temperature:    +45.0°C  (high = +60.0°C, crit = +95.0°C)  
MB Temperature:     +42.0°C  (high = +45.0°C, crit = +95.0°C)  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +38.0°C  (high = +86.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +43.0°C  (high = +86.0°C, crit = +100.0°C)
```
snmpwalk -v2c -c public localhost lm
```
LM-SENSORS-MIB::lmVoltSensorsIndex.1 = INTEGER: 0
LM-SENSORS-MIB::lmVoltSensorsIndex.2 = INTEGER: 1
LM-SENSORS-MIB::lmVoltSensorsIndex.3 = INTEGER: 2
LM-SENSORS-MIB::lmVoltSensorsDevice.1 = STRING: Vcore Voltage
LM-SENSORS-MIB::lmVoltSensorsDevice.2 = STRING: Vcore Voltage
LM-SENSORS-MIB::lmVoltSensorsDevice.3 = STRING: Vcore Voltage
LM-SENSORS-MIB::lmVoltSensorsValue.1 = Gauge32: 1168
LM-SENSORS-MIB::lmVoltSensorsValue.2 = Gauge32: 850
LM-SENSORS-MIB::lmVoltSensorsValue.3 = Gauge32: 1600
LM-SENSORS-MIB::lmMiscSensorsIndex.1 = INTEGER: 0
LM-SENSORS-MIB::lmMiscSensorsIndex.2 = INTEGER: 1
LM-SENSORS-MIB::lmMiscSensorsIndex.3 = INTEGER: 2
LM-SENSORS-MIB::lmMiscSensorsIndex.4 = INTEGER: 3
LM-SENSORS-MIB::lmMiscSensorsIndex.5 = INTEGER: 4
LM-SENSORS-MIB::lmMiscSensorsIndex.6 = INTEGER: 5
LM-SENSORS-MIB::lmMiscSensorsIndex.7 = INTEGER: 6
LM-SENSORS-MIB::lmMiscSensorsIndex.8 = INTEGER: 7
LM-SENSORS-MIB::lmMiscSensorsDevice.1 = STRING: Core 0
LM-SENSORS-MIB::lmMiscSensorsDevice.2 = STRING: Core 0
LM-SENSORS-MIB::lmMiscSensorsDevice.3 = STRING: Core 0
LM-SENSORS-MIB::lmMiscSensorsDevice.4 = STRING: Core 0
LM-SENSORS-MIB::lmMiscSensorsDevice.5 = STRING: Core 1
LM-SENSORS-MIB::lmMiscSensorsDevice.6 = STRING: Core 1
LM-SENSORS-MIB::lmMiscSensorsDevice.7 = STRING: Core 1
LM-SENSORS-MIB::lmMiscSensorsDevice.8 = STRING: Core 1
LM-SENSORS-MIB::lmMiscSensorsValue.1 = Gauge32: 38000
LM-SENSORS-MIB::lmMiscSensorsValue.2 = Gauge32: 86000
LM-SENSORS-MIB::lmMiscSensorsValue.3 = Gauge32: 100000
LM-SENSORS-MIB::lmMiscSensorsValue.4 = Gauge32: 0
LM-SENSORS-MIB::lmMiscSensorsValue.5 = Gauge32: 43000
LM-SENSORS-MIB::lmMiscSensorsValue.6 = Gauge32: 86000
LM-SENSORS-MIB::lmMiscSensorsValue.7 = Gauge32: 100000
LM-SENSORS-MIB::lmMiscSensorsValue.8 = Gauge32: 0
```

Hmm, for me snmp seems to show core temperatures in lmMiscSensors (1 and 5).
CPU Temperature won't show anywhere, neither do MB Temperature.

Something wierd...

Edit: In clean install Ubuntu 10.04 server 64bit.

---

### Post by kylegordon on 2010-05-16
Hi,

I'm also experiencing this issue. I suspect it might be a bug, so will be opening a bug report this evening.

Regards

Kyle

---

### Post by batsi on 2010-06-10
Hi folks, 

are there any news about this, or has someone already opened a bug report?
Otherwise I'd report this bug, as I would really like to monitor my servers temperatures again (without tweaking).

Batsi


edit:
just found it: [https://bugs.launchpad.net/ubuntu/+source/net-snmp/+bug/506865](https://bugs.launchpad.net/ubuntu/+source/net-snmp/+bug/506865)

---

