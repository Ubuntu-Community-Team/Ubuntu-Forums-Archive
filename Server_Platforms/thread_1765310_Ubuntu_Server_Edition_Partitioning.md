---
title: "Ubuntu Server Edition Partitioning"
date: 2011-05-22
forum: Server Platforms
---

### Post by Ghjnut on 2011-05-22
Hey everyone, I'm looking for a little guidance regarding partitioning from the command line in ubuntu server edition. Specifically, I'm looking to do this solely from the command-line.

The hard drive in question is currently partitioned as follows (parted output)

Model: ATA WDC WD1200JB-00G (scsi)
Disk /dev/sdb: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  83.9GB  83.9GB  primary   ext4
 2      83.9GB  120GB   36.1GB  extended
 5      83.9GB  119GB   34.6GB  logical   ext4
 6      119GB   120GB   1532MB  logical   linux-swap(v1)

What I'm looking to do is partition it into just 2 partitions (main and swap)

Currently, I'm the 5th (extended) partition is my boot partition. I also have another hard drive with ubuntu server installed that I can boot to so there won't be issues with modifying an active partition.

In a nut shell, I'm looking to copy the 35 gig bootable partition over to be the first partition and then set a new swap partition.

Here's the steps I assume I'll have to go through.
1. Copy sdb5 to sdb1
2. Delete sdb2
3. resize sdb1 to 115 gigs
4. create new 2 gig swap file.

I'm not sure which command-line programs this will require (parted, mke2fs...) or how I will have to modify my fstab file which is where I'm hoping you guys can fill in the blanks. Thanks in advance for any help.

---

### Post by papibe on 2011-05-22
If you have access to the server I would advice you to hook up a monitor and keyboard, since you can accomplish almost everything by using gparted on the live Ubuntu CD.

The steps would be:
[LIST=1]
[*]Backup your data!
[*]As the machine is right now, copy your files from the sd5 partition to a new folder on sd1.
[*]Boot on the live CD, run gparted. Remove the sd5 partition, and resize sd1.
[*]When done, mount the sd1 so you can edit /etc/fstab (Open Computer and double click on it). Comment the line that mounts sd5. Move the files that you copied from sd5 to the desire location.
[*] Reboot normally.
[/LIST]
This only works, if sd1 is originally your / partition

I hope it helps.

---

