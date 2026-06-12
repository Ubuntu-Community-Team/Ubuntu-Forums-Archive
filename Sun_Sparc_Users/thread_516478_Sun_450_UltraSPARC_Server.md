---
title: "Sun 450 UltraSPARC Server"
date: 2007-08-03
forum: Sun Sparc Users
---

### Post by ryan-ivey on 2007-08-03
Hello there folks, recently i've installed feisty fawn onto one of our sun 450 servers at work, which has 6 hard drives in it, two 18GB drives, and four 36GB drives (all scsi drives). It detects them all in /dev/ as sda sdb sdc sdd sde sdf. I have fdisk'd the drives, and made them so theyre all one partition, but when I mount them, they keep showing up as 2GB and 1.5 GB and such? And some of them, when I restarted the box, they came back as the SunOS default partition layout, and i have to re-fdisk them and blow away the partitions, write a new partition table, etc. And they just keep showing up as really small drives. Any help would be greatly appreciated. Thanks!

---

### Post by ryan-ivey on 2007-08-03
Also, if this helps... I have noticed that I got one of the drives to mount with the correct size, but once I mount another drive, it shows up as 1.5GB, which then changes the first one I mounted back to 1.5GB instead of the 36GB which previously showed up. This is driving me nuts, me and my boss have been working on it the past 2 days, today being the 3rd, and we're getting nowhere.

---

### Post by psychicist on 2007-08-03
I have been running Splack Linux 10.2 on a Sun Enterprise 250 I bought last week and the devices show up just fine. I needed to partition the drives with Sun disklabels otherwise SILO couldn't boot. I also tried Solaris Express b68 on a spare drive today but it wouldn't install.

I'll try to install Ubuntu on another drive this weekend. I have enough drives from another server to install Free/Net/OpenBSD on each so I can see which distribution runs best.

---

