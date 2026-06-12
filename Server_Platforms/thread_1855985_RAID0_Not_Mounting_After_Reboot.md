---
title: "RAID0 Not Mounting After Reboot"
date: 2011-10-07
forum: Server Platforms
---

### Post by dlcho on 2011-10-07
I had a working and mounted RAID0 drive that is no longer mounting after reboot.  I used mdadm to create the drive, and the details are as follows:

```

/dev/md0:
        Version : 01.01
  Creation Time : Thu Aug 18 10:50:22 2011
     Raid Level : raid0
     Array Size : 1048575680 (1000.00 GiB 1073.74 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Aug 18 10:50:22 2011
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

           Name : ip-10-91-13-206:0
           UUID : 7cfa6a6d:aa8ec21d:2b56fd4c:8b60a0f8
         Events : 0

    Number   Major   Minor   RaidDevice State
       0       8       80        0      active sync   /dev/sdf
       1       8       96        1      active sync   /dev/sdg
       2       8      112        2      active sync   /dev/sdh
       3       8      128        3      active sync   /dev/sdi
       4       8      144        4      active sync   /dev/sdj
```

When I try to mount the drive I get:

```

mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

dmesg gives me:

```

[   11.577926] md: md0 stopped.
[   11.600359] md: bind<sdg>
[   11.601084] md: bind<sdh>
[   11.601635] md: bind<sdi>
[   11.602236] md: bind<sdj>
[   11.602901] md: bind<sdf>
[   11.667459] raid0: looking at sdf
[   11.667463] raid0:   comparing sdf(419430272)
[   11.667465]  with sdf(419430272)
[   11.667466] raid0:   END
[   11.667467] raid0:   ==> UNIQUE
[   11.667468] raid0: 1 zones
[   11.667470] raid0: looking at sdj
[   11.667472] raid0:   comparing sdj(419430272)
[   11.667473]  with sdf(419430272)
[   11.667474] raid0:   EQUAL
[   11.667475] raid0: looking at sdi
[   11.667477] raid0:   comparing sdi(419430272)
[   11.667479]  with sdf(419430272)
[   11.667480] raid0:   EQUAL
[   11.667481] raid0: looking at sdh
[   11.667483] raid0:   comparing sdh(419430272)
[   11.667484]  with sdf(419430272)
[   11.667486] raid0:   EQUAL
[   11.667487] raid0: looking at sdg
[   11.667489] raid0:   comparing sdg(419430272)
[   11.667490]  with sdf(419430272)
[   11.667491] raid0:   EQUAL
[   11.667493] raid0: FINAL 1 zones
[   11.667496] raid0: done.
[   11.667498] raid0 : md_size is 2097151360 sectors.
[   11.667499] ******* md0 configuration *********
[   11.667500] zone0=[sdf/sdg/sdh/sdi/sdj/]
[   11.667505]         zone offset=0kb device offset=0kb size=1048575680kb
[   11.667507] **********************************
[   11.667507]
[   11.667519] md0: detected capacity change from 0 to 1073741496320
[   11.670087]  md0: unknown partition table

```

fdisk -l gives:

```

Disk /dev/sda1: 32.2 GB, 32212254720 bytes
255 heads, 63 sectors/track, 3916 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sda1 doesn't contain a valid partition table

Disk /dev/sdb: 450.9 GB, 450934865920 bytes
255 heads, 63 sectors/track, 54823 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdj: 214.7 GB, 214748364800 bytes
255 heads, 63 sectors/track, 26108 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xffffffff

Disk /dev/sdj doesn't contain a valid partition table

Disk /dev/sdf: 214.7 GB, 214748364800 bytes
255 heads, 63 sectors/track, 26108 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xffffffff

Disk /dev/sdf doesn't contain a valid partition table

Disk /dev/sdg: 214.7 GB, 214748364800 bytes
255 heads, 63 sectors/track, 26108 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xffffffff

Disk /dev/sdg doesn't contain a valid partition table

Disk /dev/sdh: 214.7 GB, 214748364800 bytes
255 heads, 63 sectors/track, 26108 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xffffffff

Disk /dev/sdh doesn't contain a valid partition table

Disk /dev/sdi: 214.7 GB, 214748364800 bytes
255 heads, 63 sectors/track, 26108 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xffffffff

Disk /dev/sdi doesn't contain a valid partition table

Disk /dev/md0: 1073.7 GB, 1073741496320 bytes
2 heads, 4 sectors/track, 262143920 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 327680 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

```

Is there any way I can get this drive back without losing my data?

Thanks for the help.
-Don

---

