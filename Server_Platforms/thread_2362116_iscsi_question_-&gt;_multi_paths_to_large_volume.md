---
title: "iscsi question -&gt; multi paths to large volume"
date: 2017-05-24
forum: Server Platforms
---

### Post by scojopa on 2017-05-24
I have a single large volume san -> w/ 4 paths to it. 

Connect to the iscsi target w/o issue
I see dmesg create for each iscsi path
 /dev/sdb
/dev/sdc
/dev/sdd
/dev/sde

I want to use all 4 paths to the volume, but want to presented back to ubuntu server as a single volume. 

how can I do this. 

```
Disk /dev/sdb: 1000 GiB, 1073741824000 bytes, 2097152000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xf3161ef3


Device     Boot Start        End    Sectors  Size Id Type
/dev/sdb1        2048 2097151999 2097149952 1000G 83 Linux




Disk /dev/sdc: 1000 GiB, 1073741824000 bytes, 2097152000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xf3161ef3


Device     Boot Start        End    Sectors  Size Id Type
/dev/sdc1        2048 2097151999 2097149952 1000G 83 Linux




Disk /dev/sdd: 1000 GiB, 1073741824000 bytes, 2097152000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xf3161ef3


Device     Boot Start        End    Sectors  Size Id Type
/dev/sdd1        2048 2097151999 2097149952 1000G 83 Linux




Disk /dev/sde: 1000 GiB, 1073741824000 bytes, 2097152000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xf3161ef3


Device     Boot Start        End    Sectors  Size Id Type
/dev/sde1        2048 2097151999 2097149952 1000G 83 Linux

```

---

### Post by darkod on 2017-05-24
Your partitions seem to be formatted already. If you want to use all 4 disks as single 4TB space you need to use LVM. But for that you use the partitions unformatted.

You can delete these existing partitions if there is no data on them, then create new ones but WITHOUT filesystem. If you do it in parted with mkpart it creates only the partition, no filesystem.

After that use the 4 partitions as devices for LVM.

---

### Post by scojopa on 2017-05-24
I was planning on using this storage as a ZFS pool for LXC's

There is no data that I need to keep on them. 

There is currently one partition but the iscsi connections (4 paths) make it look as if there are 4. That is why I am confused in how to rectify the four devices and present back to server as one large volume. Even though there are 4 paths via iscsi targets to the same data

---

### Post by scojopa on 2017-05-24
So when looking at fdisk output

This is my OS installed and partitions

```

Disk /dev/sda: 930.5 GiB, 999116767232 bytes, 1951399936 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x20f8bbdd


Device     Boot   Start        End    Sectors  Size Id Type
/dev/sda1  *       2048     999423     997376  487M 83 Linux
/dev/sda2       1001470 1951397887 1950396418  930G  5 Extended
/dev/sda5       1001472 1951397887 1950396416  930G 8e Linux LVM

```

These are the LVM representations?
```

Disk /dev/mapper/hyper--vg-root: 866.1 GiB, 929994637312 bytes, 1816395776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/mapper/hyper--vg-swap_1: 63.9 GiB, 68602036224 bytes, 133988352 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```

Here is where I am trying to consolidate the representation to my server but possible Linux already has?? Each of these Disks are pointing to the same LUN. I assume each are being represented individually since there are 4 iscsi target paths
```

Disk /dev/sdb: 1000 GiB, 1073741824000 bytes, 2097152000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xf3161ef3


Device     Boot Start        End    Sectors  Size Id Type
/dev/sdb1        2048 2097151999 2097149952 1000G 83 Linux




Disk /dev/sdc: 1000 GiB, 1073741824000 bytes, 2097152000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xf3161ef3


Device     Boot Start        End    Sectors  Size Id Type
/dev/sdc1        2048 2097151999 2097149952 1000G 83 Linux




Disk /dev/sdd: 1000 GiB, 1073741824000 bytes, 2097152000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xf3161ef3


Device     Boot Start        End    Sectors  Size Id Type
/dev/sdd1        2048 2097151999 2097149952 1000G 83 Linux




Disk /dev/sde: 1000 GiB, 1073741824000 bytes, 2097152000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xf3161ef3


Device     Boot Start        End    Sectors  Size Id Type
/dev/sde1        2048 2097151999 2097149952 1000G 83 Linux

```

Is this last section the LVM representation I would want to mount as a partition to the server to point my ZFS root pool to?
```

Disk /dev/mapper/36001405f9034c27ddd71d4dc0d9959de: 1000 GiB, 1073741824000 bytes, 2097152000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xf3161ef3


Device                                              Boot Start        End    Sectors  Size Id Type
/dev/mapper/36001405f9034c27ddd71d4dc0d9959de-part1       2048 2097151999 2097149952 1000G 83 Linux

```


tcp: [1] 192.168.5.211:3260,1 iqn.2000-01.com.synology:san.Target-1.cb0866b7df (non-flash)tcp: [2] 192.168.5.214:3260,1 iqn.2000-01.com.synology:san.Target-1.cb0866b7df (non-flash)
tcp: [3] 192.168.5.213:3260,1 iqn.2000-01.com.synology:san.Target-1.cb0866b7df (non-flash)
tcp: [4] 192.168.5.212:3260,1 iqn.2000-01.com.synology:san.Target-1.cb0866b7df (non-flash)

---

### Post by darkod on 2017-05-24
Hold on, you are mixing things up here... LVM is one thing, and ZFS completely different. If you want to use ZFS forget all I said, because for ZFS you don't even create partitions on the storage disks. ZFS does all it needs when creating the pool.

But there is another question I am confused about. Do you have 1 or 4 iscsi targets? If 4 disks are shown because of the multipath but actually it is only 1 target, you need to check how should it work so that it uses multipath but it shows single disk. Because as it is, ubuntu is treating this as 4 disks, sda-sdd.

And another thing connected to that: if there is only 1 target (1 iscsi disk), what's the use of using ZFS or LVM? With only 1 disk that's pointless. Multipath is just for using better bandwidth, not to give you 4x 1TB disks from one single target. You will still have only 1TB of course. So how do you plan to make zfs pool from single 1TB disk?

---

### Post by scojopa on 2017-05-24
This is all a fresh install. I have four nics connecting to my SAN but only 1 lun 

I have logged out of the targets from the ubuntu server
Removed the old volume, lun and iscsi targets on the SAN. 

So I have 1TB of storage on the SAN that I want to present to server via iscsi to use as a zfs pool for lxc

Now when I restart iscsiadm  I only see 
```

tcp: [1] 192.168.5.211:3260,1 iqn.2000-01.com.synology:san.Target-1.cb0866b7df (non-flash)

```

And fdisk is showing 
```

Disk /dev/sdb: 1.8 TiB, 1980663595008 bytes, 3868483584 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 262144 bytes

```

So I think I am in better shape now. Nothing is partitioned or formatted.

So -> starting from scratch. 

Do i have to do anything else now w/ /dev/sdb -> before I setup ZFS or can I just start setting up ZFS and make sure I point it to /dev/sdb when I want to format and point to the iscsi storage?

Thanks for your help

---

### Post by darkod on 2017-05-24
All that is good, but what do you plan to do with zfs with only one volume? zfs is like raid. Not much point using it for only one volume...

Otherwise no, you don't need to do anything else if you want to set up zfs. By using sdb for your pool it will automatically be set up with gpt table for use with zfs.

---

### Post by scojopa on 2017-05-24
I am over my head. I am really just trying to setup a new lab using lxc

Since I have a clean slate what would you recommend 

5 500GB SSD's in my synology SAN
4NICS connected from SAN to switch (which is why I was getting 4 session logged into the SAN from server via iscsiadm)
Ubuntu server has 800GB local storage (RAID5) and two nics connected to switch

I dont need ZFS just figured I would start to learn it

---

### Post by darkod on 2017-05-24
Learning is always excellent, but trying zfs with one volume is really pointless...

The 800GB local storage are too much to be left unused. And you have 1TB iscsi volume to add to it, but expect the iscsi to be slower regardless of the SSDs because it needs to go over network. Local storage will usually be faster.

If the 800GB are enough to start off your lab, I would actually configure it only with the local storage for a start. Are you realy gonna use almost 2TB for a lab?

The question is if you want to be able to add the 1TB in the future without losing the data, you need to set up new ubuntu install using LVM on the 800GB. So later when the time comes you can add the 1TB to it and it will be one continuous space...

But be careful when installing with lvm. If you are using the guided partitioning method it creates very small separate /boot so in the future it is easy to fill it up and get into trouble. I would use manual partitioning and create 2GB partition for /boot. The rest for the lvm. That way you make sure it is difficult to fill up because 2GB /boot goes a long way...

---

### Post by scojopa on 2017-05-24
ok. Will rebuild the server and create 2GB /boot in case I need it later

If I am using UEFI should I make the /boot a 2GB uefi partition?

I will hold off using the external iscsi storage for now. 

Back to iscsi: One thing I have noticed is that if I leave the iscsi session logged in the reboot hangs unless I physically power cycle the server. I have been manually logging out of iscis prior to reboot to work around this. Any suggestions. 

And thanks again for taking the time to answer my questions

---

### Post by darkod on 2017-05-24
The /boot partition is part of ubuntu linux. Don't confuse it with EFI system partition or bios_grub partition. They are al different and necessary. Any additional partitions you might need (like the EFI system partition for UEFI boot and small 1MB partition for bios_grub) you have to create manually also, and use the correct flags.

I don't use UEFI boot so I don't know exactly what you need for the EFI partition and its size, maybe the boot flag? If you use gpt table on the disk then grub2 needs small 1MB partition (no filesystem) with bios_grub flag. That is because grub2 puts one part of itself on the MBR of the disk but the rest on that small partition (grub2 doesn't fit on MBR).

For the iscsi issue I also don't know right now becaise I am not using it frequently. You will have to investigate and google around for any tips how to best set it up and hopefully that boog hang will go away.

---

