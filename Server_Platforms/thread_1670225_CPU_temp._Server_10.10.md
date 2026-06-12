---
title: "CPU temp. Server 10.10"
date: 2011-01-18
forum: Server Platforms
---

### Post by idny on 2011-01-18
Hi guys,

Been looking for a answer on google, but it appears im alone in this one.

Right i got my server running
installed lm sensors.

and when i type sensors i get this.

```
harvey@Taxman:/$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +52.0Â°C  (high = +84.0Â°C, crit = +100.0Â°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +56.0Â°C  (high = +84.0Â°C, crit = +100.0Â°C)

it8718-isa-0290
Adapter: ISA adapter
in0:         +1.14 V  (min =  +0.00 V, max =  +4.08 V)
in1:         +1.86 V  (min =  +0.00 V, max =  +4.08 V)
in2:         +3.33 V  (min =  +0.00 V, max =  +4.08 V)
in3:         +3.02 V  (min =  +0.00 V, max =  +4.08 V)
in4:         +0.64 V  (min =  +0.00 V, max =  +2.10 V)
in5:         +4.08 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in6:         +4.08 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in7:         +3.07 V  (min =  +0.00 V, max =  +4.08 V)
Vbat:        +3.10 V
fan1:       2616 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
temp1:       -55.0Â°C  (low  = +127.0Â°C, high = +127.0Â°C)  sensor = thermistor
temp2:        -2.0Â°C  (low  = +127.0Â°C, high = +127.0Â°C)  sensor = thermistor
temp3:       +28.0Â°C  (low  = +127.0Â°C, high = +127.0Â°C)  sensor = thermal diode
cpu0_vid:   +1.325 V
```

To me its pretty much unreadable. I cant understand the temp on the CPU. How can i change this format?

Thanks

---

### Post by idny on 2011-01-19
bumping for helppp

---

### Post by dargaud on 2011-01-19
What's the problem ? One core is at 52C, the other one at 56C and they are fairly healthy temperatures. On the other hand temp1/2/3 don't make sense: they are probably chipset temperatures, but then the chipset is probably not recognized properly. Maybe check the BIOS settings.

---

### Post by idny on 2011-01-19
thanks for the reply.

Well i reboot the system and checked the BIOS (server has been running 24/7 for 3 days) so the CPU was still hot, the BIOS reads 35C, then loads into ubuntu with a minute a then i ran sensors.
The CPU can't have risens 17C in a minute with hardly any load. This makes me believe its incorrect.

---

### Post by disabledaccount on 2011-01-20
> **idny said:**
> Well i reboot the system and checked the BIOS (server has been running 24/7 for 3 days) so the CPU was still hot, the BIOS reads 35C, then loads into ubuntu with a minute a then i ran sensors.
The CPU can't have risens 17C in a minute with hardly any load. This makes me believe its incorrect.Nothing strange, really. CPU temp can change very quickly, like 20deg C within several seconds. It's important to know, that CPU thermal diodes (sensors) are very inacurate - they introduce high nonlinearity together with high scatter of gain and offset. You should perceive them as thermal protection, not temperature measuring devices.

Idle temp of todays CPUs is usually below 40deg C (Idle = nearly 0% load, non-OC, power saving functions enabled). If You have more than ~45 in idle, then it can be due to cooling problems (dust, bad heat spreader or improperly mounted, damaged fan, too high ambient temp, etc)

---

### Post by idny on 2011-01-20
ok. I guess that makes more sense.

One more small question.
When i check in my BIOS is gives me the current temp and the next to it says
High = 60C   Crit = 90C

but then on the sensors output it reads High = 84C Crit =100C

How comes these values are different? As im guessing they borders/limits and not actual readings.

---

### Post by disabledaccount on 2011-01-20
Normally, those values are corresponding to **alarm level** (you should hear beeping from pc-speaker, often it's also reported by ACPI thermal alert) and **automatic turn-off level** - your PC will shut down. Real behaviour depends on more or less buggy bios and OS - it is possible to override ACPI settings (in most cases).

Difference between BIOS values and lm_sensors comes from the fact, that BIOS uses special algorithms to correct nonlinearity of sensors (a little) - You can do the same in lm_sensors config.

---

