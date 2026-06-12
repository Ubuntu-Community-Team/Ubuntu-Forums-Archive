---
title: "RAID5 - mdadm - unable to reassemble (Ubuntu 10.04)"
date: 2011-10-06
forum: Server Platforms
---

### Post by Maximilian12 on 2011-10-06
Hello !

Here is my problem :
I have a RAID5 with 6 disks connected on 2 PCI SATA controlers :

SATA controler 1 : sdb +sdc + sdd
SATA controler 2 : sdf + sdg + sdh

Unfortunately SATA controler 1 has been disconnected from the motherboard.
After reconnecting it, my RAID5 has not restarted.

Here is the situation :
```

xxxxx@fileServer:~$ sudo mdadm --detail /dev/md1 
/dev/md1: 
        Version : 00.90 
  Creation Time : Fri Jun  3 19:13:20 2011 
     Raid Level : raid5 
  Used Dev Size : 1465138496 (1397.26 GiB 1500.30 GB) 
   Raid Devices : 6 
  Total Devices : 3 
Preferred Minor : 1 
    Persistence : Superblock is persistent 

    Update Time : Mon Oct  3 19:35:09 2011 
          State : active, degraded, Not Started 
 Active Devices : 3 
Working Devices : 3 
 Failed Devices : 0 
  Spare Devices : 0 

         Layout : left-symmetric 
     Chunk Size : 64K 

           UUID : c18137a6:e03017f7:723891a1:ae6943f6 (local to host fileServer) 
         Events : 0.196 

    Number   Major   Minor   RaidDevice State 
       0       0        0        0      removed 
       1       0        0        1      removed 
       2       0        0        2      removed 
       3       8       80        3      active sync   /dev/sdf 
       4       8       96        4      active sync   /dev/sdg 
       5       8      112        5      active sync   /dev/sdh 

```and

```

xxxxx@fileServer:~$ sudo mdadm --examine /dev/sd[bcdfgh]
/dev/sdb: 
          Magic : a92b4efc 
        Version : 00.90.00 
           UUID : c18137a6:e03017f7:723891a1:ae6943f6 (local to host fileServer) 
  Creation Time : Fri Jun  3 19:13:20 2011 
     Raid Level : raid5 
  Used Dev Size : 1465138496 (1397.26 GiB 1500.30 GB) 
     Array Size : 7325692480 (6986.32 GiB 7501.51 GB) 
   Raid Devices : 6 
  Total Devices : 6 
Preferred Minor : 1 

    Update Time : Sun Oct  2 21:22:18 2011 
          State : clean 
 Active Devices : 6 
Working Devices : 6 
 Failed Devices : 0 
  Spare Devices : 0 
       Checksum : 5f458599 - correct 
         Events : 192 

         Layout : left-symmetric 
     Chunk Size : 64K 

      Number   Major   Minor   RaidDevice State 
this     0       8       16        0      active sync   /dev/sdb 

   0     0       8       16        0      active sync   /dev/sdb 
   1     1       8       32        1      active sync   /dev/sdc 
   2     2       8       48        2      active sync   /dev/sdd 
   3     3       8       80        3      active sync   /dev/sdf 
   4     4       8       96        4      active sync   /dev/sdg 
   5     5       8      112        5      active sync   /dev/sdh 
/dev/sdc: 
          Magic : a92b4efc 
        Version : 00.90.00 
           UUID : c18137a6:e03017f7:723891a1:ae6943f6 (local to host fileServer) 
  Creation Time : Fri Jun  3 19:13:20 2011 
     Raid Level : raid5 
  Used Dev Size : 1465138496 (1397.26 GiB 1500.30 GB) 
     Array Size : 7325692480 (6986.32 GiB 7501.51 GB) 
   Raid Devices : 6 
  Total Devices : 6 
Preferred Minor : 1 

    Update Time : Sun Oct  2 21:22:18 2011 
          State : clean 
 Active Devices : 6 
Working Devices : 6 
 Failed Devices : 0 
  Spare Devices : 0 
       Checksum : 5f4585ab - correct 
         Events : 192 

         Layout : left-symmetric 
     Chunk Size : 64K 

      Number   Major   Minor   RaidDevice State 
this     1       8       32        1      active sync   /dev/sdc 

   0     0       8       16        0      active sync   /dev/sdb 
   1     1       8       32        1      active sync   /dev/sdc 
   2     2       8       48        2      active sync   /dev/sdd 
   3     3       8       80        3      active sync   /dev/sdf 
   4     4       8       96        4      active sync   /dev/sdg 
   5     5       8      112        5      active sync   /dev/sdh 
/dev/sdd: 
          Magic : a92b4efc 
        Version : 00.90.00 
           UUID : c18137a6:e03017f7:723891a1:ae6943f6 (local to host fileServer) 
  Creation Time : Fri Jun  3 19:13:20 2011 
     Raid Level : raid5 
  Used Dev Size : 1465138496 (1397.26 GiB 1500.30 GB) 
     Array Size : 7325692480 (6986.32 GiB 7501.51 GB) 
   Raid Devices : 6 
  Total Devices : 6 
Preferred Minor : 1 

    Update Time : Sun Oct  2 21:22:18 2011 
          State : clean 
 Active Devices : 6 
Working Devices : 6 
 Failed Devices : 0 
  Spare Devices : 0 
       Checksum : 5f4585bd - correct 
         Events : 192 

         Layout : left-symmetric 
     Chunk Size : 64K 

      Number   Major   Minor   RaidDevice State 
this     2       8       48        2      active sync   /dev/sdd 

   0     0       8       16        0      active sync   /dev/sdb 
   1     1       8       32        1      active sync   /dev/sdc 
   2     2       8       48        2      active sync   /dev/sdd 
   3     3       8       80        3      active sync   /dev/sdf 
   4     4       8       96        4      active sync   /dev/sdg 
   5     5       8      112        5      active sync   /dev/sdh 
/dev/sdf: 
          Magic : a92b4efc 
        Version : 00.90.00 
           UUID : c18137a6:e03017f7:723891a1:ae6943f6 (local to host fileServer) 
  Creation Time : Fri Jun  3 19:13:20 2011 
     Raid Level : raid5 
  Used Dev Size : 1465138496 (1397.26 GiB 1500.30 GB) 
     Array Size : 7325692480 (6986.32 GiB 7501.51 GB) 
   Raid Devices : 6 
  Total Devices : 6 
Preferred Minor : 1 

    Update Time : Mon Oct  3 19:35:09 2011 
          State : clean 
 Active Devices : 3 
Working Devices : 3 
 Failed Devices : 2 
  Spare Devices : 0 
       Checksum : 5f46be7b - correct 
         Events : 196 

         Layout : left-symmetric 
     Chunk Size : 64K 

      Number   Major   Minor   RaidDevice State 
this     3       8       80        3      active sync   /dev/sdf 

   0     0       0        0        0      removed 
   1     1       0        0        1      faulty removed 
   2     2       0        0        2      faulty removed 
   3     3       8       80        3      active sync   /dev/sdf 
   4     4       8       96        4      active sync   /dev/sdg 
   5     5       8      112        5      active sync   /dev/sdh 
/dev/sdg: 
          Magic : a92b4efc 
        Version : 00.90.00 
           UUID : c18137a6:e03017f7:723891a1:ae6943f6 (local to host fileServer) 
  Creation Time : Fri Jun  3 19:13:20 2011 
     Raid Level : raid5 
  Used Dev Size : 1465138496 (1397.26 GiB 1500.30 GB) 
     Array Size : 7325692480 (6986.32 GiB 7501.51 GB) 
   Raid Devices : 6 
  Total Devices : 6 
Preferred Minor : 1 

    Update Time : Mon Oct  3 19:35:09 2011 
          State : clean 
 Active Devices : 3 
Working Devices : 3 
 Failed Devices : 2 
  Spare Devices : 0 
       Checksum : 5f46be8d - correct 
         Events : 196 

         Layout : left-symmetric 
     Chunk Size : 64K 

      Number   Major   Minor   RaidDevice State 
this     4       8       96        4      active sync   /dev/sdg 

   0     0       0        0        0      removed 
   1     1       0        0        1      faulty removed 
   2     2       0        0        2      faulty removed 
   3     3       8       80        3      active sync   /dev/sdf 
   4     4       8       96        4      active sync   /dev/sdg 
   5     5       8      112        5      active sync   /dev/sdh 
/dev/sdh: 
          Magic : a92b4efc 
        Version : 00.90.00 
           UUID : c18137a6:e03017f7:723891a1:ae6943f6 (local to host fileServer) 
  Creation Time : Fri Jun  3 19:13:20 2011 
     Raid Level : raid5 
  Used Dev Size : 1465138496 (1397.26 GiB 1500.30 GB) 
     Array Size : 7325692480 (6986.32 GiB 7501.51 GB) 
   Raid Devices : 6 
  Total Devices : 6 
Preferred Minor : 1 

    Update Time : Mon Oct  3 19:35:09 2011 
          State : clean 
 Active Devices : 3 
Working Devices : 3 
 Failed Devices : 2 
  Spare Devices : 0 
       Checksum : 5f46be9f - correct 
         Events : 196 

         Layout : left-symmetric 
     Chunk Size : 64K 

      Number   Major   Minor   RaidDevice State 
this     5       8      112        5      active sync   /dev/sdh 

   0     0       0        0        0      removed 
   1     1       0        0        1      faulty removed 
   2     2       0        0        2      faulty removed 
   3     3       8       80        3      active sync   /dev/sdf 
   4     4       8       96        4      active sync   /dev/sdg 
   5     5       8      112        5      active sync   /dev/sdh 

```The full details are here :
[http://forum.ubuntu-fr.org/viewtopic.php?id=657191](http://forum.ubuntu-fr.org/viewtopic.php?id=657191)
It's in french but all print-screens are in english  ;)

How can I reassemble my RAID5 without any data lost ?

Many thanks,
Max

---

### Post by rubylaser on 2011-10-06
Have you tried to force the array back together?
```
sudo -i
mdadm --stop /dev/md1
mdadm --assemble --force /dev/md1 /dev/sd[bcdfgh]
```

Edit: It looks from the French forum that you've got a bunch of mdadm arrays running.  Can you post the output of these first?
```
cat /etc/mdadm/mdadm.conf
```
```
cat /proc/mdstat
```
* You'll want to stop all of the running arrays that contain disks from this array first, and then force the arrays together as I showed above.

---

### Post by Maximilian12 on 2011-10-07
Hi !

That's OK, it works ! :P

You're right, there was a half RAID5 running due to mdadm.conf, corresponding to an assembly try during system boot.

First I (re)add removed disks :
mdadm --add /dev/md1 /dev/sd[bcd]

Due to that, my RAID has been resynchronized (it tooks 10-15 minutes)

Then I stopped it (just to be sure that it will restart correctly) :
mdadm --stop /dev/md1

And then I reassembled it :
mdadm --assemble --force /dev/md1 /dev/sd[bcdfgh]

My RAID5 is now back online !

Many thanks !
Max.

---

