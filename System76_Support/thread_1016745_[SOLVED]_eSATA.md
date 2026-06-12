---
title: "[SOLVED] eSATA"
date: 2008-12-20
forum: System76 Support
---

### Post by Lee_Machine on 2008-12-20
I recently bought a CoolMax 2.5'' HD enclosure and put a 160GB HD in it.  

It has both USB and eSATA. Actually it gets its power from the USB Kind of nice I think.

The USB works ok at around 15Mb/s but the eSATA does not work at all.

I have the drive formated as NTFS so I may use it here and at work. 

The HD is mounted just fine with USB but when I try eSATA I get nothing. When the USB is plugged in it gets power and mounts. As soon as I plug in the eSATA cable it unmounts and cannot be found. 

I tried scsitool with no luck.

I tried scsiadd with no luck.

When the USB is used it mounts as sdb1 but the the eSATA cable that device is not even found therefore I cannot manually add it. 

I'm thinking ubuntu just doesn't support this particular eSATA controller.

Also, I do have AHCI turned on in BIOS.

My system is Ubuntu 8.10 64bit on a Pangolin Performace panp4n

Any ideas?

---

### Post by Lee_Machine on 2008-12-21
So the new kernel backport modules came out and fixed the issue. I read on lauchpad that it would. So when I plugged in the eSATA hard drive I got a prompt for root authorization to mount the drive.

SOOOOO much faster than USB :D

---

### Post by Lee_Machine on 2008-12-25
One thing to add to this is that there is a bug where you cannot connect the eSATA without first mounting it as usb, umount it, plugin the eSATA cable and then click on the HD icon under places. 

This does not happen all the time, just randomly. usually when coming back from resume. 

I posted a bug report on lauchpad. 

I'm really glad USB3 will be out soon and by the looks of it on Linux first as the first drivers were built for Linux. Running on Ubuntu actually :P

---

### Post by btbluesky on 2009-06-24
MY GOD!!! It work! 
Got a intel x58-based asus P6T, been pulling my hair for 2 hours before finding this post. Just a WD 1TB w/ a brando external USB+Esata dock.

Using the latest Jaunty kernel, nothing happens when plugging in the esata, and I actually made sure my USB is not plugged in so not to confuse the kernel.

The procedure made absolutely no sense. But it works, and once working, it's pretty solid.

---

### Post by miniyak on 2009-06-25
glad to know this works, i thinking of getting a 2.5 enclosure also.

personally i'm not holding my breath for usb 3.0, i have a feeling it will be a lot like all the other usb versions, looks great on paper but sucks wind in reality. I am sure it will be and upgrade, but realistically for me the only thing that going to make it better then eSata will be data/power over the same cable.

---

