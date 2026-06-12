---
title: "Sensors returns negative temperatures intermittently"
date: 2016-07-19
forum: Server Platforms
---

### Post by scott.bouch on 2016-07-19
Results from **sensors**

These temperatures are quite normal to see, whilst I'd like to see them cooler, I don't have an air conditioned server room, just my garage:

```

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +99.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:       +93.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       +94.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:       +94.0°C  (high = +84.0°C, crit = +100.0°C)


coretemp-isa-0001
Adapter: ISA adapter
Core 0:      +100.0°C  (high = +84.0°C, crit = +100.0°C)  ALARM (CRIT)
Core 1:       +93.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       +96.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:       +98.0°C  (high = +84.0°C, crit = +100.0°C)  ALARM (CRIT)



```


Notice how ISA-0001 Core 0 has gone negative, it sometimes does this intermittently:
```
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +99.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:       +93.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       +94.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:       +94.0°C  (high = +84.0°C, crit = +100.0°C)


coretemp-isa-0001
Adapter: ISA adapter
**Core 0:       -27.0°C**  (high = +84.0°C, crit = +100.0°C)  ALARM (CRIT)
Core 1:       +94.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       +96.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:       +97.0°C  (high = +84.0°C, crit = +100.0°C)  ALARM (CRIT)




```

Any ideas? Could the core temperature be going over +100°C, and sensors just cant handle that number? Or it it likely to be the processor shutting down as it's temperature has gone above CRIT? (the upper readings show it at 100°C)

The temperature isn't always -27, here it's -25:

```
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +95.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:       +92.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       +93.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:       +93.0°C  (high = +84.0°C, crit = +100.0°C)


coretemp-isa-0001
Adapter: ISA adapter
**Core 0:       -25.0°C ** (high = +84.0°C, crit = +100.0°C)  ALARM (CRIT)
Core 1:       +93.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       +95.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:       +96.0°C  (high = +84.0°C, crit = +100.0°C)  ALARM (CRIT)

```


when it's gone to negative temperature I've tried **lscpu** to see if the core was going offline, but it appears ok:

```
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                8
On-line CPU(s) list:   0-7
Thread(s) per core:    1
Core(s) per socket:    4
Socket(s):             2
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 23
Stepping:              6
CPU MHz:               2003.000
BogoMIPS:              4666.93
Virtualisation:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              6144K
NUMA node0 CPU(s):     0-7

```
The machine is a DELL CS24-SC 1U high server with INTEL XEON E5410 processors. I've previously discussed other temperature related issues here: [https://ubuntuforums.org/showthread.php?t=2314878 ]("https://ubuntuforums.org/showthread.php?t=2314878")



Thanks, Scott.

---

### Post by scott.bouch on 2016-07-19
Ambient temperature in the garage has soared up to +35 and the server has shutdown. This is HOT for England!

But can anyone identify the issue with **Sensors**?

Thanks, Scott.

---

### Post by QIII on 2016-07-19
Hello!

Is the odd temperature reading always on the same core?

---

### Post by scott.bouch on 2016-07-19
Yes, the hottest one... I've not seen it on other cores yet.

Thanks, Scott.

---

### Post by QIII on 2016-07-19
OK.

If the temp were dropping to something reasonable, I'd say it was throttling due to temperature and might suggest replacing the thermal compound to see if you are not getting good contact at a particular spot on the CPU cap.  Since this is clearly out of range, it is a hardware issue rather than sensors.  Sensors can only report what the hardware is reporting.  If sensors were at fault, all of your cores would show questionable readings.

If your CPUs have been running that hot in that environment for any time at all, they have encountered thermal damage -- this being an indicator of that.  It is not "safe" to run electronic devices at just under their thermal limits for a long period of time.  Perhaps the damage won't occur suddenly and catastrophically.  But it will occur.

Before you do anything further, you MUST rectify the heat/environment issue.

Failing that, you will eventually have a catastrophic failure, if yyou haven't already.  Sensors is working correctly and you need to make the right interpretation.

---

### Post by scott.bouch on 2016-07-19
Thank you.. you kind of confirmed what I was suspecting...

I have the server in a sealed cabinet (industrial electrical control system Rittal panel) with filtered fan ventilation through it. 

It really needs air conditioning in weather like this to cool the ambient air of the cabinet, or I maybe should look into liquid cooling the processors... they always have been hotter than I'd have liked, I previously did manage to cool it down a bit by cleaning it out and replacing heatsink compound, but on a day like today, it just gives up.

It's off now until the weather cools down a touch. Trouble is the location too, in an un-insulated garage with a flat roof, it just bakes when the sun shines on it.

I guess when manufacturers design server computers, they expect them to go into air conditioned server rooms, not hot garages. A regular household PC may fair better...

Thanks, Scott

---

### Post by scott.bouch on 2016-07-20
Turns out that yesterday was the hottest day of 2016 in the UK.. no wonder it struggled...

When it cools down a bit I need to look into the performance of all 8 cores, as I might have lost one as you say.

Cheers, Scott

---

### Post by scott.bouch on 2016-07-20
Hmm... well, garage temperature has been lower today (30 degrees C), so I thought I'd try again.... only one core out of 8 not at CRIT temperature.

```
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       -26.0°C  (high = +84.0°C, crit = +100.0°C)  ALARM (CRIT)
Core 1:       +96.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       +98.0°C  (high = +84.0°C, crit = +100.0°C)  ALARM (CRIT)
Core 3:       +97.0°C  (high = +84.0°C, crit = +100.0°C)  ALARM (CRIT)


coretemp-isa-0001
Adapter: ISA adapter
Core 0:        +3.0°C  (high = +84.0°C, crit = +100.0°C)  ALARM (CRIT)
Core 1:       -18.0°C  (high = +84.0°C, crit = +100.0°C)  ALARM (CRIT)
Core 2:       -14.0°C  (high = +84.0°C, crit = +100.0°C)  ALARM (CRIT)
Core 3:       -13.0°C  (high = +84.0°C, crit = +100.0°C)  ALARM (CRIT)
```



```
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       -26.0°C  (high = +84.0°C, crit = +100.0°C)  ALARM (CRIT)
Core 1:       +96.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       -26.0°C  (high = +84.0°C, crit = +100.0°C)  ALARM (CRIT)
Core 3:       +99.0°C  (high = +84.0°C, crit = +100.0°C)  ALARM (CRIT)


coretemp-isa-0001
Adapter: ISA adapter
Core 0:        +2.0°C  (high = +84.0°C, crit = +100.0°C)  ALARM (CRIT)
Core 1:       -18.0°C  (high = +84.0°C, crit = +100.0°C)  ALARM (CRIT)
Core 2:       -13.0°C  (high = +84.0°C, crit = +100.0°C)  ALARM (CRIT)
Core 3:       -12.0°C  (high = +84.0°C, crit = +100.0°C)  ALARM (CRIT)
```

This time much worse than yesterday on the hottest day.

It still served my web pages ok.. but i think I'll give it a few more days to cool off.

The second processor is all wacky this time, and the first is only just better.... hmmm... hope I've not killed it....

cheers, Scott

---

