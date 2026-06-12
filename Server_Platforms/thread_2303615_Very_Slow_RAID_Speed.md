---
title: "Very Slow RAID Speed"
date: 2015-11-20
forum: Server Platforms
---

### Post by w.grim on 2015-11-20
Hello everybody. I set up a RAID5 with mdadm a couple of yours before. I use 1TB Western Digital Caviar Green Harddisks. The performance was good for a long time but it started to get very slow when one of the disks showed some SMART messages. 
```
Device: /dev/sdd, 839 Offline uncorrectable sectors
```

```
sudo smartctl -l selftest /dev/sdd
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       90%      6835         16088829
# 2  Conveyance offline  Completed: read failure       90%      6832         16088829
# 3  Short offline       Completed: read failure       90%      6831         16088829
# 4  Conveyance offline  Completed: read failure       90%      6821         16088823
# 5  Short offline       Completed: read failure       90%      6820         16088823
# 6  Conveyance offline  Completed: read failure       90%      6802         16089051
# 7  Short offline       Completed: read failure       90%      6801         16088823
# 8  Extended offline    Completed: read failure       90%      6779         16089120
# 9  Conveyance offline  Completed: read failure       90%      6778         16089051
#10  Short offline       Completed: read failure       90%      6777         16088823
#11  Short offline       Completed: read failure       10%      6758         16089120
#12  Short offline       Completed: read failure       10%      6746         16089120
#13  Short offline       Completed: read failure       10%      6694         16089120
#14  Short offline       Completed: read failure       10%      6625         16089120
#15  Short offline       Completed: read failure       10%      6590         16089120
#16  Conveyance offline  Completed: read failure       90%      6564         16088823
#17  Short offline       Completed: read failure       90%      6563         16088823
#18  Short offline       Interrupted (host reset)      10%      6561         -
#19  Conveyance offline  Completed: read failure       90%      6516         16088823
#20  Short offline       Completed: read failure       90%      6515         16089051
#21  Short offline       Completed: read failure       90%      6514         1608905
```

The average write speed now is about 1 MBit/s (!!) so there has to be a severe failure. Before I go on and buy a new harddisk to replace the failed disk I want to make sure that it's not the raid controller that is causing the very bad performance. Can you help me in troubleshooting?

In my oppinion the faulty disk alone cannot cause such a tremedous decrease in performance.

```
dd if=/dev/zero of=testfile0 bs=8k count=1000000; sync;
^C
67141+0 records in
67141+0 records out
550019072 bytes (550 MB) copied, 397.24 s, 1.4 MB/s
```

I also tried to tweack things by 
```
sudo echo 16384 > /sys/block/md0/md/stripe_cache_size
```

but this is just a buffer.

This is my mdadm config:
```
/media/grmdata/smbshare$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Sat Sep 26 13:07:46 2009
     Raid Level : raid5
     Array Size : 4395407808 (4191.79 GiB 4500.90 GB)
  Used Dev Size : 1465135936 (1397.26 GiB 1500.30 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Nov 20 11:55:44 2015
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 5f22807a:eed1b33c:c0438576:1a387ebe
         Events : 0.974306

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       8        1        1      active sync   /dev/sda1
       2       8       17        2      active sync   /dev/sdb1
       3       8       49        3      active sync   /dev/sdd1
```

---

### Post by tgalati4 on 2015-11-20
Welcome to the forums.

In my opinion, a faulty disk can cause a tremendous drop in performance.

"Green" drives are often a poor choice for a RAID pool because they tend to spin down and go into low-power mode at the wrong time causing data errors.  That is perhaps what happened.  It's also possible that one of your drives has developed an early failure.  The bathtub curve is still in effect.  You should expect 30 to 50K hours out of a disk drive, but quality-level will factor in.

Your best bet is to use Enterprise Class disk drives--the expensive ones, if you want a reliable RAID pool.  

Back up your data regardless.

---

