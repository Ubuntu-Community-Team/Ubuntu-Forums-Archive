---
title: "Reduce your Linux memory footprint"
date: 2007-12-09
forum: The Cafe
---

### Post by mips on 2007-12-09
Came across this interesting article:
[http://www.ibm.com/developerworks/linux/library/l-linux-memory.html](http://www.ibm.com/developerworks/linux/library/l-linux-memory.html)

And NO, this is not to erupt into a DE flame war ;)

---

### Post by diskotek on 2007-12-09
wow, nice article...

---

### Post by aysiu on 2007-12-10
I don't know.

If I had an 800 MHz processor with 256 MB of RAM, I would surely not use a desktop environment at all. I'd stick with a window manager like IceWM or Fluxbox.

---

### Post by D-EJ915 on 2007-12-10
> **aysiu said:**
> I don't know.

If I had an 800 MHz processor with 256 MB of RAM, I would surely not use a desktop environment at all. I'd stick with a window manager like IceWM or Fluxbox.
I have a dual core 2.2GHz opteron and I don't use a desktop environment.  But, most people want the "full featured-ness" that a DE "provides."

---

### Post by undine on 2007-12-10
Not a bad option, but in terms of memory-saving apps, one would have thought they'd include alternatives like Epiphany and Lyx in the categories they dealt with.

---

### Post by ~LoKe on 2007-12-10
I use DWM, a very lightweight environment.  Yet, I have 2GB of RAM.

All about preference. ;)

---

### Post by Tundro Walker on 2007-12-10
Default Xubuntu install ran a tad sluggish on my old 800mhz, which had 300+mb RAM.  It did run better after I trimmed off some of the bells and whistles, and, like the author said, swapped bulkier stuff for lighter things (mainly Epiphany instead of Firefox).

Of course, WinXP was the same way, until you switch off some of the unnecessary bells & whistles & services that a single-user comp doesn't need running (Indexing, etc).

Tremulous ran fine in both Windows or Xubuntu on the 800mhz.  They're still good machines, even in this  dual & quad-core age.  They obviously can't keep up with the latest games and such, but for email, office, etc stuff, they're more than enough.  They just need a little TLC to make them lean and mean.  

I know some folks would say Fluxbuntu, IceWM, etc are leaner and meaner than Xubuntu, but after trying them, I didn't really like some of the tweaking.  Xubuntu ran fine, and it was very simple to tweak.  So, to each their own.

---

### Post by crimesaucer on 2007-12-10
I've messed around with a few options on both xubuntu and Arch, and I found that the best combo I've reached yet is Archlinux-->--xfce4.4.2-->--xfwm4 with compositing. That way it's got a bit of eye candy, while staying light since I only have 512MB ram and 1GB Swap.


Getting rid of Compiz and Emerald was the best thing for my resources. I used Beryl/Compiz for a year... I liked it, but after trimming it down to xfwm4, I can really feel the difference in everything. 


I also turn tty3-tty6 off, then set my 1 GB of swap to swappiness=40 (I could set it to less...), I also do all of my Firefox/Swiftfox about:config tweaks, and I try to clear my Cache often.

---

