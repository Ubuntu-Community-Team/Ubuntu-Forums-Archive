---
title: "Fan speed reads zero, can't change divisor"
date: 2011-10-12
forum: Server Platforms
---

### Post by David Ress on 2011-10-12
Greetings,

I'm new to Ubuntu, but I have some general experience with other flavors of Unix.

We put together a quad-cpu server with a set 8-core AMD cpus. The motherboard is a Supermicro (one of the few that supports quad cpus). With some work, we can now read out voltages and temperatures in Ubuntu. However, the fan speeds on the mobo all read zero. Here is the output of sensors:

k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +32.5°C  (high = +70.0°C, crit = +70.0°C)  

k10temp-pci-00cb
Adapter: PCI adapter
temp1:       +32.5°C  (high = +70.0°C)                  

k10temp-pci-00d3
Adapter: PCI adapter
temp1:       +32.0°C  (high = +70.0°C, crit = +70.0°C)  

k10temp-pci-00db
Adapter: PCI adapter
temp1:       +30.4°C  (high = +70.0°C)                  

k10temp-pci-00e3
Adapter: PCI adapter
temp1:       +35.5°C  (high = +70.0°C, crit = +70.0°C)  

k10temp-pci-00eb
Adapter: PCI adapter
temp1:       +35.0°C  (high = +70.0°C)                  

k10temp-pci-00f3
Adapter: PCI adapter
temp1:       +28.0°C  (high = +70.0°C, crit = +70.0°C)  

k10temp-pci-00fb
Adapter: PCI adapter
temp1:       +28.0°C  (high = +70.0°C)                  

w83627ehf-isa-0290
Adapter: ISA adapter
Vcore:          +2.04 V  (min =  +2.04 V, max =  +2.04 V)   ALARM
in1:            +2.04 V  (min =  +2.04 V, max =  +2.04 V)   ALARM
AVCC:           +4.08 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
VCC:            +4.08 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
in4:            +2.04 V  (min =  +2.04 V, max =  +2.04 V)   ALARM
in5:            +2.04 V  (min =  +2.04 V, max =  +2.04 V)   ALARM
in6:            +2.04 V  (min =  +2.04 V, max =  +2.04 V)   ALARM
3VSB:           +4.08 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
Vbat:           +4.08 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
in9:            +2.04 V  (min =  +2.04 V, max =  +2.04 V)   ALARM
Fan1 Fan Speed:   0 RPM  (min =    0 RPM, div = 128)  ALARM
Fan1 Fan Speed:   0 RPM  (min =    0 RPM, div = 128)  ALARM
Fan3 Fan Speed:   0 RPM  (min =    0 RPM, div = 128)  ALARM
Fan4 Fan Speed:   0 RPM  (min =    0 RPM, div = 128)  ALARM
temp1:           -1.0°C  (high =  -1.0°C, hyst =  -1.0°C)  ALARM  sensor = diode
temp2:           +0.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = diode
temp3:           +0.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = diode
cpu0_vid:      +0.375 V


The doc suggests changing the divisors, but when I edit the relevant lines in  /etc/sensors.d/sensors.conf and then run sensors -s, I get the following errors:

Error: File /etc/sensors.d/sensors.conf, line 286: Failed to set value
Error: File /etc/sensors.d/sensors.conf, line 287: Failed to set value
Error: File /etc/sensors.d/sensors.conf, line 288: Failed to set value
Error: File /etc/sensors.d/sensors.conf, line 289: Failed to set value
Error: File /etc/sensors.d/sensors.conf, line 291: Unknown feature name
Error: File /etc/sensors.d/sensors.conf, line 292: Unknown feature name
Error: File /etc/sensors.d/sensors.conf, line 293: Unknown feature name
Error: File /etc/sensors.d/sensors.conf, line 294: Unknown feature name

These lines each refer to one of the four fans: fan1, fan2, fan3, and fan4, setting first the divisor, then the max speed:
    set fan1_div 8
    set fan2_div 8
    set fan3_div 8
    set fan4_div 8
    
    set fan1_max 800
    set fan2_max 800
    set fan3_max 800
    set fan4_max 800

I have searched but find no information on why this could be failing.

Suggestions greatly appreciated!

Thanks,
DR

---

