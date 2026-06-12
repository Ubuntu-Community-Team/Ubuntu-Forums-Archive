---
title: "SCSI disk RAID"
date: 2006-07-28
forum: Server Platforms
---

### Post by ufa on 2006-07-28
Hi all,
I have a old server from Unisys (Aquanta ES, 2x P3, 1,5 GB RAM)
It have a Symbios SCSI Controller (SYMS3C810 AND SYMS3C96).
In the boot time, it says that the sym53c8xx driver is loading, and the cd rom, that is also SCSI works good. But when partitioning stage comes, it says that there is no disks available to install. I tried to modify the raid form ( it was configured to RAID 5, I changed to RAID 0) but it still not working.
It had a Wind0ws install before, so the disks are working.
I googled a bit, and i found that may be the kernel problem, if i could upgrade it to 2.6.16, maybe it can run. I dont know it it is the problem since the server is an old one, so the drivers should be mature by now.

Well, if someone have  a clue, i appreciate.

Ufa

---

