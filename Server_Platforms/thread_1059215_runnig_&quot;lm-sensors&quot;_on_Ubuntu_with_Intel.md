---
title: "runnig &quot;lm-sensors&quot; on Ubuntu with Intel G31 motherboard"
date: 2009-02-03
forum: Server Platforms
---

### Post by zeevikn on 2009-02-03
When runnig "lm-sensors" on Ubuntu with Intel G31 motherboard, I get weird results.
```

# sensors
w83627dhg-isa-0290
Adapter: ISA adapter
VCore:       +1.14 V  (min =  +0.00 V, max =  +1.74 V)
in1:        +10.72 V  (min = +12.62 V, max = +13.46 V)   ALARM
AVCC:        +3.30 V  (min =  +4.08 V, max =  +3.70 V)   ALARM
3VCC:        +3.30 V  (min =  +4.08 V, max =  +3.06 V)   ALARM
in4:         +1.83 V  (min =  +1.81 V, max =  +1.04 V)   ALARM
in5:         +1.26 V  (min =  +2.00 V, max =  +1.53 V)   ALARM
in6:         +0.38 V  (min =  +6.48 V, max =  +1.59 V)   ALARM
VSB:         +3.28 V  (min =  +0.75 V, max =  +3.02 V)   ALARM
VBAT:        +3.17 V  (min =  +2.03 V, max =  +2.18 V)   ALARM
Case Fan:      0 RPM  (min =    0 RPM, div = 16)
CPU Fan:     827 RPM  (min = 2678 RPM, div = 8)  ALARM
Aux Fan:       0 RPM  (min =  958 RPM, div = 128)  ALARM
fan4:          0 RPM  (min = 10546 RPM, div = 128)  ALARM
fan5:          0 RPM  (min = 10546 RPM, div = 128)  ALARM
Sys Temp:    +81.0°C  (high = +63.0°C, hyst = +62.0°C)  ALARM  sensor = diode
CPU Temp:    +18.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
AUX Temp:   +119.0°C  (high = +80.0°C, hyst = +75.0°C)  ALARM  sensor = thermistor
cpu0_vid:   +2.050 V
#
```

Any suggestions ?
Should I ignore the invalid results ?
My main concern for running the lm-sensors is the temp.
Should I use another method for that ?

Thanks,
Zeevik.

---

### Post by tubezninja on 2009-02-04
I get the same alarms with the Intel G31.   The driver that lm-sensors is using apparently doesn't have the right voltage values for the sensors in this motherboard.  There may be another driver that's a better fit, but I haven't found it yet and unfortunately, it just hasn't been a priority in my case.  Considering I have boxes with this motherboard running for nearly a year without ill effect, it's really nothing to be concerned about.

There's even one sensor in my case that gets its temp read as negative value.  I only WISH! :D

Here's my output, just for grins:

```
acpitz-virtual-0
Adapter: Virtual device
temp1:       -75.0°C  (crit = +75.0°C)                  

it8718-isa-0290
Adapter: ISA adapter
in0:         +1.25 V  (min =  +2.93 V, max =  +1.01 V)   ALARM
in1:         +1.23 V  (min =  +4.06 V, max =  +3.95 V)   ALARM
in2:         +3.26 V  (min =  +2.03 V, max =  +2.02 V)   ALARM
in3:         +2.93 V  (min =  +3.31 V, max =  +4.06 V)   ALARM
in4:         +2.98 V  (min =  +3.82 V, max =  +1.94 V)   ALARM
in5:         +0.77 V  (min =  +0.00 V, max =  +4.08 V)   
in6:         +1.84 V  (min =  +4.02 V, max =  +4.08 V)   ALARM
in7:         +2.93 V  (min =  +0.00 V, max =  +3.04 V)   
in8:         +3.23 V
fan1:       1331 RPM  (min =   10 RPM)
temp1:       -53.0°C  (low  = +111.0°C, high = -100.0°C)  ALARM  sensor = transistor
temp2:       +47.0°C  (low  =  -1.0°C, high =  -9.0°C)  sensor = thermal diode
temp3:       +33.0°C  (low  = -49.0°C, high = +127.0°C)  sensor = transistor
cpu0_vid:   +0.000 V

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +52.0°C  (high = +82.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +43.0°C  (high = +82.0°C, crit = +100.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +43.0°C  (high = +82.0°C, crit = +100.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +48.0°C  (high = +82.0°C, crit = +100.0°C)
```

---

### Post by zeevikn on 2009-02-04
Thanks for the reply.

My main concern is the temp issues. I want to verify that the CPU does not get over heated.
Can I count on the CPU readings ?
(It looks fine, but I just want to know I can count on).

Zeevik.

another small note: I see that you have a reading per core.
My CPU is dual core, but yet, I get only one reading.
Does this imply on working with a "wrong" driver ?

---

### Post by gilloz on 2009-02-05
Have you tried going to the Other Community Discussions forum to Tutorial & Tips, then go to the 3rd page and look for the Thread "Install & Configure lm-sensors" by Emperor.  See if that is of any help.

---

### Post by fjgaude on 2009-02-05
My Gigabye board and lm-syensors had to have some tweaking done to get this:

frank@sunshine:~$ sensors
it8718-isa-0290
Adapter: ISA adapter
VCore:       +1.33 V  (min =  +1.01 V, max =  +1.46 V)   
VDDR:        +2.13 V  (min =  +1.81 V, max =  +2.40 V)   
+3.3V:       +3.33 V  (min =  +3.14 V, max =  +3.47 V)   
+5V:         +5.05 V  (min =  +4.76 V, max =  +5.24 V)   
+12V:        +0.13 V  (min = +11.39 V, max = +12.61 V)   ALARM
5VSB:        +5.19 V  (min =  +4.76 V, max =  +5.24 V)   
VBat:        +3.26 V
CPU Fan:     924 RPM  (min =    0 RPM)
Front Fan:  1081 RPM  (min =    0 RPM)
PS Fan:     1211 RPM  (min =    0 RPM)
Back Fan:   1171 RPM  (min =    0 RPM)
M/B Temp:    +38.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = transistor
CPU Temp:    +23.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
cpu0_vid:   +2.050 V

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +33.0°C  (high = +78.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +27.0°C  (high = +78.0°C, crit = +100.0°C)  
---

My Intel E8400 is overclocked to 4.0GH.

I'm a happy camper.

---

### Post by redroad55 on 2009-02-05
until you get the work around figured out the system BIOS should report your temps and give you fan speed adj. ..take readings there after a hard run and adj. fan speed accordingly .. at least you will sleep better until you find the right work around .. Best to you

---

### Post by graysky on 2009-04-11
> **fjgaude said:**
> My Gigabye board and lm-syensors had to have some tweaking done to get this:

frank@sunshine:~$ sensors
it8718-isa-0290
Adapter: ISA adapter
VCore:       +1.33 V  (min =  +1.01 V, max =  +1.46 V)   
VDDR:        +2.13 V  (min =  +1.81 V, max =  +2.40 V)   
+3.3V:       +3.33 V  (min =  +3.14 V, max =  +3.47 V)   
+5V:         +5.05 V  (min =  +4.76 V, max =  +5.24 V)   
+12V:        +0.13 V  (min = +11.39 V, max = +12.61 V)   ALARM
5VSB:        +5.19 V  (min =  +4.76 V, max =  +5.24 V)   
VBat:        +3.26 V
CPU Fan:     924 RPM  (min =    0 RPM)
Front Fan:  1081 RPM  (min =    0 RPM)
PS Fan:     1211 RPM  (min =    0 RPM)
Back Fan:   1171 RPM  (min =    0 RPM)
M/B Temp:    +38.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = transistor
CPU Temp:    +23.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
cpu0_vid:   +2.050 V

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +33.0°C  (high = +78.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +27.0°C  (high = +78.0°C, crit = +100.0°C)  
---

My Intel E8400 is overclocked to 4.0GH.

I'm a happy camper.

How did you know which temp reading to call "M/B Temp"?  Please see [my post here](http://ubuntuforums.org/showthread.php?t=1122514) and help if you can :)

---

### Post by Arup on 2009-04-18
I have installed lm-sensors on Intel DG31PR board and I have no such issues, all the figures match whats shown in BIOS, I use Gkrellm to monitor and have also installed hddtemp.

---

