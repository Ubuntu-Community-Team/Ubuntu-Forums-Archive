---
title: "SSD as RAID cache"
date: 2012-03-01
forum: Server Platforms
---

### Post by kingrolo on 2012-03-01
I have a SATA RAID5 setup (mdadm software raid) for data storage whilst using a 120GB SSD as the main boot/OS drive. Is there a way to use the SSD for caching? Eg. if I want to stream a movie off the RAID, it would make sense (less disk wear? less total power?) to cache it onto the SSD and stream it from there. Googling 'RAID cache' seems to only talk about memory caching.

TIA.

Ubuntu 11.10 x86_64 (3.0.0-16)

---

### Post by rubylaser on 2012-03-01
With mdadm, the only options I know of are [Bcache]("http://bcache.evilpiepirate.org/") and [Flashcache]("https://github.com/facebook/flashcache").  I'd just suggest sticking with plain mdadm. One less thing to troubleshoot, and if you spin down your disks when they're idle, my server really doesn't use that much power.

---

### Post by a2j on 2012-03-01
green WDs in my array, streaming multiple HD videos at the same time, and use little of energy. Just what I need.

---

### Post by kingrolo on 2012-03-01
thanks for the responses. It seems green is what we all want these days..I'm using 4 of these..."Samsung HD204UI Spinpoint F4 2TB Hard Drive SATA 5400RPM 32MB Cache - OEM" with 4 more on their way. I'm running on 90Watts (seems high to me) which can be reduced by 3 Watts for every HD I spin down. I'll soon be swapping for a lower power CPU and mobo. Getting a bit off topic here, but how much power are you guys using?

I'll look into Bcache and Flashcache and see if they're any use to me..I'm not expecting any performance improvement, just want to spin the disks back down asap and not have them spinning the whole time I'm watching a movie...that time would quickly add up over a year.

---

### Post by rubylaser on 2012-03-01
You might consider [Unraid]("http://lime-technology.com/").  It isn't free, but it only spins up the disk that it needs.  [Flexraid]("http://www.flexraid.com/") is another solution.  Frankly, I can't see paying for Unraid myself.

Have you verified that your disks are spinning down with hdparm?  Are you seeing 90 watts total for the system with the disks spun up?  

I see around 135 watts with all (9) 2TB disks spun up in my array and the CPU under load.  I'm  trying to save money to upgrade my older CPU (AMD X2 4400+) and motherboard. I have (6) Seagate ST2000DL003 2TB drives, (2) Hitachi 5K3000 2TB drives, and (1) Seagate ST32000542AS 2 TB drive.

---

### Post by a2j on 2012-03-01
350W total at low load, 2 proxmox servers dell T5400 (2 hd each), 1 fileserver with 4 green drives + 2 regular drives and firewall/proxy on dell T3400 (3 hds). Seems like a reasonable energy usage.

---

