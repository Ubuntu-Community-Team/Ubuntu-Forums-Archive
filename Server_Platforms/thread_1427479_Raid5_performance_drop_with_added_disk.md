---
title: "Raid5 performance drop with added disk"
date: 2010-03-11
forum: Server Platforms
---

### Post by Ellhound on 2010-03-11
I recently added a fourth disk(WD20EARS) to my raid5 array running on ICH10R. The other disks are all ST32000542AS. Recovery with this setup is ALOT slower than with the three disk array.(dropped from 75MB/s with 3 disk array to 20MB/s on 4 disk array) General performance seems ok, although I'm not an expert in this area. using hdparm -t gave me 300MB/s on the 4 disk array, and copying files to the array from a seperate drive was at around 75MB/s. I do not have read numbers for the three disk array, but I cant imagine them being higher, write speed was about 75MB/s.
hdparm -t on the seperate disks returns around 100MB/s for all the drives.

The system is running from a live USB drive while recovering, and is completely idle. 

I googled for ways to speed up recovery, and found some people saying to raise values in /proc/sys/dev/raid/speed_limit_min and /proc/sys/dev/raid/speed_limit_max, this did not help.

I'm wondering what is causing this performance drop

Specs:

Asus P5E-Q
C2D E7200
2GB ram 

```

ubuntu@ubuntu:~$ cat /proc/mdstat 
Personalities : [raid6] [raid5] [raid4] 
md0 : active raid5 sda1[4] sdb1[0] sdd1[2] sdc1[1]
      5860535808 blocks level 5, 64k chunk, algorithm 2 [4/3] [UUU_]
      [>....................]  recovery =  1.7% (34335104/1953511936) finish=1329.8min speed=24052K/sec
      
unused devices: <none>

```

```

ubuntu@ubuntu:~$ sudo mdadm -D /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Thu Mar  4 21:22:33 2010
     Raid Level : raid5
     Array Size : 5860535808 (5589.04 GiB 6001.19 GB)
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Mar 11 19:30:43 2010
          State : clean, degraded, recovering
 Active Devices : 3
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

 Rebuild Status : 1% complete

           UUID : da03124a:6addd333:e368bf24:bd0fce41 (local to host ubuntu)
         Events : 0.2191

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       4       8        1        3      spare rebuilding   /dev/sda1


```

---

### Post by Xianath on 2010-03-12
Personally, I don't have any of these drives yet so I can't speak from experience. From what I've read on these forums, I'd attribute it to the EARS having 4k-sized sectors. A grow operation requires reading an entire strip (3 stripes in your case), then writing it out anew over all four spindles. If that write happens to cross sector boundaries, the overhead is tremendous. This can happen if the partition you're using as an array component is not aligned to a 4k multiple. Google for "wd ears linux" to get the big picture and some clues.

HTH,
Peter

---

### Post by megamandos on 2010-10-19
This will erase the drives contents, but should solve your problem. You seem to be having an alignment issue.
I have an array of 4 x WD20EARS. What i had to do was this:

sudo -s
<enter your password>
apt-get install -y xfsprogs
parted /dev/(your WD20EARS)
mklabel gpt
<yes>
mkpart 
<whatever label you want for the partition>
xfs
2048
-1
<enter yes>
quit
mkifs.xfs /dev/(the new partition)
<wait for it to finish, should take like < 1 minute>

add the partition back into the array and rebuild.

---

