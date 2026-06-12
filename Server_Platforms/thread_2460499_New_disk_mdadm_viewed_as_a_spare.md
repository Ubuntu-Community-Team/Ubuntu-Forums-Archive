---
title: "New disk mdadm viewed as a spare"
date: 2021-04-12
forum: Server Platforms
---

### Post by mmmax on 2021-04-12
Hi,

I have a soft raid 10 on my server, and 1 disk failed, i replaced it and re synced it using mdam command 

At the beginning :

```
:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid0 md1[0] md2[1]
      11720778752 blocks super 1.2 512k chunks


md2 : active raid1 sdd1[2](S) sdc1[0]
      5860389696 blocks super 1.2 [2/1] [U_]


md1 : active raid1 sda1[0] sdb1[1]
      5860389696 blocks super 1.2 [2/2] [UU]
```


then i added "sdd1"
```
sudo mdadm --add /dev/md2 /dev/sdd1"
```
The disk begins to sync
```
md2 : active raid1 sdd1[2] sdc1[0]      5860389696 blocks super 1.2 [2/1] [U_]     
 [>....................]  recovery =  4.7% (276815616/5860389696) finish=512.4min speed=181595K/sec
```

But problem, after sync, the new synced disk is viewed as a spare 
```
    
Number   Major   Minor   RaidDevice State       
       0       8       33       0      active sync   /dev/sdc1
       1       0        0        1      removed


       2       8       49        -      spare   /dev/sdd1
```

How to change the disk from "spare" to "active" ?

I've read lot of old topics about it but no real answers..

Thanks
Max

---

### Post by slickymaster on 2021-04-12
Thread moved to **Server Platforms** for a better fit

---

### Post by darkod on 2021-04-12
Did you first remove the old failed member from md2?

Post the output of:
```
sudo mdadm -D /dev/md2
```

---

### Post by volkswagner on 2021-04-12
Interesting setup. It seems a bit unconventional
to build your own RAID10 array. Using a RAID0 from two MDADM mirrors.

At first, I thought you really only had a RAID0 (since the RAID0 was top-level) but
the reality seems you have the same redundancy and speed gain from
a typical MDADM RAID10 (conventional or not).

+1 for the removal first.

---

### Post by mmmax on 2021-04-13
Hi,

Thanks for answers, yes, the disk has been removed
Sync was made, but the disk remains as "spare"

Here is the result of  mdadm -D /dev/md2

```
Raid Level : raid1
     Array Size : 5860389696 (5588.90 GiB 6001.04 GB)
  Used Dev Size : 5860389696 (5588.90 GiB 6001.04 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Tue Apr 13 09:57:51 2021
          State : clean, degraded
 Active Devices : 1
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 1

           Name : server:2  (local to host server)
           UUID : 19b4b284:19eedea2:2e8552ff:dcb49fa1
         Events : 25976

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       0        0        1      removed


       2       8       49        -      spare   /dev/sdd1

.

```

---

### Post by darkod on 2021-04-13
You might hav removed the HDD itself, but in md2 you still have the slot #1 with the 'removed' device in it. Otherwise that line wouldn't be there.

I don't know if this is a bug, or is it because you are actually using md devices to create another layer of md device. The point being is that while you have that slot #1 filled, the new disk member will be as 'spare'.

---

### Post by rsteinmetz70112 on 2021-04-13
Did you mark the old drive as 'Failed"? I think that needs to be done before your "Remove" it, but it's been a while since I did this and I may be confused. 
I'm not sure how you do that without the drive being present with a device name.

---

### Post by mmmax on 2021-04-14
thanks for your answers

Yes, before removing the failed disk i did 
```
sudo mdadm --manage /dev/md2 --fail /dev/sdd1
sudo mdadm --manage /dev/md2 --remove /dev/sdd1
```

I wonder what will happen if I remove sdc1 ? Will sdd1 become active ?

---

### Post by darkod on 2021-04-14
What worries me is that you seem to have some strange situation. According to your last post you did both --fail and --remove which are the correct commands. But the slot #1 is still marked as taken.

I wouldn't recommend removing sdc1 because with sdd1 being spare I wouldn't count it has copy of the data.

You can search around on google, but I honestly don't know what to recommend you. I see on google some people had similar cases and basically ended up recreating the array from start with single disk (and the other member missing). And after that adding sdd1. Be very careful if you decide to go that way because if you want to keep the data you have to use --assume-clean parameter when creating new array from sdc1. Otherwise it will DELETE!!! all data!!

Bottom line, mdadm works really good and you shouldn't need to do any of this. It should have simply worked. Because any other actions you take have a certain level of risk involved.

---

