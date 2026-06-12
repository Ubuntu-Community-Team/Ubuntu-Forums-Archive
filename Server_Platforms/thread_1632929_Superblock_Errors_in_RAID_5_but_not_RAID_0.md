---
title: "Superblock Errors in RAID 5 but not RAID 0"
date: 2010-11-28
forum: Server Platforms
---

### Post by Dhnz on 2010-11-28
Okay. I have found a weird issue. When i try and make a RAID 5 array I get superblock errors.

I have a P4 @ 2.80GHz
Ubuntu 7.10 
786MB RAM
2 Generic SATA Controllers. 
3x 1.5TB WD Green drives. 

I will get up terminal outputs when I get home.

I can make the array, but when I try and format with EXT4 or XFS it comes up superblock errors.

But the weird thing is. I can make a RAID 0 array and it formats to EXT4 with no issues.

I am using:

> Sudo mdadm --create /dev/md5 --level=5 --raid-devices=3 /dev/sdb /dev/sdc /dev/sdd

---

