---
title: "the kernel was unable to reread the partition table /dev/mdo"
date: 2009-03-12
forum: Server Platforms
---

### Post by ludicrous50 on 2009-03-12
While loading 8.1 I am configuring raid and and then the individual file systems on the different partitions and this message pops up. "the kernel was unable to reread the partition table /dev/mdo" and then I have to reboot and when I do the raid partition table does not exit. 

It seems like to me the partition table is not being written correctly. 

I have tryed this on a home made machine and a dell server and I keep getting the same error. 

Help!!!!!!!!!!!!!!!!!!!!

---

### Post by askreet on 2009-03-17
Linux raid devices start with /dev/md0 (Zero, not not lowercase letter O).  I think you have typed /dev/mdo somewhere important.

---

