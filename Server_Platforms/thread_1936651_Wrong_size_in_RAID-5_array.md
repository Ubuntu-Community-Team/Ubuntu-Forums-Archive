---
title: "Wrong size in RAID-5 array"
date: 2012-03-06
forum: Server Platforms
---

### Post by Fahrbot on 2012-03-06
So this is the first time I'm using RAID and I started with a 2x2TB RAID-5 array since I only had two disks at the time. Yesterday I got my third 2TB disk and was going to expand my RAID array to a 3x2TB RAID-5.

So I used the following commands to expand my array and then let it resync.
```
sudo mdadm --add /dev/md0 /dev/sdd1 
sudo mdadm --grow /dev/md0 --raid-devices=3
```But after the resync I still only have 2TB available in my RAID array, ideas anyone?

```
fahrbot@Zoidberg:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Thu Feb 23 21:29:14 2012
     Raid Level : raid5
     Array Size : 3907023872 (3726.03 GiB 4000.79 GB)
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent

    Update Time : Tue Mar  6 17:04:53 2012
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : Zoidberg:0  (local to host Zoidberg)
           UUID : 187e4d9c:3d6379d7:74d70d32:60fe4e1a
         Events : 41684

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       2       8       33        1      active sync   /dev/sdc1
       3       8       49        2      active sync   /dev/sdd1

fahrbot@Zoidberg:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             222G   21G  190G  10% /
udev                  3.9G  8.0K  3.9G   1% /dev
tmpfs                 1.6G  624K  1.6G   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  3.9G     0  3.9G   0% /run/shm
/dev/md0              1.8T  1.6T  194G  89% /media/raid
```

---

### Post by ian dobson on 2012-03-06
Hi,

Now you need to expand your filesystem using resize2fs.

Regards
Ian Dobson

---

### Post by Fahrbot on 2012-03-06
Ah, thank you so much! After doing **resize2fs /dev/md0** everything works fine. \\:D/

---

