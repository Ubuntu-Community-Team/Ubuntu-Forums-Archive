---
title: "Hardware RAID card for 10.4 LTS server"
date: 2011-02-02
forum: Server Platforms
---

### Post by jbarntt on 2011-02-02
I need advice for a hardware RAID card, capable of doing RAID 10 with 4 drives plus a spare. SAS drives. I can do either x23 or 64.

I don't want fakeraid or software RAID.

Any advice appreciated.

TIA

jbarntt

---

### Post by doogy2004 on 2011-02-03
Sorry I don't have a recommendation for hardware raid.  Do you mind if I ask why you don't want software RAID?

---

### Post by jbarntt on 2011-02-04
It's for a Samba file server, accessed by a lot of people simultaneously. I/O is critical and hardware RAID is faster than software RAID. (I do use MD RAID on another file server, but it is less important that I/O is as fast as possible on that one.)

jbarnt

---

### Post by rubylaser on 2011-02-04
The Dell Perc 5/i via ebay will do this fine.  Allow I would dispute your comment that hardware RAID is faster than software RAID.  I manage numerous LSI, HP 400i, Dell 5/i & 6/i hardware RAID cards, as well as numerous mdadm RAID arrays.  As long as you have decent processors in the server, I see no difference in performance between hardware/software arrays.  In fact in many situations, mdadm is faster with Linux distros.

If you need as fast as possible, I'd be looking at SSD drives or much faster (and more pricey) [http://www.fusionio.com/products/iodriveduo/]("http://www.fusionio.com/products/iodriveduo/")

I've seen these in email servers, and they are ridiculously fast.  Good luck with your choice.

---

### Post by doogy2004 on 2011-02-04
Here is a "guide" to building a ZFS SAN, it has lots of benchmarks that you may want to look at.

[http://www.zfsbuild.com/](http://www.zfsbuild.com/)

---

### Post by Vegan on 2011-02-04
I suggest a modern RAID6 solution will last longer.

---

