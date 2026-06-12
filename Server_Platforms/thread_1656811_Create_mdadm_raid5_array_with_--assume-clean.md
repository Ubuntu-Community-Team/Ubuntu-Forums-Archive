---
title: "Create mdadm raid5 array with --assume-clean"
date: 2010-12-31
forum: Server Platforms
---

### Post by lotharz0r on 2010-12-31
Hello.
I have a 4 disk raid5 array consisting of 4 2TB hdds.
I used this command to create the array
>  mdadm --create /dev/md0 --level=5 --verbose --raid-devices=4 /dev/sda1 missing /dev/sdc1 /dev/sdd1

I created this array with one drive missing, because /dev/sdb1 contained all the data I wanted on the array.
When I had copied the data from /dev/sdb1 onto /dev/md0 I added /dev/sdb1 to the md0 raid array.

During the rebuild operation, something bad happened, and sdd1 got marked as failed.
Now I've got only two working drives in a 4 disk raid 5 array.

I have done a lot of searching around and found that you can create the array again with the --assume-clean option to copy data from it.

I tried this, but I get an error message:
> root@terra:~# mdadm --create /dev/md0 --assume-clean --level=5 --verbose --raid-devices=4 /dev/sda1 missing /dev/sdc1 /dev/sdd1
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 64K
mdadm: Cannot open /dev/sda1: Device or resource busy
mdadm: /dev/sdc1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Mon Dec 27 14:59:29 2010
mdadm: /dev/sdd1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Mon Dec 27 14:59:29 2010
mdadm: create aborted


What do I need to do to prepare my system for creating the array again with this command?

I tried starting the system from a USB Ubuntu Rescue Remix, but then I could not find any raid devices at all with mdadm -D --scan, or mdadm --assemble --scan.

What am I doing wrong here?
I tried commenting out the line for /dev/md0 in /etc/mdadm/mdadm.conf, but the command still failed.

---

### Post by rubylaser on 2011-01-01
Have you verified that all your disks pass a SMART test?  Disks don't normally get kicked out of a mdam array unless they have a read/write failure either due to a disk failure or a bad connection.  Also, can you run you run this on each of your disks in the array?
```
mdadm --examine /dev/sdb1
```

```
root@fileserver:# sudo mdadm --examine mdadm -E /dev/sd[bcde]1
/dev/sdb1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : d4e58776:640274d8:e368bf24:bd0fce41
  Creation Time : Sun Aug  1 16:26:04 2010
     Raid Level : raid6
  Used Dev Size : 976759808 (931.51 GiB 1000.20 GB)
     Array Size : 5860558848 (5589.06 GiB 6001.21 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

    Update Time : Sat Jan  1 07:05:35 2011
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 56417c28 - correct
         Events : 16764

         Layout : left-symmetric
     Chunk Size : 512K

      Number   Major   Minor   RaidDevice State
this     0       8       17        0      active sync   /dev/sdb1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       65        1      active sync   /dev/sde1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       33        3      active sync   /dev/sdc1
   4     4       8       97        4      active sync   /dev/sdg1
   5     5       8      129        5      active sync   /dev/sdi1
   6     6       8      113        6      active sync   /dev/sdh1
   7     7       8       81        7      active sync   /dev/sdf1

```

---

