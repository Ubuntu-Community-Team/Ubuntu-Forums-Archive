---
title: "HDD partition and mount size not the same"
date: 2010-04-18
forum: Server Platforms
---

### Post by darylohrt on 2010-04-18
have ubuntu 9.10 server that i just set up.

have public shared hdd that is 1TB 

i mounted the drive but it only shows available size of 100G.

here is fdisk-1  out put


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcb7fa287

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14035   112736106   83  Linux
/dev/sda2           14036       14593     4482135    5  Extended
/dev/sda5           14036       14593     4482103+  82  Linux swap / Solaris

Disk /dev/sdb: **1000.2 GB**, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6076ed1d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux



here is the **df -h **output for the mount point



Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1 **            106G**   97G  4.5G  96% /


what did i do wrong?

---

### Post by Drenriza on 2010-04-18
the 1tb disk and the disk you made the fdisk-1 on are not the same. So im not sure i understand.

---

### Post by darylohrt on 2010-04-18
figured out my error.

had the mount point in fstab listed as ext3 but the drive is actually fat23.  fixed fstab, rebooted and fixed issue.

---

