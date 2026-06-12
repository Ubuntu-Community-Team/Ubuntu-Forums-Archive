---
title: "Can someone help with my raid problem and get my server back up without losing it?"
date: 2014-02-03
forum: Server Platforms
---

### Post by Snaglpuss on 2014-02-03
FakeRaid question 
now I'm not a total noob but back when I was, started building my first server with 6.10, everything ran fine in 07 then i did an upgrade in place to 7.10 which crashed!! and not having time to mess with it till 08 i found out that out of 4 sata drives @300gb ea sdb failed but that was 6 months after the upgrade failed, related to video problems and ati rage xl issues that weren't solved and prevented it from booting to GUI and left me at intramfs which at the time i didn't understand.

so i tried to replace with another drive thinking rebuild was automatic which it wasn't. not having time since to go into 6 different directions of rebuilding i set the unit aside tho i had just transferred all my nas files over to build a bigger nas when the failure occurred. now, having finally removed myself from 80 hr work weeks and unbury all the other projects..

I finally got back to this one. after a few checks I found no bootable live versions that would give me video and GUI except 10.10 desktop, which showed a partial array. with that hope, I went to explore mdadm and found no working versions for 10.10 from term. legacy I guess. Since the array booted from the upgrade and died at console I tried and found that mdadm was available from the 7.10 upgrade. ran mdstat found the arrays md1 md2 active md0 inactive except for the failed one md0 then started having other failures after 24hrs of runtime. terminated the machine pulled a sata cable loose and replaced it and others with a new one and found the drives started to work without failure.

since i could not make the new drive work in the array and looked and had no superblock info much less uuids on any of the remaining arrays i figured out my method of madness of my original redundancy plan, created a 4 drive (only had 4 channels) raid 5 and then raid 1 the three internal partitions 1 a boot drive 1 a swap and 1 a data drive. since that time i have put back the original "bad drive" with a new cable and its the only one now with a uuid, date codes, and shows sync when all the rest show as spares and unknown statuses.

reading through all wikis have left me confused on how not to clobber my data by making a wrong mdadm or parted move, from this ver 7.10 mdadm. any help with directional restoration of the original raid and then the secondaries would be great oh and couldn't find an edit tool to even look at mdadm.conf from intramfs, so, what to do?.. i want to transfer that data back once i get this up! 

your help would be appreciated
Thanks

---

### Post by Snaglpuss on 2014-02-05
here is a list of examined drives 1234 are raid 5 and has 3 raid 1 partitions partition 1 is the one unable to respond 2 and 3 are boot and swap system boots to intramfs md 1 and 2 active md 0 inactive via mdstat

now it took 4 hours to boot and fix problem with video and ran 13.04 from live and this is what the latest mdadm e found...

ubuntu@ubuntu:~$ sudo mdadm -E /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 00000000:00000000:00000000:00000000
  Creation Time : Fri Jan 17 10:33:05 2014
     Raid Level : -unknown-
   Raid Devices : 0
  Total Devices : 3
Preferred Minor : 127

    Update Time : Fri Jan 17 10:35:55 2014
          State : active
 Active Devices : 0
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 3
       Checksum : 6045b19c - correct
         Events : 1


      Number   Major   Minor   RaidDevice State
this     2       8        1        2      spare   /dev/sda1

   0     0       8       65        0      spare   /dev/sde1
   1     1       8       33        1      spare   /dev/sdc1
   2     2       8        1        2      spare   /dev/sda1
ubuntu@ubuntu:~$ sudo mdadm -E /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : a09697a0:af946cb9:45b68825:38f0cff6
  Creation Time : Thu Nov 29 11:47:24 2007
     Raid Level : raid5
  Used Dev Size : 293049600 (279.47 GiB 300.08 GB)
     Array Size : 586099200 (558.95 GiB 600.17 GB)
   Raid Devices : 3
  Total Devices : 2
Preferred Minor : 0

    Update Time : Wed Jul  9 12:36:01 2008
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 1974269c - correct
         Events : 3837411

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
ubuntu@ubuntu:~$ sudo mdadm -E /dev/sdc1
/dev/sdc1:
   MBR Magic : aa55
Partition[0] :    432871117 sectors at   3224498923 (type 07)
Partition[1] :   1953460034 sectors at   3272020941 (type 16)
Partition[3] :    924335794 sectors at     50200576 (type 00)
ubuntu@ubuntu:~$ sudo mdadm -E /dev/sdd1
mdadm: No md superblock detected on /dev/sdd1.
ubuntu@ubuntu:~$ sudo mdadm -E /dev/sde1
/dev/sde1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 00000000:00000000:00000000:00000000
  Creation Time : Fri Jan 17 10:33:05 2014
     Raid Level : -unknown-
   Raid Devices : 0
  Total Devices : 3
Preferred Minor : 127

    Update Time : Fri Jan 17 10:35:55 2014
          State : active
 Active Devices : 0
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 3
       Checksum : 6045b1d8 - correct
         Events : 1


      Number   Major   Minor   RaidDevice State
this     0       8       65        0      spare   /dev/sde1

   0     0       8       65        0      spare   /dev/sde1
   1     1       8       33        1      spare   /dev/sdc1
   2     2       8        1        2      spare   /dev/sda1

---

