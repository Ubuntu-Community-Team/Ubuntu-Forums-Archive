---
title: "Too few (or 0) LVM PEs"
date: 2010-09-04
forum: Server Platforms
---

### Post by hatdragon on 2010-09-04
I'm now entering into day 3 of the worst install experience I have ever had.

I'm trying to build a simple Ubuntu file server. I have nearly full 1.5 and 2 TB hard drives, and an empty 2TB hard drive. My plan was to install Ubuntu onto an encrypted LVM on the empty 2TB drive, copy data from the other drives and add them to the LVM one-by-one.

I'm using:
Athlon II X2
1 GB RAM
2 TB WD Caviar Green (WD20EARS 64M cache)
and am using but would prefer not to use:
Onyx 32GB OCZ SSD

All this is done with Ubuntu Server 10.04, updated ASAP with no additional packages.

Previous: skip unless you think it's relevant (it might or might not be)

My installations failed probably around 20 times; sometimes the kernel failed to install, sometimes the core packages failed to install, sometimes the installer was unable to partition the disks. I ran a random write-read badblocks test over the drive (no bad blocks), and three passes of memtest completed successfully. Every CD disk integrity check I ran showed a good disk. I tried installing from both CD-ROM and USB, and while they had very different problems, neither worked. I decided to give up on encryption and just use an LVM. I manually set up the partitioning scheme I wanted, including the LVM, under the Live Desktop CD so that I wouldn't rely on the Ubuntu Server default settings. I tried these in many combinations, usually zeroing out (sometimes randomizing) the first 1-10GB of the disk in between.

None of that worked at all; I installed to a thumb drive, intending to add the disk later. LVM failed; but since I didn't need it on an 8GB drive, I used manual partitions and it worked. Except my BIOS wouldn't read the MBR off USB, apparently. I ripped an SSD out of my other computer, and installed to that. Again, installing with an LVM failed. Installing without LVM was successful on the fourth try. As you can imagine, I've already pulled out most of my hair at this point.

Current issue: this is the important stuff.

I now have an SSD system disk that seems happy. I want to use all of my 2TB drive as an LVM. This is what I'm doing:

```

root@euler:/home/hugh# dd if=/dev/zero of=/dev/sdb bs=4K count=2M
2097152+0 records in
2097152+0 records out
8589934592 bytes (8.6 GB) copied, 70.1899 s, 122 MB/s
root@euler:/home/hugh# cfdisk /dev/sdb

root@euler:/home/hugh# fdisk -l

Disk /dev/sda: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004aaa7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3727    29931520   83  Linux
/dev/sda2            3727        3893     1332225    5  Extended
/dev/sda5            3727        3893     1332224   82  Linux swap / Solaris

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243201  1953512001   8e  Linux LVM
root@euler:/home/hugh# pvcreate /dev/sdb1
  Physical volume "/dev/sdb1" successfully created
root@euler:/home/hugh# vgcreate -s 32M vg0 /dev/sdb1
  Volume group "vg0" successfully created
root@euler:/home/hugh# vgdisplay vg0
  --- Volume group ---
  VG Name               vg0
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  1
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                0
  Open LV               0
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               96.00 MiB
  PE Size               32.00 MiB
  Total PE              3
  Alloc PE / Size       0 / 0   
  Free  PE / Size       3 / 96.00 MiB
  VG UUID               noeoMN-Jo0W-wLNK-TrkV-ImuK-Cub0-9RjC9r

```

Am I doing something wrong? Sometimes I have 35 PEs, sometimes i have none. I should have about 1.82TB / 32M!

When I was manually partitioning under the Live Desktop CD, this wasn't a problem, but I sometimes did run into problems when I tried to put a filesystem on top of a logical volume.

---

