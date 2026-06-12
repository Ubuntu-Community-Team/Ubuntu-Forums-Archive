---
title: "Hard disks in raid array constantly working when mounted"
date: 2012-01-29
forum: Server Platforms
---

### Post by Sab3r on 2012-01-29
This has been solved. See [post #13](http://ubuntuforums.org/showpost.php?p=11656726&postcount=13).

I'm using Ubuntu Server 11.10 and the hard drives in my (md) raid-5 array are constantly working (I can hear them crunching) when I mount them. Soon after I unmount them, they stop. 

I've got 3 Seagate Barracuda Green 2TB and 1 WD Caviar Green 2TB running in raid-5 and 'cat /proc/mdstat' outputs the following: 
```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sde[4] sdd[2] sdc[1] sdb[0]
      5860540224 blocks super 1.2 level 5, 64k chunk, algorithm 2 [4/4] [UUUU]
      bitmap: 2/15 pages [8KB], 65536KB chunk

unused devices: <none>

```

I don't want my drives to die prematurely, so how can I figure out what's making them work constantly?

---

### Post by Wayne_V on 2012-01-29
$ tail /var/log/{dmesg,*log}

and then mount the drive and see if any errors are being logged

run "$ sudo smartctl -a /dev/sdX" on each of the drives and check for errors.

see what iostat says (may need to play around with the options a little):

$ sudo iostat -p sdb sdc sdd sde md0 5

---

### Post by Sab3r on 2012-01-29
No errors regarding mount or md in the '/var/log's. 

Here are 5 logs with 5 sec intervals from iostat. I don't know how to read from this. 
```


Linux 3.0.0-15-generic (Imbi2) 	01/29/2012 	_x86_64_	(2 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.10    0.00    0.56    1.10    0.00   98.24

Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
sdb               6.90         2.78       473.65      36188    6176170
sdc               6.15         3.01       457.18      39198    5961434
sdd               6.34        28.64       457.19     373489    5961538
sde               6.93        15.00       470.82     195634    6139314
md0              22.15         0.73      1342.88       9520   17510652

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.10    0.00    0.00    2.20    0.00   97.70

Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
sdb               4.80         2.40       390.60         12       1953
sdc               4.60         0.00       393.00          0       1965
sdd               5.00        28.00       386.60        140       1933
sde               4.40        12.80       290.60         64       1453
md0              19.80         0.00      1231.20          0       6156

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.00    0.00    0.10    1.52    0.00   98.38

Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
sdb               5.60         2.40       330.60         12       1653
sdc               4.60         0.00       316.20          0       1581
sdd               4.80        28.00       305.00        140       1525
sde               6.00        12.80       431.40         64       2157
md0              13.40         0.00       821.60          0       4108

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.00    0.00    0.10    1.49    0.00   98.41

Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
sdb               5.60         3.20       430.00         16       2150
sdc               5.40         0.00       419.60          0       2098
sdd               5.40        28.00       417.20        140       2086
sde               5.40        12.80       432.40         64       2162
md0              19.80         0.00      1231.20          0       6156

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.00    0.00    0.10    0.10    0.00   99.80

Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
sdb               5.00         0.80       430.00          4       2150
sdc               4.80         0.00       417.20          0       2086
sdd               4.80        25.60       417.20        128       2086
sde               4.80        12.80       430.00         64       2150
md0              19.20         0.00      1228.80          0       6144

``` 

Can you make anything from this? 

Thanks.

---

### Post by codmate on 2012-01-29
Something is doing a lot of writing.

Have you looked in 'top' to see if anything is growing in memory usage. You can order the fields in 'top' by pressing CTRL+f and then the appropriate letter. o,p,q,r,s and t; all related to memory, could be of interest.

'vmstat' could also be useful:
[http://linuxcommand.org/man_pages/vmstat8.html](http://linuxcommand.org/man_pages/vmstat8.html)

---

### Post by Wayne_V on 2012-01-30
is the 'cat /proc/mdstat' from when the drives were mounted?

---

### Post by Sab3r on 2012-01-30
*(I've been talking about "mounting the **drives**", what I've meant was "mounting the **partitions**". Not that it should make any difference.)*

Yes. The only thing that changes in 'cat /proc/mdstat' when I unmount the partitions is bitmap, it goes from '**bitmap: 2/15 pages [8KB]**' to '**bitmap: 0/15 pages [0KB]**'. 

UPDATE: Been looking more into the iostat log. Am I right to read from it that every 5 sec, around 6 MBytes are written onto the array?

UPDATE 2: Confirmed. When the partitions are unmounted, iostat reports 0 "wrtn" to all the drives, during 5 sec intervals. 

UPDATE 3: According to 'top', when the partitions are mounted, md0_raid5 is demanding the most (by far) CPU time (still with 0% CPU usage and MEM usage). As soon as I unmount the partitions, md0_raid5 stops demanding CPU time.  Also, it makes no difference if I kill all significant services (webmin, apache, samba & ssh). I think md0_raid5 is the culprit. Now I just need to figure out what it's doing and why.

---

### Post by Sab3r on 2012-01-31
I need to figure this out before I start using the server. 

Does it matter that instead of creating a partition on each of the drives and then adding them to raid array, I made the array out the disks themselves and then added a GPT partition table and two ext4 partitions to the array? (using 'parted' and 'gdisk') 

Why would the md0_raid5 service be demanding so much CPU time... anyone? :confused:

---

### Post by wirelessmonkey on 2012-01-31
Syncing and parity calculation, maybe?

---

### Post by Sab3r on 2012-01-31
So it's normal that it's writing 1.5 MBytes/sec to the array constantly, even though nothing is being done on the partitions/drives? 

Isn't it supposed to calculate parity the same time it writes user files to the partitions?

---

### Post by Wayne_V on 2012-01-31
can you post the output of

$ sudo mdadm --detail /dev/md0
$ for D in b c d e ; do sudo mdadm --examine /dev/sd${D} ; done

---

### Post by Sab3r on 2012-01-31
> **Wayne_V said:**
> $ sudo mdadm --detail /dev/md0

```

/dev/md0:
        Version : 1.2
  Creation Time : Sat Jan 28 17:03:38 2012
     Raid Level : raid5
     Array Size : 5860540224 (5589.05 GiB 6001.19 GB)
  Used Dev Size : 1953513408 (1863.02 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent

  Intent Bitmap : Internal

    Update Time : Tue Jan 31 21:51:29 2012
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           Name : Imbi:0
           UUID : 404e89ba:f56d9455:62009335:51e318d8
         Events : 29

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc
       2       8       48        2      active sync   /dev/sdd
       4       8       64        3      active sync   /dev/sde

```

> **Wayne_V said:**
> $ for D in b c d e ; do sudo mdadm --examine /dev/sd${D} ; done
```


/dev/sdb:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 404e89ba:f56d9455:62009335:51e318d8
           Name : Imbi:0
  Creation Time : Sat Jan 28 17:03:38 2012
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 3907027120 (1863.02 GiB 2000.40 GB)
     Array Size : 11721080448 (5589.05 GiB 6001.19 GB)
  Used Dev Size : 3907026816 (1863.02 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 2d959798:82c91b97:6760408f:ba7c8343

Internal Bitmap : 2 sectors from superblock
    Update Time : Tue Jan 31 21:53:32 2012
       Checksum : a21c5f32 - correct
         Events : 29

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 0
   Array State : AAAA ('A' == active, '.' == missing)
/dev/sdc:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 404e89ba:f56d9455:62009335:51e318d8
           Name : Imbi:0
  Creation Time : Sat Jan 28 17:03:38 2012
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 3907027120 (1863.02 GiB 2000.40 GB)
     Array Size : 11721080448 (5589.05 GiB 6001.19 GB)
  Used Dev Size : 3907026816 (1863.02 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 02e27d14:c0410829:7388281f:de5e75cb

Internal Bitmap : 2 sectors from superblock
    Update Time : Tue Jan 31 21:53:32 2012
       Checksum : c7c92e75 - correct
         Events : 29

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 1
   Array State : AAAA ('A' == active, '.' == missing)
/dev/sdd:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 404e89ba:f56d9455:62009335:51e318d8
           Name : Imbi:0
  Creation Time : Sat Jan 28 17:03:38 2012
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 3907027120 (1863.02 GiB 2000.40 GB)
     Array Size : 11721080448 (5589.05 GiB 6001.19 GB)
  Used Dev Size : 3907026816 (1863.02 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : c1e2ccf8:b93cece3:ff0da327:8180bdd5

Internal Bitmap : 2 sectors from superblock
    Update Time : Tue Jan 31 21:53:32 2012
       Checksum : 79bed15f - correct
         Events : 29

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 2
   Array State : AAAA ('A' == active, '.' == missing)
/dev/sde:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 404e89ba:f56d9455:62009335:51e318d8
           Name : Imbi:0
  Creation Time : Sat Jan 28 17:03:38 2012
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 3907027120 (1863.02 GiB 2000.40 GB)
     Array Size : 11721080448 (5589.05 GiB 6001.19 GB)
  Used Dev Size : 3907026816 (1863.02 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : f73a5095:e45f8b15:8e132920:6291d129

Internal Bitmap : 2 sectors from superblock
    Update Time : Tue Jan 31 21:53:32 2012
       Checksum : 947b6330 - correct
         Events : 29

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 3
   Array State : AAAA ('A' == active, '.' == missing)

``` 

Thanks Wayne for not giving up on me. 
[img]http://www.controlledlabsforum.com/images/smilies/3.gif[/img]

---

### Post by Wayne_V on 2012-02-01
The only other thing I can think of is to check to make sure the block size is the same on all the disks:

$ fdisk -l /dev/sd[bcde]

If they are, maybe you should switch to using partitions instead of the raw block device.   Would be a good exercise for disk recovery too ;)


- back up any data you might have on the array already!!!!!

-then, for each disk sdb, sdc, sdd, sde do (example using sdb):

$ sudo mdadm --fail /dev/md0 /dev/sdb
$ sudo mdadm --remove /dev/md0 /dev/sdb
$ sudo fdisk /dev/sdb
--- create one partition on entire disk
$ sudo mdadm --add /dev/md0 /dev/sdb1
$ sudo cat /proc/mdstat
(wait for reconstruction to complete before starting the next drive)

---

### Post by Sab3r on 2012-02-01
I think I may have wasted your time for nothing. I let the server run through the night with the partitions mounted and lo & behold, this morning the drives had stopped crunching. 'iostat' reports nothing being written to the drives and 'md5_raid5' is not demanding any CPU time. 'cat /proc/mdstat' reports "bitmap: 0/15 pages...", like when the partitions were not mounted before, but they are definitely mounted this time. 

Don't know what it was doing, but I guess I never gave it a chance to finish. #-o 

Thanks guys and so sorry again for wasting your time. 

Noobs: When creating an md array, when it has finished (re)constructing the array (which took around 10 hours for me), let it still run through the night and then check it for 100% functionality.

---

### Post by Wayne_V on 2012-02-02
good to hear - odd tho, I would have expected to see a status in mdstat that it was still building the array.  something like what you see when it is recovering a drive:

```

md0 : active raid1 hdb1[2] hda1[1]
      119684160 blocks [2/1] [_U]
      [>....................]  recovery =  0.2% (250108/119684160) finish=198.8min speed=10004K/sec

```

---

