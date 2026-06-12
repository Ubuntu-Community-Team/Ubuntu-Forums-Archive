---
title: "RAID wont mount"
date: 2010-08-18
forum: Server Platforms
---

### Post by nienaber on 2010-08-18
I have a RAID drive on my ubuntu 10.04.1 server install. It is a backup drive and not the primary drive. It worked while I had ubuntu 9.04 on the machine, but since my upgrade to 10.04 I haven't been able to get it to mount.
 mdadm -E
```

host:~> sudo mdadm -E /dev/sdd
/dev/sdd:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : e79fb4b4:82ba4910:631accc6:0d932874 (local to host)
  Creation Time : Wed Jun  2 05:36:15 2010
     Raid Level : raid0
  Used Dev Size : 0
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Wed Jun  2 05:36:15 2010
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 1c408f2c - correct
         Events : 1

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       48        1      active sync   /dev/sdd

   0     0       8       32        0      active sync   /dev/sdc
   1     1       8       48        1      active sync   /dev/sdd



host:~> sudo mdadm -E /dev/sdc
/dev/sdc:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : e79fb4b4:82ba4910:631accc6:0d932874 (local to host)
  Creation Time : Wed Jun  2 05:36:15 2010
     Raid Level : raid0
  Used Dev Size : 0
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Wed Jun  2 05:36:15 2010
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 1c408f1a - correct
         Events : 1

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       32        0      active sync   /dev/sdc

   0     0       8       32        0      active sync   /dev/sdc
   1     1       8       48        1      active sync   /dev/sdd
host:~> 

```

Its a RAID - 0 with just two 160GB drives.

```


Disk /dev/sdc: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2738fad6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       40046   321669463+  42  SFS

Disk /dev/sdd: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

```

cat /proc/mdstat

```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md_d0 : inactive sdd[1](S)
      160836416 blocks
       
unused devices: <none>


```

Advice would be appreciated.

---

### Post by brettg on 2010-08-18
I have had problems with RAID after rebuilding machines before.

Do ls -al /dev/md*

Do you have a /dev/md_d0 listed?

When this happens to me it seems to be building the raid automatically after a boot but doing it wrong. To fix it I need to stop the md_d0 device, recreate the array using mdadm, build a mdadm.conf file using mkconf and add the appropriate entry to fstab.

Step by step instructions can be found [here]("http://tuxnetworks.blogspot.com/2009/06/software-raid.html")

Good luck

---

### Post by nienaber on 2010-08-19
> **brettg said:**
> I have had problems with RAID after rebuilding machines before.

Do ls -al /dev/md*

Do you have a /dev/md_d0 listed?

When this happens to me it seems to building the raid automatically after a boot but doing it wrong. To fix it I need to stop the md_d0 device, recreate the array using mdadm, build a mdadm.conf file using mkconf and add the appropriate entry to fstab.

Step by step instructions can be found [here]("http://tuxnetworks.blogspot.com/2009/06/software-raid.html")

Good luck

Perfect. That solved my problem. Thanks!
It looks like the RAID drive was mounting only one of the drives and would then remain inactive. The advice of stopping it all and rebuilding worked out perfectly.

---

### Post by brettg on 2010-08-19
Glad I could help!

---

### Post by kgatan on 2010-08-19
Beware of the md_0d, i had alot of problems with it earlier.
It worked OK to stop and then remount the md0 but on reboot the md_0d came back.
 
I dont know if its the same for you but after googling it alot many seem to get it back after reboot.

---

