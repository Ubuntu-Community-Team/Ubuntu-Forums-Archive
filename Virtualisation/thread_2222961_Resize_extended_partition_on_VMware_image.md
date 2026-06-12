---
title: "Resize extended partition on VMware image"
date: 2014-05-08
forum: Virtualisation
---

### Post by 1clue on 2014-05-08
Hi,
I have an Ubuntu Server 12.04 **VM on an ESXi host.**

[LIST=1]
[*]I started with an 8G drive for some reason.  I'm out of space.
[*]I resized to 32G (sparse) in the ESXi control panel.
[*]Internally, the VM still looks the same size.
[*]The server is a default install, meaning it has the old partition table, a /boot on sda1 and an LVM as sda5.
[*]The extended partition is too small now that I've resized the drive.
[/LIST]


```

fdisk -l /dev/sda
Disk /dev/sda: 34.4 GB, 34359738368 bytes
255 heads, 63 sectors/track, 4177 cylinders, total 67108864 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b169a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux        # This is /boot
/dev/sda2          501758    16775167     8136705    5  Extended  # This is too small
/dev/sda5          501760    16775167     8136704   8e  Linux LVM # This is where / is.

```

There is no sign internally that the drive is bigger.  I've shut down the VM, turned it off, turned it back on again and restarted the VM.  No difference.

**What I NEED** is for the LVM partition to be bigger.  But the extended partition (sda2) is too small to grow sda5, and of course sda5 can't grow.

**What I would LIKE **to have is a GPT partition table that looks something like this, barring sizes of partitions:
```

GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 1465149168 sectors, 698.6 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 736B3181-5AB6-416B-B5C8-96D2C7B7B267
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1465149134
Partitions will be aligned on 2048-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048            6143   2.0 MiB     EF02  bios
   2            6144         1054719   512.0 MiB   EF00  /boot
   3         1054720        22026239   10.0 GiB    0700  /
   4        22026240      1465149134   688.1 GiB   8E00  Linux LVM

```

I'm not asking for partitioning help, rather I'm after either a way to resize the existing extended partition and the lvm2 partition inside, or to copy the data to another drive which will be already partitioned.

Having thought about it awhile I think it might be best to create a new drive and copy data over.

This is a running system and we need it to stay running as much as possible. I know I can use DD to transfer at the filesystem level, but I want to change sizes of the filesystems.  (disk destroyer!)

I could probably create a new disk with my preferred partition layout, recursive copy the /boot partition and use LVM2 to copy the filesystems over, but I'm not really sure how to be sure it's right.  This is a business system, don't really have the option to mess it up.

Thanks.

---

### Post by TheFu on 2014-05-09
ESXi altered the size of the virtual HDD only.  Inside the VM, you need a partition tool to resize the partitions. That cannot be accomplished on a running system - i.e. with the partition mounted.  The easiest solution is to boot off a gparted ISO, run gparted against the VMDK and resize the partitions.

Then you can use LVM inside the booted VM and resize whatever.

Sparse partitions are slower - much slower. That's fine if on SSDs, but really sucks on spinning disks.

Oh - and if the machine is MBR partitioned, you cannot trivially change to GPT. Sorry. To the OS, that is a brand new HDD. Create a new vHDD, apply the GPT partitioning, and ddrescue the data over using a gparted ISO boot with both vHDDs available inside the VM.

Lastly - fdisk does NOT work with GPT partition tables.  It is best, IMHO, to STOP USING fdisk, sfdisk, cfdisk, until they are updated across the board, on every release to support GPT and 4K sector HDDs.  In the meantime, just use parted, gparted, and gdisk. Much safer, plus these tools handle the 4K sector alignment automatically.

---

### Post by 1clue on 2014-05-09
OK thanks.

I didn't realize that sparse was much slower, I knew there was some difference but not that it was large.

I knew that switching to GPT would require a different disk image, and thinking on the internal configuration changes I think that's probably off the table here.  If I had installed the image there would never have been an MBR partition table, and certainly no extended partitions especially when there are only 2 that count.

Fdisk does support gpt now, at least on some distros.  I generally use gdisk because back when I learned this it was mid 90s or so, and fdisk setup is in my brain permanently.  But when it's an MBR table I revert to fdisk for some reason.

---

