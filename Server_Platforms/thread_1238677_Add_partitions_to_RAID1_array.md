---
title: "Add partitions to RAID1 array"
date: 2009-08-12
forum: Server Platforms
---

### Post by R.Bucky on 2009-08-12
I have a RAID1 array with a hot spare. My partitions are configured  with 15GB for the '/' directory, a swap, and 230 GB for my webserver files. I checked my array and realized that I only added the '/' partition to the array. How would I add my webserver files partition to the array? Would I need to create another directory of /dev/md1 for the webserver files and then use this command?
```
mdadm --assemble /dev/md1 /dev/sda2 /dev/sdb2 /dev/sdc2
```

I assume that I would include the hot spare in the --assemble command. Here is my current config.
```
/dev/md0:
        Version : 00.90.03
  Creation Time : Thu May 28 20:40:36 2009
     Raid Level : raid1
     Array Size : 14651200 (13.97 GiB 15.00 GB)
  Used Dev Size : 14651200 (13.97 GiB 15.00 GB)
   Raid Devices : 2
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Aug 12 14:08:37 2009
          State : clean
 Active Devices : 2
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 2

           UUID : b5a7d2ec:b3fbedb9:0e71e86d:fe45bc84
         Events : 0.20

    Number   Major   Minor   RaidDevice State
       0       8       18        0      active sync   /dev/sdb2
       1       8       19        1      active sync   /dev/sdb3

       2       8       33        -      spare   /dev/sdc1
       3       8       34        -      spare   /dev/sdc2

```

---

### Post by alastair on 2009-08-12
Something seems wrong there ... you have a RAID 1 mirror with :

a) 4 partitions!
b) 2 partitions mirrored on the same disk (sdb2,sdb3)
c) The other 2 spare

Firstly - I hope you have backups of any data because you might need to start again.

You can get rid of the spares (I think) via :

mdadm --manage /dev/md0 --remove /dev/sdc1
mdadm --manage /dev/md0 --remove /dev/sdc2

But that still leaves you with a silly /dev/md0 "mirror".

I'd start again if possible.


Creation would be something like :

mdadm --create /dev/md1 --level=1 --raid-devices=2 /dev/sdb2 /dev/sdc2
mdadm --create /dev/md2 --level=1 --raid-devices=2 /dev/sdb3 /dev/sdc3

Note - RAID-1 "mirror" generally has 2 devices mirrored e.g.

<code>
Disk sda  |-- a1 --|-- a2 --|---- a3 ----|
Disk sdb  |-- b1 --|-- b2 --|---- b3 ----|

Giving : 

md0 = a1 + b1
md2 = a2 + b2
md3 = a3 + b3 etc.
</code>

---

### Post by R.Bucky on 2009-08-12
the mdadm query does show 4 partitions. I inserted a formatted ext3 for file storage independent of the array. It does appear that the array is FUBAR. damn it Jim! I'm a doctor... I will backup my files and try repairing the array.

---

