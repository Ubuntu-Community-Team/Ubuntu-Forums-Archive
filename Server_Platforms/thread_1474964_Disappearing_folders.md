---
title: "Disappearing folders"
date: 2010-05-06
forum: Server Platforms
---

### Post by msigley on 2010-05-06
I am perplexed as to why my Ubuntu 9.04 server just loses files sometimes. I am using ext3 on my system and data partitions. I have a software raid setup as follows:

Swap: RAID 1
System: RAID 1
DATA: RAID 5

Could anyone point me in the right direction as to figure out the cause.? I did a memtest yesterday and it came back clean.

---

### Post by BobVila on 2010-05-06
> **msigley said:**
> I am perplexed as to why my Ubuntu 9.04 server just loses files sometimes. I am using ext3 on my system and data partitions. I have a software raid setup as follows:

Swap: RAID 1
System: RAID 1
DATA: RAID 5

Could anyone point me in the right direction as to figure out the cause.? I did a memtest yesterday and it came back clean.

Where are the files that are being lost? On the system raid or the data raid?

---

### Post by msigley on 2010-05-07
Data RAID

---

### Post by msigley on 2010-05-10
No one has any idea where to look for filesystem errors?

---

### Post by TheFuturian on 2010-05-10
I'm not experienced with Ubuntu RAID, however there is normally some kind of log within the /var/log folder that gives some kind of insight. I'd start with:-

```
cat /var/log/dmesg | less
```

There is a folder named "fsck" within /var/log which is probably worth a check. Maybe if you could supply a little information about how you RAID array was/is configured then someone might chip in with better suggestions.

---

### Post by msigley on 2010-05-10
Ask and you shall recieve.

Checked the /var/log/dmesg, nothing that looks like a file system error just startup messages from the kernel.

Check the /var/log/fsck/ folder, two log files exist checkfs and checkroot both had the successful results of the last filesystem checks.

As far as details in how the RAID is setup goes, I have three SATA drives (sda, sdb, and sdc). I partitioned each of them into three partitions, a system partition, a swap partition, and a data partition where I have the Apache web folder located.

I ran a raid1 across three discs for the system and swap partitions and ran a raid5 across three discs for the data partition using the mdadm tool.

I have included the output of mdadm --detail for the three raid partitions.

System partition
> 
md0:
        Version : 00.90
  Creation Time : Sat Jun 27 13:25:04 2009
     Raid Level : raid1
     Array Size : 8787456 (8.38 GiB 9.00 GB)
  Used Dev Size : 8787456 (8.38 GiB 9.00 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon May 10 23:23:24 2010
          State : active
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

           UUID : 5bee0075:caca2274:cee93d59:f4c54711
         Events : 0.59

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1


Swap partition
> 
md1:
        Version : 00.90
  Creation Time : Sat Jun 27 13:27:20 2009
     Raid Level : raid1
     Array Size : 979840 (957.04 MiB 1003.36 MB)
  Used Dev Size : 979840 (957.04 MiB 1003.36 MB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Mon May 10 23:29:24 2010
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

           UUID : 6bd203fa:8324dd07:451f02b3:605ddb76
         Events : 0.76

    Number   Major   Minor   RaidDevice State
       0       8        2        0      active sync   /dev/sda2
       1       8       34        1      active sync   /dev/sdc2
       2       8       18        2      active sync   /dev/sdb2


Data partition
> 
md2:
        Version : 00.90
  Creation Time : Sat Jun 27 13:27:37 2009
     Raid Level : raid5
     Array Size : 136712960 (130.38 GiB 139.99 GB)
  Used Dev Size : 68356480 (65.19 GiB 70.00 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 2
    Persistence : Superblock is persistent

    Update Time : Mon May 10 18:41:45 2010
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : d9e17ac8:9da90fd2:365e9636:3f868293
         Events : 0.80

    Number   Major   Minor   RaidDevice State
       0       8        3        0      active sync   /dev/sda3
       1       8       19        1      active sync   /dev/sdb3
       2       8       35        2      active sync   /dev/sdc3


The server is an old Dell desktop I repurposed. I do daily restarts because it doesn't have ECC ram. Could this have anything to with the data loss on the RAID5?

PS. Thanks for the reply.

---

### Post by TheFuturian on 2010-05-11
> **msigley said:**
> I do daily restarts because it doesn't have ECC ram.

A volume may possibly need longer then a day to rebuild/resync if/when it needs to. Yes, this action could be the source of your woes. I don't understand why the lack of **_[parity]("http://en.wikipedia.org/wiki/RAM_parity")_** would be a reason for daily reboots. If you absolutely must do this then wouldn't monthly be a better timeframe to work with?

I think it's prudent to work out if the array is currently deemed "healthy" or "rebuilding". I think "State : clean" should suggest that it's healthy. It is probable that a better understanding of mdadm would provide answers to your questions..

[http://en.wikipedia.org/wiki/Mdadm](http://en.wikipedia.org/wiki/Mdadm)

---

### Post by msigley on 2010-05-11
After a few google searches, I determined that clean does in fact mean it is a healthy raid array. It will read status, active rebuilding if recovering from a drive error.

I have never see it read anything other than "clean" even right after a folder "disappears" on the data raid.

The daily restarts are more necessary because the server only 512MB of RAM and it will start using swap if I don't restart it, which makes it run slow. I am putting in another 1.5GB of RAM today so that issue should be resolved.

I always thought that running a server on non-ECC RAM will cause issues, which is why I thought daily/weekly restarts would be a good idea. Is this not the case?

One last thing anyone have an opinion on how often fsck should be run on my raid arrays?

---

