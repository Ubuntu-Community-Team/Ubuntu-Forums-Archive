---
title: "Measuring CPU/mobo temps?"
date: 2009-04-22
forum: Server Platforms
---

### Post by submute on 2009-04-22
What's a good Ubuntu package to accomplish this? Some preliminary Googling returned something about lm_sensors-- is this part of some Ubuntu package, or is there a better method?

Thanks!

---

### Post by fjgaude on 2009-04-22
**lm_sensors** is what many of us use... read the man pages after you install and all will be clear. It's pretty cool once you add it to your panel and show all the temps, voltages, etc., for your box.

Or if you don't use a GUI, just running "sensors" from the command line shows all. Does take a little bit of a custom setup for your particular motherboard. Here's mine:

```
frank@sunshine:~$ sensors
it8718-isa-0290
Adapter: ISA adapter
VCore:       +1.28 V  (min =  +1.01 V, max =  +1.46 V)   
VDDR:        +2.21 V  (min =  +1.81 V, max =  +2.40 V)   
+3.3V:       +3.33 V  (min =  +3.14 V, max =  +3.47 V)   
+5V:         +5.08 V  (min =  +4.76 V, max =  +5.24 V)   
5VSB:        +5.19 V  (min =  +4.76 V, max =  +5.24 V)   
VBat:        +3.26 V
CPU Fan:     969 RPM  (min =    0 RPM)
Front Fan:  1510 RPM  (min =    0 RPM)
PS Fan:     1178 RPM  (min =    0 RPM)
Back Fan:   1394 RPM  (min =    0 RPM)
M/B Temp:    +43.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = transistor
CPU Temp:    +27.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
cpu0_vid:   +2.050 V

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +36.0°C  (high = +78.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +30.0°C  (high = +78.0°C, crit = +100.0°C)
```

Good sensoring!

---

