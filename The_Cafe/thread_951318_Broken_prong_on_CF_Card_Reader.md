---
title: "Broken prong on CF Card Reader"
date: 2008-10-18
forum: The Cafe
---

### Post by jamieh on 2008-10-18
Ughh.. one of the prongs in my CF Card Reader bent when I put a CF card in there crooked.
The CF slot still works fine for reading and writing though.. Can anyone tell me what that last prong is used for?

Thanks

---

### Post by MaxIBoy on 2008-10-18
Power, probably.

---

### Post by Rhubarb on 2008-10-18
It looks like Pin # 26, which is signal ground.
As it has other ground pins, it may work ok as you suggest, perhaps with a chance of some data corruption possibly.

[http://www.interfacebus.com/CompactFlash_Memory_Module_pinout.html](http://www.interfacebus.com/CompactFlash_Memory_Module_pinout.html)

If you want to fix it, grab some needle nose pliers and straighten out the pin.

If your CF reader is using it as an IDE --> CF, then Pin 26 appears to be a n/c (no connection, which means it isn't even used)
[http://pinouts.ru/DiskCables/ide2cf_cable_pinout.shtml](http://pinouts.ru/DiskCables/ide2cf_cable_pinout.shtml)

---

### Post by mips on 2008-10-18
> **Rhubarb said:**
> 
If you want to fix it, grab some needle nose pliers and straighten out the pin.


A pair of tweesers could also do the job.

---

### Post by regomodo on 2008-10-18
#

---

### Post by Rhubarb on 2008-10-18
Oh yeah, I forgot CF readers have a denser pin layout than IDE drives do (which is what I've fixed before).
Tweezers it is then!

---

### Post by jamieh on 2008-10-18
Okay I'll try fixing it with tweezers.

I payed $60 for that piece of crap a bit over a year ago, now it looks like memory card readers are going for $12 and under.

---

### Post by mips on 2008-10-20
> **jamieh said:**
> Okay I'll try fixing it with tweezers.


Bend the pin really slowly though.

---

### Post by MaxIBoy on 2008-10-20
Reminds me of the time I bent about 50 pins on my CPU putting it back in (I was cleaning out the heatsink, and the CPU was stuck to it.) I tried straightening them, and about three snapped off.

It was great! I had an excuse to ditch that crappy Sempron and build a real rig!

---

