---
title: "RAID won't assemble: failed to add /dev/sda to /dev/md0: Invalid argument"
date: 2010-07-03
forum: Server Platforms
---

### Post by u-slayer on 2010-07-03
My hard drives kept dropping out of the raid array, so I finally identified the problem as a bad sata cable. I redid the wires and now when I try to assemble I get this:

```
mdadm -v --assemble --scan /dev/md0
mdadm: looking for devices for /dev/md0
mdadm: no recogniseable superblock on /dev/sde4
mdadm: /dev/sde4 has wrong uuid.
mdadm: no recogniseable superblock on /dev/sde3
mdadm: /dev/sde3 has wrong uuid.
mdadm: cannot open device /dev/sde2: Device or resource busy
mdadm: /dev/sde2 has wrong uuid.
mdadm: cannot open device /dev/sde1: Device or resource busy
mdadm: /dev/sde1 has wrong uuid.
mdadm: cannot open device /dev/sde: Device or resource busy
mdadm: /dev/sde has wrong uuid.
mdadm: /dev/sdd is identified as a member of /dev/md0, slot 2.
mdadm: /dev/sdc is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sdb is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sda is identified as a member of /dev/md0, slot 824.
mdadm: added /dev/sdb to /dev/md0 as 1
mdadm: added /dev/sdd to /dev/md0 as 2
mdadm: no uptodate device for slot 3 of /dev/md0
mdadm: failed to add /dev/sda to /dev/md0: Invalid argument
mdadm: added /dev/sdc to /dev/md0 as 0
mdadm: /dev/md0 assembled from 2 drives and -1 spares - not enough to start the array.

```


I tried examining each of the devices that are supposed to be in the array and I get confusing results:

```
mdadm --examine /dev/sda
/dev/sda:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 5ad42d4a:e216b702:e368bf24:bd0fce41
  Creation Time : Fri Oct  9 17:30:42 2009
     Raid Level : raid5
  Used Dev Size : 976762368 (931.51 GiB 1000.20 GB)
     Array Size : 2930287104 (2794.54 GiB 3000.61 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0

    Update Time : Fri Jul  2 23:32:57 2010
          State : active
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 57d3fc11 - expected 57d5b5fa
         Events : 698627

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this    72       0      955      824      faulty active sync write-mostly

   0     0       8       48        0      active sync   /dev/sdd
   1     1       0        0        1      faulty removed
   2     2       8       64        2      active sync   /dev/sde
   3     3       8       32        3      active sync   /dev/sdc

mdadm --examine /dev/sdb
/dev/sdb:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 5ad42d4a:e216b702:e368bf24:bd0fce41
  Creation Time : Fri Oct  9 17:30:42 2009
     Raid Level : raid5
  Used Dev Size : 976762368 (931.51 GiB 1000.20 GB)
     Array Size : 2930287104 (2794.54 GiB 3000.61 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Wed Jun 23 14:49:26 2010
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 57d24281 - correct
         Events : 697297

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     1       8       32        1      active sync   /dev/sdc

   0     0       8       48        0      active sync   /dev/sdd
   1     1       8       32        1      active sync   /dev/sdc
   2     2       8       64        2      active sync   /dev/sde
   3     3       8        0        3      active sync   /dev/sda

mdadm --examine /dev/sdc
/dev/sdc:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 5ad42d4a:e216b702:e368bf24:bd0fce41
  Creation Time : Fri Oct  9 17:30:42 2009
     Raid Level : raid5
  Used Dev Size : 976762368 (931.51 GiB 1000.20 GB)
     Array Size : 2930287104 (2794.54 GiB 3000.61 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0

    Update Time : Fri Jul  2 23:33:01 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 2
  Spare Devices : 0
       Checksum : 57dea532 - correct
         Events : 698629

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     0       8       48        0      active sync   /dev/sdd

   0     0       8       48        0      active sync   /dev/sdd
   1     1       0        0        1      faulty removed
   2     2       8       64        2      active sync   /dev/sde
   3     3       0        0        3      faulty removed


mdadm --examine /dev/sdd
/dev/sdd:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 5ad42d4a:e216b702:e368bf24:bd0fce41
  Creation Time : Fri Oct  9 17:30:42 2009
     Raid Level : raid5
  Used Dev Size : 976762368 (931.51 GiB 1000.20 GB)
     Array Size : 2930287104 (2794.54 GiB 3000.61 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0

    Update Time : Fri Jul  2 23:33:01 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 2
  Spare Devices : 0
       Checksum : 57dea546 - correct
         Events : 698629

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     2       8       64        2      active sync   /dev/sde

   0     0       8       48        0      active sync   /dev/sdd
   1     1       0        0        1      faulty removed
   2     2       8       64        2      active sync   /dev/sde
   3     3       0        0        3      faulty removed


```


I'm starting to think my data would be safer if it wasn't in a RAID array. Pls. Help

---

### Post by u-slayer on 2010-07-04
:p

---

### Post by fjgaude on 2010-07-04
I can't say what might be wrong... try using this command:

```
sudo mdadm -D /dev/md0
```

and see what it shows.

You might try a force command if you are certain your drives are good:

```
sudo mdadm --assemble --scan -f
```

Good luck!

---

### Post by u-slayer on 2010-07-05
I used --force and it worked just fine. Rebuilding Now.

---

### Post by u-slayer on 2010-07-05
I think RAID is actually more likely to loose all of your data then normal drives. With RAID you have to have at least 4 disks for it to make sense and then you put all of your data in one array. When you inevitably screw up a command you can easily wipe out all you data on the RAID. With hard drives you only loose the data on that individual drive.

---

### Post by fjgaude on 2010-07-07
It is wise to backup all data that are on a RAID array... it's standard policy in companies that never lose data. Please always have at least one backup of important stuff; I usually have three.

---

