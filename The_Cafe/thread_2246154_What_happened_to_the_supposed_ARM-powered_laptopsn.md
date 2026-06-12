---
title: "What happened to the supposed ARM-powered laptops/netbooks of the near future?"
date: 2014-09-28
forum: The Cafe
---

### Post by user1397 on 2014-09-28
I remember a few years ago at the height of the netbook craze, that people in the tech world and especially in this forum were often mentioning how the future of mobile computers were to be ARM-powered netbooks/laptops that had extremely long battery lives and very low power consumption/heat, and that combined with solid state drives they would have no moving parts as even fans would be redundant (because of the low operating temps).

As far as I know, this never happened (I don't recall seeing one ARM powered laptop on the market).

---

### Post by buzzingrobot on 2014-09-28
The chips in iPhones and iPads are integrated units based on ARM and using the ARM instruction set.

Improving capabilities and battery life of phones, as well as laptops like the Macbook Air have, I think, done away with the netbook market. The few I used were way underpowered with dim screens.  It makes little difference how long a battery lasts if you don't really want to use the thing in the frist place.

---

### Post by endlessinstant on 2014-09-29
Haswell and Baytrail CPUs are beating ARM CPUs in battery life.  There's a few different ARM chromebooks out there, probably the largest such example of a notebook powered by ARM.   If you were so inclined, it'd be little trouble to reflash the BIOS on one of the newer ones and legacy boot a Linux desktop.  Fewer packages compiled for ARM though so meh.

---

### Post by mips on 2014-10-02
I think tablets took over from netbooks and most of those are Arm based.

---

### Post by mcduck on 2014-10-03
I'm doing decent part of my work (and most of my movie watching etc)  on a tablet with a nice keyboard, so I suppose the only difference to "ARM-powered laptop/netbook" is that it has touchscreen, it doesn't feel horribly cheap, and it runs Android rather than a desktop OS (which makes such a small and relatively low-powered device much more comfortable than trying to deal with normal desktop on a small screen would be). And of course that I can leave the keyboard part away when I don't need it... Come to thnk of it, most poepel use tablets for exatly the same purposes netbooks were sold at the time.

And of course there are Chromebooks around, I'd definitety consider those as laptops, and some models use ARM processors.

So I'd pretty much say the ARM-notebook/netbook actually did happen, it just ended being more mobile and less desktop OS than what people expected. ;)

---

### Post by Michael_McKenney on 2014-10-03
tablets and phablets killed the laptop.

---

### Post by user1397 on 2014-10-17
Yea I guess I didn't really think about the latest developments and form factors and the lower consumption haswell processors and the like.  Still, anyone know of a fanless laptop?  Don't know if one exists.  I guess you could have a liquid cooled one but then it would look pretty clunky no?

---

### Post by glyczak on 2014-10-18
Just an idea but I think that with a little tweaking companies could make a lot of money of of a raspberry-pi-like net-book.

---

### Post by glyczak on 2014-10-18
The only issue would be that it's hard to find a five volt display that could be attached to the pi.

---

### Post by HermanAB on 2014-10-20
What happened?  People complained about the cramped keyboards of netbooks, so they were removed altogether...

There are billions of Android Linux tablets and phones out there.  Windows now occupies a small niche market.  The rest is Linux.

---

### Post by haplorrhine on 2014-10-20
> **ubuntuman001 said:**
> Yea I guess I didn't really think about the latest developments and form factors and the lower consumption haswell processors and the like.  Still, anyone know of a fanless laptop?  Don't know if one exists.  I guess you could have a liquid cooled one but then it would look pretty clunky no?

fanless laptop?

Acer Aspire E11

---

### Post by user1397 on 2014-10-20
> **haplorrhine said:**
> fanless laptop?

Acer Aspire E11
hmm...it still has a regular HDD...that has to at least have a fan right?

---

### Post by haplorrhine on 2014-10-20
> **ubuntuman001 said:**
> hmm...it still has a regular HDD...that has to at least have a fan right?

"It doesn't need a fan, so it's whisper-quiet and runs cool."
[http://us.acer.com/ac/en/US/content/series/aspire-e11](http://us.acer.com/ac/en/US/content/series/aspire-e11)

---

### Post by haplorrhine on 2014-10-20
If you remind me of the command, I can tell you what temp it's running at.

---

### Post by pqwoerituytrueiwoq on 2014-10-20
sensors-detect
sensors
also there is this one for cpu temp
echo $(($(cat /sys/class/thermal/thermal_zone0/temp)/1000))°C

---

### Post by haplorrhine on 2014-10-20
temp1 stays around 47-49.
The core temps are loitering around 48-51, but have gone to 45 and 56.

Adapter: Virtual device
temp1:        +49.0°C  (crit = +105.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +48.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:       +48.0°C  (high = +105.0°C, crit = +105.0°C)

---

### Post by Kale_Freemon on 2014-10-21
> **HermanAB said:**
> What happened?  People complained about the cramped keyboards of netbooks, so they were removed altogether...

There are billions of Android Linux tablets and phones out there.  Windows now occupies a small niche market.  The rest is Linux.

I sure hope that Android is not the future. Windows Phone is so much better, in my honest opinion, than Android is. But, that's just me. As long as I get my Windows Phone, I'm happy.

On the desktop, however, Linux all the way (except for the times that I do use Windows as needed for games and non-Linux compatible applications).

But, no, netbooks are pretty much dead. They were quickly killed off by tablets and phones. I also can't imagine using an ARM laptop. Just not enough compatible software. It's a better tablet processor than anything.

---

