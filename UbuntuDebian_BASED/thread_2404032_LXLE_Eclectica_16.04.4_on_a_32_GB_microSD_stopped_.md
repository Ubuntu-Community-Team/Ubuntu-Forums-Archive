---
title: "LXLE Eclectica 16.04.4 on a 32 GB microSD stopped booting - please help"
date: 2018-10-19
forum: Ubuntu/Debian BASED
---

### Post by batbwc on 2018-10-19
I sure am hopeful for some help. I did a full install of LXLE Eclectica 16.04.4 on a 32 GB microSD card that's in a USB 3.0 SD-card-to-USB-converter. I've been booting into this Linux distro, one or more times every day for over a year. Within the last few weeks for the first time, I've had some issues arise that required fsck to fix. I also recently used gparted to add a Windows ntfs partition to the microSD card. Somehow accidently, after shrinking the original main partition, I also moved something that when after the changes were written to the card, I had a 71 MB unallocated area at the beginning. I "held my breath" as I rebooted, but everything worked fine, until a few days later booting went to a black screen with a seemingly enlarged or maybe bold underline cursor & went no further. Had to use power button to get out of this situation. I began searching for ways to fix things & never really found anything close enough to my particular situation to enable me to make repairs. All the files appear to be intact, but something just prevents the SD card from booting.

Here's what things look like in gparted (using a live Chalet OS).
 - - (main screen)

[ATTACH=CONFIG]281380[/ATTACH]

- - (sdc1 info screen)

[ATTACH=CONFIG]281381[/ATTACH]


I have gotten an error from gparted occasionally, stating that gparted shows 2048 but Linux has 512.
Here's some views using fsck.

chaletos-user@chaletos-user:~$ sudo fsck -y /dev/sdc1
fsck from util-linux 2.27.1
e2fsck 1.42.13 (17-May-2015)
/dev/sdc1: clean, 304068/1368064 files, 3255041/5469696 blocks


chaletos-user@chaletos-user:~$ sudo fsck -y /dev/sdc
fsck from util-linux 2.27.1
e2fsck 1.42.13 (17-May-2015)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdc

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

Trying the recommendations in the fsck for sdc didn't seem to do anything.

So I came across a post in Ubuntu forum by someone who had the "bad magic #" situation, who was able to fix things with testdisk. I feel it could also get me back up & running, but I seek help to make the right choices. I backed up the full SD card using EaseUS todo backup (in Windows).
Here's what testdisk shows.

Select a media (use Arrow keys, then press Enter):
>Disk /dev/sda - 1000 GB / 931 GiB - HGST HTS541010A9E680
 Disk /dev/sdb - 120 GB / 111 GiB - Mass Storage Device
 Disk /dev/sdc - 31 GB / 29 GiB - Generic- SD/MMC
 Disk /dev/mmcblk0 - 31 GB / 28 GiB

 Intel partition table type has been detected.

Disk /dev/sdc - 31 GB / 29 GiB - CHS 30436 64 32
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * Linux                   71   0  1 21436  63 32   43757568

Warning: Bad ending sector (CHS and LBA don't match)
 2 P HPFS - NTFS          21437   0  1 30435  63 32   18429952

Warning: Bad starting sector (CHS and LBA don't match)


*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted

And after a quick search for partition

Disk /dev/sdc - 31 GB / 29 GiB - CHS 30436 64 32
     Partition               Start        End    Size in sectors
>* Linux                    0   1 32 21366   1 31   43757568
 P HPFS - NTFS          21437   0  1 30435  63 32   18429952

So I selected the * Linux (Primary bootable) partition & hit "A" to add it which resulted in

  No partition         21366   1 32 21436  63 32     145345


>[Cylinder]  [  Head  ]  [ Sector ]  [Cylinder]  [  Head  ]  [ Sector ]
 [  Type  ]  [  Done  ]

And this is where I can't determine what to do next. I have no familiarity with "CHS and LBA don't match" so if you know this may be what needs fixed to allow booting, please let me know how to fix it

 Any assistance will be greatly appreciated. If you need more info, let me know what you need & how to get it. TY.

I'll include one other thing. I right-clicked on the Linux partition in gParted & chose "check" - here's the details showing no errors...

GParted 0.25.0 --enable-libparted-dmraid --enable-online-resize

Libparted 3.2
Check and repair file system (ext2) on /dev/sdc1  00:00:43    ( SUCCESS )
         
calibrate /dev/sdc1  00:00:00    ( SUCCESS )
         
path: /dev/sdc1 (partition)
start: 145408
end: 43902975
size: 43757568 (20.87 GiB)
check file system on /dev/sdc1 for errors and (if possible) fix them  00:00:43    ( SUCCESS )
         
e2fsck -f -y -v -C 0 /dev/sdc1  00:00:43    ( SUCCESS )
         
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

304068 inodes used (22.23%, out of 1368064)
18194 non-contiguous files (6.0%)
341 non-contiguous directories (0.1%)
# of inodes with ind/dind/tind blocks: 15830/280/0
3255041 blocks used (59.51%, out of 5469696)
0 bad blocks
1 large file

238364 regular files
35989 directories
1 character device file
0 block device files
0 fifos
35 links
29140 symbolic links (27509 fast symbolic links)
565 sockets
------------
304094 files
e2fsck 1.42.13 (17-May-2015)
grow file system to fill the partition  00:00:00    ( SUCCESS )
         
resize2fs -p /dev/sdc1  00:00:00    ( SUCCESS )
         
resize2fs 1.42.13 (17-May-2015)
The filesystem is already 5469696 (4k) blocks long. Nothing to do!

========================================

---

### Post by wildmanne39 on 2018-10-19
*Thread moved to **Ubuntu/Debian BASED for a more appropriate fit**.*

---

