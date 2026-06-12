---
title: "RAID5 help. Wont start"
date: 2010-02-02
forum: Server Platforms
---

### Post by hcker2000 on 2010-02-02
Hello some thing weird happened last night and my raid5 failed. I am trying to re activate it and see if my data is dead or what.

When I run mdadm -Asv /dev/md0 I get

```
mdadm: looking for devices for /dev/md0
mdadm: cannot open device /dev/dm-1: Device or resource busy
mdadm: /dev/dm-1 has wrong uuid.
mdadm: cannot open device /dev/dm-0: Device or resource busy
mdadm: /dev/dm-0 has wrong uuid.
mdadm: cannot open device /dev/sde2: Device or resource busy
mdadm: /dev/sde2 has wrong uuid.
mdadm: cannot open device /dev/sde1: Device or resource busy
mdadm: /dev/sde1 has wrong uuid.
mdadm: cannot open device /dev/sde: Device or resource busy
mdadm: /dev/sde has wrong uuid.
mdadm: cannot open device /dev/sdd: Device or resource busy
mdadm: /dev/sdd has wrong uuid.
mdadm: cannot open device /dev/sdc: Device or resource busy
mdadm: /dev/sdc has wrong uuid.
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: /dev/sdb has wrong uuid.
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: /dev/sda has wrong uuid.

```

I'm not sure whats up or how to fix this particular issue. Any help would be a life saver.

---

### Post by vpadro on 2010-02-02
Maybe this helps:

> 
sudo cat /proc/mdstat

and write down the line that shows the UUID, then:
> 
sudo nano /etc/mdadm/mdadm.conf

and check if its the correct UUID in:
> 
ARRAY /dev/md0 uuid=


then:
> 
sudo mdadm --detail /dev/md0


---

### Post by hcker2000 on 2010-02-02
Here are the results of the command in the order you posted.

```
Personalities : [raid6] [raid5] [raid4] 
md0 : inactive sdc[2](S) sdd[3](S) sdb[1](S) sda[0](S)
      3907049984 blocks

```

As you can see that dosnt list a UUID. This is my mdadm.conf file

```
DEVICE partitions
ARRAY /dev/md0 metadata=0.90 UUID=936cb745:496bfdbc:dc950017:ef97e63b

```

I ran mdadm --detail --scan and it gives me

```
mdadm: md device /dev/md0 does not appear to be active.
```

Not sure what else to try.

---

### Post by hcker2000 on 2010-02-02
This is the result of an fdisk -l in case it helps.

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
1 heads, 63 sectors/track, 31008336 cylinders
Units = cylinders of 63 * 512 = 32256 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               2    33546112  1056702496   40  Venix 80286
Partition 1 does not end on cylinder boundary.
/dev/sdd3               2    33546112  1056702496   40  Venix 80286
Partition 3 does not end on cylinder boundary.

Disk /dev/sde: 33.8 GB, 33820286976 bytes
255 heads, 63 sectors/track, 4111 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00095377

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1          26      204800   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sde2              26        4111    32816776   8e  Linux LVM

Disk /dev/dm-0: 30.5 GB, 30547116032 bytes
255 heads, 63 sectors/track, 3713 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/dm-1: 3053 MB, 3053453312 bytes
255 heads, 63 sectors/track, 371 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/dm-1 doesn't contain a valid partition table

```

---

### Post by hcker2000 on 2010-02-02
Here is a bit more info.

 mdadm --examine /dev/sda
```
/dev/sda:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 936cb745:496bfdbc:dc950017:ef97e63b (local to host hcker2000t1)
  Creation Time : Thu Jan  7 18:42:36 2010
     Raid Level : raid5
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
     Array Size : 2930287488 (2794.54 GiB 3000.61 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Mon Feb  1 19:42:33 2010
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 231822a0 - correct
         Events : 34082

         Layout : left-symmetric
     Chunk Size : 4K

      Number   Major   Minor   RaidDevice State
this     0       8        0        0      active sync   /dev/sda

   0     0       8        0        0      active sync   /dev/sda
   1     1       8       16        1      active sync   /dev/sdb
   2     2       8       32        2      active sync   /dev/sdc
   3     3       8       48        3      active sync   /dev/sdd

```

mdadm --examine /dev/sdb
```
/dev/sdb:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 936cb745:496bfdbc:dc950017:ef97e63b (local to host hcker2000t1)
  Creation Time : Thu Jan  7 18:42:36 2010
     Raid Level : raid5
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
     Array Size : 2930287488 (2794.54 GiB 3000.61 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Mon Feb  1 19:42:33 2010
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 231822b2 - correct
         Events : 34082

         Layout : left-symmetric
     Chunk Size : 4K

      Number   Major   Minor   RaidDevice State
this     1       8       16        1      active sync   /dev/sdb

   0     0       8        0        0      active sync   /dev/sda
   1     1       8       16        1      active sync   /dev/sdb
   2     2       8       32        2      active sync   /dev/sdc
   3     3       8       48        3      active sync   /dev/sdd

```

mdadm --examine /dev/sdc
```
/dev/sdc:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 936cb745:496bfdbc:dc950017:ef97e63b (local to host hcker2000t1)
  Creation Time : Thu Jan  7 18:42:36 2010
     Raid Level : raid5
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
     Array Size : 2930287488 (2794.54 GiB 3000.61 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Tue Feb  2 06:46:04 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 2318bf13 - correct
         Events : 34173

         Layout : left-symmetric
     Chunk Size : 4K

      Number   Major   Minor   RaidDevice State
this     2       8       32        2      active sync   /dev/sdc

   0     0       0        0        0      removed
   1     1       0        0        1      faulty removed
   2     2       8       32        2      active sync   /dev/sdc
   3     3       8       48        3      active sync   /dev/sdd

```

mdadm --examine /dev/sdd
```
/dev/sdd:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 936cb745:496bfdbc:dc950017:ef97e63b (local to host hcker2000t1)
  Creation Time : Thu Jan  7 18:42:36 2010
     Raid Level : raid5
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
     Array Size : 2930287488 (2794.54 GiB 3000.61 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Tue Feb  2 06:46:04 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 2318bf25 - correct
         Events : 34173

         Layout : left-symmetric
     Chunk Size : 4K

      Number   Major   Minor   RaidDevice State
this     3       8       48        3      active sync   /dev/sdd

   0     0       0        0        0      removed
   1     1       0        0        1      faulty removed
   2     2       8       32        2      active sync   /dev/sdc
   3     3       8       48        3      active sync   /dev/sdd

```

---

