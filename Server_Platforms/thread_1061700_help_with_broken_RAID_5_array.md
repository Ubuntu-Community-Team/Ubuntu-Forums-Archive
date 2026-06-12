---
title: "help with broken RAID 5 array"
date: 2009-02-06
forum: Server Platforms
---

### Post by anon0 on 2009-02-06
After a computer crash my 4-disk RAID 5 array (md2) stopped working. I tried the basics but it didn't help:

```
# mdadm --assemble --scan
mdadm: /dev/md2 assembled from 2 drives - not enough to start the array.

```

```

# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md3 : active raid1 sdc4[0] sdd4[1]
      29302464 blocks [2/2] [UU]
      
md2 : inactive sda1[0](S) sdd3[3](S) sdc3[2](S) sdb1[1](S)
      312592384 blocks
       
md0 : active raid1 sdc1[0] sdd1[1]
      7815488 blocks [2/2] [UU]
      
md1 : active raid1 sdc2[0] sdd2[1]
      1951808 blocks [2/2] [UU]
      
unused devices: <none>

```

```

# mdadm -A /dev/md2 /dev/sda1 /dev/sdb1 /dev/sdc3 /dev/sdd3
mdadm: /dev/md2 assembled from 2 drives - not enough to start the array.

```

Help, anyone?

Some more info:

```

# mdadm --examine /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : da607e6e:b9d4cbd8:e368bf24:bd0fce41
  Creation Time : Tue Feb  3 19:24:50 2009
     Raid Level : raid5
  Used Dev Size : 78148096 (74.53 GiB 80.02 GB)
     Array Size : 234444288 (223.58 GiB 240.07 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2

    Update Time : Thu Feb  5 20:11:44 2009
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 2
  Spare Devices : 0
       Checksum : 759760e0 - correct
         Events : 502

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        1        0      active sync   /dev/sda1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed

```

```

# mdadm --examine /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : da607e6e:b9d4cbd8:e368bf24:bd0fce41
  Creation Time : Tue Feb  3 19:24:50 2009
     Raid Level : raid5
  Used Dev Size : 78148096 (74.53 GiB 80.02 GB)
     Array Size : 234444288 (223.58 GiB 240.07 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2

    Update Time : Thu Feb  5 20:11:44 2009
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 2
  Spare Devices : 0
       Checksum : 759760f2 - correct
         Events : 502

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed

```


```

# mdadm --examine /dev/sdc3
/dev/sdc3:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : da607e6e:b9d4cbd8:e368bf24:bd0fce41
  Creation Time : Tue Feb  3 19:24:50 2009
     Raid Level : raid5
  Used Dev Size : 78148096 (74.53 GiB 80.02 GB)
     Array Size : 234444288 (223.58 GiB 240.07 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2

    Update Time : Thu Feb  5 20:09:57 2009
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 75975e89 - correct
         Events : 499

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       35        2      active sync   /dev/sdc3

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       35        2      active sync   /dev/sdc3
   3     3       8       51        3      active sync   /dev/sdd3

```

```

# mdadm --examine /dev/sdd3
/dev/sdd3:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : da607e6e:b9d4cbd8:e368bf24:bd0fce41
  Creation Time : Tue Feb  3 19:24:50 2009
     Raid Level : raid5
  Used Dev Size : 78148096 (74.53 GiB 80.02 GB)
     Array Size : 234444288 (223.58 GiB 240.07 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2

    Update Time : Thu Feb  5 20:09:57 2009
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 75975e9b - correct
         Events : 499

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       51        3      active sync   /dev/sdd3

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       35        2      active sync   /dev/sdc3
   3     3       8       51        3      active sync   /dev/sdd3

```


SMART data shows that /dev/sdc has generated many errors:
smartctl -a /dev/sda: ATA Error Count: 1
smartctl -a /dev/sdb: No Errors Logged
smartctl -a /dev/sdc: ATA Error Count: 495 (device log contains only the most recent five errors) (!!)
smartctl -a /dev/sdd: No Errors Logged

---

### Post by fjgaude on 2009-02-06
Since it seems that sdc has lots of errors you might try a forced assemble with just three of the likely good drives:

```
sudo mdadm --assemble --force /dev/sda /dev/sdb /dev/sdd
```

If that works, then try to add the /dev/sdc back into the array, then stop it, umount it, and then run **fsck** on the array.

Let us know how things go.

---

### Post by anon0 on 2009-02-06
> **fjgaude said:**
> Since it seems that sdc has lots of errors you might try a forced assemble with just three of the likely good drives:

```
sudo mdadm --assemble --force /dev/sda /dev/sdb /dev/sdd
```

If that works, then try to add the /dev/sdc back into the array, then stop it, umount it, and then run **fsck** on the array.

Let us know how things go.

Thanks, I tried that but got a segmentation error:
```
# mdadm --assemble --force /dev/sda1 /dev/sdb1 /dev/sdd3
mdadm: forcing event count in /dev/sdd3(3) from 499 upto 502
Segmentation fault

```

Also, running examine on sda1 returns this:
```

# mdadm --examine /dev/sda1
mdadm: No md superblock detected on /dev/sda1.

```
Examining the other three partitions do not return the same message.

---

### Post by fjgaude on 2009-02-08
Gosh, it is hard to say what has happened for sure. Looks like two drives have sector corruption. I guess you don't have data backup?

As a last resort you could do this: re-name the /etc/mdadm/mdadm.conf file, remove mdadm using apt-get, and re-start your computer. Then re-install mdadm and run this:

sudo mdadm --assemble --scan

That will auto create a new mdadm.conf file if mdadm finds enought UUIDs to assemble arrays. I'm sure your md0/1 will assemble okay.

Now if you have important data backed up I'd advise to re-create the raid5 array from scratch. If have to zero the superblocks for each partition of the raid5 to enable doing this.

Let us know what happens.

---

### Post by anon0 on 2009-02-08
I actually managed to restore the array by repartitioning /dev/sda1 and do:
```
# mdadm --create /dev/md2 --assume-clean --level=5 --verbose --raid-devices=4 missing /dev/sdb1 /dev/sdc3 /dev/sdd3
# mdadm --manage /dev/md2 --add /dev/sda1

```

It's not clear to me whether the source of the problem is a bad disk or some other reason.

---

### Post by fjgaude on 2009-02-08
Great going... glad you were able to figure it out yourself... I always have multiple data backups to get out of drive, hardware failures.

---

