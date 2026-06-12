---
title: "[SOLVED] CPU Heat Tolerance"
date: 2008-09-17
forum: The Cafe
---

### Post by aaaantoine on 2008-09-17
What is worse for the longevity of a CPU?

A. Constant, high temperature (in this case, let's say it's 74 degrees C).

B. Temperature that repeatedly fluctuates between 50 C and 70 C.

I run Folding@Home, but I like to periodically give my CPU a break by scaling down its frequency until the temperature hits 47 or so, and then scale it back up to full, until it hits 72.  I find that when I do this, the temperature doesn't quite reach the 70s until after about five or ten minutes.  So it runs a little cooler for a while.

However, do the repetitive heat fluctuations make for a potentially unstable processor?  Do I risk breaking something if I keep adjusting the frequency?

(Please note that I am not overclocking or underclocking *per se*; I'm switching between the two available frequencies available to the AMD Turion 64 X2.)

---

### Post by artir on 2008-09-17
It deppends on the processor and if its  a laptop or a desktop.
On desktops, a Q6600 can happily run at 74 degrees happily but 75 is not a good thing.
On yours it will deppend.

---

### Post by jrharvey on 2008-09-17
Find out what your CPU temp threashold is from AMD. Mine is 71 degrees so i know to try and keep it around 65 to be safe. If not you could look into a better heatsink for around 30 dollars.

---

### Post by Kvark on 2008-09-17
When working with tech support I was told heat doesn't wear down Integrated Circuits like CPU, GPU and chipset. What it can cause is weird errors usually of the BSOD type, bad performance through automatic downclocking, sudden reboots through emergency shutdown and harmless color changes on the motherboard around the hot areas. But if it runs fine then the longevity of ICs is not reduced by heat or temperature changes.

We did get a few warranty cases where the hardware worked fine for a while then just died without any apparent fault but those where rare. I don't know if those where caused by heat, customers messing with the voltage settings in the BIOS or what. So maybe what they really meant was that heat usually doesn't reduce the lifespan so much that it dies before the warranty runs out.

---

### Post by aaaantoine on 2008-09-17
> **jrharvey said:**
> Find out what your CPU temp threashold is from AMD. Mine is 71 degrees so i know to try and keep it around 65 to be safe. If not you could look into a better heatsink for around 30 dollars.

I read somewhere that the threshold for Turion 64 X2s is in the 90s, though I can't find any definitive numbers online.

Edit: While Googling [amd turion 64 x2 "heat tolerance"] for an exact number, I came upon this thread.  Already!? :lolflag:

---

### Post by Whiffle on 2008-09-17
Looks to me like mid 90's is max.  [http://users.erols.com/chare/elec.htm](http://users.erols.com/chare/elec.htm)


I'd run it rull throttle and not worry about it in a Desktop.  But since its in a laptop I'd be certain to make sure that the laptop itself has plenty of cooling, and then run it full.  I've heard Acer laptops have issues with heat anyway, so I'd double check.

---

### Post by aaaantoine on 2008-09-17
Thanks for the info.

Apparently there are a pair of additional temperature sensors in this laptop that I was not previously aware of. I don't know what they're for, but the numbers are about 10 degrees higher at any given time than the sensor I looked at previously.

So I have THRM under ACPI, hwmon0 (1), and hwmon0 (3).  hwmon0 (3) peaked at 80 degrees a moment ago, and has probably kicked up even higher than that.

I'm gonna try to get a F@H work unit in before the deadline, and then I'll set the governor back to ondemand until it starts getting colder out.

---

### Post by mips on 2008-09-17
AMD website should give you the specs for your cpu, see datasheets maybe.

---

### Post by petermck on 2008-09-28
The most common causes for failure in all electronic circuits can often be traced back to the mechanical damage of connections on a microscopic scale caused by thermal expansion and contraction.
Two golden rules are:-
[LIST=1]
[*]The cooler the better within reason.
[*]The more constant the temperature the better.
[/LIST]

---

### Post by Frak on 2008-09-28
If you hit 150 degrees Celsius and keep working, give me your manufacterers number.

Anyways, fluctuating temperture is worse than a high stable. This is ALWAYS the case. It damages the circuits because they are constantly being shifted around due to temperature changes.

---

### Post by aaaantoine on 2008-10-02
> **Frak said:**
> If you hit 150 degrees Celsius and keep working, give me your manufacterers number.

Anyways, fluctuating temperture is worse than a high stable. This is ALWAYS the case. It damages the circuits because they are constantly being shifted around due to temperature changes.

I figured as much.  Thanks.

---

### Post by Frak on 2008-10-02
> **aaaantoine said:**
> I figured as much.  Thanks.
On a second note, did you build this yourself, or was it manufactured? From what I've found, depending on the manufacturer, some don't apply enough thermal paste on the processor. This usually causes high heat. Also, replace your thermal compound every, say, 3-5 years (if you have it that long). TC breaks down over time due to temperature fluctuation.

---

### Post by Polygon on 2008-10-02
my cpu basically has been running at 100% for like a year straight and averages around 60 degrees C, and its still alive and kicking (i run WorldCommunityGrid, which uses all my spare cpu processing power so its 100% all the time)

it depends on the cpu really. I noticed my cpu doesnt shut down until it reaches 75 degrees C

---

