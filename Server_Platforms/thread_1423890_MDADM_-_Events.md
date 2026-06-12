---
title: "MDADM - Events?"
date: 2010-03-07
forum: Server Platforms
---

### Post by Go3Team on 2010-03-07
I currently have an 8 disk RAID 6 array that I have expanded twice offline and online.  

When I check the array using sudo mdadm --detail /dev/md0, I notice the number after events climbing.  I've tried searching and searching, but have not found the answer to what that number means, or where to find the log for MDADM.

```
burke@Media-Server:~$ sudo mdadm --detail /dev/md0
[sudo] password for burke:
mdadm: metadata format 00.90 unknown, ignored.
/dev/md0:
        Version : 00.90
  Creation Time : Fri Feb 12 12:36:20 2010
     Raid Level : raid6
     Array Size : 5860558848 (5589.06 GiB 6001.21 GB)
  Used Dev Size : 976759808 (931.51 GiB 1000.20 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Mar  7 07:51:19 2010
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 512K

           UUID : 373296bb:e8051edc:a1519ad4:a537d611 (local to host Media-Server)
         Events : 0.17352

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       8       65        1      active sync   /dev/sde1
       2       8       81        2      active sync   /dev/sdf1
       3       8       97        3      active sync   /dev/sdg1
       4       8      113        4      active sync   /dev/sdh1
       5       8      129        5      active sync   /dev/sdi1
       6       8       49        6      active sync   /dev/sdd1
       7       8      145        7      active sync   /dev/sdj1

```

Thanks

---

### Post by njparton on 2012-03-06
Any luck with this?  I'm wondering the same thing as my RAID 1 array has >40 events now...

---

### Post by Go3Team on 2012-03-06
No.

This is what it is looking like right now:

```

/dev/md0:
        Version : 00.90
  Creation Time : Fri Feb 12 12:36:20 2010
     Raid Level : raid6
     Array Size : 14651397120 (13972.66 GiB 15003.03 GB)
  Used Dev Size : 976759808 (931.51 GiB 1000.20 GB)
   Raid Devices : 17
  Total Devices : 18
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Mar  6 08:05:07 2012
          State : clean
 Active Devices : 17
Working Devices : 17
 Failed Devices : 1
  Spare Devices : 0

     Chunk Size : 512K

           UUID : 373296bb:e8051edc:a1519ad4:a537d611 (local to host Media-Server)
         Events : 0.434536

    Number   Major   Minor   RaidDevice State
       0       8       65        0      active sync   /dev/sde1
       1       8       97        1      active sync   /dev/sdg1
       2       8      113        2      active sync   /dev/sdh1
       3       8      129        3      active sync   /dev/sdi1
       4       8      145        4      active sync   /dev/sdj1
       5       8      161        5      active sync   /dev/sdk1
       6       8       81        6      active sync   /dev/sdf1
       7       8      177        7      active sync   /dev/sdl1
       8       8      209        8      active sync   /dev/sdn1
       9      65        1        9      active sync   /dev/sdq1
      10      65       17       10      active sync   /dev/sdr1
      11       8      225       11      active sync   /dev/sdo1
      12       8      241       12      active sync   /dev/sdp1
      13      65       49       13      active sync   /dev/sdt1
      14      65       33       14      active sync   /dev/sds1
      15       8       49       15      active sync   /dev/sdd1
      16       8       17       16      active sync   /dev/sdb1

      17       8      193        -      faulty spare   /dev/sdm1

```

Just had a drive go bad, and it automatically picked up the hot spare.  Still works like it did since day 1, over 2 years ago.

---

### Post by njparton on 2012-03-06
I've googled this a fair bit today but the word "events" is both specific to our question but also quite generic so it's difficult finding an answer.

I've tried all the mdadm switches I can find and none of them give me the detail I need.

I've not even managed to track down a mdadm log file to read through...

---

### Post by Go3Team on 2012-03-06
Just did a bit myself.

It seems the event counts I've seen were from someone posting the output of mdadm --detail.  The highest I saw was in the 700k range.  Mine is still 0.4X so I really don't know what to make of it.  As I said in the last post, everything functions normally.  The events figure has remained pretty much static for at least the last year.  I even did a grow a few weeks ago, and it stayed pretty close to the same, as well as Sunday when I lost a drive.  At this point, without finding any concrete reason that the events number exists, I'm not going to worry about it.

---

