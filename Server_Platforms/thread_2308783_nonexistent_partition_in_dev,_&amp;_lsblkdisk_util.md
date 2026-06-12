---
title: "nonexistent partition in /dev, &amp; lsblk/disk util misbehaving with btrfs raid in luks"
date: 2016-01-05
forum: Server Platforms
---

### Post by DiagonalArg on 2016-01-05
**Edit: This is happening with random-filled disks, so it has nothing to do with luks/btrfs.  See additional "Edit", below.**

I have two identically prepared luks disks with no partition table and no luks header (it's a detached header).  I used that pair for a raid1 btrfs filesystem.  That looks fine when I check it with `btrfs filesystem show`, and when I check with parted it doesn't see anything on the disk:

```
GNU Parted 3.2
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print
Error: /dev/sda: unrecognised disk label
Model: ATA WDC WD2002FAEX-0 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags:
```

but when I check with `lsblk`, I see one disk with partitions and the other without:

```
NAME MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
sda 8:0 0 1.8T 0 disk
&#9492;&#9472;sda2 8:2 0 1.6T 0 part

NAME MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
sdb 8:16 0 1.8T 0 disk
```

and the Disk utility agrees (below). 

 [B]Also, /dev/disk/by-id contains an entry pointing to sda and one pointing to sda2.  So it really does think there's a second partition there.
[Edit: I've completely wiped the disks with random data, and now sda is showing properly in Disks utility as an "unknown disk", but sdb shows a second partition!][/B]

Any thoughts on what's going on? The disks were prepared identically. I am thinking that I should remove /dev/sda, wipe the BtrFS metadata, and then re-add it. (But then I can't figure out how to remove the metadata, and don't want to spend 24 hours re-blanking the disk! Anyone know how to do this?)

Thanks
/DA

[IMG]http://ibin.co/2SQv4KbH06Mz[/IMG]

---

### Post by DiagonalArg on 2016-01-06
Since I've wiped the disks with random data and am finding the same problem (now with sda and sdb reversed) this clearly has nothing to do with luks/btrfs.  It's all a problem with the system identifying the presence of a device that's not there (/dev/sda2).  I have to guess that lsblk and Disks utility works off of that.  I have [reported the bug]("https://bugs.launchpad.net/ubuntu/+bug/1531404").

---

