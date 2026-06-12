---
title: "Mess up my raid 5 array looking for ways to recover"
date: 2010-10-02
forum: Server Platforms
---

### Post by Ray-ubunter on 2010-10-02
Hi, 

My raid 5 array seems to have broken due to a hardware failure (strange thing remains that the failure seems to have coincided with a SW upgrade).

I have tried several attempts at recovery but only seem to be gettig in deeper and deeper.

First some details

My array contains 3 disks each with 2 200Gb partitions
out of this I created 2 raid arrays

/dev/md1 <- /dev/sda1 /dev/sdb1 /dev/sdc1 (raid 5)
/dev/md1 <- /dev/sda1 /dev/sdb1 /dev/sdc1 (raid 0)

At first it seemed that only the raid 5 was broken (which indeed would be odd), but at the moment neither array seems to come up.

I don't really care about the raid0 so I will focus on the raid5 array as this in theory should be recoverable.

By the initial looks of thing the /dev/sda1 disk seemed to be broken. So I tried to remove that and run the array with just sdb1 and sdc1, unfortunate I may have misinterpreted the data as I am now fairly convinced sdb1 is the drive that is broken.

So i detached sdb and try to run with just sdc and sda (by reading a). Unfortunately this resulted sda to be added as a spare (and a possible sync attempt, don't think however that there was actually any data written to the disk).

a bit more tinkering resulted in things looking like this:

remi@Sam:~/Desktop$ sudo mdadm --examine /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 7bc5c6a8:12ce4264:98c25d26:617376e8 (local to host Sam)
  Creation Time : Fri Aug  1 08:54:17 2008
     Raid Level : raid5
  Used Dev Size : 195350272 (186.30 GiB 200.04 GB)
     Array Size : 390700544 (372.60 GiB 400.08 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 1

    Update Time : Sat Oct  2 11:24:15 2010
          State : clean
 Active Devices : 1
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 1
       Checksum : d2d537fe - correct
         Events : 34636

         Layout : left-symmetric
     Chunk Size : 32K

      Number   Major   Minor   RaidDevice State
this     4       8        1        4      spare   /dev/sda1

   0     0       0        0        0      removed
   1     1       0        0        1      faulty removed
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       17        3      faulty   /dev/sdb1



remi@Sam:~/Desktop$ sudo mdadm --examine /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 7bc5c6a8:12ce4264:98c25d26:617376e8 (local to host Sam)
  Creation Time : Fri Aug  1 08:54:17 2008
     Raid Level : raid5
  Used Dev Size : 195350272 (186.30 GiB 200.04 GB)
     Array Size : 390700544 (372.60 GiB 400.08 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 1

    Update Time : Sat Oct  2 11:23:09 2010
          State : clean
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1
       Checksum : d2d537a9 - correct
         Events : 34624

         Layout : left-symmetric
     Chunk Size : 32K

      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       0        0        0      removed
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8        1        3      spare   /dev/sda1


remi@Sam:~/Desktop$ sudo mdadm --examine /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 7bc5c6a8:12ce4264:98c25d26:617376e8 (local to host Sam)
  Creation Time : Fri Aug  1 08:54:17 2008
     Raid Level : raid5
  Used Dev Size : 195350272 (186.30 GiB 200.04 GB)
     Array Size : 390700544 (372.60 GiB 400.08 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 1

    Update Time : Sat Oct  2 11:24:15 2010
          State : clean
 Active Devices : 1
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 1
       Checksum : d2d53820 - correct
         Events : 34636

         Layout : left-symmetric
     Chunk Size : 32K

      Number   Major   Minor   RaidDevice State
this     2       8       33        2      active sync   /dev/sdc1

   0     0       0        0        0      removed
   1     1       0        0        1      faulty removed
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       17        3      faulty   /dev/sdb1


If I try to assemble the array without sdb1 this happens

remi@Sam:~/Desktop$ sudo mdadm --assemble --verbose --force --update=resync /dev/md1 /dev/sda1 /dev/sdc1
mdadm: looking for devices for /dev/md1
mdadm: /dev/sda1 is identified as a member of /dev/md1, slot 4.
mdadm: /dev/sdc1 is identified as a member of /dev/md1, slot 2.
mdadm: no uptodate device for slot 0 of /dev/md1
mdadm: no uptodate device for slot 1 of /dev/md1
mdadm: added /dev/sda1 to /dev/md1 as 4
mdadm: added /dev/sdc1 to /dev/md1 as 2
mdadm: /dev/md1 assembled from 1 drive and 1 spare - not enough to start the array.

If I try to assemble it with sdb1

remi@Sam:~/Desktop$ sudo mdadm --assemble --verbose --force --update=resync /dev/md1 /dev/sda1 /dev/sdb1 /dev/sdc1
mdadm: looking for devices for /dev/md1
mdadm: /dev/sda1 is identified as a member of /dev/md1, slot 4.
mdadm: /dev/sdb1 is identified as a member of /dev/md1, slot 1.
mdadm: /dev/sdc1 is identified as a member of /dev/md1, slot 2.
mdadm: forcing event count in /dev/sdb1(1) from 34618 upto 34621
mdadm: no uptodate device for slot 0 of /dev/md1
mdadm: added /dev/sdc1 to /dev/md1 as 2
mdadm: added /dev/sda1 to /dev/md1 as 4
mdadm: added /dev/sdb1 to /dev/md1 as 1
mdadm: /dev/md1 has been started with 2 drives (out of 3) and 1 spare.


On paper (screen) this seems ok, but if I actually try to access the file system it appears clear that the array is not working properly (file system incomplete and drive making clicking noises).


So what I wonder is whether the is a way to force the array to start just sda and sdc in a way that sda is not seen as a spare.

I can imaging this may involve erasing the superblocks of some of the partitions but before attempting this I wanted to make sure to check with people that are a little bit more skilled than I am.

Thanks for any suggestions people may have.

Remi

---

