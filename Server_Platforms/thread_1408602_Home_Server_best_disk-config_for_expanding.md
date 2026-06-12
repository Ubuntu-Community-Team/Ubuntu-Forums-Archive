---
title: "Home Server: best disk-config for expanding"
date: 2010-02-16
forum: Server Platforms
---

### Post by chrisi99 on 2010-02-16
Hi There!

I am currently working on a home-server (serving files, iscsi target for backup), running on an intel-based P55M-UD2 (Gigabyte) Mainboard.

I am experienced with ubuntu as a desktop system and linux in general, but I am not firm in "Server-concepts".

I boot the system from a SSD (16 GB) and have 8GB of Ram available (thanks to another system that died on me ;) )

The disk-space available in the beginning should be around 2TB.

Which setup is to be considered "best" in regard of future expansion and "fail safety"?

If I set it up as a software RAID1 over 2 2TB disks, can I easily expand it by putting in another set of 2 disks for example? how "fail safe" is the linux-software raid anyway (a good hardware RAID Controller is quite expensive ..) in terms of replacing one disk (using the fake-raid on a intel board I experienced no problem under Windows, but I never ever before used a linux software raid (; )

I dont think of "worst case" scenarios, multiple fails and so on, because on my current desktop in 2 years of 24/7 exactly one disk died and the server case and disk-bay is very well cooled.

Hope I did not confuse you (because I am obviously ;) ) since english is not my native language just ask if anythin is unclear!

best wishes
Chris

---

### Post by Girya on 2010-02-16
I use lvm2 for my home server and haven't had a problem with it.

---

### Post by chrisi99 on 2010-02-17
hi!

Thank you for your reply!

As far as I understood it, LVM creates a "layer" between the partitions and the filesystem as the users sees it.

Kind of the Dynamic Volumes in Windows I guess...

How is the actual disk-setup on your machine (raid oder single disks?)? And how handy is lvm2 in "growing" the filesystem?

best wishes

---

### Post by DSK on 2010-02-19
I am going through the same process.  So far I am planning on building a server with Raid 1+0 (aka Raid 10) with LVM.  I like the speed and redundancy with this raid setup and the ability to expand with LVM.  

Wikipedia is a good source to understand your Raid options [http://en.wikipedia.org/wiki/RAID]("http://en.wikipedia.org/wiki/RAID")

As for hardware I will go with 8GB of ram on a tri-core AMD with 3 750GB disks.

---

### Post by chrisi99 on 2010-02-19
hey there!

I would be interested in comparing our setups and performances!

My setup is:

Asus P7H55-M
Core i3 - 540
4GB of DDR3 RAM
Gbit Lan onboard 
2x1TB HDD (5400rpm) in Raid 1
16GB SSD for System only

I would like to compare NFS read/write of large files VS power consumption =)

best wishes

---

