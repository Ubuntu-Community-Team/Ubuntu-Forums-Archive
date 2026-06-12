---
title: "ZFS create"
date: 2024-09-16
forum: Server Platforms
---

### Post by sgt-mike on 2024-09-16
Just starting out on ZFS. 
I did a test run of some scrub laptop drive in six drive  1- 5.25" bay enclosure (Sata only and thin drives I think 2.5" 9mm or less for each bay) to create a pool which I will destroy as many here have warned against the usage of laptop drive within any type of RAID configuration method.
Like I said this was a test before the arrival of actual enterprise class drives and a supporting HBA/cabling arrives within the next 2 weeks
```


mike@beastie:~$ zpool status
  pool: teststore
 state: ONLINE
  scan: scrub repaired 0B in 00:00:26 with 0 errors on Sun Sep 15 07:19:36 2024
config:


        NAME        STATE     READ WRITE CKSUM
        teststore   ONLINE       0     0     0
          raidz1-0  ONLINE       0     0     0
            sda1    ONLINE       0     0     0
            sdb1    ONLINE       0     0     0
            sdc1    ONLINE       0     0     0
            sdd1    ONLINE       0     0     0
            sde1    ONLINE       0     0     0
        spares
          sdf1      AVAIL


errors: No known data errors
mike@beastie:~$ zpool list
NAME        SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
teststore  2.27T   504G  1.77T        -         -     0%    21%  1.00x    ONLINE  -
mike@beastie:~$ zpool list
NAME        SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
teststore  2.27T   566G  1.71T        -         -     0%    24%  1.00x    ONLINE  -
mike@beastie:~$ zpool list
NAME        SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
teststore  2.27T   858G  1.43T        -         -     0%    36%  1.00x    ONLINE  -
mike@beastie:~$ zpool list
NAME        SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
teststore  2.27T  1018G  1.27T        -         -     0%    43%  1.00x    ONLINE  -
mike@beastie:~$ zpool list
NAME        SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
teststore  2.27T  1.02T  1.24T        -         -     0%    45%  1.00x    ONLINE  -
mike@beastie:~$ zpool status
  pool: teststore
 state: ONLINE
  scan: scrub repaired 0B in 00:00:26 with 0 errors on Sun Sep 15 07:19:36 2024
config:


        NAME        STATE     READ WRITE CKSUM
        teststore   ONLINE       0     0     0
          raidz1-0  ONLINE       0     0     0
            sda1    ONLINE       0     0     0
            sdb1    ONLINE       0     0     0
            sdc1    ONLINE       0     0     0
            sdd1    ONLINE       0     0     0
            sde1    ONLINE       0     0     0
        spares
          sdf1      AVAIL


errors: No known data errors
mike@beastie:~$ zpool list
NAME        SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
teststore  2.27T  1.22T  1.05T        -         -     0%    53%  1.00x    ONLINE  -
mike@beastie:~$ zpool list
NAME        SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
teststore  2.27T  1.23T  1.04T        -         -     0%    54%  1.00x    ONLINE  -
mike@beastie:~$ zpool list
NAME        SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
teststore  2.27T  1.34T   947G        -         -     0%    59%  1.00x    ONLINE  -
mike@beastie:~$ zpool iostat -vl teststore
              capacity     operations     bandwidth    total_wait     disk_wait    syncq_wait    asyncq_wait  scrub   trim
pool        alloc   free   read  write   read  write   read  write   read  write   read  write   read  write   wait   wait
----------  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----
teststore   1.34T   947G      0    239  2.84K  39.9M   30ms    7ms   30ms    3ms    1us    1us    4us    3ms   52ms      -
  raidz1-0  1.34T   947G      0    239  2.84K  39.9M   30ms    7ms   30ms    3ms    1us    1us    4us    3ms   52ms      -
    sda1        -      -      0     49    564  7.98M   30ms    6ms   29ms    3ms    1us    2us    1us    2ms   28ms      -
    sdb1        -      -      0     49    623  7.98M   30ms    7ms   30ms    3ms    2us    1us    1us    3ms   62ms      -
    sdc1        -      -      0     49    575  7.98M   30ms    6ms   29ms    3ms    1us    1us   16us    2ms   50ms      -
    sdd1        -      -      0     45    573  7.98M   32ms    8ms   31ms    4ms    1us    1us    1us    4ms   60ms      -
    sde1        -      -      0     46    572  7.98M   30ms    7ms   29ms    4ms    1us    1us    1us    3ms   63ms      -
----------  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----
mike@beastie:~$ zpool list
NAME        SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
teststore  2.27T  1.34T   947G        -         -     0%    59%  1.00x    ONLINE  -
mike@beastie:~$ zpool status
  pool: teststore
 state: ONLINE
  scan: scrub repaired 0B in 00:00:26 with 0 errors on Sun Sep 15 07:19:36 2024
config:


        NAME        STATE     READ WRITE CKSUM
        teststore   ONLINE       0     0     0
          raidz1-0  ONLINE       0     0     0
            sda1    ONLINE       0     0     0
            sdb1    ONLINE       0     0     0
            sdc1    ONLINE       0     0     0
            sdd1    ONLINE       0     0     0
            sde1    ONLINE       0     0     0
        spares
          sdf1      AVAIL


errors: No known data errors
mike@beastie:~$ lsblk
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
loop0         7:0    0  63.9M  1 loop /snap/core20/2105
loop1         7:1    0  63.9M  1 loop /snap/core20/2318
loop2         7:2    0    87M  1 loop /snap/lxd/27037
loop3         7:3    0    87M  1 loop /snap/lxd/29351
loop4         7:4    0  40.4M  1 loop /snap/snapd/20671
loop5         7:5    0  38.8M  1 loop /snap/snapd/21759
sda           8:0    0 465.8G  0 disk
&#9492;&#9472;sda1        8:1    0 465.8G  0 part
sdb           8:16   0 465.8G  0 disk
&#9492;&#9472;sdb1        8:17   0 465.8G  0 part
sdc           8:32   0 465.8G  0 disk
&#9492;&#9472;sdc1        8:33   0 465.8G  0 part
sdd           8:48   0 465.8G  0 disk
&#9492;&#9472;sdd1        8:49   0 465.8G  0 part
sde           8:64   0 465.8G  0 disk
&#9492;&#9472;sde1        8:65   0 465.8G  0 part
sdf           8:80   0 465.8G  0 disk
&#9492;&#9472;sdf1        8:81   0 465.8G  0 part
nvme0n1     259:0    0 238.5G  0 disk
&#9500;&#9472;nvme0n1p1 259:1    0     1G  0 part /boot/efi
&#9492;&#9472;nvme0n1p2 259:2    0 237.4G  0 part/

```

It went well so far, and I'm impressed with the ease, although still learning. 

But it started me to thinking, thus leading to an actual question. 

 I had seen a post/article elsewhere where a person assigned an alias to the drives versus them just using the standard /dev/sd*# method. Which seems to make some sense in order to cleanly track down a faulty drive. 
(I'll have to reread the article/post as I don't recall if when he assembled if he used the assigned alias or drive id, but I think he used the alias)

 I've seen where others use the drive ID, which makes a lot of sense vs the method I used. 

In creating a pool with the incoming SAS drives (6 - 4TB each), which is the best method to assembling the drives into a single zpool? 
I know that is a subjective question.  

(this will be in a NAS/NFS machine to back up media from the Plex server, and basically some documents such as tax stamp documents from ATF & DD214's.  Which I'm planning on using wakon lan configuration so it's not on 24x7)

---

### Post by sgt-mike on 2024-09-18
While I have been waiting on a response on the above post I played with striped pools and Raisz1 in differing scenarios / configurations. meanwhile reading various write ups. 
Ran across one that discussed the 512 vs the 4096 alignment of the pool. so I decided to try it.

```
mike@beastie:~$ mike@beastie:~$ sudo zpool historyHistory for 'testpool':
2024-09-17.23:04:14 zpool create -o ashift=12 testpool raidz1 sda1 sdb1 sdc1 sdd1 sde1 -f
2024-09-17.23:15:13 zfs set compress=lz4 testpool


# checking for the Pools Algined sectors is 4K aka ashift 12 which if memory serves me correct for a 512 the ashift value is 9


mike@beastie:~$  sudo zdb -C testpool | grep ashift
                ashift: 12


# ok great all the drives are aligned 


mike@beastie:~$ sudo zpool status
  pool: testpool
 state: ONLINE
config:


        NAME        STATE     READ WRITE CKSUM
        testpool    ONLINE       0     0     0
          raidz1-0  ONLINE       0     0     0
            sda1    ONLINE       0     0     0
            sdb1    ONLINE       0     0     0
            sdc1    ONLINE       0     0     0
            sdd1    ONLINE       0     0     0
            sde1    ONLINE       0     0     0


errors: No known data errors
mike@beastie:~$ sudo zpool list
NAME       SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
testpool  2.27T  22.8G  2.24T
mike@beastie:~$ sudo zpool iostat -vl 30 5
              capacity     operations     bandwidth    total_wait     disk_wait    syncq_wait    asyncq_wait  scrub   trim
pool        alloc   free   read  write   read  write   read  write   read  write   read  write   read  write   wait   wait
----------  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----
testpool     190G  2.08T      0    507  1.59K  96.6M   32ms    6ms   32ms    3ms    1us    1us      -    2ms      -      -
  raidz1-0   190G  2.08T      0    507  1.59K  96.6M   32ms    6ms   32ms    3ms    1us    1us      -    2ms      -      -
    sda1        -      -      0    109    309  19.3M   25ms    5ms   25ms    3ms    1us    1us      -    2ms      -      -
    sdb1        -      -      0    104    286  19.3M   33ms    5ms   33ms    3ms    1us  953ns      -    2ms      -      -
    sdc1        -      -      0     95    271  19.3M   31ms    7ms   31ms    4ms    1us  998ns      -    3ms      -      -
    sdd1        -      -      0     93    470  19.3M   37ms    8ms   37ms    4ms    2us  975ns      -    3ms      -      -
    sde1        -      -      0    105    288  19.3M   25ms    5ms   25ms    3ms    1us    1us      -    2ms      -      -
----------  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----
              capacity     operations     bandwidth    total_wait     disk_wait    syncq_wait    asyncq_wait  scrub   trim
pool        alloc   free   read  write   read  write   read  write   read  write   read  write   read  write   wait   wait
----------  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----
testpool     194G  2.08T      0    813    955   139M   25ms    5ms   25ms    3ms    2us    1us      -    2ms      -      -
  raidz1-0   194G  2.08T      0    813    955   139M   25ms    5ms   25ms    3ms    2us    1us      -    2ms      -      -
    sda1        -      -      0    174      0  27.8M      -    4ms      -    2ms      -    1us      -    1ms      -      -
    sdb1        -      -      0    163    136  27.8M   25ms    4ms   25ms    3ms    1us  816ns      -    1ms      -      -
    sdc1        -      -      0    158    136  27.8M   25ms    6ms   25ms    3ms    3us  928ns      -    2ms      -      -
    sdd1        -      -      0    150    682  27.8M   25ms    6ms   25ms    3ms    2us  976ns      -    2ms      -      -
    sde1        -      -      0    166      0  27.8M      -    4ms      -    3ms      -    1us      -    1ms      -      -
----------  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----
              capacity     operations     bandwidth    total_wait     disk_wait    syncq_wait    asyncq_wait  scrub   trim
pool        alloc   free   read  write   read  write   read  write   read  write   read  write   read  write   wait   wait
----------  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----
testpool     198G  2.07T      0    647    819   131M   25ms    7ms   25ms    4ms    1us    1us      -    3ms      -      -
  raidz1-0   198G  2.07T      0    647    819   131M   25ms    7ms   25ms    4ms    1us    1us      -    3ms      -      -
    sda1        -      -      0    144      0  26.2M      -    5ms      -    3ms      -    1us      -    2ms      -      -
    sdb1        -      -      0    139    409  26.2M   20ms    6ms   20ms    3ms    1us    1us      -    2ms      -      -
    sdc1        -      -      0    117    136  26.2M   12ms   10ms   12ms    5ms  768ns    1us      -    4ms      -      -
    sdd1        -      -      0    117    273  26.2M   37ms    9ms   37ms    5ms    1us    1us      -    4ms      -      -
    sde1        -      -      0    128      0  26.2M      -    6ms      -    4ms      -    1us      -    3ms      -      -
----------  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----
              capacity     operations     bandwidth    total_wait     disk_wait    syncq_wait    asyncq_wait  scrub   trim
pool        alloc   free   read  write   read  write   read  write   read  write   read  write   read  write   wait   wait
----------  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----
testpool     202G  2.07T      0    567    819   139M   31ms    9ms   31ms    5ms    1us  876ns      -    4ms      -      -
  raidz1-0   202G  2.07T      0    567    819   139M   31ms    9ms   31ms    5ms    1us  876ns      -    4ms      -      -
    sda1        -      -      0    115      0  27.8M      -    9ms      -    5ms      -    1us      -    4ms      -      -
    sdb1        -      -      0    116    136  27.8M   25ms    9ms   25ms    5ms    1us  752ns      -    4ms      -      -
    sdc1        -      -      0    110    409  27.8M   29ms    9ms   29ms    5ms    1us  720ns      -    4ms      -      -
    sdd1        -      -      0    102    273  27.8M   37ms   11ms   37ms    6ms  768ns  752ns      -    5ms      -      -
    sde1        -      -      0    122      0  27.8M      -    7ms      -    4ms      -  912ns      -    3ms      -      -
----------  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----
              capacity     operations     bandwidth    total_wait     disk_wait    syncq_wait    asyncq_wait  scrub   trim
pool        alloc   free   read  write   read  write   read  write   read  write   read  write   read  write   wait   wait
----------  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----
testpool     205G  2.07T      0    573    682   132M   20ms    8ms   20ms    4ms    2us    1us      -    4ms      -      -
  raidz1-0   205G  2.07T      0    573    682   132M   20ms    8ms   20ms    4ms    2us    1us      -    4ms      -      -
    sda1        -      -      0    122    136  26.4M   25ms    7ms   25ms    4ms  768ns    1us      -    3ms      -      -
    sdb1        -      -      0    116      0  26.3M      -    8ms      -    4ms      -  787ns      -    3ms      -      -
    sdc1        -      -      0    109    136  26.4M   12ms    9ms   12ms    5ms  768ns  844ns      -    4ms      -      -
    sdd1        -      -      0    102    273  26.4M   18ms   10ms   18ms    6ms    4us  921ns      -    5ms      -      -
    sde1        -      -      0    122    136  26.4M   25ms    7ms   25ms    4ms  768ns  979ns      -    3ms      -      -
----------  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----
mike@beastie:~$
```

when I ran the iostat I had my plex server (second gen i7) sending data to the NAS/NFS via scp,   for my 2GB files the transfer was approx 15 secs or less. 

When I tried a pool that wasn't aligned I had a little higher bandwidth on the writes(by about 2 MB) but my reads was lower than with the sectors aligned. 
For some strange reason out of the 5 test drives I'm using /dev/sba1 was I/O min optimal at 4096 but the rest of the drive reported 512
```

mike@beastie:~$ sudo fdisk -l /dev/sd[abcde][sudo] password for mike:
Disk /dev/sda: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk model: TOSHIBA MQ01ABF0
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: D8F0C9C3-F33A-284C-B647-5DE4701FD79D


Device     Start       End   Sectors   Size Type
/dev/sda1   2048 976773134 976771087 465.8G Linux filesystem




Disk /dev/sdb: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk model: TOSHIBA MQ01ABF0
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 31DAF47B-2E32-7740-BFE9-6EB48600A314


Device     Start       End   Sectors   Size Type
/dev/sdb1   2048 976773134 976771087 465.8G Linux filesystem




Disk /dev/sdc: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk model: TOSHIBA MQ01ABF0
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: F81E7542-8C6C-AC42-B52D-5333E42A1063


Device     Start       End   Sectors   Size Type
/dev/sdc1   2048 976773134 976771087 465.8G Linux filesystem




Disk /dev/sdd: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk model: TOSHIBA MQ01ABF0
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: CA5AEF9E-6E7E-0043-9477-06D2CF49999B


Device     Start       End   Sectors   Size Type
/dev/sdd1   2048 976773134 976771087 465.8G Linux filesystem




Disk /dev/sde: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk model: TOSHIBA MQ01ABF0
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 465CD09B-2631-844D-A651-A3632B376784


Device     Start       End   Sectors   Size Type
/dev/sde1   2048 976773134 976771087 465.8G Linux filesystem
mike@beastie:~$
```

Part of the reason I'm posting this is I'm not 100% sure if a higher bandwidth on read write is actually better. I'm assuming it is. 
I even tried a pool with 3 drives in one raidz1-0 (vdev) and the other two drives in a raidz1-1 (vdev) into one pool. 

The only downside I can think of in my testing is that it will be dependent on my network throughput. I could use FIO but not familiar with it yet.

---

### Post by sgt-mike on 2024-09-18
I stumbled upon some fio commands for benchmarking ran some test on the testpool . 
Here are the results

```

mike@beastie:/testpool$ sync;fio --randrepeat=1 --ioengine=libaio --direct=1 --name=test --filename=test --bs=4M --size=4G --readwrite=write --ramp_time=4test: (g=0): rw=write, bs=(R) 4096KiB-4096KiB, (W) 4096KiB-4096KiB, (T) 4096KiB-4096KiB, ioengine=libaio, iodepth=1
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][30.8%][w=216MiB/s][w=54 IOPS][eta 00m:18s]
test: (groupid=0, jobs=1): err= 0: pid=1777710: Wed Sep 18 11:33:46 2024
  write: IOPS=54, BW=221MiB/s (231MB/s)(844MiB/3825msec); 0 zone resets
    slat (usec): min=16906, max=20276, avg=18196.26, stdev=739.38
    clat (nsec): min=1620, max=19497, avg=4672.02, stdev=2344.46
     lat (usec): min=16912, max=20278, avg=18207.51, stdev=736.89
    clat percentiles (nsec):
     |  1.00th=[ 1688],  5.00th=[ 1960], 10.00th=[ 2288], 20.00th=[ 3344],
     | 30.00th=[ 3728], 40.00th=[ 4016], 50.00th=[ 4320], 60.00th=[ 4640],
     | 70.00th=[ 4960], 80.00th=[ 5920], 90.00th=[ 6752], 95.00th=[ 7072],
     | 99.00th=[17280], 99.50th=[17280], 99.90th=[19584], 99.95th=[19584],
     | 99.99th=[19584]
   bw (  KiB/s): min=212992, max=238044, per=99.99%, avg=225933.14, stdev=9390.00, samples=7
   iops        : min=   52, max=   58, avg=55.14, stdev= 2.27, samples=7
  lat (usec)   : 2=5.71%, 4=31.43%, 10=60.95%, 20=1.90%
  cpu          : usr=0.31%, sys=9.41%, ctx=6756, majf=0, minf=58
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,210,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1


Run status group 0 (all jobs):
  WRITE: bw=221MiB/s (231MB/s), 221MiB/s-221MiB/s (231MB/s-231MB/s), io=844MiB (885MB), run=3825-3825msec
mike@beastie:/testpool$ sync;fio --randrepeat=1 --ioengine=libaio --direct=1 --name=test --filename=test --bs=4M --size=4G --readwrite=read --ramp_time=4
test: (g=0): rw=read, bs=(R) 4096KiB-4096KiB, (W) 4096KiB-4096KiB, (T) 4096KiB-4096KiB, ioengine=libaio, iodepth=1
fio-3.28
Starting 1 process
Jobs: 1 (f=0)
test: (groupid=0, jobs=1): err= 0: pid=1801830: Wed Sep 18 11:34:04 2024
  read: IOPS=928, BW=3714MiB/s (3894MB/s)(4096MiB/1103msec)
  cpu          : usr=0.00%, sys=99.91%, ctx=0, majf=0, minf=1032
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=1024,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1


Run status group 0 (all jobs):
   READ: bw=3714MiB/s (3894MB/s), 3714MiB/s-3714MiB/s (3894MB/s-3894MB/s), io=4096MiB (4295MB), run=1103-1103msec
mike@beastie:/testpool$

```

To be honest I don't know if the results are bad good average or what? Some feed back would be appreciated. 
My intent here is to have a baseline before the actual drives go in and to actually gain some knowledge before that.

---

### Post by 1fallen on 2024-09-18
> **sgt-mike said:**
> 
To be honest I don't know if the results are bad good average or what? Some feed back would be appreciated. 
My intent here is to have a baseline before the actual drives go in and to actually gain some knowledge before that.

I would say those are above average read writes.

Not many here to my knowledge use ZFS on Buntu ATT. (Experimental)

And what you now see will change randomly, depending on the load on transfers. (Size/Memory)

There is a few very good posts here in UF, Search for MAFoElffen, I use Arch for my ZFS systems so I won't be much use to you.

Here is one of many: [https://ubuntuforums.org/showthread.php?t=2497598&highlight=MAFoElffen](https://ubuntuforums.org/showthread.php?t=2497598&highlight=MAFoElffen)

---

### Post by sgt-mike on 2024-09-18
> **1fallen2 said:**
> I would say those are above average read writes.

Not many here to my knowledge use ZFS on Buntu ATT. (Experimental)

And what you now see will change randomly, depending on the load on transfers. (Size/Memory)

There is a few very good posts here in UF, Search for MAFoElffen, I use Arch for my ZFS systems so I won't be much use to you.


Yes 1fallen2

MAFoElffen was the person whom helped me attempt to assemble this server (which is still not done, some more components and drives are en-route within the next few days/weeks USPS dependent), and we held brief discussions on ZFS. 

With me stating I would use the filesystem on that server, as I thought it would be great to learn that.

 As of late I've been unable to contact him, so as you mentioned I'll pretty much have to glean from what he has written in the past in other post. This leaves me hoping that nothing has happened except a simple vacation.
Couple that with 1fallen stating he is leaving the forum, news /discussion within the cafe about a migration of the forum, make my view from the foxhole kinda bleak to say the least. 

On the server hardware side currently it is at 32GB ram (Asus X-99A MB, i7-5930K, boot drive is a WD NVMe 128gb) which within the next thirty days I plan on doubling the ram . I updated the BIOS to the latest from ASUS before anything was installed. From the Documentation from Asus it's kinda fuzzy, I'm not sure if it will address 64 or 128GB Ram Maximum which ever it is I plan of shooting to max out the Ram 32 GB at a time. That should boost some things in the write/read sides. 

The data drives (I guess calling them a vdev is correct verbiage) for this test are  5- Toshiba MQ01ABF050 family 500GB -5400rpm 2.5" in a 6 bay SATA drive enclosure. Driven by the MB SATA ports. Which I had used in a media server with MDADM raid5 configuration. 

They will be replaced with 6 - Dell Constellation ES.3 7.2K rpm 4TB SAS-6Gps connected to a LSI 9300-16i 16 port SAS HBA. 
(even though the seller stated what they did in the ad I'm hoping that the LSI Controller is in IT mode and not IR, while I'm sure I can flash the BIOS over to IT mode. I haven't flashed a SCSI Bios since the mid 1980's when drives was only in 5.25" sizes. That leaves me leery actually cautious of performing the task). 

My main reason for choosing the SAS controller was so I could use either SATA or SAS drives (obviously not in the same pool). 

Within the Asus Bios I have the capability to shut down the controller that is not driving the boot drive (the board has two SATA controllers). 
Which I'm considering doing, but on the fence - leaving them alone or if I should disable 1 controller,  when the LSI HBA is installed. Thoughts anyone? In my mind it seems as it "should" clear some IRQ's

---

### Post by 1fallen on 2024-09-18
> **sgt-mike said:**
> 
 As of late I've been unable to contact him, so as you mentioned I'll pretty much have to glean from what he has written in the past in other post. This leaves me hoping that nothing has happened except a simple vacation.



Yep on my end as well, We all hope the best here.
> **sgt-mike said:**
> Yes 1fallen

Within the Asus Bios I have the capability to shut down the  controller (the board has two controllers) that is not driving the boot  drive. 
Which I'm considering doing, but on the fence on - leaving them alone or  if I should disable 1 controller,  when the LSI HBA is installed.  Thoughts anyone?


Well just to be safe , be sure to export that pool or pools first. If that becomes necessary.

---

### Post by sgt-mike on 2024-09-18
Normally yes I would export but the pool actually contains nothing that can't reloaded,  so no loss there. As you mentioned researching some of his post i did just that.
 
Reviewed when he would test his system and the Fio commands, there is no way my current  2.5" 20 + year old 5400rpm scrub rusty drives would even think about keep up with MAL's (Mike's)  samsung 870 2TB SSD's.  

I Destroyed the pool and then  re - created this time as a 5 disk raidZ2  and still used the -o ashift=12 in the create command 
(see first line I ran zpool history, shows the setup commands I used supposed to align the drives, not sure if it really needed performance wise, I would have used uuid's to assemble the drives but it is strange that. When I run blkid or attempt to get the drive's with lsblk those drive's don't report the uuid. The NVMe does however show the uuid every time )

```

mike@beastie:/$ sudo zpool historyHistory for 'testpool':
2024-09-18.16:39:05 zpool create -o ashift=12 testpool raidz2 sda1 sdb1 sdc1 sdd1 sde1 -f
2024-09-18.16:40:24 zfs set compress=lz4 testpool


mike@beastie:/$ sudo zpool status
  pool: testpool
 state: ONLINE
config:


        NAME        STATE     READ WRITE CKSUM
        testpool    ONLINE       0     0     0
          raidz2-0  ONLINE       0     0     0
            sda1    ONLINE       0     0     0
            sdb1    ONLINE       0     0     0
            sdc1    ONLINE       0     0     0
            sdd1    ONLINE       0     0     0
            sde1    ONLINE       0     0     0


errors: No known data errors
mike@beastie:/$ sudo zpool list
NAME       SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
testpool  2.27T  1.23M  2.27T        -         -     0%     0%  1.00x    ONLINE  -

mike@beastie:/testpool$ fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
TEST: Laying out IO file (1 file / 2048MiB)
Jobs: 1 (f=1): [W(1)][38.9%][w=554MiB/s][w=553 IOPS][eta 00m:11s]
Jobs: 1 (f=1): [W(1)][56.5%][w=208MiB/s][w=208 IOPS][eta 00m:10s]
Jobs: 1 (f=1): [W(1)][76.0%][w=436MiB/s][w=436 IOPS][eta 00m:06s]
Jobs: 1 (f=1): [W(1)][89.3%][w=199MiB/s][w=199 IOPS][eta 00m:03s]
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s]
Jobs: 1 (f=1): [W(1)][97.4%][eta 00m:01s]
Jobs: 1 (f=1): [W(1)][97.4%][eta 00m:01s]
TEST: (groupid=0, jobs=1): err= 0: pid=319677: Wed Sep 18 16:45:12 2024
  write: IOPS=267, BW=268MiB/s (281MB/s)(10.0GiB/38246msec); 0 zone resets
    slat (usec): min=274, max=9307, avg=2764.48, stdev=1544.85
    clat (usec): min=2, max=9938.6k, avg=115141.89, stdev=542234.64
     lat (usec): min=320, max=9940.5k, avg=117907.03, stdev=542325.14
    clat percentiles (msec):
     |  1.00th=[   11],  5.00th=[   13], 10.00th=[   15], 20.00th=[   24],
     | 30.00th=[   56], 40.00th=[   70], 50.00th=[   85], 60.00th=[  104],
     | 70.00th=[  123], 80.00th=[  138], 90.00th=[  150], 95.00th=[  155],
     | 99.00th=[  159], 99.50th=[  159], 99.90th=[ 9866], 99.95th=[ 9866],
     | 99.99th=[10000]
   bw (  KiB/s): min=200704, max=2181120, per=100.00%, avg=358184.42, stdev=311594.61, samples=57
   iops        : min=  196, max= 2130, avg=349.79, stdev=304.29, samples=57
  lat (usec)   : 4=0.02%, 10=0.03%, 500=0.01%, 750=0.01%, 1000=0.01%
  lat (msec)   : 2=0.04%, 4=0.08%, 10=0.87%, 20=12.54%, 50=11.25%
  lat (msec)   : 100=33.48%, 250=41.37%, >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=1168, max=1168, avg=1168.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[ 1176],  5.00th=[ 1176], 10.00th=[ 1176], 20.00th=[ 1176],
     | 30.00th=[ 1176], 40.00th=[ 1176], 50.00th=[ 1176], 60.00th=[ 1176],
     | 70.00th=[ 1176], 80.00th=[ 1176], 90.00th=[ 1176], 95.00th=[ 1176],
     | 99.00th=[ 1176], 99.50th=[ 1176], 99.90th=[ 1176], 99.95th=[ 1176],
     | 99.99th=[ 1176]
  cpu          : usr=1.44%, sys=10.42%, ctx=68611, majf=0, minf=14
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32


Run status group 0 (all jobs):
  WRITE: bw=268MiB/s (281MB/s), 268MiB/s-268MiB/s (281MB/s-281MB/s), io=10.0GiB (10.7GB), run=38246-38246msec
mike@beastie:/testpool$ fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=0): [f(1)][-.-%][r=3682MiB/s][r=3682 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=364773: Wed Sep 18 16:45:37 2024
  read: IOPS=3561, BW=3562MiB/s (3735MB/s)(10.0GiB/2875msec)
    slat (usec): min=229, max=890, avg=278.54, stdev=37.48
    clat (usec): min=2, max=23476, avg=8613.45, stdev=1134.15
     lat (usec): min=262, max=24368, avg=8892.27, stdev=1164.29
    clat percentiles (usec):
     |  1.00th=[ 5342],  5.00th=[ 8291], 10.00th=[ 8291], 20.00th=[ 8356],
     | 30.00th=[ 8356], 40.00th=[ 8356], 50.00th=[ 8356], 60.00th=[ 8356],
     | 70.00th=[ 8455], 80.00th=[ 8455], 90.00th=[10028], 95.00th=[10159],
     | 99.00th=[12649], 99.50th=[13042], 99.90th=[20317], 99.95th=[21890],
     | 99.99th=[23200]
   bw (  MiB/s): min= 2844, max= 3714, per=99.12%, avg=3530.40, stdev=384.01, samples=5
   iops        : min= 2844, max= 3714, avg=3530.40, stdev=384.01, samples=5
  lat (usec)   : 4=0.05%, 500=0.05%, 750=0.05%, 1000=0.05%
  lat (msec)   : 2=0.20%, 4=0.34%, 10=85.87%, 20=13.29%, 50=0.11%
  cpu          : usr=1.08%, sys=98.82%, ctx=8, majf=0, minf=8205
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32


Run status group 0 (all jobs):
   READ: bw=3562MiB/s (3735MB/s), 3562MiB/s-3562MiB/s (3735MB/s-3735MB/s), io=10.0GiB (10.7GB), run=2875-2875msec
mike@beastie:/testpool$

```

on this attempt (test) the drives did pick up a bit in write, and drop a bit in read. looking over the data from a striped, raidZ1 vs the raidZ2. 
I think I'm preferring similar to MALFoELffen's setup the best.

Edit added: as a after thought after posting, I rebooted the server and reran the fio test just to see if any differences  - results was VERY close to the same.

---

### Post by 1fallen on 2024-09-18
Refresh my memory here, do you have the same control-board as MAFoElffen?
Also his drives for storage were Samsung 980 pro's
> When I run blkid or attempt to get the drive's with lsblk those drive's don't report the uuid.
Use this, but what you see is normal with "lsblkid"
```
[FONT=monospace][COLOR=#000000] lsblk -f [/COLOR]
NAME        FSTYPE     FSVER LABEL            [COLOR=#FF0000]UUID[/COLOR]                                 FSAVAIL FSUSE% MOUNTPOINTS 
sda                                                                                                
&#9500;&#9472;sda1      vfat       FAT32                  [COLOR=#FF0000]174D-2B3B [/COLOR]                                           
&#9492;&#9472;sda2      zfs_member 5000  zpcachyos        [COLOR=#FF0000]16371488555828878549 [/COLOR]               [/FONT]
```[FONT=monospace]
[/FONT]

---

### Post by sgt-mike on 2024-09-18
I don't remember let me check some post's de did but he did recommend that HBA that I chose

Ohh here is the output of lsblk -f which is what I used at first 

```
 mike@beastie:/testpool$  lsblk -fNAME FSTYPE FSVER LABEL UUID                                 FSAVAIL FSUSE% MOUNTPOINTS
loop0
                                                                   0   100% /snap/core20/2318
loop1
                                                                   0   100% /snap/core20/2379
loop2
                                                                   0   100% /snap/lxd/27037
loop3
                                                                   0   100% /snap/lxd/29351
loop4
                                                                   0   100% /snap/snapd/20671
loop5
                                                                   0   100% /snap/snapd/21759
sda
&#9492;&#9472;sda1
     zfs_me 5000  testpool
                        3633765842062420381
sdb
&#9492;&#9472;sdb1
     zfs_me 5000  testpool
                        3633765842062420381
sdc
&#9492;&#9472;sdc1
     zfs_me 5000  testpool
                        3633765842062420381
sdd
&#9492;&#9472;sdd1
     zfs_me 5000  testpool
                        3633765842062420381
sde
&#9492;&#9472;sde1
     zfs_me 5000  testpool
                        3633765842062420381
nvme0n1
&#9474;
&#9500;&#9472;nvme0n1p1
&#9474;    vfat   FAT32       4CB7-A6FA                                 1G     1% /boot/efi
&#9492;&#9472;nvme0n1p2
     ext4   1.0         886863a1-0959-4ebb-b189-c5aa9521430a  212.2G     4% /
mike@beastie:/testpool$ 
```

as those drives have been in multiple systems etc I suspect I did something on my end is why the UUID are not showing up

---

### Post by 1fallen on 2024-09-18
> **sgt-mike said:**
> I don't remember let me check some post's de did but he did recommend that HBA that I chose



Ok I thought so I just need to get my head around a thread so long back.  Yep that's a good one then.
I can't even remember yesterday with distinct clarity. :lolflag:

---

### Post by sgt-mike on 2024-09-18
duplicate see below

---

### Post by sgt-mike on 2024-09-18
LMAO that is me  toooo many combat tours ...

Oh finally went to his response on the thread he and I was discussing 

```
 [COLOR=#000000]Dang. I wrote you a post last night... With lots of links for 12 port LSI SAS HBA cards @ EBay. And don't see it now.[/COLOR]

[COLOR=#000000]The best deal I found for you was this one:[/COLOR]
[https://www.ebay.com/itm/20414862155...BoCsSsQAvD_BwE]("https://www.ebay.com/itm/204148621555?chn=ps&norover=1&mkevt=1&mkrid=711-166974-028196-7&mkcid=2&mkscid=101&itemid=204148621555&targetid=2290620803403&device=c&mktype=pla&googleloc=9033510&poi=&campaignid=20688831350&mkgroupid=158250977497&rlsatarget=pla-2290620803403&abcId=9326636&merchantid=101984566&geoid=9033510&gad_source=1&gclid=CjwKCAjwwr6wBhBcEiwAfMEQszPiITEZa_xnjclEe086aZYYQMw6pFFyHFJEd4j1-7L1ci3q9WL9uBoCsSsQAvD_BwE")

[COLOR=#000000]It is PCIe x8 gen 3.0. The 4 port SAS cables usually run about $18 each. 4 x4 = 16. That card supports SAS/SATA.[/COLOR]

[COLOR=#000000]On GPU for a files server. No doesn't matter. The onboard -GPU is fine. It's just a file server. For that matter, if you wanted to store your media files there is an NFS share, it will be fine. <-- Then your media server can cannect to the file, and it's GPU can help with decoding...[/COLOR]

[COLOR=#000000]For a file server, your priorities are storage pools, disk I/O and network throughput... And the ability to add more and more storage as needed. Then the ability to manage that storage.[/COLOR]

[COLOR=#000000]The types of disks depend on what they will be used for and the priority of the I/O, whether reads or writes, and how large 'the files' are.[/COLOR]

[COLOR=#000000]HDD is good for mass media and backups... Though too slow a disk, and your backups will take longer. 20TB Recertified Enterprise HDD drives are cheap. Even if you look into Recert'ed "lots" of SAS drives...[/COLOR]

[COLOR=#000000]There is this:[/COLOR]
[https://www.ebay.com/itm/26416718817...RoC0uQQAvD_BwE]("https://www.ebay.com/itm/264167188175?chn=ps&norover=1&mkevt=1&mkrid=711-166974-028196-7&mkcid=2&mkscid=101&itemid=264167188175&targetid=2282899792497&device=c&mktype=pla&googleloc=9033513&poi=&campaignid=20938509022&mkgroupid=154882361170&rlsatarget=pla-2282899792497&abcId=9367438&merchantid=118916553&geoid=9033513&gad_source=1&gclid=CjwKCAjwwr6wBhBcEiwAfMEQs9eDkcOfcBHNn6iouezp0HjVwbqMT5AByk2w-iULcbWLzHjx3go78RoC0uQQAvD_BwE")

[COLOR=#000000]Just an example, but... Big investment outlay out-front. New 15K rpm SAS drives 20x 600GB = $1100. That comes out to $50 each. But that is only a little over 11 TB total.[/COLOR]

[COLOR=#000000]This one is a lot of 10 new SAS 600GB drives which comes out to about $59 each:[/COLOR]
[https://www.ebay.com/itm/25453017628...86.c101224.m-1]("https://www.ebay.com/itm/254530176280?_trkparms=amclksrc%3DITM%26aid%3D1110006%26algo%3DHOMESPLICE.SIM%26ao%3D1%26asc%3D262498%26meid%3De0c2491348614db38851bb3a3c8b2772%26pid%3D101224%26rk%3D4%26rkt%3D5%26sd%3D264167188175%26itm%3D254530176280%26pmt%3D0%26noa%3D1%26pg%3D4429486%26algv%3DDefaultOrganicWebV9BertRefreshRanker%26brand%3DSeagate&_trksid=p4429486.c101224.m-1")

[COLOR=#000000]This is a 5-pack of Factory Refurbished 20TB 7200k Enterprise SATA HDD's: [/COLOR][https://www.amazon.com/Seagate-Exos-...c&gad_source=1]("https://www.amazon.com/Seagate-Exos-7200RPM-5-Pack-Enterprise/dp/B0CKS32PTN/ref=asc_df_B0CKS32PTN/?tag=hyprod-20&linkCode=df0&hvadid=677903220948&hvpos=&hvnetw=g&hvrand=16361069529211915720&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9033513&hvtargid=pla-2244679454123&psc=1&mcid=44dba8c99cf13e88b127282cb105a76c&gad_source=1")

[COLOR=#000000]That comes out to about 57 TB of usable storage in RAIDZ2. Refurb'ed 20TB enterprise drives run about $250 each. But you can find 12 TB refurb'ed Enterprise drives at NewEgg for $99 each...[/COLOR]
[https://www.newegg.com/seagate-exos-...BoCqpwQAvD_BwE]("https://www.newegg.com/seagate-exos-x14-st12000nm0538-12tb/p/1Z4-002P-022C7?item=9SIA5ADJZF0288&source=region&nm_mc=knc-googlemkp-pc&cm_mmc=knc-googlemkp-pc-_-pla-goharddrive-_-hard+drives-_-9SIA5ADJZF0288&utm_source=google&utm_medium=paid+shopping&utm_campaign=knc-googlemkp-pc-_-pla-goharddrive-_-hard+drives-_-9SIA5ADJZF0288&id0=Google&id1=19482421907&id2=146598832444&id3=&id4=&id5=pla-2275542440526&id6=&id7=9033513&id8=&id9=g&id10=c&id11=&id12=CjwKCAjwwr6wBhBcEiwAfMEQs-cncKzM2SwyCFtNGqOaoPSZUkJPuht9qEBlTZlsRr3gYfr3GQTgfBoCqpwQAvD_BwE&id13=&id14=Y&id15=&id16=643915474301&id17=&id18=&id19=&id20=&id21=pla&id22=100715614&id23=online&id24=9SIA5ADJZF0288&id25=US&id26=2275542440526&id27=Y&id28=&id29=&id30=1603825120928049848&id31=en&id32=&id33=&id34=&gclsrc=aw.ds&gad_source=1&gclid=CjwKCAjwwr6wBhBcEiwAfMEQs-cncKzM2SwyCFtNGqOaoPSZUkJPuht9qEBlTZlsRr3gYfr3GQTgfBoCqpwQAvD_BwE")

[COLOR=#000000]Be aware that the warranty on Seagate Factory Refurbished Exos X14 Enterprise drives is 2 years, compared to 3 years new.[/COLOR]

[COLOR=#000000]You can find deals if you shop around. And with the hardware foundation more open, you have a lot more choices open to you with what you can do.[/COLOR]

[COLOR=#000000]If ZFS RAIDZ2, I would start out at vdevs of RAIDZ2, and add each of those vdevs of the same. At 12 TB each for 5 drives, that comes out to 34 TB per each vdev @ $495 per vdev, or $14.50 per TB of storage and fairly fast enterprise drives. If you need more, then later on, add another vdev of 34 TB RAIDZ2 when you can afford it, to that same pool.[/COLOR]

[COLOR=#000000]Is an investment...[/COLOR] 
```

I had to check just be sure that I did order the one (model) HBA  he pointed at  as my CRS is kicking in loudly today...... YEP I did....
the best part that I seen on his advice is I can use this  [https://www.ebay.com/itm/395595171727](https://www.ebay.com/itm/395595171727)   to slave to the 16 port and expand to almost 30 (26 I think is the correct number) . What I find is interesting with the Intel expander is it can be powered via molex vs a pci-e slot.

(besides already went to Broadcom's site to pull down the latest bios etc for that card so it's standing by when it arrives)

edit to add a bit more information on the LSI 9300-16i-16 port HBA
-----------From the user's manual-----
This section lists the LSI 12Gb/s SAS HBA features.
 &#61550; Implements two LSI SAS 3008 eight-port 12Gb/s SAS to PCIe 3.0 controllers
 &#61550; Supports eight-lane, full-duplex PCIe 3.0 performance
 &#61550; Supports sixteen internal 12Gb/s SATA+SAS ports
 &#61550; Supports SATA link rates of 3Gb/s and 6Gb/s
 &#61550; Supports SAS link rates of 3Gb/s, 6Gb/s, and 12Gb/s
 &#61550; Provides four x4 internal mini-SAS HD connectors (SFF-8643)
 &#61550; Supports passive copper cable
 &#61550; Supports up to 1024 SATA or SAS end devices
 &#61550; Offered with a full-height bracket
&#61550; Provides two heartbeat LEDs
----------------------------------------------
So with the correct (#) of expander cards with a high port # such as 24 ports or more daisy chained one can control 1024 SATA or SAS devices.
This is not the only LSI HBA that does this but the number does vary newer versions as I understand can support more than this one if I recall some conversations with others.
hmm another thought just crossed my mind when I ordered the drives I didn't think to ask the seller if they was 520 or 512 sectors. Oh well I'll know soon enough there maybe some low level formatting in my future... haven't done that since the mid 1980's

---

### Post by 1fallen on 2024-09-18
All that is great advice, I will try my best to help when I can.
That looks to me as great starting point with room to grow. Nice!

---

### Post by sgt-mike on 2024-09-18
did one more check on the zpool creation leaving off the -o ashift=12
and leaving off compression as well
```
 
mike@beastie:/metapool$ sudo zpool historyHistory for 'metapool':
2024-09-18.18:59:07 zpool create metapool raidz2 sda1 sdb1 sdc1 sdd1 sde1 -f


mike@beastie:/metapool$ fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
TEST: Laying out IO file (1 file / 2048MiB)
Jobs: 1 (f=1): [W(1)][43.8%][w=407MiB/s][w=407 IOPS][eta 00m:09s]
Jobs: 1 (f=1): [W(1)][56.5%][w=200MiB/s][w=200 IOPS][eta 00m:10s]
Jobs: 1 (f=1): [W(1)][76.0%][w=297MiB/s][w=297 IOPS][eta 00m:06s]
Jobs: 1 (f=1): [W(1)][89.3%][w=199MiB/s][w=199 IOPS][eta 00m:03s]
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s]
Jobs: 1 (f=1): [W(1)][97.4%][eta 00m:01s]
TEST: (groupid=0, jobs=1): err= 0: pid=63250: Wed Sep 18 19:01:40 2024
  write: IOPS=274, BW=275MiB/s (288MB/s)(10.0GiB/37276msec); 0 zone resets
    slat (usec): min=273, max=5649, avg=2693.44, stdev=1534.30
    clat (usec): min=3, max=9683.3k, avg=112275.40, stdev=528669.95
     lat (usec): min=296, max=9684.9k, avg=114969.53, stdev=528747.76
    clat percentiles (msec):
     |  1.00th=[   11],  5.00th=[   14], 10.00th=[   17], 20.00th=[   27],
     | 30.00th=[   54], 40.00th=[   67], 50.00th=[   81], 60.00th=[   97],
     | 70.00th=[  115], 80.00th=[  140], 90.00th=[  153], 95.00th=[  157],
     | 99.00th=[  159], 99.50th=[  161], 99.90th=[ 9731], 99.95th=[ 9731],
     | 99.99th=[ 9731]
   bw (  KiB/s): min=43008, max=1923072, per=100.00%, avg=364580.57, stdev=296478.87, samples=56
   iops        : min=   42, max= 1878, avg=356.04, stdev=289.53, samples=56
  lat (usec)   : 4=0.01%, 10=0.03%, 20=0.01%, 500=0.01%, 750=0.01%
  lat (usec)   : 1000=0.01%
  lat (msec)   : 2=0.04%, 4=0.10%, 10=0.59%, 20=13.05%, 50=12.72%
  lat (msec)   : 100=35.31%, 250=37.81%, >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=1218, max=1218, avg=1218.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[ 1224],  5.00th=[ 1224], 10.00th=[ 1224], 20.00th=[ 1224],
     | 30.00th=[ 1224], 40.00th=[ 1224], 50.00th=[ 1224], 60.00th=[ 1224],
     | 70.00th=[ 1224], 80.00th=[ 1224], 90.00th=[ 1224], 95.00th=[ 1224],
     | 99.00th=[ 1224], 99.50th=[ 1224], 99.90th=[ 1224], 99.95th=[ 1224],
     | 99.99th=[ 1224]
  cpu          : usr=1.47%, sys=10.71%, ctx=67787, majf=0, minf=15
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32


Run status group 0 (all jobs):
  WRITE: bw=275MiB/s (288MB/s), 275MiB/s-275MiB/s (288MB/s-288MB/s), io=10.0GiB (10.7GB), run=37276-37276msec
mike@beastie:/metapool$ fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=0): [f(1)][-.-%][r=3668MiB/s][r=3668 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=109995: Wed Sep 18 19:02:33 2024
  read: IOPS=3571, BW=3572MiB/s (3745MB/s)(10.0GiB/2867msec)
    slat (usec): min=230, max=925, avg=277.80, stdev=38.00
    clat (usec): min=2, max=24505, avg=8587.61, stdev=1108.96
     lat (usec): min=261, max=25431, avg=8865.67, stdev=1138.93
    clat percentiles (usec):
     |  1.00th=[ 5407],  5.00th=[ 8291], 10.00th=[ 8291], 20.00th=[ 8291],
     | 30.00th=[ 8291], 40.00th=[ 8291], 50.00th=[ 8356], 60.00th=[ 8356],
     | 70.00th=[ 8356], 80.00th=[ 8455], 90.00th=[10028], 95.00th=[10028],
     | 99.00th=[11600], 99.50th=[11863], 99.90th=[20317], 99.95th=[22676],
     | 99.99th=[24249]
   bw (  MiB/s): min= 2874, max= 3730, per=99.09%, avg=3539.20, stdev=373.67, samples=5
   iops        : min= 2874, max= 3730, avg=3539.20, stdev=373.67, samples=5
  lat (usec)   : 4=0.05%, 500=0.05%, 750=0.05%, 1000=0.05%
  lat (msec)   : 2=0.20%, 4=0.34%, 10=84.79%, 20=14.37%, 50=0.12%
  cpu          : usr=0.94%, sys=99.02%, ctx=7, majf=0, minf=8206
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32


Run status group 0 (all jobs):
   READ: bw=3572MiB/s (3745MB/s), 3572MiB/s-3572MiB/s (3745MB/s-3745MB/s), io=10.0GiB (10.7GB), run=2867-2867msec

```

Huh so the zpool create -o ashift=12 <poolname> uuid/sd*1 -f  command when adding the drives which is supposed to make the zfs pool faster according to a website OTHER THAN this forum.
 
Doesn't ...... it actually slow it down at least for these drives. Performance is better in this run. 

Good to know.

BTW figured out why when I ran lsblk -f or blkid the system didn't show a uuid  for the 500gb drives ... the drives was unformatted derrrr...ppp.....

(finally looked up that laptop drives benchmark performance 106Mb/s write  wow  so actually so it is actually smoking along at approx 275Mb/s with ZFS)

---

### Post by 1fallen on 2024-09-18
Don't get worried when read writes slows seemly to a crawl, it just happens. :(

---

### Post by sgt-mike on 2024-09-19
Been reviewing this article/ website in a attempt to comprehend the way zfs works [https://klarasystems.com/articles/openzfs-understanding-zfs-vdev-types/](https://klarasystems.com/articles/openzfs-understanding-zfs-vdev-types/)  
Luckily for me that the page addressee's  what I have settled on raidz2 which draws some questions.
```

Storage Vdevs
    |_ raidz2-0  : I am planning 5 4TB SAS drives, - so two drives are lost to parity, 3 receive data with a 5 drive configuration
    |_  raidz2-1: when I add this storage I understand that the pool should be at least three drives, but I'll probably use 5 again for my ocd/ sanity sake it can be composed of 1TB drive 2 TB 4TB or even 8TB drive again I'll lose two drives to parity to raidz2-1 Vdev and the remaining drive get data
    |_ raidz2-*: same as above 

```
 Q. As more zraid2 Vdevs are added each (zraid2-*) they each will have parity loss of two drives for their respective storage Vdev raidz2 within each individual Vdev raidz2-# ?  
I think I get it thus far or do I?
Is the graphic of the link that I hyperlinked accurate? If it is that way then I got it and understand it.

Now moving on to  support Vdevs (if I decide to use them)
  Cache - would a SSD work well here? or a waste? or because I'm using rusty spinner disks should it be a faster drive? I think somewhere I read it should be half the value of installed ram 
  Log - again same question a fast ssd? regular drive and what should the capacity be ? or does it even matter?
  Spare - Yep no brainer if added to the Zpool should it be in a mixed setup matching the highest capacity individual drive. or if matching storage vdevs - individual drive capacity

* Spare (when the storage Vdevs are greater than 1) make a lot of sense to utilize

---

### Post by 1fallen on 2024-09-19
I told MAFoElffen that I did create a swap disk 256 Gig worth, and I notice no difference.

This one helps a bit:
```
[FONT=monospace][COLOR=#000000]free -g [/COLOR]
               total        used        free      shared  buff/cache   available 
Mem:              13           3           6           0           2           9 
Swap:             45           0          45

[/FONT]
```[FONT=monospace]
and this:
[/FONT]```
[FONT=monospace][COLOR=#000000]vmstat [/COLOR]
procs -----------memory---------- ---swap-- -----io---- -system-- -------cpu------- 
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st gu 
 0  0      0 7209124   3180 3152128    0    0   252   140 3858    4  1  1 98  0  0  0

[/FONT]
```
```
[FONT=monospace][COLOR=#000000]Filename                                Type            Size            Used            Priority [/COLOR]
/swap/swapfile                          file            33554428        0               -2 
/dev/zram0                              partition       14159868        0               100



```[/FONT]
[FONT=monospace] I've only seen it kick in maybe 2 or three times, but all this may vary on your setup.
But SSD's are faster than spinners.
[/FONT]

---

### Post by sgt-mike on 2024-09-20
Went back and read some post from MAFoELffen where he was helping with the speed on a Raidz3 setup. He addressed the cache and the log vdevs while not at great length but I noted he specifically called for small (64gb or less for cache, and I want to say about the same amount for the Log) NVMe usage for the log vdev. He even noted that it wouldn't help much except for certain writes VM's, database, etc which he was doing. But ram did more than anything for the system vs the usage of the cache/log vdevs.  I'll have to reread it but my take away was I really don't need to worry about it until I max my onboard ram. And even then will probably not be needed until later. 

Still war gaming my first true actual pool and cabling requirement to the HBA so I don't waste ports. I know at some point I'll need to go outside my case and setup a DAS to expand if I stick with the Z2 configuration. Also set and thought about the number of drives. I know I at first said go 5 drives but I would be wasting ports on the HBA and cabling with the first raidz* vdev if I go 5, so 4 drive will be better.  
Now the questions Z1 or Z2.  Z1 at 4 4TB 1 Vdev will afford me 10TB useable but a practical of 8.2 TB calculating a 20% slope, Z2 same setup usable = 7.1 practical =5.7 TB, it's redundancy vs storage that I have to look at. I really like the fault tolerance of he double parity and I Like the storage of the single parity. 
I'll mull it over again and again until I set the drives in the case. One saving grace is that my media, is still small enough (little less than 2.8 TB) to sit on the a Z2 configuration as I stated. just will have to add the second storage Vdev faster than if I went single parity. But the writing this out helps me to think through what I want to do.... (we won't discuss how many time I've hit the post quick reply. Typed out what I thinking made a decision and didn't post to this thread,, so yeah it's my sounding board). 

In my test pool results earlier and after actually reading some old posts. I realized that I was getting really good results for old sata spinners in both read and writes. As I actually considered it I also realized that what I really should be concerned about is read speed. At some point soon if continue to add more media I'll have to clear the media from the plex server. Then have the NAS/NFS provide / host the media to the plex server.

---

### Post by sgt-mike on 2024-09-22
Yesterday parts arrived and a set back occurred the LSI HBA was DOA.... bummer, at least the ebay vendor has a return /refund policy.

 I'll just have to re-order /wait for a HBA to ship, with hind sight in mind. Maybe I should order a multiple this time. But with my luck when I order a multiple, all will work . Still debating 2 or 3, 3 will afford the most probability of a usable item.

------This part is me just thinking out loud before ordering  --------------

I did find a LSI 9300-8i , which the LSI 9300-16i is simply two 9300-8i on the same board supporting 16 drives versus 8, I might go that route with the 8i and order a expander with 8 ports external at the same time 36 ports total on the expander. losing 8 port to slaving to the 9300-8i and 8 port to external leaves me with 20 ports internal.  As I do plan on adding outside the case, now after much internal debate. 
[https://www.ebay.com/itm/196570304608?_skw=lsi+hba+it+mode&itmmeta=01J8DMMWR6CMDAXBT2NHE4FXWF&hash=item2dc480d060:g:De0AAOSwfoNlZ6Jx&itmprp=enc%3AAQAJAAAA0HoV3kP08I](https://www.ebay.com/itm/196570304608?_skw=lsi+hba+it+mode&itmmeta=01J8DMMWR6CMDAXBT2NHE4FXWF&hash=item2dc480d060:g:De0AAOSwfoNlZ6Jx&itmprp=enc%3AAQAJAAAA0HoV3kP08I)
This is the expander I'm considering of ordering with the 9300-8i, I was already considering it with the 9300-16i anyways, all support SAS-3 at 12 Gps. The Intel expander I was considering only supported up to 6 Gps. 
[https://www.ebay.com/itm/135244175645](https://www.ebay.com/itm/135244175645) 

After all unless I go with 2.5" drives, the Cooler Master case it can support 12 - 3.5" drives in the case using some OEM drive /case modules (internal 3.5" =5 with 5 -5.25" bays external). 
[https://www.newegg.com/athena-power-bp-tla3141sas12-other/p/N82E16816119046?Item=9SIAZ8XJ1U6752](https://www.newegg.com/athena-power-bp-tla3141sas12-other/p/N82E16816119046?Item=9SIAZ8XJ1U6752)
[https://www.newegg.com/athena-power-bp-tla2131sac-other/p/N82E16817995109](https://www.newegg.com/athena-power-bp-tla2131sac-other/p/N82E16817995109)

---

### Post by madscientist032 on 2024-09-22
I'm glad I found this thread, looks like you and I are in similar spots. I'm in the process of rebuilding my home NAS and dabbling with RAID. Nothing too fancy (I'm not going ZFS or anything, at least not as of writing). but I did want to share the parts & have and experience, maybe this would help you with your build 

1 - [My HBA is this guy right here]("https://www.ebay.com/itm/225562380765?var=524635830061")  - it works like a dream out of the box and the [Fractal Design Define R5]("https://www.bhphotovideo.com/c/product/1561224-REG/fractal_design_fd_ca_def_r5_bk_define_r5_black.html") it sits in houses just as much drives as the card itself can handle. I currently have 2x 4port SATA breakouts connected, and it can handle 4x 4 for a total of 16 drives. The major difference b/t this one and what you've linked is cost. As of this post, this listing is 110 USD but I got it for half that.. if you really don't need 16 drives then perhaps one of your two HBAs mentioned above will do the job just fine, just make sure the controller is up to the task (which it seems you've already ran into some of that!)  used [This post from ServeTheHome]("https://www.servethehome.com/buyers-guides/top-hardware-components-for-truenas-freenas-nas-servers/top-picks-truenas-freenas-hbas/") as my starting point. One thing I haven't yet looked into is how SATA based SSDs function on this HBA. I've heard some folks mention this LSI controller doesn't support TRIM, some claim it does, so YMMV (and for my case, I'm using all mechanical HDDs except for the boot drive). Another item you'll want to keep in mind is that the HBA's heatsinks can get quite toasty, so ensure you've got adequate airflow and if not, might be worth finding a 3dprinted fan shroud mount for a fan and get things cooled off that way. I *think* this drive supports SAS 3 so you should be good there too. 

2 - I have had GREAT success with those hotswap bays that you've listed above. Mine was an KingWin, but [it looks exactly the same as the Athena Power 3x HDD cage]("https://www.ebay.com/itm/256309426903") I use this for data ingestion & drive testing as I've been in the process of validating all drives in my possession + new/refurbished drives that have been arriving. It's been great. The only thing I need to mention is that the drives do get a bit toasty in there (35-42c), and the included fan is not a standard size, it's 75cm ?? I think? I don't recall, because I replaced mine with a 60mm Noctua fan as soon as the hotswap bay arrived 4 years ago. The fan is duck-taped to the cage + plugged into one of the motherboard chassis fan headers. I would recommend doing that if you do end up committing to these hard drive cages.

I'm not trying to steamroll this thread, only wanted to share my knowledge in the hopes it would benefit your build.

---

### Post by sgt-mike on 2024-09-23
> **madscientist032 said:**
> I'm glad I found this thread, looks like you and I are in similar spots. I'm in the process of rebuilding my home NAS and dabbling with RAID. Nothing too fancy (I'm not going ZFS or anything, at least not as of writing). but I did want to share the parts & have and experience, maybe this would help you with your build 

1 - [My HBA is this guy right here]("https://www.ebay.com/itm/225562380765?var=524635830061")  - it works like a dream out of the box and the [Fractal Design Define R5]("https://www.bhphotovideo.com/c/product/1561224-REG/fractal_design_fd_ca_def_r5_bk_define_r5_black.html") it sits in houses just as much drives as the card itself can handle. I currently have 2x 4port SATA breakouts connected, and it can handle 4x 4 for a total of 16 drives. The major difference b/t this one and what you've linked is cost. As of this post, this listing is 110 USD but I got it for half that.. if you really don't need 16 drives then perhaps one of your two HBAs mentioned above will do the job just fine, just make sure the controller is up to the task (which it seems you've already ran into some of that!)  used [This post from ServeTheHome]("https://www.servethehome.com/buyers-guides/top-hardware-components-for-truenas-freenas-nas-servers/top-picks-truenas-freenas-hbas/") as my starting point. One thing I haven't yet looked into is how SATA based SSDs function on this HBA. I've heard some folks mention this LSI controller doesn't support TRIM, some claim it does, so YMMV (and for my case, I'm using all mechanical HDDs except for the boot drive). Another item you'll want to keep in mind is that the HBA's heatsinks can get quite toasty, so ensure you've got adequate airflow and if not, might be worth finding a 3dprinted fan shroud mount for a fan and get things cooled off that way. I *think* this drive supports SAS 3 so you should be good there too. 

2 - I have had GREAT success with those hotswap bays that you've listed above. Mine was an KingWin, but [it looks exactly the same as the Athena Power 3x HDD cage]("https://www.ebay.com/itm/256309426903") I use this for data ingestion & drive testing as I've been in the process of validating all drives in my possession + new/refurbished drives that have been arriving. It's been great. The only thing I need to mention is that the drives do get a bit toasty in there (35-42c), and the included fan is not a standard size, it's 75cm ?? I think? I don't recall, because I replaced mine with a 60mm Noctua fan as soon as the hotswap bay arrived 4 years ago. The fan is duck-taped to the cage + plugged into one of the motherboard chassis fan headers. I would recommend doing that if you do end up committing to these hard drive cages.

I'm not trying to steamroll this thread, only wanted to share my knowledge in the hopes it would benefit your build.

@madscientist032 

LOL I'm glad you popped on with the links that will be a great help, and personally I don't consider you steamrolling this thread with your post. In a matter of fact really I should have posted the last post to the thread I started dealing with the hardware build. When MAFoELffen recommended that HBA LSI 9300-16i I downloaded the manual and have been scouring it quite a bit. When I seen the ads for the LSI 9003-8i the only difference I could see within the manuals was number of ports and the heatsink is a lot larger on on the 16 port internal version. And of course cost is bit more affordable in the 8i version. And your timing is perfect with the vendor. On the HBA I'm planning on adding a fan to the heatsink to it to help with heat there as well. I'll look at the fans on the enclosures as you mentioned one thought is to a (or multiple) fan rack behind the enclosures and cabling to suck more air across the drives (something like this [https://www.ebay.com/itm/145986384739](https://www.ebay.com/itm/145986384739) ), or simply replace them.  

On the HBA's that we mentioned I know soon after I populate the drive bays. I will want to go outside the case for additional drives into the pool which brings in the use of a expander (been eyeballing this one hard Adaptec AEC-82885T has 2 external SFF-8644 port out. listed with 36 ports @12Gps) which can be powered either by bus or via molex so it won't take up a slot. I actually drew the two different HBA cabling diagram to the Adaptec expander. The 16i definitely won if cabled correctly with SFF-8643 to SFF-8644 adapter provided one more external SFF-8644 double port. (which means I can use other existing computers drive bays and power to the NFS, or use drive shelves).  

In closing this leaves me with deciding between three COA's to use in order to replace the defective HBA
a. send the original vendor a offer for two HBA's at a greatly reduced cost, thus affording them a chance to redeem themselves.
b. just find a different vendor at the same price point or lower of the first vendor I used.
c. Message your vendor and have them send me a offer 
(unfortunately for me I live in one of the few states that collect taxes on online sales, so I'm a cheap skate)

I really need to post my hardware stuff back in my post dealing with the hardware of the build and stop the thread drift that I did on this one.
[https://ubuntuforums.org/showthread.php?t=2496263](https://ubuntuforums.org/showthread.php?t=2496263)

---

### Post by kirtr on 2024-09-23
> **sgt-mike said:**
> Just starting out on ZFS. 
I had seen a post/article elsewhere where a person assigned an alias to the drives versus them just using the standard /dev/sd*# method. Which seems to make some sense in order to cleanly track down a faulty drive. 
(I'll have to reread the article/post as I don't recall if when he assembled if he used the assigned alias or drive id, but I think he used the alias)

 I've seen where others use the drive ID, which makes a lot of sense vs the method I used. 



Hi Mike,

It is recommended that the devices in /dev/disk/by-id, not the /dev/sd* versions get used for building your vdevs / pools.

Sometimes the order that drives get detected by the hardware can differ and has that has caused problems with software raid style systems. The /dev/disk/by-id devices names are guaranteed to be unique for each device.

If nothing else, it gives you the piece of mind to swap them to a new hba or mb and not have the device numbers change or even having to worry about which order you are plugging them in. :-)

-Kirt

---

### Post by madscientist032 on 2024-09-23
> **kirtr said:**
> Hi Mike,

It is recommended that the devices in /dev/disk/by-id, not the /dev/sd* versions get used for building your vdevs / pools.

Sometimes the order that drives get detected by the hardware can differ and has that has caused problems with software raid style systems. The /dev/disk/by-id devices names are guaranteed to be unique for each device.

If nothing else, it gives you the piece of mind to swap them to a new hba or mb and not have the device numbers change or even having to worry about which order you are plugging them in.

-Kirt

Can confirm. I used to have a crontab entry that would mount via sd[a-c]1 however one day I replaced a drive, swapped things around in the chassis and all my mounts were messed up. Made for a helluva Sunday morning trying to fix, but in the end it forced me to re-think my setup (both my NAS & my primary linux workstation) and I had to do some learning on proper storage management & administration. 

So needless to say, I ended up learning real quick about UUIDs, /etc/fstab, and lsblk -f. 

Lsblk is critical for identifying drives, it shows where they are mounted (if mounted!) as well as any labels applied & dev information. 

Here's a sample of what we're talking about, this will def help with your drive troubleshooting when that comes into play:

My lsblk output: (Note i am filtering out loopback devices for clarity & readability purposes)

```
madsci@madsci-nas:~$ lsblk -f | grep -v loop
NAME        FSTYPE            FSVER LABEL           UUID                                 FSAVAIL FSUSE% MOUNTPOINTS
sda                                                                                                    
&#9492;&#9472;sda1      ext4              1.0   archive         e9f7b0eb-7ebc-431c-8b25-de22b9715ee5    5.2T    37% /archive
sdb                                                                                                    
&#9492;&#9472;sdb1      ext4              1.0   sandbox01       879b4b26-d7cb-48ff-b0d5-f378dfc8a79f    1.7T     1% /tmp/disk3
sdc                                                                                                    
&#9492;&#9472;sdc1      ext4              1.0   media           f71fde5d-baeb-472a-8fdd-dbf79c9f7c22      2T    39% /data/media
sdd                                                                                                    
&#9492;&#9472;sdd1      ext4              1.0   music           73801dd5-f2b0-48a9-98bd-80786291c443    1.2T    27% /data/music
sde         linux_raid_member 1.2   madsci-nas:0     d257ac4d-7b66-eb63-141e-1300f398cc01                
&#9492;&#9472;md0       ext4              1.0                   5f164fcd-7d18-419a-9d41-ea92094f0cff   77.8G    82% /scratch
sdf         linux_raid_member 1.2   madsci-nas:0     d257ac4d-7b66-eb63-141e-1300f398cc01                
&#9492;&#9472;md0       ext4              1.0                   5f164fcd-7d18-419a-9d41-ea92094f0cff   77.8G    82% /scratch
sdg                                                                                                    
&#9492;&#9472;sdg1      ext4              1.0   sandbox02       93a58c53-d8f0-4b73-a87d-00d239b5b721    1.6T     5% /tmp/disk1
nvme0n1                                                                                                
&#9500;&#9472;nvme0n1p1 vfat              FAT32                 F20B-6791                             504.9M     1% /boot/efi
&#9492;&#9472;nvme0n1p2 ext4              1.0   main            bc0e1b91-54e9-11ea-ae6e-a8a15900bd9c  221.9G    47% /

```


Next here's what my /etc/fstab looks like (comments for clarity):

```
madsci@madsci-nas: ~$ cat /etc/fstab
# 1TB Samsung 980 Pro        (M.2 NVME SSD, primary boot disk)
UUID=bc0e1b91-54e9-11ea-ae6e-a8a15900bd9c / ext4 defaults 0 0
UUID=F20B-6791 /boot/efi vfat defaults 0 0
#
# 10 TB Seagate IronWolf     (3.5 HDD 7200 RPM)
UUID=e9f7b0eb-7ebc-431c-8b25-de22b9715ee5 /archive ext4 defaults 0 0
#
# 2TB Samsung Spinpoint      (2.5 HDD 5400 RPM)
UUID=73801dd5-f2b0-48a9-98bd-80786291c443 /data/music ext4 defaults 0 0
#
# 4TB Seagate Barracuda      (3.5 HDD 5400 RPM)
UUID=f71fde5d-baeb-472a-8fdd-dbf79c9f7c22 /data/video ext4 defaults 0 0
#
/swap.img       none    swap    sw      0       0

```

You can see that the UUIDs tie together, and that the information from lsblk is used to build the /etc/fstab entries. 

One word of caution, is that if the fstab file is not constructed properly or if there is an issue with a drive upon boot-up, the system will go into emergency mode and drop you into a root terminal. 

[Here are some additional resources (albeit from DigitalOcean, hope that's okay!)]("https://www.digitalocean.com/community/tutorials/how-to-perform-basic-administration-tasks-for-storage-devices-in-linux") that may come in handy (or are a good refresher if you're already versed!)

---

### Post by sgt-mike on 2024-09-24
@kirtr  and @ madscientist032 
Thanks a lot for your replies and advice, when I proceed this time with the SAS drives and the actual zpool for production. 

I'll go back over this again as well as the Digital Ocean links (which I have used before for multiple things). 

In my playing around I used sata 2.5" laptop drives to test configuring ZFS and establish a baseline to compare  the soon to be installed actual SAS drives I ordered. I figured out what my actual problem was when I attempted lsblk -f and why I never seen the UUID for the drives. 
1. Those drives had been used in a madam array (yes I zeroed he superblocks)
2. Because ZFS is a file system and soft raid I never formatted the drives, thus the uuid wasn't present for lsblk -f to pick up and report derrrp. Never crossed my mind until later when I was creating and destroying the Zpool to play with differing setups , striped zraid, zraid2 etc.  

When I did format (ext4) the drives to be used prior to creating the Zpool they did report the UUID which I then used lsblk -f reported UUID's to create the zpool . Versus the earlier  sd# when the drives was unformatted. 

What ZFS did every time I created the zpool was automatically reformat the vdev (zraid2 array) and mount it. The process I did really helped me to kind of understand it a little better. I really liked the ease of setting the zpool up, and even adding another zraid2 vdev to it was extremely painless. When I checked the zpool using 2 vdevs consisting zraid2 it would report it as zraid2-0, zraid2-1 respectfully.  One other ting that set ZFS apart was I never had to edit /etc/fstab in my test when I rebooted multiple time soft / hard  ZFS automictically mount the zpool  with each Vdev. 

Another observation I did notice with ZFS vs Mdadm is that one can one a spare (s) to the pool to service each of the makeup zraid vdevs  really neat vs Mdadm needing to add one or two for each array. 
One way to think of it even though probably (actually not probably but actually is) wrong and inaccurate but makes sense in my head is that one can pool together multiple mdadm raid# arrays into one pool. 

---------------------------------------------------------------
Got some news on the hardware update which I'll post in my other post when I asked for advice on the hardware build.
______________________________________________________________________________
9/25/2024 --- this is updated info hardware but will affect throughput testing in the future of this post bumped system to 96Gb ram versus 64used earlier.
Been reading more on the forming of the raidz2 vdev's used in the pool. I was going to use 4 drives each, BUT according to an article/ post I read that number of drives would not be optimal for a zraid2. What was stated in the article as 5-7 drives in each vdev for a zraid2. This has caused me to rethink the first pool makeup. I need tp scour this site to see what most are using, I did see that MAFoELffen uses 5 drive but I really need to see if in his posting if that is spinners or soild state.

---

### Post by sgt-mike on 2024-09-29
Finally the HBA(s) arrived yesterday both checked out in IT mode etc. I added a fan to the LSI 9300-16i heat sink (zip ties are great) in order to help with cooling. (reserving the LSI 9300-8i into back up, or maybe use in a test bench system to format drives)

Only when I took /installed the SAS drives that bought in a lot (of 6) did it become apparent that the vendor shipped two different model numbers, same capacity 4TB, same manufacturer. 

Which changed a lot of things in the way I had intended to assemble the vdevs for the pool(s). What I had received from the vendor /seller was three 6 gb/s and three 12 gb/s. Originally I intended to go 6 drives per pool, but after much thought of throughput. Even though mixing them only had 1 drawback the 12' have to step down to the 6's. Too easy to order three more 12 gp/s drives in order to cure my OCD and get back to my original plan, 6 drives raidZ2.

So I whipped into action with a plan running face first into a brick wall at mach 8 ... pool 's would not assemble complaining of LVM or device busy, Huh I just checked them they are all on 512 sector. Now proceeding at a crawl I started to investigate (meaning I did a lot of googling on here and elsewhere). I found out that some of the drives had came out of Microsoft Server environment and had not been sanitized as advertised. Bummer... no wonder they won't assemble, so I jumped into sg_utils and sg_format, formatted all six at the same time. Now it wasn't quick (about 16hrs) but the 12gb/s drives was far outrunning the 6gb/s drives.  Problem solved drives assemble beautifully.

Now with all that transpired I had decided to use the 12gb/s drives into a raidZ1 pool three wide. So the three 6gb/s drives went into another pool, this one a stripped pool basically raid 0 (everything here data wise is backed up with the raidz1 pool and external drives)  to feed the Movies/TV shows to the plex server. 
I'm aware that 3 drives is really too small to allow the raidZ1 to be effective in throughput with even a bigger penalty in raidZ2. So I'll simply order more 12's to get to a minimum of six drive wide on that array and bump it up by adding another drive in parity (raidZ2). 

Currently I have 1 pool named plexdata raidZ1 (three 4TB 12gb/s drives) and 1 pool named plexserve stripped (three 4TB 6gb/s drives). I assembled them via alias's from their uuid's. Because of haste I assembled them as whole drives, because I didn't quite understand how to assemble them on a partition using drive alias's. Until I did both pools, no problem when I get the other drives and set them on partitions vs whole drives.  I'll implement that method later when I obtain a few more drives.  
After using the drive alias's method I really like it. Now I can somewhat tell which bay and drive number might be failing in the future for drive replacement vs a serial number hunt. Really when the system report back int1D1  degraded ... hey that's the internal bays disk1. 

So, how do the two pools stack up against each other? Not surprisingly the stripped pools really is doing good.

```

mike@beastie:/plexserv$ sudo fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=5g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
TEST: Laying out IO file (1 file / 5120MiB)
Jobs: 1 (f=1): [W(1)][58.3%][w=536MiB/s][w=536 IOPS][eta 00m:05s]
Jobs: 1 (f=1): [W(1)][86.7%][w=536MiB/s][w=535 IOPS][eta 00m:02s]
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s]
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=34992: Sun Sep 29 19:05:42 2024
  write: IOPS=471, BW=472MiB/s (495MB/s)(10.0GiB/21713msec); 0 zone resets
    slat (usec): min=201, max=3831, avg=1504.26, stdev=692.03
    clat (usec): min=2, max=6321.0k, avg=65618.34, stdev=344197.00
     lat (usec): min=330, max=6322.8k, avg=67123.13, stdev=344263.32
    clat percentiles (msec):
     |  1.00th=[    9],  5.00th=[   10], 10.00th=[   11], 20.00th=[   16],
     | 30.00th=[   41], 40.00th=[   57], 50.00th=[   58], 60.00th=[   59],
     | 70.00th=[   60], 80.00th=[   62], 90.00th=[   65], 95.00th=[   71],
     | 99.00th=[   82], 99.50th=[   87], 99.90th=[ 6275], 99.95th=[ 6342],
     | 99.99th=[ 6342]
   bw (  KiB/s): min=354304, max=2258944, per=100.00%, avg=658597.16, stdev=443965.52, samples=31
   iops        : min=  346, max= 2206, avg=643.16, stdev=433.56, samples=31
  lat (usec)   : 4=0.02%, 500=0.01%, 750=0.01%, 1000=0.01%
  lat (msec)   : 2=0.04%, 4=0.06%, 10=8.30%, 20=14.21%, 50=10.73%
  lat (msec)   : 100=66.31%, >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=1190, max=1190, avg=1190.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[ 1192],  5.00th=[ 1192], 10.00th=[ 1192], 20.00th=[ 1192],
     | 30.00th=[ 1192], 40.00th=[ 1192], 50.00th=[ 1192], 60.00th=[ 1192],
     | 70.00th=[ 1192], 80.00th=[ 1192], 90.00th=[ 1192], 95.00th=[ 1192],
     | 99.00th=[ 1192], 99.50th=[ 1192], 99.90th=[ 1192], 99.95th=[ 1192],
     | 99.99th=[ 1192]
  cpu          : usr=2.19%, sys=14.37%, ctx=61743, majf=1, minf=14
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.2%, 16=0.3%, 32=99.4%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32


Run status group 0 (all jobs):
  WRITE: bw=472MiB/s (495MB/s), 472MiB/s-472MiB/s (495MB/s-495MB/s), io=10.0GiB (10.7GB), run=21713-21713msec
mike@beastie:/plexserv$ sudo fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=5g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs
=1 --runtime=60 --group_reporting
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1)
TEST: (groupid=0, jobs=1): err= 0: pid=59840: Sun Sep 29 19:06:15 2024
  read: IOPS=3633, BW=3634MiB/s (3810MB/s)(10.0GiB/2818msec)
    slat (usec): min=229, max=977, avg=273.12, stdev=42.13
    clat (usec): min=2, max=25607, avg=8477.49, stdev=1126.32
     lat (usec): min=256, max=26581, avg=8750.89, stdev=1164.08
    clat percentiles (usec):
     |  1.00th=[ 8094],  5.00th=[ 8094], 10.00th=[ 8094], 20.00th=[ 8094],
     | 30.00th=[ 8094], 40.00th=[ 8160], 50.00th=[ 8160], 60.00th=[ 8160],
     | 70.00th=[ 8160], 80.00th=[ 8160], 90.00th=[ 9896], 95.00th=[10028],
     | 99.00th=[12911], 99.50th=[13435], 99.90th=[21890], 99.95th=[23725],
     | 99.99th=[25297]
   bw (  MiB/s): min= 2850, max= 3816, per=99.10%, avg=3601.20, stdev=422.17, samples=5
   iops        : min= 2850, max= 3816, avg=3601.20, stdev=422.17, samples=5
  lat (usec)   : 4=0.02%, 500=0.02%, 750=0.02%, 1000=0.02%
  lat (msec)   : 2=0.08%, 4=0.16%, 10=95.22%, 20=4.32%, 50=0.15%
  cpu          : usr=1.38%, sys=98.58%, ctx=9, majf=0, minf=8203
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.2%, 16=0.3%, 32=99.4%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32


Run status group 0 (all jobs):
   READ: bw=3634MiB/s (3810MB/s), 3634MiB/s-3634MiB/s (3810MB/s-3810MB/s), io=10.0GiB (10.7GB), run=2818-2818msec
---------------now to test pool plexdata-------------------------------------------------------------------------
mike@beastie:/plexdata$ sudo fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=5g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjob
s=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
TEST: Laying out IO file (1 file / 5120MiB)
Jobs: 1 (f=1): [W(1)][50.0%][w=343MiB/s][w=343 IOPS][eta 00m:07s]
Jobs: 1 (f=1): [W(1)][68.4%][w=316MiB/s][w=316 IOPS][eta 00m:06s]
Jobs: 1 (f=1): [W(1)][90.5%][w=345MiB/s][w=345 IOPS][eta 00m:02s]
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s]
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s]
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=59884: Sun Sep 29 19:08:54 2024
  write: IOPS=317, BW=318MiB/s (333MB/s)(10.0GiB/32234msec); 0 zone resets
    slat (usec): min=208, max=4409, avg=2156.49, stdev=1124.99
    clat (usec): min=2, max=10200k, avg=97425.75, stdev=555468.28
     lat (usec): min=283, max=10203k, avg=99582.82, stdev=555597.61
    clat percentiles (msec):
     |  1.00th=[    9],  5.00th=[   10], 10.00th=[   10], 20.00th=[   18],
     | 30.00th=[   49], 40.00th=[   87], 50.00th=[   88], 60.00th=[   89],
     | 70.00th=[   91], 80.00th=[   92], 90.00th=[   95], 95.00th=[  102],
     | 99.00th=[  112], 99.50th=[  116], 99.90th=[10134], 99.95th=[10134],
     | 99.99th=[10134]
   bw (  KiB/s): min=30720, max=2840576, per=100.00%, avg=453700.27, stdev=434427.67, samples=45
   iops        : min=   30, max= 2774, avg=443.07, stdev=424.25, samples=45
  lat (usec)   : 4=0.02%, 500=0.01%, 750=0.01%, 1000=0.01%
  lat (msec)   : 2=0.04%, 4=0.08%, 10=14.39%, 20=5.71%, 50=9.92%
  lat (msec)   : 100=64.39%, 250=5.11%, >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=972, max=972, avg=972.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  972],  5.00th=[  972], 10.00th=[  972], 20.00th=[  972],
     | 30.00th=[  972], 40.00th=[  972], 50.00th=[  972], 60.00th=[  972],
     | 70.00th=[  972], 80.00th=[  972], 90.00th=[  972], 95.00th=[  972],
     | 99.00th=[  972], 99.50th=[  972], 99.90th=[  972], 99.95th=[  972],
     | 99.99th=[  972]
  cpu          : usr=1.62%, sys=9.34%, ctx=62597, majf=0, minf=15
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.2%, 16=0.3%, 32=99.4%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32


Run status group 0 (all jobs):
  WRITE: bw=318MiB/s (333MB/s), 318MiB/s-318MiB/s (333MB/s-333MB/s), io=10.0GiB (10.7GB), run=32234-32234msec
mike@beastie:/plexdata$ sudo fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=5g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs
=1 --runtime=60 --group_reporting
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1)
TEST: (groupid=0, jobs=1): err= 0: pid=109236: Sun Sep 29 19:09:21 2024
  read: IOPS=3629, BW=3630MiB/s (3806MB/s)(10.0GiB/2821msec)
    slat (usec): min=225, max=947, avg=273.48, stdev=40.52
    clat (usec): min=2, max=24871, avg=8487.41, stdev=1089.44
     lat (usec): min=260, max=25820, avg=8761.18, stdev=1125.83
    clat percentiles (usec):
     |  1.00th=[ 8094],  5.00th=[ 8094], 10.00th=[ 8094], 20.00th=[ 8160],
     | 30.00th=[ 8160], 40.00th=[ 8160], 50.00th=[ 8160], 60.00th=[ 8160],
     | 70.00th=[ 8160], 80.00th=[ 8225], 90.00th=[10028], 95.00th=[10028],
     | 99.00th=[12518], 99.50th=[13304], 99.90th=[21103], 99.95th=[22938],
     | 99.99th=[24511]
   bw (  MiB/s): min= 2864, max= 3806, per=99.11%, avg=3597.60, stdev=412.03, samples=5
   iops        : min= 2864, max= 3806, avg=3597.60, stdev=412.03, samples=5
  lat (usec)   : 4=0.02%, 500=0.02%, 750=0.02%, 1000=0.02%
  lat (msec)   : 2=0.08%, 4=0.16%, 10=93.69%, 20=5.86%, 50=0.14%
  cpu          : usr=0.67%, sys=99.29%, ctx=5, majf=0, minf=8203
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.2%, 16=0.3%, 32=99.4%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32


Run status group 0 (all jobs):
   READ: bw=3630MiB/s (3806MB/s), 3630MiB/s-3630MiB/s (3806MB/s-3806MB/s), io=10.0GiB (10.7GB), run=2821-2821msec
mike@beastie:/plexserv$  sudo zpool iostat -v 30 5
              capacity     operations     bandwidth
pool        alloc   free   read  write   read  write
----------  -----  -----  -----  -----  -----  -----
plexdata     340K  10.9T      0     18  2.30K  6.23M
  raidz1-0   340K  10.9T      0     18  2.30K  6.23M
    int1d1      -      -      0      6    783  2.08M
    int1d2      -      -      0      6    783  2.08M
    int1d3      -      -      0      6    783  2.08M
----------  -----  -----  -----  -----  -----  -----
plexserv     202K  10.9T      0     11     65  9.15M
  int1d4      71K  3.62T      0      3     21  3.07M
  int1d5      68K  3.62T      0      4     21  3.03M
  ext1d1      63K  3.62T      0      3     21  3.06M
----------  -----  -----  -----  -----  -----  -----
              capacity     operations     bandwidth
pool        alloc   free   read  write   read  write
----------  -----  -----  -----  -----  -----  -----
plexdata     340K  10.9T      0      0      0      0
  raidz1-0   340K  10.9T      0      0      0      0
    int1d1      -      -      0      0      0      0
    int1d2      -      -      0      0      0      0
    int1d3      -      -      0      0      0      0
----------  -----  -----  -----  -----  -----  -----
plexserv     202K  10.9T      0      0      0      0
  int1d4      71K  3.62T      0      0      0      0
  int1d5      68K  3.62T      0      0      0      0
  ext1d1      63K  3.62T      0      0      0      0
----------  -----  -----  -----  -----  -----  -----
              capacity     operations     bandwidth
pool        alloc   free   read  write   read  write
----------  -----  -----  -----  -----  -----  -----
plexdata     340K  10.9T      0      0      0      0
  raidz1-0   340K  10.9T      0      0      0      0
    int1d1      -      -      0      0      0      0
    int1d2      -      -      0      0      0      0
    int1d3      -      -      0      0      0      0
----------  -----  -----  -----  -----  -----  -----
plexserv     202K  10.9T      0      0      0      0
  int1d4      71K  3.62T      0      0      0      0
  int1d5      68K  3.62T      0      0      0      0
  ext1d1      63K  3.62T      0      0      0      0
----------  -----  -----  -----  -----  -----  -----
              capacity     operations     bandwidth
pool        alloc   free   read  write   read  write
----------  -----  -----  -----  -----  -----  -----
plexdata     340K  10.9T      0      0      0      0
  raidz1-0   340K  10.9T      0      0      0      0
    int1d1      -      -      0      0      0      0
    int1d2      -      -      0      0      0      0
    int1d3      -      -      0      0      0      0
----------  -----  -----  -----  -----  -----  -----
plexserv     202K  10.9T      0      0      0      0
  int1d4      71K  3.62T      0      0      0      0
  int1d5      68K  3.62T      0      0      0      0
  ext1d1      63K  3.62T      0      0      0      0
----------  -----  -----  -----  -----  -----  -----
              capacity     operations     bandwidth
pool        alloc   free   read  write   read  write
----------  -----  -----  -----  -----  -----  -----
plexdata     340K  10.9T      0      0      0      0
  raidz1-0   340K  10.9T      0      0      0      0
    int1d1      -      -      0      0      0      0
    int1d2      -      -      0      0      0      0
    int1d3      -      -      0      0      0      0
----------  -----  -----  -----  -----  -----  -----
plexserv     202K  10.9T      0      0      0      0
  int1d4      71K  3.62T      0      0      0      0
  int1d5      68K  3.62T      0      0      0      0
  ext1d1      63K  3.62T      0      0      0      0
----------  -----  -----  -----  -----  -----  -----
mike@beastie:/plexserv$



```

I suspect that the pool plexdata will increase in throughput once I re-set it up back up with 6 to 11 matching drives , plus adding a spare drive or two for insurance for that pool.  
The pool plexserve I really don't see a point to buff it up until SSD's drop in price. 

I did one more thing different on  the NFS, I am trying out cockpit vs what I normally use (webmin). So far I kinda like it. but would really like it if I could monitor temps, and smart data vs going to CLI to find out that. Those two points webmin excels. Just my point of view. 

```
 mike@beastie:~$ sudo zpool status  pool: plexdata
 state: ONLINE
config:


        NAME        STATE     READ WRITE CKSUM
        plexdata    ONLINE       0     0     0
          raidz1-0  ONLINE       0     0     0
            int1d1  ONLINE       0     0     0
            int1d2  ONLINE       0     0     0
            int1d3  ONLINE       0     0     0


errors: No known data errors


  pool: plexserv
 state: ONLINE
config:


        NAME        STATE     READ WRITE CKSUM
        plexserv    ONLINE       0     0     0
          int1d4    ONLINE       0     0     0
          int1d5    ONLINE       0     0     0
          ext1d1    ONLINE       0     0     0


errors: No known data errors
mike@beastie:~$ sudo zpool history
History for 'plexdata':
2024-09-29.18:38:47 zpool create plexdata raidz1 int1d1 int1d2 int1d3 -f
2024-09-29.19:14:23 zfs set compress=lz4 plexdata


History for 'plexserv':
2024-09-29.19:01:14 zpool create plexserv int1d4 int1d5 ext1d1 -f
2024-09-29.19:14:15 zfs set compress=lz4 plexserv


mike@beastie:~$  
```

All in all so far really like ZFS, is it better than Mdadm? I "think so" although Mdadm has some feature I really like. In the end It's kinda a wash and personal choice. 
Will the current system expand .... yep!

Now I need to research how to setup / use ZFS share methods so that the Plex server isn't having to host files unloading that old HP i7 second gen.

---

### Post by sgt-mike on 2024-10-07
Since my last post I've had several things happen HBA failure (my backup HBA is running right now), acquired more 3 drives. Ordered enclosures cables etc everything to fill bays from newegg in my existing case. Bought a new case (Cooler Master HAf 922 same as the I have now) it was on auction still in the original box, I suspect it is new open stock,  i'll find out when it arrives. 

When the drives arrived the 3 - 4TB SAS (brings me up to 9 on hand) I was going through sg_format to make sure they was clean this time rather than the last batch when I assembled the pools. All went well except this one last remaining drive from that last batch order. It did not format properly while the other two did. Stumped checked my command .. exactly the same except for the drive ID. so I decided to shutdown and reboot to see if it made a difference. Now the HBA decided it was old and died on reboot I pulled it out put the 8i and into service it went, spend Hours on trying to revive the sas9033-16i at one point thought I had it nope. contacted the vendor they was kind enough to send a replacement. turned back to the last drive with the sas 9300-8i in and reissued a sg) format and now I sit here right now after HOURRSS. The time to rerun sg_format has caused me to actually rethink what I was doing with a Z1 pool and different pool with no parity or mirrors to send files to my media server. and both pools would host the exact files .......hmmmm  OK nice for practice and play but NOT really efficient use of the data pools.  I know what I was thinking, the one pool without mirrors and parity should be a good bit faster in reads ... and it is. But really do I need the speed?  Or is a Z2 vdev pool fast enough? 
My network through put is setting stable at 980 mb/s on the slow side to 1gb/s on the fast side. 

(BTW side note the drive is at 94.31% complete everyone cross your fingers that it doesn't come out at 0 bytes again) 

But the waiting game is still on with the new egg order. Why didn't I look for a US located company versus one in china for the sas cables. Excitement and pricing took over I guess.  ---- Estimated delivery 22 Oct  any way enough whining.

I know I want to use a Z2 pool so instead of my original path of two pools for movies and such.
Just do one pool and send that one to the media server , not two pools with one going to the media server. The 9th drive (that is in format) is the stickler I would like to have 2 spares to that pool, so IF it formats correctly and checks out fully. That means I would use 7 - 4 TB drives in that vdev to form the pool with 2 spares total 9. That configuration should net me  17.9TB of storage, calculating a 20% slope (free space) that means I'll have 14.3 TB usable. 
If it doesn't then it's 6 - 4TB drives in the vdev and 2 spares totals 8 drives nets 14.3TB of storage, calculating a 20% slope (free) that means I'll have 11.4 TB usable. 

Either way that will house the appox.  3 to 3.5 TB of movies etc that I have at the moment quite nicely I should think at least so for a little bit of time . Allowing me time to find some deals on either 6 or 8Tb drives to set aside. To replace either failures or expansion which ever occurs first. 

What caused the ninth drive's failure to format correctly? I don't know for sure, it could have been the HBA, or when I ssh' ed in on a different terminal and was doing stuff in the background or because the HBA was on it's last legs didn't like formatting three drives at once. Or last but not least it just died, but the smart report looked good prior to me formatting it, so I'm doubting that.

---

### Post by sgt-mike on 2024-10-07
Drive formatted correctly so 7 drives into the vdev and two spares it is... now to move data in preparation

---

### Post by sgt-mike on 2024-10-08
Ok so many changes all self inflicted (hardware wise, the raid method is pretty well locked in)...LMAO some I addressed earlier. Although I will list the the actual question on the last lines

(why I'm I posting this , simple the wife doesn't want to hear it, the daughter doesn't care, the dog and the cats just look at me and walk off. The neighbors give me a indignant look and walk off. So, I'm left with pestering ya'll ......LMAO hope you don't mind) 
After finding a couple of cases on Goodwill auctions. I acquired them, one was a cooler Master HAF 922 looked to be new in a open box. This is the same case as what my NFS server is in currently. The other was a cooler master HAF 945 as listed complete system with a 650w PSU / motherboard cpu ram 3 GPU's description was very vague  (according to my research on cooler master's web site it is actually a HAF X case). Now naturally one would ask why get these two more cases. Simple driving reason was the HAF 922 case I had gotten has a somewhat broken I/O panel when I purchased it (now is it fixed yep I super glued the I/O panel to the case, my last resort after the epoxying the broken retaining screw post and tabs failed). Now functional irritating because of the repair method, the other is that the HAF X (Haf945 as goodwill describes) has 1 more 5.25 exposed bay. Heyyyy more drives wooho.  Having already ordered the 5.25" drive bay modules before winning those cases. It will change the drive layout, which I decided to add a 2.5" 4 - drive module. Which will support 16 drives with all the bays vs 12 in the 922 case. That shift in cases causes a complete stop on my progress to finish the NFS, until the 28th of October when the last parts are scheduled to arrive via slow boat from China. I could go into details on my plans for the other two remaining 922 cases, but I won't until asked.

[COLOR=#0000cd]A (the) ACTUAL Question:[/COLOR]
We discussed the assembling of the drive into the pool (s) by using UUID, I agree with everything others said. But the delay listed above got me to thinking harder on that, not a good thing sometimes. I know one can assemble in ZFS and/or MDADM using the different UUID methods,  or even use the WWN # (world wide number) either are completely acceptable. Yet I really don't see or hear anyone advocating for the usage of the wwn ? 
I wonder why that is?
Is it because no one has thought of it, or uses that method?  Or just easier to explain when using blkid at the command prompt ?

To me it seems that a persistent ID such as wwn is better than software driven UUID. As the drive retains that ID no matter what system it is plugged into or how many times the drive is formatted. I know kind of a moot point, one really is as good as the other. And doesn't amount to a hill of beans between the two methods, they are pretty much the same animal.  I also know some drives are labeled (wwn) with it, some not, mine happen to be.  

( This is the Wiki that started my thinking on this, which led to this silly question [https://wiki.archlinux.org/title/Persistent_block_device_naming#Using_persistent_naming](https://wiki.archlinux.org/title/Persistent_block_device_naming#Using_persistent_naming) blame the arch linux guys LOL)

---

### Post by sgt-mike on 2024-10-23
Well finally everything aligned the Bay modules are in the new case populated. 
This first part is to share Benchmark data first before I get into a question or rather advise before I do anymore.
The System has nine 4TB drives wide into a pool. These drives are mixed what I mean by that is all are same Manufacture etc etc EXCEPT three are 12GP/s the other 6 are 6GP/s. System Memory is at 96GB

```
 
mike@Beastie:/mediapool1$ fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reportingTEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.36
Starting 1 process
TEST: Laying out IO file (1 file / 2048MiB)
Jobs: 1 (f=1): [W(1)][-.-%][eta 00m:00s]
Jobs: 1 (f=1): [W(1)][-.-%][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=575956: Wed Oct 23 20:34:17 2024
  write: IOPS=1103, BW=1104MiB/s (1157MB/s)(10.0GiB/9278msec); 0 zone resets
    slat (usec): min=130, max=2871, avg=292.06, stdev=166.68
    clat (usec): min=3, max=6258.6k, avg=28016.62, stdev=343258.61
     lat (usec): min=183, max=6258.8k, avg=28308.68, stdev=343254.79
    clat percentiles (msec):
     |  1.00th=[    5],  5.00th=[    6], 10.00th=[    6], 20.00th=[    6],
     | 30.00th=[    7], 40.00th=[    7], 50.00th=[    7], 60.00th=[    8],
     | 70.00th=[    8], 80.00th=[   15], 90.00th=[   17], 95.00th=[   19],
     | 99.00th=[   30], 99.50th=[   31], 99.90th=[ 6275], 99.95th=[ 6275],
     | 99.99th=[ 6275]
   bw (  MiB/s): min= 1460, max= 4856, per=100.00%, avg=3323.00, stdev=1421.97, samples=6
   iops        : min= 1460, max= 4856, avg=3323.00, stdev=1421.97, samples=6
  lat (usec)   : 4=0.03%, 10=0.02%, 250=0.03%, 500=0.05%, 750=0.04%
  lat (usec)   : 1000=0.05%
  lat (msec)   : 2=0.21%, 4=0.39%, 10=76.29%, 20=18.54%, 50=4.05%
  lat (msec)   : >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=6253.5M, max=6253.5M, avg=6253512170.00, stdev= 0.00
    sync percentiles (msec):
     |  1.00th=[ 6275],  5.00th=[ 6275], 10.00th=[ 6275], 20.00th=[ 6275],
     | 30.00th=[ 6275], 40.00th=[ 6275], 50.00th=[ 6275], 60.00th=[ 6275],
     | 70.00th=[ 6275], 80.00th=[ 6275], 90.00th=[ 6275], 95.00th=[ 6275],
     | 99.00th=[ 6275], 99.50th=[ 6275], 99.90th=[ 6275], 99.95th=[ 6275],
     | 99.99th=[ 6275]
  cpu          : usr=5.10%, sys=23.78%, ctx=2389, majf=0, minf=11
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32


Run status group 0 (all jobs):
  WRITE: bw=1104MiB/s (1157MB/s), 1104MiB/s-1104MiB/s (1157MB/s-1157MB/s), io=10.0GiB (10.7GB), run=9278-9278msec
mike@Beastie:/mediapool1$ fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize
=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.36
Starting 1 process
Jobs: 1 (f=1): [R(1)][-.-%][r=3204MiB/s][r=3204 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=576116: Wed Oct 23 20:35:08 2024
  read: IOPS=3108, BW=3109MiB/s (3260MB/s)(10.0GiB/3294msec)
    slat (usec): min=223, max=1183, avg=318.60, stdev=39.38
    clat (usec): min=2, max=28008, avg=9839.33, stdev=1131.03
     lat (usec): min=304, max=28980, avg=10157.93, stdev=1159.49
    clat percentiles (usec):
     |  1.00th=[ 6194],  5.00th=[ 9634], 10.00th=[ 9634], 20.00th=[ 9634],
     | 30.00th=[ 9634], 40.00th=[ 9634], 50.00th=[ 9634], 60.00th=[ 9634],
     | 70.00th=[ 9765], 80.00th=[ 9765], 90.00th=[11207], 95.00th=[11338],
     | 99.00th=[12125], 99.50th=[13304], 99.90th=[22676], 99.95th=[25297],
     | 99.99th=[27395]
   bw (  MiB/s): min= 2604, max= 3216, per=99.42%, avg=3090.67, stdev=241.79, samples=6
   iops        : min= 2604, max= 3216, avg=3090.67, stdev=241.79, samples=6
  lat (usec)   : 4=0.05%, 500=0.05%, 750=0.05%, 1000=0.05%
  lat (msec)   : 2=0.15%, 4=0.29%, 10=84.14%, 20=15.07%, 50=0.16%
  cpu          : usr=0.58%, sys=99.39%, ctx=9, majf=0, minf=8203
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32


Run status group 0 (all jobs):
   READ: bw=3109MiB/s (3260MB/s), 3109MiB/s-3109MiB/s (3260MB/s-3260MB/s), io=10.0GiB (10.7GB), run=3294-3294msec
mike@Beastie:/mediapool1$    

```

To be Honest I'm quite happy with the bench mark of these Rust drives. Actually exceeded my expectations. 

Now come the actual question because I was playing so much before I could actually set these SAS drive in like I wanted at on point I actually set up alais name via /etc/zfs/vdev_id.config. At that point I could create a pool using the drive aliases name. 
Then I wound up waiting  on hardware so I actually forgot HOW I did it with the laptop drives. I attempted again failed, so I used partition UUID to create the Pool played with exporting and importing the pool via disk/by-id and returning back to part-uuid setup. is there a way to export and import the pool back using the Drive alaises used in the vdev_id.config setup. 

here is how the pool is listed right now with a history of what I have done thus far.

```
mike@Beastie:/mediapool1$ sudo zpool status -v[sudo] password for mike:
  pool: mediapool1
 state: ONLINE
  scan: scrub repaired 0B in 00:44:43 with 0 errors on Wed Oct 23 10:31:45 2024
config:


        NAME                                      STATE     READ WRITE CKSUM
        mediapool1                                ONLINE       0     0     0
          raidz2-0                                ONLINE       0     0     0
            11a27fcc-ebbd-4864-9bc9-5cc7f01dc785  ONLINE       0     0     0
            1ccc6753-a8af-41a9-8a3e-3ee420d90f81  ONLINE       0     0     0
            507cbe23-0408-48b3-bfbe-e589d19ef8fe  ONLINE       0     0     0
            15bf2071-4741-4bde-9b95-15aa69e50c61  ONLINE       0     0     0
            169b4665-7aa6-4a6e-bec0-f7364f7097c4  ONLINE       0     0     0
            72d42ad6-ebeb-4fb7-a276-51285483bfba  ONLINE       0     0     0
            714d75bb-9b2e-43c2-b38b-e4068b21e105  ONLINE       0     0     0
            ca189b0c-4e82-49c0-80fe-aa6f9243f01c  ONLINE       0     0     0
            9431154c-4449-4716-9c6e-b51e436721d3  ONLINE       0     0     0


errors: No known data errors
mike@Beastie:/mediapool1$ sudo zpool history
History for 'mediapool1':
2024-10-22.09:48:04 zpool create -f mediapool1 raidz2 /dev/disk/by-partuuid/11a27fcc-ebbd-4864-9bc9-5cc7f01dc785 1ccc6753-a8af-41a9-8a3e-3ee420d90f81 507cbe23-0408-48b3-bfbe-e589d19ef8fe 15bf2071-4741-4bde-9b95-15aa69e50c61 169b4665-7aa6-4a6e-bec0-f7364f7097c4 72d42ad6-ebeb-4fb7-a276-51285483bfba 714d75bb-9b2e-43c2-b38b-e4068b21e105 ca189b0c-4e82-49c0-80fe-aa6f9243f01c 9431154c-4449-4716-9c6e-b51e436721d3
2024-10-22.09:53:48 zfs set compress=lz4 mediapool1
2024-10-22.09:55:57 zpool set autoexpand=on mediapool1
2024-10-22.21:21:13 zpool export mediapool1
2024-10-22.21:21:32 zpool import -d /dev/disk/by-id mediapool1
2024-10-22.21:22:22 zpool export mediapool1
2024-10-22.21:23:19 zpool import -d /dev/disk/by-partuuid mediapool1
2024-10-22.21:24:47 zpool export mediapool1
2024-10-22.21:25:03 zpool import -d /dev/disk/by-partuuid mediapool1
2024-10-22.21:25:30 zpool scrub mediapool1
2024-10-22.21:32:59 zpool scrub -s mediapool1
2024-10-22.21:43:56 zpool import -c /etc/zfs/zpool.cache -aN
2024-10-22.21:47:12 zpool import -c /etc/zfs/zpool.cache -aN
2024-10-22.21:57:06 zpool import -c /etc/zfs/zpool.cache -aN
2024-10-22.22:22:41 zpool import -c /etc/zfs/zpool.cache -aN
2024-10-22.22:35:45 zpool import -c /etc/zfs/zpool.cache -aN
2024-10-23.09:47:06 zpool scrub mediapool1
2024-10-23.20:19:33 zfs snapshot mediapool1@test1-snapshot
2024-10-23.20:24:08 zfs destroy mediapool1@test1-snapshot
2024-10-23.20:24:34 zfs snapshot -r mediapool1@test1-snapshot
2024-10-23.20:24:54 zfs destroy mediapool1@test1-snapshot
2024-10-23.20:25:44 zfs snapshot -r mediapool1@2024.10.23-snapshot


mike@Beastie:/mediapool1$

```

I was thinking that I should be able to export the pool and simply run "sudo zpool import -d /dev/disk/by-vdev_id mediapool1 " and then that would allow me to see the drives in their alias's name when I run  zpool status. 

 Or do I have to actually destroy the pool and start back from scratch? 

Figured I would ask first before doing silly commands.
ok that command didn't work
Finally found the answer 
export the pool 
have the vdev Id.config file loaded issue the udem trigger
import the pool with 
sudo zpool import -d /dev/disk/by-vdev mediapool1 
works close enough to what I wanted but it did add a -part1 for the partition to the name /alais


```

mike@Beastie:/$ sudo zpool export mediapool1
mike@Beastie:/$ sudo zpool import -d /dev/disk/by-vdev mediapool1
mike@Beastie:/$ sudo zpool list
NAME         SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
mediapool1  32.7T  3.43T  29.3T        -         -     0%    10%  1.00x    ONLINE  -
mike@Beastie:/$ sudo zpool status
  pool: mediapool1
 state: ONLINE
  scan: scrub repaired 0B in 00:44:43 with 0 errors on Wed Oct 23 10:31:45 2024
config:


        NAME                  STATE     READ WRITE CKSUM
        mediapool1            ONLINE       0     0     0
          raidz2-0            ONLINE       0     0     0
            bay1drive1-part1  ONLINE       0     0     0
            bay1drive2-part1  ONLINE       0     0     0
            bay1drive3-part1  ONLINE       0     0     0
            bay2drive4-part1  ONLINE       0     0     0
            bay2drive5-part1  ONLINE       0     0     0
            bay2drive6-part1  ONLINE       0     0     0
            bay3drive7-part1  ONLINE       0     0     0
            bay3drive8-part1  ONLINE       0     0     0
            bay3drive9-part1  ONLINE       0     0     0


errors: No known data errors
mike@Beastie:/$
```

That is way close enough to my goal and I can live with the -part1 without having to destroy the pool and redo it.

---

