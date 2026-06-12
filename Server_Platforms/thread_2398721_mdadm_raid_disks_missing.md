---
title: "mdadm raid disks missing"
date: 2018-08-16
forum: Server Platforms
---

### Post by petersonal2 on 2018-08-16
Dear all!
I have an ubuntu server lts  4.4.0-62-generic. I have set up a raid5 with 4 disk. I needed to remove one of the disks. I followed this blog post :[https://blog.stalkr.net/2009/10/reducing-number-of-devices-in-raid-5.html](https://blog.stalkr.net/2009/10/reducing-number-of-devices-in-raid-5.html) 
used commands: 
e2fsck -f /dev/md0
resize2fs -M /dev/md0
mdadm /dev/md0 --grow --array-size=671088640 (or some similar number what the command suggested)
mdadm /dev/md0 --grow --raid-devices=3 --backup-file=/home/petersonal/backups
/mdadm0816.backup
Still nice, raid synced 3 disk running. Time to remove the disk. Disk removed. Power on. Disks are gone:
 
mdadm -Q -D /dev/md0
/dev/md0:
        Version : 1.2
     Raid Level : raid0
  Total Devices : 3
    Persistence : Superblock is persistent

State : inactive

Name : zeus:0
           UUID : 3a745d38:272ad772:f941ee1f:ba5a7195
         Events : 135174

Number   Major   Minor   RaidDevice

-       8        1        -        /dev/sda1
       -       8       17        -        /dev/sdb1
       -       8       33        -        /dev/sdc1
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sda1[0](S) sdb1[5](S) sdc1[4](S)
      937317351 blocks super 1.2

If i examine 1 disk output is:

 mdadm --examine /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 3a745d38:272ad772:f941ee1f:ba5a7195
           Name : zeus:0
  Creation Time : Sun Feb 14 15:03:23 2016
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 624878223 (297.97 GiB 319.94 GB)
     Array Size : 624877568 (595.93 GiB 639.87 GB)
  Used Dev Size : 624877568 (297.96 GiB 319.94 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=655 sectors
          State : clean
    Device UUID : 154fe866:ec34876e:bcb5c76c:9d2da95f

Update Time : Thu Aug 16 11:49:33 2018
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 1b9d3438 - correct
         Events : 135174

Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : AAA ('A' == active, '.' == missing, 'R' == replacing)

I am very afraid to do the worng step, could someone help me please?
Should i try [COLOR=#000000]mdadm --re-add --verbose /dev/md0?
[/COLOR]

---

### Post by darkod on 2018-08-16
When you say "disk removed", did you first remove the disk from the array or you physically removed it from the server right away?

As you can see, the --grow command doesn't say which 3 raid members remain. So how did you decide which disk to remove? And as I said above, how exactly did you remove it?

---

### Post by petersonal2 on 2018-08-16
I removed the disk from the array ([COLOR=#000000]mdadm /dev/md0 --grow --raid-devices=3 --backup-file=/home/petersonal/backups[/COLOR]
[COLOR=#000000]/mdadm0816.backup)
[/COLOR]After that i checked last time with mdadmin, everything was fine, showing 3 disk, up and running, clean state, sync finished.[COLOR=#000000]
[/COLOR]I tured off the server, before that wrote down serial nubmer and disk type, searched it, pulled the matching disk out (physically), Power back on.

When the shrinking was [IMG]https://imgur.com/mboiumQ[/IMG]in progress, i could saw that sdd1 was marked to be out of the array ([https://imgur.com/mboiumQ](https://imgur.com/mboiumQ) ) This is how i decided. But if i removed the wrong disk, the other two sould be up state i think.

---

### Post by darkod on 2018-08-16
I think you missed a step. You probably needed to do --remove too, to tell mdadm to really remove it from the array. By using --grow --raid-devices=3 it doesn't actually remove a disk from the array. It reshapes the array to have 3 members and the 4th is made spare. But that is still considered part of the array.

Hence you need to do --remove.

I would connect sdd again and try to power on the server. see if that assembles the array and from there you can do checks which disk to remove and how.

Also, i see no image attached to the thread. If you are using email only i suggest to visit the forum page. Don't do forum support over email, it's not the same.

---

### Post by petersonal2 on 2018-08-16
Placed back the disk, now the raid started working. The sdd was marked as spare. I marked sdd as failed, tried mdadm --remove /dev/sdd1
but i get: mdadm: /dev/sdd1 does not appear to be an md device
started working with mdadm --remove /dev/md0 /dev/sdd1
mdadm: hot removed /dev/sdd1 from /dev/md0

Now no failed/spare disk everthing ok.
Server off. Disk off.
Turned out i was pulling out the wrong disk the whole time...
Thanks for helping out :)

---

### Post by darkod on 2018-08-16
Glad you figured it out. You can mark the thread as solved in Thread Tools above the first post.

---

