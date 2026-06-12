---
title: "Raid5 failure after just one drive failed"
date: 2017-03-09
forum: Server Platforms
---

### Post by lars17 on 2017-03-09
Hi. 
I have a problem With my RAID5 array, when i came home and went Down i head that one drive had failed. I found the drive and stoped the Server since i dont have HOTswap i had turn it of and replace the drive. when i had replace the drive the Array had failed. even With just one drive failure. now i cannot assemble the array even With 8 out of 9 drives present.

```
sudo mdadm --assemble --scan --force
mdadm: /dev/md1 assembled from 7 drives - not enough to start the  array.

```

here is the output of ```
 sudo mdadm --examine /dev/sd#
```

```
/dev/sda:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : e6bac54f:96358ee6:f7234534:9c04635e
           Name : DAVID:1  (local to host DAVID)
  Creation Time : Fri Sep 30 21:16:50 2016
     Raid Level : raid5
   Raid Devices : 9
 Avail Dev Size : 1464887024 (698.51 GiB 750.02 GB)
     Array Size : 3906043904 (3725.09 GiB 3999.79 GB)
  Used Dev Size : 976510976 (465.64 GiB 499.97 GB)
    Data Offset : 231424 sectors
   Super Offset : 8 sectors
   Unused Space : before=231336 sectors, after=488406768 sectors
          State : clean
    Device UUID : 2df4c294:a7353a28:d959d06f:d01a9e2b
Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Mar  6 11:43:21 2017
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 279ca274 - correct
         Events : 313662
         Layout : left-asymmetric
     Chunk Size : 1024K
   Device Role : Active device 7
   Array State : AAAAAA.A. ('A' == active, '.' == missing, 'R' == replacing)


/dev/sdb:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : e6bac54f:96358ee6:f7234534:9c04635e
           Name : DAVID:1  (local to host DAVID)
  Creation Time : Fri Sep 30 21:16:50 2016
     Raid Level : raid5
   Raid Devices : 9
 Avail Dev Size : 976525360 (465.64 GiB 499.98 GB)
     Array Size : 3906043904 (3725.09 GiB 3999.79 GB)
  Used Dev Size : 976510976 (465.64 GiB 499.97 GB)
    Data Offset : 231424 sectors
   Super Offset : 8 sectors
   Unused Space : before=231336 sectors, after=30768 sectors
          State : clean
    Device UUID : 1de608f8:525e69c3:c3ae3c67:14ecfac7
Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Mar  6 11:43:21 2017
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 9cbf147f - correct
         Events : 313662
         Layout : left-asymmetric
     Chunk Size : 1024K
   Device Role : Active device 2
   Array State : AAAAAA.A. ('A' == active, '.' == missing, 'R' == replacing)


/dev/sdd:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : e6bac54f:96358ee6:f7234534:9c04635e
           Name : DAVID:1  (local to host DAVID)
  Creation Time : Fri Sep 30 21:16:50 2016
     Raid Level : raid5
   Raid Devices : 9
 Avail Dev Size : 976511024 (465.64 GiB 499.97 GB)
     Array Size : 3906043904 (3725.09 GiB 3999.79 GB)
  Used Dev Size : 976510976 (465.64 GiB 499.97 GB)
    Data Offset : 231424 sectors
   Super Offset : 8 sectors
   Unused Space : before=231336 sectors, after=30768 sectors
          State : clean
    Device UUID : 6222d78e:889336b7:d6ef454c:35075f50
Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Mar  6 11:43:21 2017
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 94c7aa24 - correct
         Events : 313662
         Layout : left-asymmetric
     Chunk Size : 1024K
   Device Role : Active device 0
   Array State : AAAAAA.A. ('A' == active, '.' == missing, 'R' == replacing)


/dev/sdg:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : e6bac54f:96358ee6:f7234534:9c04635e
           Name : DAVID:1  (local to host DAVID)
  Creation Time : Fri Sep 30 21:16:50 2016
     Raid Level : raid5
   Raid Devices : 9
 Avail Dev Size : 976511024 (465.64 GiB 499.97 GB)
     Array Size : 3906043904 (3725.09 GiB 3999.79 GB)
  Used Dev Size : 976510976 (465.64 GiB 499.97 GB)
    Data Offset : 231424 sectors
   Super Offset : 8 sectors
   Unused Space : before=231336 sectors, after=30768 sectors
          State : clean
    Device UUID : 01246b4b:3ca65d2a:95191dec:eb859afd
Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Mar  6 11:43:21 2017
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 119566ee - correct
         Events : 313662
         Layout : left-asymmetric
     Chunk Size : 1024K
   Device Role : Active device 1
   Array State : AAAAAA.A. ('A' == active, '.' == missing, 'R' == replacing)


/dev/sdi:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : e6bac54f:96358ee6:f7234534:9c04635e
           Name : DAVID:1  (local to host DAVID)
  Creation Time : Fri Sep 30 21:16:50 2016
     Raid Level : raid5
   Raid Devices : 9
 Avail Dev Size : 976511024 (465.64 GiB 499.97 GB)
     Array Size : 3906043904 (3725.09 GiB 3999.79 GB)
  Used Dev Size : 976510976 (465.64 GiB 499.97 GB)
    Data Offset : 231424 sectors
   Super Offset : 8 sectors
   Unused Space : before=231336 sectors, after=30768 sectors
          State : clean
    Device UUID : cc1f68ed:311ef1ec:04ad81ad:431b1c0a
Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Mar  6 11:35:09 2017
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 44140189 - correct
         Events : 313657
         Layout : left-asymmetric
     Chunk Size : 1024K
   Device Role : Active device 6
   Array State : AAAAAAAA. ('A' == active, '.' == missing, 'R' == replacing)


/dev/sdj:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : e6bac54f:96358ee6:f7234534:9c04635e
           Name : DAVID:1  (local to host DAVID)
  Creation Time : Fri Sep 30 21:16:50 2016
     Raid Level : raid5
   Raid Devices : 9
 Avail Dev Size : 976511024 (465.64 GiB 499.97 GB)
     Array Size : 3906043904 (3725.09 GiB 3999.79 GB)
  Used Dev Size : 976510976 (465.64 GiB 499.97 GB)
    Data Offset : 231424 sectors
   Super Offset : 8 sectors
   Unused Space : before=231336 sectors, after=30768 sectors
          State : clean
    Device UUID : 87031d81:14e905e0:344d5033:15f4d6a3
Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Mar  6 11:43:21 2017
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : ea5f2b17 - correct
         Events : 313662
         Layout : left-asymmetric
     Chunk Size : 1024K
   Device Role : Active device 4
   Array State : AAAAAA.A. ('A' == active, '.' == missing, 'R' == replacing)


/dev/sdk:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : e6bac54f:96358ee6:f7234534:9c04635e
           Name : DAVID:1  (local to host DAVID)
  Creation Time : Fri Sep 30 21:16:50 2016
     Raid Level : raid5
   Raid Devices : 9
 Avail Dev Size : 976511024 (465.64 GiB 499.97 GB)
     Array Size : 3906043904 (3725.09 GiB 3999.79 GB)
  Used Dev Size : 976510976 (465.64 GiB 499.97 GB)
    Data Offset : 231424 sectors
   Super Offset : 8 sectors
   Unused Space : before=231336 sectors, after=30768 sectors
          State : clean
    Device UUID : e7402979:1d9e9688:7579b303:bba17b96
Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Mar  6 11:43:21 2017
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 4e03f768 - correct
         Events : 313662
         Layout : left-asymmetric
     Chunk Size : 1024K
   Device Role : Active device 5
   Array State : AAAAAA.A. ('A' == active, '.' == missing, 'R' == replacing)


/dev/sdl:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : e6bac54f:96358ee6:f7234534:9c04635e
           Name : DAVID:1  (local to host DAVID)
  Creation Time : Fri Sep 30 21:16:50 2016
     Raid Level : raid5
   Raid Devices : 9
 Avail Dev Size : 976511024 (465.64 GiB 499.97 GB)
     Array Size : 3906043904 (3725.09 GiB 3999.79 GB)
  Used Dev Size : 976510976 (465.64 GiB 499.97 GB)
    Data Offset : 231424 sectors
   Super Offset : 8 sectors
   Unused Space : before=231336 sectors, after=30768 sectors
          State : clean
    Device UUID : 381eb16f:467d8316:8508636e:00dd24cc
Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Mar  6 11:43:21 2017
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 72d17e35 - correct
         Events : 313662
         Layout : left-asymmetric
     Chunk Size : 1024K
   Device Role : Active device 3
   Array State : AAAAAA.A. ('A' == active, '.' == missing, 'R' == replacing)


```

Ive been Reading a bit and found out that maybe the events number can be a problem. so i checked all disk and found out that [SIZE=4][COLOR=#ff0000]/dev/sdi[/COLOR][/SIZE] had a diffrent events number then the rest. Can that be part of the problem that i cannot assemble the array??

I have replaced the broken drive in the pc but not in the array, so the array has 8 of 9 drives. 


Is there a way to get mdadm understand that all drives are in the same array?'

output of mdadm.conf
```

  GNU nano 2.5.3       Fil: /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#
# by default (built-in), scan all partitions (/proc/partitions) an$
# containers for MD superblocks. alternatively, specify devices to$
# wildcards if desired.
#DEVICE partitions containers
# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes
# automatically tag new arrays as belonging to the local system
HOMEHOST <system>
# instruct the monitoring daemon where to send mail alerts
MAILADDR root
# definitions of existing MD arrays
ARRAY /dev/md/0  metadata=1.2 UUID=347a4c62:484d5799:88b37d14:ebfd$
# This file was auto-generated on Mon, 12 Sep 2016 18:51:51 +0200
# by mkconf $Id$
ARRAY /dev/md0 uuid=e69b1c65:abe12134:986db965:5c50c26f
ARRAY /dev/md1 uuid=e6bac54f:96358ee6:f7234534:9c04635e


```

---

### Post by darkod on 2017-03-09
Few pieces of advice...

1. Do not use whole disks as mdadm members. Create one single partition on the disk and leave the last 15-20MB unpartitioned (unused). Then use the partitions to create the array. The reason is that not all disks are always equal to the exact number of sectors. And if a new disk is few sectors smaller, you will not be able to add it to the array. Leaving 15MB unused at the end makes it possible to almost always create partitions of the same size and add them to the array without issues.
2. raid5 of so many disks is not really recommended. Think about switching to raid6 or even ZFS.

Now to your problem... The assemble force should have assembled it. Next to try is adding --run. So try something like:
```
sudo mdadm --assemble --force --verbose /dev/md1 /dev/sd[abdgijkl]
sudo mdadm --assemble --force --run --verbose /dev/md1 /dev/sd[abdgijkl]
```

That should work and if it doesn't the --verbose option will give you little bit more details.

---

### Post by lars17 on 2017-03-09
So ive tried it and it stil won't assemble. saying that /dev/sdi is out of date

```
sudo mdadm --assemble --force --verbose /dev/md1 /dev/sd[abdgijkl]
mdadm: looking for devices for /dev/md1
mdadm: /dev/sda is identified as a member of /dev/md1, slot 7.
mdadm: /dev/sdb is identified as a member of /dev/md1, slot 2.
mdadm: /dev/sdd is identified as a member of /dev/md1, slot 0.
mdadm: /dev/sdg is identified as a member of /dev/md1, slot 1.
mdadm: /dev/sdi is identified as a member of /dev/md1, slot 6.
mdadm: /dev/sdj is identified as a member of /dev/md1, slot 4.
mdadm: /dev/sdk is identified as a member of /dev/md1, slot 5.
mdadm: /dev/sdl is identified as a member of /dev/md1, slot 3.
mdadm: added /dev/sdg to /dev/md1 as 1
mdadm: added /dev/sdb to /dev/md1 as 2
mdadm: added /dev/sdl to /dev/md1 as 3
mdadm: added /dev/sdj to /dev/md1 as 4
mdadm: added /dev/sdk to /dev/md1 as 5
mdadm: added /dev/sdi to /dev/md1 as 6 (possibly out of date)
mdadm: added /dev/sda to /dev/md1 as 7
mdadm: no uptodate device for slot 16 of /dev/md1
mdadm: added /dev/sdd to /dev/md1 as 0
mdadm: /dev/md1 assembled from 7 drives - not enough to start the array.
```

I was going to ad a 10th drive and Upgrade the array to RAID6 after my backup was finisher but one drive failed before even the backup was complete.

So as i suspected, /dev/sdi is giving me a problem

so i was checking this link: [http://askubuntu.com/questions/621824/re-assemble-out-of-date-raid5](http://askubuntu.com/questions/621824/re-assemble-out-of-date-raid5) but i'm not sure how to proceed.
is thats my case at all.

---

### Post by darkod on 2017-03-09
Did you try by adding --run? That can handle out of date members usually.

---

### Post by lars17 on 2017-03-09
Not working :(

```
sudo mdadm --assemble --force --run --verbose /dev/md1 /dev/sd[abdgijkl]
mdadm: looking for devices for /dev/md1
mdadm: /dev/sda is identified as a member of /dev/md1, slot 7.
mdadm: /dev/sdb is identified as a member of /dev/md1, slot 2.
mdadm: /dev/sdd is identified as a member of /dev/md1, slot 0.
mdadm: /dev/sdg is identified as a member of /dev/md1, slot 1.
mdadm: /dev/sdi is identified as a member of /dev/md1, slot 6.
mdadm: /dev/sdj is identified as a member of /dev/md1, slot 4.
mdadm: /dev/sdk is identified as a member of /dev/md1, slot 5.
mdadm: /dev/sdl is identified as a member of /dev/md1, slot 3.
mdadm: added /dev/sdg to /dev/md1 as 1
mdadm: added /dev/sdb to /dev/md1 as 2
mdadm: added /dev/sdl to /dev/md1 as 3
mdadm: added /dev/sdj to /dev/md1 as 4
mdadm: added /dev/sdk to /dev/md1 as 5
mdadm: added /dev/sdi to /dev/md1 as 6 (possibly out of date)
mdadm: added /dev/sda to /dev/md1 as 7
mdadm: no uptodate device for slot 16 of /dev/md1
mdadm: added /dev/sdd to /dev/md1 as 0
mdadm: failed to RUN_ARRAY /dev/md1: Input/output error
mdadm: Not enough devices to start the array.

```

---

### Post by lars17 on 2017-03-09
I just need to Access my data so i can do a backup of the latest files so can recreate my array if that's the case

---

### Post by darkod on 2017-03-09
The last thing you can try is recreating the array but be VERY careful with the command because you need to use the --assume-clean option. Otherwise --create creates new blank array without that option. You also need to use the same order of the members, but you already have the order in the verbose output above.

So the command would be something like (use stop array first just in case anything is active):
```
sudo mdadm --stop /dev/md1
sudo mdadm --create --assume-clean --verbose --level=raid5 --raid-devices=9 /dev/md1 /dev/sdd /dev/sdg /dev/sdb /dev/sdl /dev/sdj /dev/sdk /dev/sdi /dev/sda missing
```

That should recreate it letting it know that the last member is missing, and keeping all data intact. Double check the members order but I think I got it right. Good luck.

---

### Post by lars17 on 2017-03-09
So this is what i get now. is this safe??

```
 sudo mdadm --create --assume-clean --verbose --level=raid5 --raid-devices=9 /dev/md1 /dev/sdd /dev/sdg /dev/sdb /dev/sdl /dev/sdj /dev/sdk /dev/sdi /dev/sda missing
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 512K
mdadm: /dev/sdd appears to be part of a raid array:
       level=raid5 devices=9 ctime=Fri Sep 30 21:16:50 2016
mdadm: partition table exists on /dev/sdd but will be lost or
       meaningless after creating array
mdadm: /dev/sdg appears to be part of a raid array:
       level=raid5 devices=9 ctime=Fri Sep 30 21:16:50 2016
mdadm: partition table exists on /dev/sdg but will be lost or
       meaningless after creating array
mdadm: /dev/sdb appears to be part of a raid array:
       level=raid5 devices=9 ctime=Fri Sep 30 21:16:50 2016
mdadm: partition table exists on /dev/sdb but will be lost or
       meaningless after creating array
mdadm: /dev/sdl appears to be part of a raid array:
       level=raid5 devices=9 ctime=Fri Sep 30 21:16:50 2016
mdadm: partition table exists on /dev/sdl but will be lost or
       meaningless after creating array
mdadm: /dev/sdj appears to be part of a raid array:
       level=raid5 devices=9 ctime=Fri Sep 30 21:16:50 2016
mdadm: partition table exists on /dev/sdj but will be lost or
       meaningless after creating array
mdadm: /dev/sdk appears to be part of a raid array:
       level=raid5 devices=9 ctime=Fri Sep 30 21:16:50 2016
mdadm: partition table exists on /dev/sdk but will be lost or
       meaningless after creating array
mdadm: /dev/sdi appears to be part of a raid array:
       level=raid5 devices=9 ctime=Fri Sep 30 21:16:50 2016
mdadm: partition table exists on /dev/sdi but will be lost or
       meaningless after creating array
mdadm: /dev/sda appears to be part of a raid array:
       level=raid5 devices=9 ctime=Fri Sep 30 21:16:50 2016
mdadm: partition table exists on /dev/sda but will be lost or
       meaningless after creating array
mdadm: size set to 488255488K
mdadm: automatically enabling write-intent bitmap on large array
mdadm: largest drive (/dev/sda) exceeds size (488255488K) by more than 1%

```

---

### Post by darkod on 2017-03-09
Looks OK, no errors reported. Did it assemble the array?

I am surprised to see a message there is partition table on the disks. Are you sure you are using disks as members and not partitions?

Just in case, don't mount the array and don't start writing on it.

---

### Post by lars17 on 2017-03-09
```
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md1 started.

```

```
sudo mdadm --examine /dev/md1
mdadm: No md superblock detected on /dev/md1.

```

So here is what i see now

```

 sudo mdadm --detail /dev/md1
/dev/md1:
        Version : 1.2
  Creation Time : Thu Mar  9 22:42:56 2017
     Raid Level : raid5
     Array Size : 3906043904 (3725.09 GiB 3999.79 GB)
  Used Dev Size : 488255488 (465.64 GiB 499.97 GB)
   Raid Devices : 9
  Total Devices : 8
    Persistence : Superblock is persistent
  Intent Bitmap : Internal
    Update Time : Thu Mar  9 22:42:56 2017
          State : clean, degraded
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0
         Layout : left-symmetric
     Chunk Size : 512K
           Name : DAVID:1  (local to host DAVID)
           UUID : 173b15e6:d1d95111:2e1c7893:9a6698ae
         Events : 0
    Number   Major   Minor   RaidDevice State
       0       8       48        0      active sync   /dev/sdd
       1       8       96        1      active sync   /dev/sdg
       2       8       16        2      active sync   /dev/sdb
       3       8      176        3      active sync   /dev/sdl
       4       8      144        4      active sync   /dev/sdj
       5       8      160        5      active sync   /dev/sdk
       6       8      128        6      active sync   /dev/sdi
       7       8        0        7      active sync   /dev/sda
      16       0        0       16      removed


```

---

### Post by darkod on 2017-03-09
Looks good, no? Try mounting it, if it finds the filesystem it's OK. If it doesn't find the filesystem it won't mount anyway. You can use temporary mount location just to check mounting.
```
sudo mount /dev/md1 /mnt
```

If that works check what's inside /mnt to check for your data. And if all looks good, you can try adding the new disk to the array.

---

### Post by lars17 on 2017-03-10
managed to get the Raid online and mounted some how. but everything is gone. tried to repair the broken superblocks but nothing worked. It was just media on that array so no biggie. but its tobad it had to go before i could backup all of it. think i got around 80-90% of the data atleat

---

### Post by lars17 on 2017-03-10
> **darkod said:**
> Few pieces of advice...

1. Do not use whole disks as mdadm members. Create one single partition on the disk and leave the last 15-20MB unpartitioned (unused). Then use the partitions to create the array. The reason is that not all disks are always equal to the exact number of sectors. And if a new disk is few sectors smaller, you will not be able to add it to the array. Leaving 15MB unused at the end makes it possible to almost always create partitions of the same size and add them to the array without issues.



can you help me with this. I'm havent used Command for partitioning drives before

---

### Post by darkod on 2017-03-10
Post the output of one of the 500gb disks, for example:
```
sudo parted /dev/sdb unit MiB print
```

---

