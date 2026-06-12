---
title: "Samba/Windows 3TB Share Issue"
date: 2011-08-02
forum: Server Platforms
---

### Post by owarya on 2011-08-02
Hi There, 
Bit new to the forums so I didn't really know where to being, I've had a look at a couple dozen pages of threads to find a similar problem/solution. Nothing.

I have been running samba shares for a couple of months on ubuntu server 11.04, never had an issue other than the various permission problems I stumble upon.

I have just installed a brand new Hitachi 3TB Sata drive in the machine. I have successfully partitioned (just the one partition), formatted (ext4) and mounted (dir: /media/threetb) the drive. All is working well including the samba share I have set up to /media/threetb/Movies. Permissions are all correct.

Problem is this, when I map the network drive from my windows 7 PC, it shows the empty drive as having 1.96TB free space out of 1.96TB total space. On my OS X Lion it shows a 2.16TB total and free space. Large amounts sure, but not the near 3TB figure i was hoping for.

I have searched around for hours trying to find out what the deal is, originally thinking it could've been the fact that I was using ext3, but even after reformatting it into ext4 the problem still exists.

Any suggestions to help solve my dilemma? Let me know if you need more information!

---

### Post by ian dobson on 2011-08-02
Hi,

I'm not sure if this helps much, but I have a large RAID5 array (6Tb usable) and that shows up correctly in windows7, through a samba share. Also running 11.04.

What happens when you write afew 100Gb to the fs, does windows/mac still show the same amount of free space?

What does df on the server show? 
What did you use to partition the drive? 
What does fdisk /Path/toDrive -l show?

Regards
Ian Dobson

---

### Post by Gyokuro on 2011-08-02
Hi,

it seems that you should use the GPT partition scheme and later format your drive with ext4 and afterwards  you should be able to access the complete HD space.

HTH

---

### Post by owarya on 2011-08-02
> **ian dobson said:**
> Hi,

I'm not sure if this helps much, but I have a large RAID5 array (6Tb usable) and that shows up correctly in windows7, through a samba share. Also running 11.04.

What happens when you write afew 100Gb to the fs, does windows/mac still show the same amount of free space?

What does df on the server show? 
What did you use to partition the drive? 
What does fdisk /Path/toDrive -l show?

Regards
Ian Dobson

```
 df
Filesystem           1K-blocks Used Available Use% Mounted on
/dev/mapper/R2D2-root
                     147653088   3303548 136849152   3% /
none                   1020220       200   1020020   1% /dev
none                   1028248         0   1028248   0% /dev/shm
none                   1028248       608   1027640   1% /var/run
none                   1028248         0   1028248   0% /var/lock
/dev/sda1               233191     66696    154054  31% /boot
/dev/sdb1            2113784984 1128576880 979839404  54% /media/threetb
```

To partition the drive I used sudo fdisk /dev/sdb > selected "n" for new partition > selected the very first cylinder and the very last cylinder, both by defaults > selected "w" for write. I then formatted as ext4 using sudo mkfs -t ext4 /dev/sdb1.

```

Disk /dev/sdb1: 2199.0 GB, 2199020350464 bytes
255 heads, 63 sectors/track, 267348 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb1 doesn't contain a valid partition table
```

I followed this tutorial on installing and formatting the hard drive, [https://help.ubuntu.com/community/InstallingANewHardDrive]("https://help.ubuntu.com/community/InstallingANewHardDrive") although I am now starting to believe that this obviously only caters for much smaller hard drives.

I'll google around for some instructions on GPT partitioning and try that, thanks!

---

### Post by srs5694 on 2011-08-02
Using fdisk creates a Master Boot Record (MBR) partition table, which maxes out at 2 TiB (assuming 512-byte sectors). You can use parted, GParted, gdisk, or various other GPT-aware utilities to create a fresh GUID Partition Table (GPT), which uses 64-bit sector pointers and so maxes out at 8 ZiB.

If you've already got data on the disk, you can use gdisk to convert it from MBR to GPT form and then use GParted to expand your ~2TiB partition out to fill the entire disk. Most other tools will only convert to GPT destructively; you'll lose the data already on the disk.

BTW, the last output you posted seems to be the result of "sudo fdisk -l /dev/sdb1" or something similar. This attempts to interpret a partition table in a partition, which is almost certainly not useful information. When using any partitioning tool, you should generally operate on the entire disk (/dev/sda, /dev/sdb, etc.), not a partition (/dev/sda2, /dev/sdb1, etc.). The only exception would be if you're using a partition to hold an entire disk's contents, as in with virtualization software or as some sort of backup tool. In such a case you might have a partition table within a partition, but such uses are pretty rare.

---

### Post by owarya on 2011-08-02
> **srs5694 said:**
> Using fdisk creates a Master Boot Record (MBR) partition table, which maxes out at 2 TiB (assuming 512-byte sectors). You can use parted, GParted, gdisk, or various other GPT-aware utilities to create a fresh GUID Partition Table (GPT), which uses 64-bit sector pointers and so maxes out at 8 ZiB.

If you've already got data on the disk, you can use gdisk to convert it from MBR to GPT form and then use GParted to expand your ~2TiB partition out to fill the entire disk. Most other tools will only convert to GPT destructively; you'll lose the data already on the disk.

BTW, the last output you posted seems to be the result of "sudo fdisk -l /dev/sdb1" or something similar. This attempts to interpret a partition table in a partition, which is almost certainly not useful information. When using any partitioning tool, you should generally operate on the entire disk (/dev/sda, /dev/sdb, etc.), not a partition (/dev/sda2, /dev/sdb1, etc.). The only exception would be if you're using a partition to hold an entire disk's contents, as in with virtualization software or as some sort of backup tool. In such a case you might have a partition table within a partition, but such uses are pretty rare.

Okay I've partitioned it using gdisk and windows is now recognising 2.68TB total space. I know the whole byte - bit difference means the value loses a lot.. but is 300gb correct?

It's solely a data drive so I've set the root space (or whatever it's called) to .1%. 
```
sudo tune2fs -m 0.1 /dev/sdb1
```
So that can't be much of an issue.

gdisk "print" output
```
Command (? for help): print
Disk /dev/sdb: 5860533168 sectors, 2.7 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 0802D080-CA7E-4CEB-A6B2-7DC527800229
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 5860533134
Partitions will be aligned on 2048-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048      5860533134   2.7 TiB     0700  Linux/Windows data
```
Is this a problem or is this what I should expect?

---

### Post by srs5694 on 2011-08-03
1 byte = 8 bits, at least in most contexts. This isn't the issue.

The confusion over sizing relates to a different issue entirely -- [SI prefixes,](http://en.wikipedia.org/wiki/Si_prefix) which are technically power-of-10 values, vs. [IEEE-1541 units,](http://en.wikipedia.org/wiki/IEEE_1541-2002) which are power-of-2 values. Unfortunately, in computing's early days, SI prefixes were inappropriately applied to power-of-2 units that are now better described by IEEE-1541 units. The confusion/error on this score is small with small units (1,000 vs. 1,024 for kilo vs. kibi, for instance), but it gets bigger with bigger units. At the scale of a big modern hard disk, it's huge; 1 TiB = ~1.1 TB. Thus, a 3 TB disk is, in IEEE-1541 units, about 2.73 TiB. That's the bulk of the effect you're seeing. (Note that some utilities, particularly outside of the open source world, still inappropriately apply SI prefixes to IEEE-1541 units. Disk manufacturers have used SI prefixes appropriately for years, but disk utilities are split on whether they use SI or IEEE-1541 units.)

There's also probably some effect from filesystem overhead -- the journal, inodes, etc., all consume disk space. This probably accounts for the difference between 2.68 TiB and 2.73 TiB.

---

### Post by owarya on 2011-08-04
> **srs5694 said:**
> 1 byte = 8 bits, at least in most contexts. This isn't the issue.

The confusion over sizing relates to a different issue entirely -- [SI prefixes,](http://en.wikipedia.org/wiki/Si_prefix) which are technically power-of-10 values, vs. [IEEE-1541 units,](http://en.wikipedia.org/wiki/IEEE_1541-2002) which are power-of-2 values. Unfortunately, in computing's early days, SI prefixes were inappropriately applied to power-of-2 units that are now better described by IEEE-1541 units. The confusion/error on this score is small with small units (1,000 vs. 1,024 for kilo vs. kibi, for instance), but it gets bigger with bigger units. At the scale of a big modern hard disk, it's huge; 1 TiB = ~1.1 TB. Thus, a 3 TB disk is, in IEEE-1541 units, about 2.73 TiB. That's the bulk of the effect you're seeing. (Note that some utilities, particularly outside of the open source world, still inappropriately apply SI prefixes to IEEE-1541 units. Disk manufacturers have used SI prefixes appropriately for years, but disk utilities are split on whether they use SI or IEEE-1541 units.)

There's also probably some effect from filesystem overhead -- the journal, inodes, etc., all consume disk space. This probably accounts for the difference between 2.68 TiB and 2.73 TiB.

Awesome thanks, I did a little bit of research and found this too but I didn't know exactly what value to be looking for. 

Thanks again!

---

