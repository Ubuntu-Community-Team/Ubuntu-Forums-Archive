---
title: "cpu temperature readings never change"
date: 2011-12-18
forum: Server Platforms
---

### Post by brighty22 on 2011-12-18
Hi,

I assembled a home server in July, initially with FreeNAS on but then Ubuntu Server 11.04. The CPU temperatures reported by both have never read anything other than 45 and 39C (whether it's immediately after booting, or when the server has been running for days). I've been noticing it for a while, but haven't done anything about it until now. This is the output from the lm-sensors utility:

```
george@bright2a:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +45.0°C  (high = +76.0°C, crit = +100.0°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +39.0°C  (high = +76.0°C, crit = +100.0°C)

it8718-isa-0290
Adapter: ISA adapter
in0:         +1.07 V  (min =  +0.00 V, max =  +4.08 V)
in1:         +1.81 V  (min =  +0.00 V, max =  +4.08 V)
in2:         +3.33 V  (min =  +0.00 V, max =  +4.08 V)
+5V:         +2.91 V  (min =  +0.00 V, max =  +4.08 V)
in4:         +0.58 V  (min =  +0.00 V, max =  +2.10 V)
in5:         +4.08 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in6:         +4.08 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in7:         +3.06 V  (min =  +0.00 V, max =  +4.08 V)
Vbat:        +3.22 V
fan1:       1144 RPM  (min =   10 RPM)
fan2:       1218 RPM  (min =   10 RPM)
temp1:       -55.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:        -2.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp3:       +18.0°C  (low  = +127.0°C, high = +60.0°C)  sensor = thermal diode
cpu0_vid:   +3.300 V


```

The temperatures report correctly (well... they change) in the BIOS... what could be wrong?

Thanks for any help :)

---

