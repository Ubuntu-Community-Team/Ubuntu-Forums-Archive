---
title: "RAID cannot mount with illegal inode number"
date: 2016-07-19
forum: Server Platforms
---

### Post by grant-roch on 2016-07-19
Something happened to our RAID.  After running smart monitor it was found that one disk was corrupt and so now we have two disks /dev/sdc and /dev/sde.  The RAID was assembled with

```

sudo mdadm --assemble --force /dev/md0 /dev/sdc1 /dev/sde1
mdadm: /dev/md0 has been started with 2 drives (out of 3).
```

And mdstat looks fine:
```
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sde1[0] sdc1[3]
      1953260544 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/2] [U_U]
```

After assembling, mounting fails with:
```
sudo mount -t ext4 /dev/md0 /data
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

There are suggestions here [https://ubuntuforums.org/archive/index.php/t-1245536.html](https://ubuntuforums.org/archive/index.php/t-1245536.html) to run e2fsck and fix the disk.  Is the below the appropriate action?  Are there more steps that should be done to diagnose what the problem is?
```
sudo e2fsck /dev/md0
e2fsck 1.42.9 (4-Feb-2014)
Superblock has an invalid journal (inode 8).
Clear<y>? cancelled!
e2fsck: Illegal inode number while checking ext3 journal for /dev/md0

/dev/md0: ********** WARNING: Filesystem still has errors **********
```

---

### Post by darkod on 2016-07-19
Hmm, that message says the filesystem is ext3 while in your manual mount command you used ext4. Better not to use any -t parameter if you are not sure of the filesystem, let it detect it automatically.

Also, was it raid5 with three members? In such case losing one member is acceptable and you didn't have to use the --force parameter. The array should have assembled correctly.

Try to check superblock details with:
```
sudo mdadm --examine /dev/sdc1
sudo mdadm --examine /dev/sde1
etc (run that for each member partition including the failed one if still present)
```

Post the results if you need help with them.

---

### Post by grant-roch on 2016-07-20
Had to restart the server so drives are now labelled sdb and sdd.  Also, then the array was working before the entry in our fstab mounts with ext4 so I believe that should be fine.  The mention of ext3, however, does confuse me as well.

```
#/dev/md0    /data        ext4    defaults    1    2
```

Assembling through --scan gives the below which is also weird as tests on sdd were fine:

```
localadmin@main ~ $ sudo mdadm --assemble --scan
mdadm: ignoring /dev/sdb1 as it reports /dev/sdd1 as failed
mdadm: /dev/md0 assembled from 1 drive - not enough to start the array.
```

--examine results in the below:
```
localadmin@main ~ $ sudo mdadm --examine /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 87171c35:08aa450f:f7fef45b:1f244bca
           Name : main:0  (local to host main)
  Creation Time : Sun Apr 21 17:22:33 2013
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 1953260976 (931.39 GiB 1000.07 GB)
     Array Size : 1953260544 (1862.77 GiB 2000.14 GB)
  Used Dev Size : 1953260544 (931.39 GiB 1000.07 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : e021a760:edee11cc:8a0dee56:6d9a1170

    Update Time : Sun May  1 02:36:48 2016
       Checksum : 75dda45 - correct
         Events : 3245847

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : AAA ('A' == active, '.' == missing)
localadmin@main ~ $ sudo mdadm --examine /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 87171c35:08aa450f:f7fef45b:1f244bca
           Name : main:0  (local to host main)
  Creation Time : Sun Apr 21 17:22:33 2013
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 1953260976 (931.39 GiB 1000.07 GB)
     Array Size : 1953260544 (1862.77 GiB 2000.14 GB)
  Used Dev Size : 1953260544 (931.39 GiB 1000.07 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : fc14aacd:7e0e9c8f:45ce23ce:dc27bf5b

    Update Time : Mon Jul 18 09:51:43 2016
       Checksum : 9b336b8d - correct
         Events : 3245847

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : ..A ('A' == active, '.' == missing)

```

It is not clear from here what I should do.

---

### Post by darkod on 2016-07-20
Well, according to the examine data, all is good on sdb1 and sdd1. If you take a look, the array UUID is the same, the Events are identical, and even the State is clean. It should assemble with these two partitions from three.

Maybe you only need to force it, to clear any faulty tags that it might have set.

The command to try would be (if the first doesn't work you can try the second):
```
sudo mdadm --assemble --force --verbose /dev/md0 /dev/sdd1 /dev/sdb1
sudo mdadm --assemble --force --run --verbose /dev/md0 /dev/sdd1 /dev/sdb1
```

See if that helps you... First it has to assemble, later you can work on the filesystem issue.

---

