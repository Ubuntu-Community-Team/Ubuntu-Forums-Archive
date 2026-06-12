---
title: "hard disk reliability reconsidered"
date: 2014-09-25
forum: Server Platforms
---

### Post by Vegan on 2014-09-25
Looking at hard disks in my shop seems to diverge from what larger centers experience. I tend to use disks for a long time. Big 2 TB disks hold a lot of software so I have not needed to move to bigger ones. Yet.

Working on my page, I realized I was all wrong. Again. Sure my MTBF number is all proper, the problem is that I retire functional disks. This means the real life may be longer, much longer, but my data censored this by way of retirement.

I own a bunch of disks, so my numbers are not miles away from larger shops

[http://windows-it.azurewebsites.net/wp/disk-reliability.php]("http://windows-it.azurewebsites.net/wp/disk-reliability.php")

I notice that a disk I was thinking of buying is more flakey than I like, failure rates up around 14% are a real headache

This is my I bought a BD drive to backup my more important files. Never can be too safe.

Backup today.

---

### Post by Vegan on 2014-09-26
Found a page for the Seagate disks with new firmware, so now I need to research the issue more deeply.

This is more subtle than I realized.

---

### Post by Michael_McKenney on 2014-09-26
Firmware upgrades can help with SMART functionality and other issues.  RAID arrays can make it hard to flash the drives.  In SCSI and SAS RAID on some controllers, you need to break the arrays to flash them.  Backup before you flash firmware on a drive.

---

### Post by tgalati4 on 2014-09-26
So are you saying that, in your experience, your disk drives (averaging 20k power-on hours) are not reaching the published mean time before failure (MBTF) of 113k hours as advertised by the manufacturers?

I think there are too many factors to make definitive statements about drive reliability.  Google found they needed to replace drives on a 3-year cycle because drive failures went up significantly in Year-4 and Year-5 of a disk drive's life.  So after 3 years of 24 hours per day, 7 days per week service, a disk will have accumulated 26,280 hours.  Most consumer drives are designed for 50K MTBF and enterprise/server disks are anywhere from 100K to 300K hours.

To get a solid 20k hours out of a disk, you would need to design it at least 3 times that amount or 60K hours to account for extreme use cases:  spin ups, hard power-offs, retracts, overtemps, long writes, etc.  So the 50K MTBF for consumer drives is about right.

Even if you found the perfect disk drive in terms of longevity (5 years after it was produced), good luck finding new ones of that model.

As far as retiring drives, you could build SAN arrays with the retired disks and use them for backup.  Although it defies logic, disks that have worked for several years will continue to function for a long, long time.  Those disks make good candidates for backup pools since they are write once, read few, and they have a proven track record.

The alternative is to run the drives until the bearings wear to a nub and they squeel.  Then replace them.  Drives get louder as they get older, so you could use a stick-to-the-ear method to listen for loud drives.  When a server fails, regardless of the cause, you would need a failover strategy anyway.

---

### Post by Michael_McKenney on 2014-09-26
MTBF and duty cycle are two characteristics of a drive.  Duty cycle % is hours of use per day.  You also have to have optimal conditions like perfect power and proper cooling to extend the life of a drive.  Turning off and on can lower a drive's life span.  Server room drives last longer because they are left on most of the time.  Only power failures that kill the UPS cause them to go off.  You also have clean power and air conditioning systems to remove most heat from the enclosures.   I worked with Maxtor on a SATA failure issue.  I was going through 1-2 drives a month.  They said the duty cycle of these drives was 50% or 12 hours a day.  Once we were done testing it was 12% or 3 hours a day.  My workstation has its own 20A circuit and Tripp Lite Line Conditioners.  The chassis has Panflo fans.  The issue was the PCB over heating due to poor design.  I switches to Seagate Cheetah SAS drives.

RAID 0 arrays can change your failure rates as you add drives.  RAID 1,10,5, 6, 50 and 60 arrays are designed to failover to spare drives.  RAID 6 gives you two drive failure but increased parity calculations and lowers write performance.  SAS and SCSI RAID 10 are RAID 1 pairs striped together.  So you can lose one drive per pair before failure.  So a 10 drive RAID 10 array in SAS/SCSI can give you 5 drive failure before losing the array.  SATA RAID 1+0 or 0+1 have different failure characteristics.  Software RAID has its issues with unexpected failures.  

No matter which drive you buy all will eventually fail.  Backup your critical data often.

---

