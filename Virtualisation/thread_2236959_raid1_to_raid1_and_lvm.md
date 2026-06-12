---
title: "raid1 to raid1 and lvm"
date: 2014-07-29
forum: Virtualisation
---

### Post by ajonen on 2014-07-29
I would like to go from a RAID1 setup to RAID1 with LVM.
I read up on a post to tar backup the entire install at [https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR).
Then i figured i could repartition the drives with RAID1 and LVM.
Then i could restore according to the above link to the LVM partion.

Does this sound right?  

I am using software raid for the raid1.

here is what i have.


Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0003d22b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   195350527    97674240   fd  Linux raid autodetect
/dev/sda2   *   195350528  3907028991  1855839232   fd  Linux raid autodetect

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000cd8db

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   195350527    97674240   fd  Linux raid autodetect
/dev/sdb2   *   195350528  3907028991  1855839232   fd  Linux raid autodetect

Disk /dev/md1: 1900.2 GB, 1900244959232 bytes
2 heads, 4 sectors/track, 463926992 cylinders, total 3711415936 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/md0: 100.0 GB, 99951181824 bytes
2 heads, 4 sectors/track, 24402144 cylinders, total 195217152 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

---

### Post by ajonen on 2014-07-29
edit. sorry double posted.

---

