---
title: "Recover EXT4 partition from RAID 5 failure"
date: 2011-12-19
forum: Server Platforms
---

### Post by wehttamb on 2011-12-19
Hi. I had a raid 5 setup on my media server with 6 x 1tb drives. mdadm told me that 2 of the drives had failed but i recreated the array and then was informed that only 1 drive was down and the array was being repaired
```
matthew@server:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid5 sdd[6] sda[4] sdb[3] sdc[2] sdf[1] sdh[0]
      4883812480 blocks level 5, 64k chunk, algorithm 2 [6/5] [UUUUU_]
      [>....................]  recovery =  0.6% (6068096/976762496) finish=402.8min speed=40154K/sec

```
The problem is that now i cant find the ext4 partition to mount. The partition table has dissapeared. Here is what i get from fdisk -lu
```
Disk /dev/md1: 5001.0 GB, 5001023979520 bytes
2 heads, 4 sectors/track, 1220953120 cylinders, total 9767624960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 327680 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

```
Anyone have any suggestions on how i can recover the data?

---

### Post by rubylaser on 2011-12-19
What was the exact command you used to recreate the array.  If you didn't use the missing option, you caused the array to resync likely hosing your data :(

---

