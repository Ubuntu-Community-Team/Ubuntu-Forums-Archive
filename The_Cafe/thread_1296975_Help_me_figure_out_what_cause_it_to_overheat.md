---
title: "Help me figure out what cause it to overheat"
date: 2009-10-21
forum: The Cafe
---

### Post by elliotn on 2009-10-21
My PC overheats a lot, then it shuts down, I cleaned the heatsink and the fan but problem still persist, Then I down clocked it from its 1.8ghz to 800mhz but still it overheat. What maybe wrong here, is it my power supply or what, please help am desperate here

---

### Post by hoppipolla on 2009-10-21
thermal paste.

or a malfunctioning CPU o.O

Probably thermal paste :)

---

### Post by Xbehave on 2009-10-21
most PCs come with a few sensors that track temperature, there are GUI tools that can be used to log them, then look which is climbing just before the computer restarts it self. Something like ksensors / gnome-applet-sensors , should work (last time i used them it needed some configuration but nothing too hard)

If you want to take a look at the temperature manually something like
```
 find /sys/ | grep temp | grep -v k8temp
```
Will give you a list of temperature sensors (may not be all of them), cat them to get temperatures in C*1000 (accuracy is usually to just 1C). 
```
cat /sys/devices/virtual/thermal/thermal_zone0/temp /sys/devices/pci0000:00/0000:00:18.3/temp1_input /sys/devices/pci0000:00/0000:00:18.3/temp3_input
32000
30000
30000

```
Typically processors run between 30-40C and the rest of my laptop is at 25-35C if anything is higher than that it is probably overheating.

---

### Post by Paqman on 2009-10-21
> **Xbehave said:**
> Something like ksensors / gnome-applet-sensors.

The Gnomey package in the repos is sensors-applet, just install it then run:
```
sudo sensors-detect
```

---

### Post by JillSwift on 2009-10-21
> **hoppipolla said:**
> thermal paste.

or a malfunctioning CPU o.O

Probably thermal paste :)
This.

Your heat sink may have come apart from your CPU. New paste is teh thing!

---

### Post by hoppipolla on 2009-10-21
Additionally, I am also buying a new heatsink and fan for my CPU as we speak (inspired by this convo probably lol) - just make sure your heatsink is reasonable - put a picture up here for people to tell you but it's still most likely the thermal paste :)

---

### Post by craigeo on 2009-10-21
I was having the same issue about a month ago of my computer overheating and shutting down.
I finally took it apart and a cricket had jammed itself in the cpu fan and burned it out (and fried itself).... :-)
(Sorry, kind of relevant so had to share.)

---

### Post by hoppipolla on 2009-10-21
> **craigeo said:**
> I was having the same issue about a month ago of my computer overheating and shutting down.
I finally took it apart and a cricket had jammed itself in the cpu fan and burned it out (and fried itself).... :-)
(Sorry, kind of relevant so had to share.)

haha that's crazy, my friend used to have all kinds of bugs setting up home inside his computer (we could see them through the side window), but never anything as large as a cricket!

---

### Post by JillSwift on 2009-10-21
> **hoppipolla said:**
> haha that's crazy, my friend used to have all kinds of bugs setting up home inside his computer (we could see them through the side window), but never anything as large as a cricket!
Did he register them on launchpad.net?

---

### Post by Skripka on 2009-10-21
> **JillSwift said:**
> This.

Your heat sink may have come apart from your CPU. New paste is teh thing!

That is the only thing you can fix/do anything about.  My money is on a b0rked thermostat on the CPU/mainboard.  When folks run their laptops hot, and strees their systems those critters don't last long.

Of course, the OP never told us if his laptop is hot to the touch, and if the thermal warnings seem valid or not.

---

### Post by Niko Johnson on 2009-10-21
haha thats funny to hear!! how did a cricket get in there!!! that's pretty crazy and unusual

---

### Post by hoppipolla on 2009-10-21
> **JillSwift said:**
> Did he register them on launchpad.net?

they weren't interested ._.

---

### Post by Stavro on 2009-10-21
Most probably thermal paste. You mentioned you cleaned the heat sink but did you reapply new thermal paste evenly onto the processor before fitting the heat sink in place again? Get a quality brand of thermal paste and you won't have any more over heating problems.

---

### Post by craigeo on 2009-10-22
> **Niko Johnson said:**
> haha thats funny to hear!! how did a cricket get in there!!! that's pretty crazy and unusual

Late summer I get crickets in the house.
I didn't have all the slots covered with blanks in the back of my computer (do now).  :-)

---

