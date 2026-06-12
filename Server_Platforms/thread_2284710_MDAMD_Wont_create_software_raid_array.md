---
title: "MDAMD Wont create software raid array"
date: 2015-07-01
forum: Server Platforms
---

### Post by Jarno_Matikainen on 2015-07-01
When i try create software raid 1 with mdadm, it spits out every single time following text.

```
mdadm: An option must be given to set the mode before a second device
       (/dev/md1) is listed
```

fdisk -l
```
Disk /dev/sdb: 3000.6 GB, 3000592982016 bytes
90 heads, 3 sectors/track, 21705678 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8bb1610f
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  4294967294  2147482623+  83  Linux
Disk /dev/sdc: 3000.6 GB, 3000592982016 bytes
90 heads, 3 sectors/track, 21705678 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb83211c1
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  4294967294  2147482623+  83  Linux
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00039378
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    16779264     8388608+  82  Linux swap / Solaris
/dev/sda2        16781312    17829888      524288+  83  Linux
/dev/sda3        17831936   234439600   108303832+  83  Linux


```

Command i use with mdadm
```
mdadm &#8211;create /dev/md1 &#8211;level=1 &#8211;raid-devices=2 /dev/sdb /dev/sdc
```

Anyone have any idea why its saying that?

Have tried with unpartitioned and partitioned disks, but i guess issue is somewhere in command i use to create the mdadm software raid.

---

### Post by darkod on 2015-07-01
I don't know if it is a typo, but you need -- in front of options, not just one.
```
sudo mdadm --create /dev/md1 --level=1 --raid-devices=2 /dev/sdb /dev/sdc
```

Also you better use partitions as members, not disks as you are trying to do. Replace them with /dev/sdb1 /dev/sdc1.

PS. Also I see you formatted the partitions. That is not needed but it doesn't matter much if you leave it. For mdadm you only create partitions on the disks, don't format them with any filesystem. The md devices is formatted and holds the filesystem, not the partitions.

---

