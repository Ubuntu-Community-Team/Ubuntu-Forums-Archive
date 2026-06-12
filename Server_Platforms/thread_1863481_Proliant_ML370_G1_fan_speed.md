---
title: "Proliant ML370 G1 fan speed"
date: 2011-10-17
forum: Server Platforms
---

### Post by arcane^ on 2011-10-17
I have recently acquired a Compaq/HP Proliant ML370 generation 1 server and installed server 10.04 on it. Everything so far has worked flawlessly except that the fan at the rear of the server which I believe is responsible for the cooling of the CPU is running at full speed constantly which is so noisy it is driving the entire household nuts :(. I have tried the smartstart 5.05 server disc to inspect the BIOS in an attempt to find a setting that controls fan speed but there doesn't appear to be one (g2-g4 all have an option in BIOS but g1 does not). acpi -V states:

acpi -V
Thermal 0: ok, 8.3 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 31.3 degrees C
Thermal 0: trip point 1 switches to mode passive at temperature 9.8 degrees C
Cooling 0: Processor 0 of 0

8.3 C is obviously not correct... 

Is there anyway to control the fan speed using drivers or some kind of support pack? If I cannot get any answers here I'll consider slowing it down by adding resistors to the power supply cables but I'm fairly sure it will throw an error.. please help :)

---

### Post by SMarcB on 2013-01-18
Have you found an answer to this anywhere? I have the EXACT same problem. That fan makes the server rack sound like a wind tunnel. I tried using an aftermarket CoolerMaster fan by converting the plug, and the BIOS does not recognize the fan as being plugged in, and shuts down.

---

