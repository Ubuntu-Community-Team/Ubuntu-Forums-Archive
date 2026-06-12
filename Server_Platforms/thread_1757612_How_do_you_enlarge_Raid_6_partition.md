---
title: "How do you enlarge Raid 6 partition"
date: 2011-05-13
forum: Server Platforms
---

### Post by Antoniya001 on 2011-05-13
Hi, people.. (second post, don't shoot me.)
 
Reason of post : I am trying to grow my array to make full use of my drives.
I have a raid 6 using mdadm on my home server. The array used to consist of 6 1.5TB drives when it was created. Since then I've been replacing the 1.5TB drives with new 2TB drives. And now I have replaced the last 2 drives.
 
When I added the first 3 disks I did not use the whole disk for the raid partition but rather made it the same size as the 1.5 partitions. As it turns out this may have been a bad idea. (But it gave me another 3 partitions of 500GB that I turned into 1 disk using mhddfs.)
 
Now I'm trying to grow the array. I've been testing in a virtual enviroment on how to do it but I cannot find another method than this :
 
1) fail 1 disk.
2) re-partition the disk with the size of the whole disk.
3) re-add the drive as a spare.
4) start the now degraded array to let it resync.
5) wait quite a while. (aprox 5 hours)
6) start again from step 1 for the other disks.
7) use mdadm with grow command to enlarge the array
8) use resize2fs to fill array to max size
 
Now although since this is a raid 6, I keep some redundancy but I still worry about degrading the array so manny times and rebuilding the whole thing. I mean I read the thing out 3 or 4 times over doing this.
 
The question : Is there a better way to accomplish this ?
 
Arjan

---

### Post by rubylaser on 2011-05-13
This is going to take a very long time to do, and frankly mixing in the mhddfs disk combined from 3 disk partitions, you're really only running a RAID5.  As soon as you change 1 of those disks, you will lose both disks of parity that you have.

If this data is at all important to you, you really need to figure out a way to back it up before you do this.  Also, it will take much longer than 5 hours to sync 6 2TB disks (more like 15 hours) each time you do this.

The first disk you'll want to fail is the mhddfs disk as that's tied to 3 other disks anyways. But, again, the safest way to do this would be to backup, and just recreate the partitions and array properly and restore from backup.

---

### Post by Antoniya001 on 2011-05-14
```

root@IOSERV:/mnt# mdadm --detail --scan /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Sat Mar 12 12:57:04 2011
     Raid Level : raid6
     Array Size : 5860544512 (5589.05 GiB 6001.20 GB)
  Used Dev Size : 1465136128 (1397.26 GiB 1500.30 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0
    Persistence : Superblock is persistent
    Update Time : Sat May 14 09:09:51 2011
          State : clean, degraded, recovering
 Active Devices : 5
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 1
     Chunk Size : 1024K
 Rebuild Status : 0% complete
           UUID : 4412cd66:938bf29f:c2120627:d49a58dc
         Events : 0.363
    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       6       8       33        1      spare rebuilding   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1
       4       8       81        4      active sync   /dev/sdf1
       5       8       97        5      active sync   /dev/sdg1
[EMAIL="root@IOSERV:/mnt"]root@IOSERV:/mnt[/EMAIL]# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid6 sdc1[6] sdd1[2] sdf1[4] sde1[3] sdb1[0] sdg1[5]
      5860544512 blocks level 6, 1024k chunk, algorithm 2 [6/5] [U_UUUU]
      [>....................]  recovery =  0.2% (3210240/1465136128) finish=241.9min speed=100710K/sec
      
unused devices: <none>

```
 
It actually goes faster than I thought.. Did implement a lot of speed optimisations. max resync/max speed/big stripe cache and the whole process takes 3x 250min. Do not know how long the resize2fs will take though.
 
I got rid of most mhddfs disks and 2 of 3 disks are resynced.
 
The most important parts of the array have a backup (original actually), the rest of the array contains a lot of data but is not important enough to spend that ammount of cash on, to back it up.
 
Still would like to know if I could have done it in a single pass. Some setting in mdadm that would have enlarged the raid partitions on the disks to the full size.
 
Arjan

---

### Post by rubylaser on 2011-05-14
resizing the filesystem will only take a few minutes :)  That's very fast sync time.  I've never been able to get mine to sync that fast (more like 60 MB/s).  I would probably unmount the filesystem if you haven't done that already and do and fsck before each resize2fs, that way you ensure your filesystem is in good shape and stays that way :)

Just for my own info, what is your hardware, and what size do you have your min/max sync, and stripe cache size set at.  Because I also tweak those and more values besides. Thanks.

---

### Post by Antoniya001 on 2011-05-14
Drives are simple Samsung 2GB Sata drives 204UI. Server is a Asus P5Q board running a Pentium Dual Core E6500. Running 10.10 Ubuntu.
Raid card is an eight-port LSI MegaRAID® SAS 9240-8i. Not using the raid functions of the device and having the device on the x16 PCI-E port.
 
Biggest speed difference is from the LSI card. The build in Fake-raid cannot compete.
 
My create log :
 
create array :
sudo mdadm --create /dev/md0 --chunk=1024 --level=6 --raid-devices=6 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1 /dev/sdg1
Create filesystem :
sudo mkfs.ext4 /dev/md0
Create config file :
echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
Creeer mount point :pico /etc/fstab
mkdir /mnt/raid
Add in fstab :
/dev/md0 /mnt/raid ext4 defaults,nobootwait 1 2
Write speed increase :
pico /etc/udev/rules.d/set-raid-write-cache.rules
Add :
SUBSYSTEM=="block", KERNEL=="md*", ACTION=="change", TEST=="md/stripe_cache_size", ATTR{md/stripe_cache_size}="8192"
Check with :
cat /sys/block/md0/md/stripe_cache_size
Check rebuild speed
cat /proc/sys/dev/raid/speed_limit_min
cat /proc/sys/dev/raid/speed_limit_max
Set it higher :
echo 200000 > /proc/sys/dev/raid/speed_limit_min
echo 300000 > /proc/sys/dev/raid/speed_limit_max
 
Not done right now but can help :
 
echo 1024 > /sys/block/sdx/queue/read_ahead_kb
echo 256 > /sys/block/sdx/queue/nr_requests
 
Arjan

---

### Post by Antoniya001 on 2011-05-14
Reply to myself (hope it doesn't break any rule)..
 
After setting the last drive to 2TB mdadm has taken it on itself to grow the array !
 
Is that normal ? I haven't used the grow command. (I have used it before but not after replacing the last drive.)
 
When I did use the command it just entered without any feedback. This is my terminal from 19:30.. it seems to have started on its own.. Wondering if I will need to use the resize2fs command after. 
 
Did not see any of this in the virtual enviroment.
 
Arjan
 
root@IOSERV:/home/sinnige# mdadm --grow /dev/md0 --size=max
root@IOSERV:/home/sinnige# mdadm --detail /dev/md0
/dev/md0:
Version : 00.90
Creation Time : Sat Mar 12 12:57:04 2011
Raid Level : raid6
Array Size : 7814049792 (7452.06 GiB 8001.59 GB)
Used Dev Size : 1953512448 (1863.01 GiB 2000.40 GB)
Raid Devices : 6
Total Devices : 6
Preferred Minor : 0
Persistence : Superblock is persistent
Update Time : Sat May 14 19:32:51 2011
State : active, resyncing
Active Devices : 6
Working Devices : 6
Failed Devices : 0
Spare Devices : 0
Chunk Size : 1024K
Rebuild Status : 75% complete
UUID : 4412cd66:938bf29f:c2120627:d49a58dc
Events : 0.392
Number Major Minor RaidDevice State
0 8 17 0 active sync /dev/sdb1
1 8 33 1 active sync /dev/sdc1
2 8 49 2 active sync /dev/sdd1
3 8 65 3 active sync /dev/sde1
4 8 81 4 active sync /dev/sdf1
5 8 97 5 active sync /dev/sdg1
root@IOSERV:/home/sinnige# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid6 sdc1[1] sdd1[2] sdf1[4] sde1[3] sdb1[0] sdg1[5]
7814049792 blocks level 6, 1024k chunk, algorithm 2 [6/6] [UUUUUU]
[===============>.....] resync = 75.4% (1473706304/1953512448) finish=172.2min speed=94136K/sec
 
unused devices: <none>
 
Weird...
 
Update : still required resize2fs after this self expansion of the array.

---

