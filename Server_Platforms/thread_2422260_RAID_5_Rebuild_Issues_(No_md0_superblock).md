---
title: "RAID 5 Rebuild Issues (No md0 superblock)"
date: 2019-07-04
forum: Server Platforms
---

### Post by greenrubberducky on 2019-07-04
Hi all...first time starting a post here. Over the last DECADE, this forum has helped me with large and small problems, simply via searching and reading. But this one is a bit worse and I can't find the right answers here (at least not yet).

I'm running a software RAID 5 array for home storage. I build it in 2013-ish. Runs 16.04, kept up-to-date. I have 4 1TB Western Digital drives in there, all of them part of the array. I also run a Plex server from it. Sweet and stable setup for many years. The majority of my data is backed up to a Google cloud storage location, but the wealth of movies & TV (I burn all our disks to it, as well has use it for storing HD tv recordings from an antenna box) are not backed up...just too much data. 

At one point, a drive failed and I was successfully able to recover it fairly easily. However, the other 3 original drives are another story. The server was suggesting a reboot post-software update. It never came back up. Opened the box and found one of the drives was clicking, a tell-tale end of life sign. After all of my diagnosing was done, one drive was dead and the other two originals (WDC10EALS) were showing S.M.A.R.T. errors. The SMART errors were preventing normal boot and array assembly when after I replaced the bad drive. 

Here's where things get desperate. I created a Parted Magic bootable USB drive. Using the clone tools, I cloned the two SMART errored drives. With (maybe) the array and the data on the drives more or less safe (should reassemble from 3 drives), I launced the server again. When the /dev/md0 startup routine failed, it dropped me into maintenance mode. 

I used fdisk to create a new partition on the fresh blank drive and set it to "fd", linux_raid. One of the cloned drives needed the partition filesystem switched from plain linux to linux_raid as well. Not sure if that will end up being a critical misstep or not...

I tried to reassemble the existing array at this point:
```
mdadm --assemble --force /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
```

It didn't reassemble, so after further research I decided to try re-creating the array.
```
mdadm --stop /dev/md0
mdadm --create /dev/md0 --verbose --level=5 --raid-devices=4 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
```

From this, the system reported the array built, but I received a strange error (sorry, not verbatim) "VSR: filesystem ext2 not set up" or something like that. When I ran cat /proc/mdstat, I get this:
```
Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10]
md0 : active raid5 sdc1[1] sdb1[0] sde1[3] sdd1[2]
      2929889280 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]
      bitmap: 0/8 pages [0KB], 65536KB chunk

unused devices: <none>

```
It never re-assembled itself. 

At this point, I tried to mount it to a folder location:
```
root@big-box:~# mount /dev/md0 /mnt/big-box
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

```

And there's this:
```
root@big-box:~# mdadm -E /dev/md0
mdadm: No md superblock detected on /dev/md0.

```

Some other info to fully inform:
lsblk:
```
root@big-box:~# lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
NAME    FSTYPE              SIZE MOUNTPOINT LABEL
sda                        74.5G
&#9500;&#9472;sda1  ext4               72.6G /
&#9500;&#9472;sda2                        1K
&#9492;&#9472;sda5  swap                  2G [SWAP]
sdb                       931.5G
&#9492;&#9472;sdb1  linux_raid_member 931.5G            big-box:0
  &#9492;&#9472;md0                     2.7T
sdc                       931.5G
&#9492;&#9472;sdc1  linux_raid_member 931.5G            big-box:0
  &#9492;&#9472;md0                     2.7T
sdd                       931.5G
&#9492;&#9472;sdd1  linux_raid_member 931.5G            big-box:0
  &#9492;&#9472;md0                     2.7T
sde                       931.5G
&#9492;&#9472;sde1  linux_raid_member 931.5G            big-box:0
  &#9492;&#9472;md0                     2.7T

```

fdisk -l
```
root@big-box:~# fdisk -l
Disk /dev/sda: 74.5 GiB, 80026361856 bytes, 156301488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000b7660

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sda1  *         2048 152178687 152176640 72.6G 83 Linux
/dev/sda2       152180734 156301311   4120578    2G  5 Extended
/dev/sda5       152180736 156301311   4120576    2G 82 Linux swap / Solaris


Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xe3fa9f11

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdb1        2048 1953525167 1953523120 931.5G fd Linux raid autodetect


Disk /dev/sdd: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00008c12

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdd1        2048 1953525167 1953523120 931.5G fd Linux raid autodetect


Disk /dev/sde: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x00059a37

Device     Boot Start        End    Sectors   Size Id Type
/dev/sde1        2048 1953523711 1953521664 931.5G fd Linux raid autodetect


Disk /dev/sdc: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x000aa131

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdc1        2048 1953523711 1953521664 931.5G fd Linux raid autodetect


Disk /dev/md0: 2.7 TiB, 3000206622720 bytes, 5859778560 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 524288 bytes / 1572864 bytes

```

mdadm -E
```
root@big-box:~# mdadm -E /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 45a0d36f:99beabeb:4b01986c:7e18288e
           Name : big-box:0  (local to host big-box)
  Creation Time : Wed Jul  3 17:11:30 2019
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 1953260976 (931.39 GiB 1000.07 GB)
     Array Size : 2929889280 (2794.16 GiB 3000.21 GB)
  Used Dev Size : 1953259520 (931.39 GiB 1000.07 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=1456 sectors
          State : clean
    Device UUID : c0d9fd3d:e6fcd9a8:d3896888:91747c9a

Internal Bitmap : 8 sectors from superblock
    Update Time : Wed Jul  3 17:11:30 2019
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 142a7443 - correct
         Events : 0

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)

root@big-box:~# mdadm -D /dev/sdb1
mdadm: /dev/sdb1 does not appear to be an md device

root@big-box:~# mdadm -E /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 45a0d36f:99beabeb:4b01986c:7e18288e
           Name : big-box:0  (local to host big-box)
  Creation Time : Wed Jul  3 17:11:30 2019
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 1953259520 (931.39 GiB 1000.07 GB)
     Array Size : 2929889280 (2794.16 GiB 3000.21 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=0 sectors
          State : clean
    Device UUID : ba8afe6b:f8a099ed:3f116853:99a8f507

Internal Bitmap : 8 sectors from superblock
    Update Time : Wed Jul  3 17:11:30 2019
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : bf637f13 - correct
         Events : 0

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)

root@big-box:~# mdadm -D /dev/sdc1
mdadm: /dev/sdc1 does not appear to be an md device

root@big-box:~# mdadm -E /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 45a0d36f:99beabeb:4b01986c:7e18288e
           Name : big-box:0  (local to host big-box)
  Creation Time : Wed Jul  3 17:11:30 2019
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 1953260976 (931.39 GiB 1000.07 GB)
     Array Size : 2929889280 (2794.16 GiB 3000.21 GB)
  Used Dev Size : 1953259520 (931.39 GiB 1000.07 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=1456 sectors
          State : clean
    Device UUID : 676ce38e:05b87ef1:8aa54bf8:45914a34

Internal Bitmap : 8 sectors from superblock
    Update Time : Wed Jul  3 17:11:30 2019
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : b765fa76 - correct
         Events : 0

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)

root@big-box:~# mdadm -D /dev/sdd1
mdadm: /dev/sdd1 does not appear to be an md device

root@big-box:~# mdadm -E /dev/sde1
/dev/sde1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 45a0d36f:99beabeb:4b01986c:7e18288e
           Name : big-box:0  (local to host big-box)
  Creation Time : Wed Jul  3 17:11:30 2019
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 1953259520 (931.39 GiB 1000.07 GB)
     Array Size : 2929889280 (2794.16 GiB 3000.21 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=0 sectors
          State : clean
    Device UUID : 97ddc8a0:6bb21ca3:01a7b909:1ca217f3

Internal Bitmap : 8 sectors from superblock
    Update Time : Wed Jul  3 17:11:30 2019
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 4b2472ab - correct
         Events : 0

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 3
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)

root@big-box:~# mdadm -D /dev/sde1
mdadm: /dev/sde1 does not appear to be an md device

root@big-box:~# mdadm -E /dev/md0
mdadm: No md superblock detected on /dev/md0.

root@big-box:~# mdadm -D /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Wed Jul  3 17:11:30 2019
     Raid Level : raid5
     Array Size : 2929889280 (2794.16 GiB 3000.21 GB)
  Used Dev Size : 976629760 (931.39 GiB 1000.07 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent

  Intent Bitmap : Internal

    Update Time : Wed Jul  3 17:11:30 2019
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : big-box:0  (local to host big-box)
           UUID : 45a0d36f:99beabeb:4b01986c:7e18288e
         Events : 0

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1

```

One last thing...I did try to move stored superblocks from backup (there were maybe 12-14 of them), but nothing worked there. Can't recall the command...e2fsck -b 32768 perhaps?

SO...I've settled into the idea that the array might be hosed, but I don't think I've done anything to completely delete the data stripes on the drives. Looking for some ideas on how to try and salvage this. I'll post additional output if required. Thanks!

---

### Post by darkod on 2019-07-04
I don't know if you can save this yet, because you made a very big error. The good part might be that you never managed to mount the new array and write to it, so that leaves little hope to get the original data.

Your big mistake was the --create. NEVER, EVER, EVER do a --create without adding --assume-clean if you want to keep your existing data!!! With --create you make a NEW EMPTY array. The --assume-clean parameter tells mdadm you want to make a NEW array but keepign existing data.

Do you know or remember which chunk size you had in the original array? You will need that if you want to try recreate your array.

If you never used specific chunk size in the original command, it is probably safe to try default chunk size first. Also the disk order is important, with all that was happening (one disk replaced, second failed, two cloned) you can easily lose count of the order. It might not be B C D E...

But it doesn't hurt to try.

First stop the current md0 array because it's worthless if you want to try accessing your old data. Then try recreating it again:
```
sudo mdadm --stop /dev/md0
sudo mdadm --create /dev/md0 --assume-clean --verbose --level=raid5 --raid-devices=4 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
```

When troubleshooting always add --verbose because it gives you more messages what might be wrong.

After you recreate the array try mounting it read only. If it doesn't mount it means it doesn't detect filesystem on md0. There can be different reasons. If the chunk size is not identical to the previous it will not detect the filesystem correctly. Also if the data is completely gone again it will not detect any filesystem...

```
sudo mount -o ro /dev/md0 /mnt
```

If by any chance mounting works, look inside:
```
cd /mnt
ls
```

---

### Post by greenrubberducky on 2019-07-04
Thanks for the input, Darko. I'm not sure what the original chunk size was as I was even more of a novice back when I created the array (if that's really possible). I am fairly certain that I didn't adjust it from default, so I'm guessing that it will be 512KB. I do know that I used --assume-clean on most of my attempts, so I'm hoping I haven't hosed it. We'll see. I'll try some different disk combinations and see what happens.

---

### Post by greenrubberducky on 2019-07-04
Some of the output as I'm going...

```
root@big-box:~# mdadm --stop /dev/md0
mdadm: stopped /dev/md0
root@big-box:~# mdadm --create /dev/md0 --assume-clean --verbose --level=raid5 --raid-devices=4 /dev/sdc1 /dev/sdb1 /dev/sdd1 /dev/sde1
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 512K
mdadm: /dev/sdc1 appears to be part of a raid array:
       level=raid5 devices=4 ctime=Wed Jul  3 17:11:30 2019
mdadm: /dev/sdb1 appears to contain an ext2fs file system
       size=976760832K  mtime=Wed Dec 31 19:00:00 1969
mdadm: /dev/sdb1 appears to be part of a raid array:
       level=raid5 devices=4 ctime=Wed Jul  3 17:11:30 2019
mdadm: /dev/sdd1 appears to contain an ext2fs file system
       size=2930282304K  mtime=Tue May 28 20:11:14 2019
mdadm: /dev/sdd1 appears to be part of a raid array:
       level=raid5 devices=4 ctime=Wed Jul  3 17:11:30 2019
mdadm: /dev/sde1 appears to be part of a raid array:
       level=raid5 devices=4 ctime=Wed Jul  3 17:11:30 2019
mdadm: size set to 976629760K
mdadm: automatically enabling write-intent bitmap on large array
Continue creating array?

```

Also got that VFS messge again..."EXT4-fs (md0): VFS: Can't find ext4 filesystem"

---

### Post by greenrubberducky on 2019-07-04
Right, so I ran through all 24 permutations of drive arrangements, no dice. All create runs ended with:
```
root@big-box:~# mdadm -E /dev/md0
mdadm: No md superblock detected on /dev/md0.

```

So hosed, right? I must have run --create without --assume-clean in there somewhere.

Any suggestions for a good walkthrough on zapping and completely re-initializing the array? Should I go back into Parted Magic and zap the drives?

I'll hold off for a couple days, see if anyone has some last minute heroics for me to try.

---

### Post by darkod on 2019-07-04
That no superblock message is not an error. You run mdadm -D on an array. You ran mdadm -E on members of the array.

That is why you get that message, it's normal.

Best way to test is trying to mount the array read only. Correctly recreated array that contains your data and filesystem, will mount. If it doesn't detect filesystem, it won't mount.

But yes, in your first post the command you posted said only --create, without --assume-clean. That is why I said it was an error, assuming you actually ran it like that and it wasn't a typo.

---

### Post by greenrubberducky on 2019-07-04
So on the read-only mount, I'm correct when I think that this is a bad create?

```
root@big-box:~# mount -o ro /dev/md0 /mnt/big-box
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

```

---

### Post by darkod on 2019-07-04
Yes, it's bad. It can't find the filesystem to mount (wrong fs type).

---

### Post by greenrubberducky on 2019-07-04
Right, so none of the permutaions of drive order would mount read-only. Same error every time. 

Again, seems hosed, but I'll let it rest for a while and see who else replies.

---

### Post by greenrubberducky on 2019-07-22
To close this out...all the copying and cloning and the multiple drive failures did indeed hose my array. I formatted all 4 drives and deleted partitions, started over. New array built easily and works fine. The vast majority of content (and all of my irreplaceable content) was safe in the cloud (2TB from Google is only $10/month, SOOOOOO worth it!) and what I lost I can always get again. Just have to re-burn some DVDs (of course).

Thanks for the help!

---

