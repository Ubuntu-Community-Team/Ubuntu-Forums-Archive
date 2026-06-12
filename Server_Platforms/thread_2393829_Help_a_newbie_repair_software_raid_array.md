---
title: "Help a newbie repair software raid array"
date: 2018-06-08
forum: Server Platforms
---

### Post by heywesty on 2018-06-08
I'm struggling to understand how best to approach repairing a software raid 5 array. I've searched and read through other answers but I'm a bit confused due to the number of partitions I have on each of my drives. My server (running 16.10) suffered a failed drive a couple of days ago and now the drive has been replaced I'm not sure how to get it back into the array.

If I check the status of the raid array I can see a disk is missing:

```
 cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md2 : active raid5 sdd3[4] sda3[0] sdb3[1]
      1073347584 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/3] [UU_U]
      bitmap: 3/3 pages [12KB], 65536KB chunk


md3 : active raid5 sdd4[4] sda4[0] sdb4[1]
      7689919488 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/3] [UU_U]
      bitmap: 10/20 pages [40KB], 65536KB chunk


md1 : active raid1 sda2[0] sdb2[1] sdd2[3]
      523712 blocks super 1.2 [4/3] [UU_U]


md0 : active (auto-read-only) raid1 sda1[0] sdb1[1] sdd1[3]
      8380416 blocks super 1.2 [4/3] [UU_U]



```

If I check one of the disks still in the raid array I can see it's got a few partitions.

```

sudo fdisk -l /dev/sda
Disk /dev/sda: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 1988C885-FD94-48A8-A2A2-E6F9AD7FF991


Device         Start        End    Sectors   Size Type
/dev/sda1       4096   16781311   16777216     8G Linux RAID
/dev/sda2   16781312   17829887    1048576   512M Linux RAID
/dev/sda3   17829888  733657087  715827200 341.3G Linux RAID
/dev/sda4  733657088 5860533134 5126876047   2.4T Linux RAID
/dev/sda5       2048       4095       2048     1M BIOS boot


Partition table entries are not in disk order.

```

Checking a single instance gives me:

```

sudo mdadm -D /dev/md3
/dev/md3:
        Version : 1.2
  Creation Time : Sat Dec 17 16:07:34 2016
     Raid Level : raid5
     Array Size : 7689919488 (7333.68 GiB 7874.48 GB)
  Used Dev Size : 2563306496 (2444.56 GiB 2624.83 GB)
   Raid Devices : 4
  Total Devices : 3
    Persistence : Superblock is persistent


  Intent Bitmap : Internal


    Update Time : Fri Jun  8 19:24:17 2018
          State : clean, degraded
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 512K


           Name : rescue:3
           UUID : 6f002593:54be0ea8:b76dbddc:eda73d8f
         Events : 126525


    Number   Major   Minor   RaidDevice State
       0       8        4        0      active sync   /dev/sda4
       1       8       20        1      active sync   /dev/sdb4
       -       0        0        2      removed
       4       8       52        3      active sync   /dev/sdd4

```

And I can see that /dev/sdc has no partitions... so I'm guessing that's the new drive:

```
Disk /dev/sdc: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```

Could anyone help me out with instructions on how to get this new drive into my raid array please?

---

### Post by darkod on 2018-06-08
You just need to create identical partitions on sdc as on the other disks. Then you add each partition to the corresponding md device (array).

Personally I prefer using parted for checking and creating partitions. You can also use procedure to copy the partition table from one disk to the new one (which should be the easiest method). Just make sure the commend is correct.

If you want to check your current disk partitions with parted, you can do so with following command:
```
sudo parted /dev/sda unit MiB print
```

That will print you the details of sda.

---

### Post by darkod on 2018-06-08
According to this [https://askubuntu.com/questions/57908/how-can-i-quickly-copy-a-gpt-partition-scheme-from-one-hard-drive-to-another?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa](https://askubuntu.com/questions/57908/how-can-i-quickly-copy-a-gpt-partition-scheme-from-one-hard-drive-to-another?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa) you should be able to copy the partition table from sda to sdc easily with:
```
sudo apt-get install gdisk
sudo sgdisk /dev/sda -R /dev/sdc
sudo sgdisk -G /dev/sdc
```

After that you simply add the partition to the array where it needs to be, one by one... For example for sdc1 and md0 you would do:
```
sudo mdadm /dev/md0 --add /dev/sdc1
```

You will need to do that for all 4 arrays with the sdc partition that corresponds.

---

### Post by heywesty on 2018-06-08
Ah, thanks for the speedy response. I've come across this command:

```
sfdisk -d /dev/sdb | sfdisk /dev/sdc
```

Which appears to have done what you suggested to do with parted.

I've begun to add the corresponding partitions back in as per your suggested command. Seems to be going ok. Time-consuming but at least I've not lost any data. 

Many thanks [COLOR=#000000]darkod[/COLOR]!

---

### Post by darkod on 2018-06-08
Raid5 allows you to lose one disk without losing data. Now that you added new partitions in the arrays, they will automatically sync the data. You can check it with the cat /proc/mdstat from time to time. You will see when it has finished.

---

### Post by heywesty on 2018-06-09
Thanks so much for the assistance darkod. It's all back as it should be now in a clean state.

---

### Post by mörgæs on 2018-06-09
Good, please mark the thread solved.

---

