---
title: "lm_sensors and CPU temps"
date: 2009-12-09
forum: Server Platforms
---

### Post by submute on 2009-12-09
Below is my lm_sensors dump. I'm trying to figure out what are the temps of my CPU, and therefore what I need to worry about and graph w/ Cacti. Is it the k8temp output, or the output of it8718 temp1, temp2, and temp3?

Thanks for clearing this up.

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +22.0°C                                    
Core0 Temp:  +23.0°C                                    
Core1 Temp:  +25.0°C                                    
Core1 Temp:  +25.0°C                                    

it8718-isa-0228
Adapter: ISA adapter
in0:         +0.99 V  (min =  +0.00 V, max =  +4.08 V)   
in1:         +1.95 V  (min =  +0.00 V, max =  +4.08 V)   
in2:         +3.30 V  (min =  +0.00 V, max =  +4.08 V)   
in3:         +2.96 V  (min =  +0.00 V, max =  +4.08 V)   
in4:         +3.10 V  (min =  +0.00 V, max =  +4.08 V)   
in5:         +3.17 V  (min =  +0.00 V, max =  +4.08 V)   
in6:         +4.08 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in7:         +3.30 V  (min =  +0.00 V, max =  +4.08 V)   
in8:         +3.23 V
fan1:       1147 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
temp1:       +30.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:       +23.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:       +63.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor

---

### Post by craigp84 on 2009-12-10
Hi,

Looks like it's the k8temp for CPU.

The it8718 readings look like motherboard readouts. North bridge, south bridge and something else i'd guess. The fan readings will correspond with fans connected to the motherboard.

---

