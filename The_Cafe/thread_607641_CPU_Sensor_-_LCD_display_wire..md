---
title: "CPU Sensor - LCD display wire."
date: 2007-11-09
forum: The Cafe
---

### Post by Perfect Storm on 2007-11-09
Greetings,

I've bought a NZXT SENTRY 1 Accessories/LCD Controller ([http://www.nzxt.com/products/sentry_1/](http://www.nzxt.com/products/sentry_1/)). What I like to know is; Where do I set the CPU sensor wire to an AM2 CPU? 
[img]http://bilder3.guenstiger.de/prodfoto/amdathlon64x26000.jpg[/img]
In the manual it explain for all other CPU types, but not the AM2. The wire most not be on the chip itself, but right next to it. But it's hard to see where.

---

### Post by slimdog360 on 2007-11-09
From the manual
> The temperature sensors can be adhered to any part of CPU, EXCEPT THE MICROCHIP AREA
I dont see a microchip area on that cpu. Just place it between the heatsink and the cpu, remembering that if you remove the heatsink to put on the sensor that you are going to have to clean the surface of the cpu and put on thermal paste before putting the heat sink back on.

---

### Post by svtfmook on 2007-11-09
you don't want to put the thermal probe in between the heatsink and cpu heat spreader.  for the heatsink to work properly, it needs to have full contact with the heatspreader.  the microchip is under the heat spreader (big aluminum thing ontop of the cpu).  i always stick my probes on the underside of the heatsink on a section that is wider than the cpu as close to the heatspreader as possible.  if i'm using an aftermarket cooler, i will put is on the side or even the top side of the heatsink.

---

### Post by Zero Prime on 2007-11-09
I just stuck mine into one of the tighter grooves on my heatsink.  It has a nice tight fit.  I also have one on my video card and in between my harddrives.   They always read a nice cool temp.  But having a total of 6 fans might have something to do with that.  God bless Thermaltake!!

---

### Post by svtfmook on 2007-11-09
i only have 4 fans, although, 1 of them is 200mm and 3 of them are 60+cfm fans.

---

### Post by Perfect Storm on 2007-11-09
> **slimdog360 said:**
> From the manual

I dont see a microchip area on that cpu. Just place it between the heatsink and the cpu, remembering that if you remove the heatsink to put on the sensor that you are going to have to clean the surface of the cpu and put on thermal paste before putting the heat sink back on.

Is that the white "glue" stuff upon the CPU?

---

### Post by dasunst3r on 2007-11-09
I assume that the sensor you're trying to place is quite flat, so I would try to slide it right under the processor socket.  I would do that about two years ago, so my advice may be a bit dated.

---

### Post by Perfect Storm on 2007-11-09
Aye, it's flat.

I just had to ask, as it says in the manual you can damage the CPU if it aren't done right. I guess it can affect the cooling of the CPU?

---

### Post by Perfect Storm on 2007-11-09
Done. Probe inserted. If it goes wrong I've a self-inflicted damage  insurance for all my electronic parts that I have in my house. :lolflag:


I wonder if the 3 pins wire that says "SYS" is also needed to be set somewhere. I can't see anywhere on the MB where it should be.
So far I have set probe on HDD, CPU and the cabinet in general. Also set monotoring the Fan on the CPU - can now control it via the display (3 pins) and set control on HDD led (2 pins)

Now 2 left.
(3 pins) for a fan to control one of them - my system doesn't use 3 pins for my fans so it's ruled out.
and the last 3 pins that says SYS which I don't know where to go - but again it can be my MB doesn't have it. (can't either find it on the manual).

---

### Post by mcduck on 2007-11-09
The 'sys' wire is probably just for monitoring the overall system temperature. So you can leave it anywhere inside the case. Myself, I would probably glue it to the side of the north bridge (the biggest chip on your motherboard, bit down from the CPU and usually under a heat sink and possibly a fan too).

edit. I misread your post. If it's not a sensor but a wire with a 3-pin connector, it's supposed to go to some fan connector on your motherboard.. Most likely the one you use for case fan. This is so your motherboard can also get the fan speed information (if you have a fan with a speed sensor, of course)

---

### Post by svtfmook on 2007-11-09
yeah, sys would be your ambient temp, ie the temp inside the case.  it's good for comparing with others how well your cooling solution is working.  for example, if my opteron 165 was running at 30º with an ambient temp of 35º and you had the same setup, clock speed, voltage, but you were running 32º, you would know it was because your ambient temp is 37º.  so you're next step would be lowering your ambient temps by replacing your case, case fans or even modifying your case to fit more fans.

---

