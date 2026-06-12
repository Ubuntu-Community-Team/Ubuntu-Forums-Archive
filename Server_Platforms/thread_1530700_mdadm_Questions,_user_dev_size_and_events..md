---
title: "mdadm Questions, user dev size and events."
date: 2010-07-14
forum: Server Platforms
---

### Post by xoddoza on 2010-07-14
Hey!

Well I installed by fresh copy of ubuntu last night, partitioned by disks, and started the raid setup and went to bed. Woke up this morning and found that it had encountered some errors in a drive sda in this case and had booted it out. Cool, doesn't worry me, glad I found it now rather than later.

I've just got a couple of questions i've not been able to find the answer too.

```
/dev/md0:
        Version : 01.02
  Creation Time : Tue Jul 13 20:44:41 2010
     Raid Level : raid6
     Array Size : 7325679040 (6986.31 GiB 7501.50 GB)
  Used Dev Size : 2930271616 (2794.52 GiB 3000.60 GB)
   Raid Devices : 7
  Total Devices : 6
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Jul 14 15:44:36 2010
          State : clean, degraded
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

           Name : entity:0  (local to host entity)
           UUID : f2bd306b:5161d5a6:498825fd:be29b25a
         Events : 1038

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1
       4       8       81        4      active sync   /dev/sdf1
       5       8       97        5      active sync   /dev/sdg1
       6       8      113        6      active sync   /dev/sdh1

```

Firstly, How come the Used Dev Size is 3000 GB. My friends arrays, the size is = too the size of one hdd.

Secondly, Events 1038. The Number of events seems to increase quite quickly. I've got it emailing me, but I've only received 2-3 emails about the degraded array status. What are the other evens likely to be, and is there a way to check them?

And thirdly, it thinks the version is 01.02 Is that a problem? Shouldn't it be 1.2?

Otherwise its going well. Getting 150 MB/s writes and 420 MB/s Reads while degraded.

7x 1.5 TB Samsung F2 Eco Green, and 1x 1tb Samsung F1 Os drive.

Thanks for your help!

---

### Post by seanharris on 2010-07-14
The usable capacity of a RAID 6 array is (N - 2) * *S*min, where *N* is the total number of drives in the array and *S*min is the capacity of the smallest drive in the array. 
 
What this means is that since you are using 1.5 and 1.0 TB drives your usable space per drive is reduced to 1.0 TB. Hope it helps.

---

### Post by xoddoza on 2010-07-14
> **seanharris said:**
> The usable capacity of a RAID 6 array is (N - 2) * *S*min, where *N* is the total number of drives in the array and *S*min is the capacity of the smallest drive in the array. 
 
What this means is that since you are using 1.5 and 1.0 TB drives your usable space per drive is reduced to 1.0 TB. Hope it helps.

The 1TB drive is the OS drive only. Not part of the raid set at all. So the raid 6 Array with 7x 1.5TB losing 2 too parity should be 7.5TB. After formatting it is all showing correctly, ie 6.8TB. I'm just curious as to the 'Used Dev Size' which is showing up as 3000 GB, and what that means. As well as the other two questions.

Thanks anyway :)

---

### Post by xoddoza on 2010-07-15
Anyone have any advances on those questions?

I'm not too worried I think, as it seems worked fine, and remounting correctly after restarts etc.

Next issue to tackle will be samba performance and permissions though.

---

### Post by jacekk015 on 2010-07-16
You have bought virtually 1,5TB.
I have on my laptop 250GB disk, and I see only 232GB.

[http://en.wikipedia.org/wiki/Hard_disk_drive](http://en.wikipedia.org/wiki/Hard_disk_drive)

```
Hard disk manufacturers quote disk capacity in [SI]("http://en.wikipedia.org/wiki/SI_prefix")-standard  powers of 1000, wherein a terabyte is 1000 gigabytes and a gigabyte is  1000 megabytes. With [file systems]("http://en.wikipedia.org/wiki/File_system") that measure capacity in powers of  1024, available space appears somewhat [less]("http://en.wikipedia.org/wiki/Binary_prefix#Inconsistent_use_of_units") than advertised capacity.
```

---

### Post by YesWeCan on 2010-07-16
[QUOTE=jacekk015]You have bought virtually 1,5TB.
I have on my laptop 250GB disk, and I see only 232GB.

Only in the world of computing can 250GB=232GB ;)
[http://en.wikipedia.org/wiki/Kilobyte](http://en.wikipedia.org/wiki/Kilobyte)

---

### Post by xoddoza on 2010-07-16
Thanks for the responses guys, however its not exactly what I'm asking. I fully understand the SI vs Computer usage of bits/bytes etc. Perhaps i'm not being clear enough.

My question is what does

```
Used Dev Size : 2930271616 (2794.52 GiB 3000.60 GB)
```

What is used dev size? Along with events, and my superblock version being reported as 01.02

---

### Post by jacekk015 on 2010-07-16
Maybe this?

[http://www.linuxquestions.org/questions/red-hat-31/what-does-used-dev-size-mean-mdadm-detail-767177/#post3746618](http://www.linuxquestions.org/questions/red-hat-31/what-does-used-dev-size-mean-mdadm-detail-767177/#post3746618)

---

