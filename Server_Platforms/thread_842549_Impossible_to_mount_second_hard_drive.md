---
title: "Impossible to mount second hard drive"
date: 2008-06-27
forum: Server Platforms
---

### Post by volmark on 2008-06-27
Impossible to mount second hard drive

:~$ sudo mount /dev/sdb1 /media/hd2/
mount: you must specify the filesystem type

~$ sudo mount -t ext3 /dev/sdb1 /media/hd2/
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
missing codepage or helper program, or other error
In some cases useful info is found in syslog &#8211; try dmesg | tail  or so

~$ sudo fdisk -l

Disk /dev/sda: 36.4 GB, 36419584000 bytes
255 heads, 63 sectors/track, 4427 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3cd54c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4240    34057768+  83  Linux
/dev/sda2            4241        4427     1502077+   5  Extended
/dev/sda5            4241        4427     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3b64465

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161   83  Linux

What's wrong???

---

### Post by koenn on 2008-06-27
is this a new, blank harddisk ?

---

### Post by MJN on 2008-06-27
...and did anything appear in syslog as advised?

Mathew

---

### Post by volmark on 2008-06-28
1. It is totally new blank disk. I’m free to destroy everything on it.
2. Nothing special in syslog. There are some syslogs and I’ve looked in /var/logs/syslog and /var/logs/syslog.0

---

### Post by MJN on 2008-06-28
> **volmark said:**
> 1. It is totally new blank disk. 

As Koenn was likely steering towards, you need to lay a filesystem on the partition before it can be mounted (the ID of 83 alone is insufficient).

Hence, for an ext3 FS run [B]sudo mkfs -t ext3 /dev/sdb1

[/B]Mathew

---

### Post by koenn on 2008-06-28
my work here is done. :)

---

### Post by AlanR8 on 2008-06-28
Have a look at the below......copied unashamedly from another post elsewhere on this forum.

Find out where it lives: 
Code:
sudo fdisk -l
My guess is it's (and for the sake of this example I'm assuming it's) /dev/hdb1

Ensure it's not already mounted: 
Code:
sudo umount /dev/hdb1
Create a mount point for it: 
Code:
sudo mkdir /second_drive
Back up the fstab: 
Code:
sudo cp /etc/fstab /etc/fstab_backup
Edit the fstab: 
Code:
sudo nano /etc/fstab
Add in this line at the end of the file: 
Code:
/dev/hdb1 /second_drive ext3 defaults 0 0
Save the file: Control-X, Y, Enter [code] Mount the drive: 
Code:
sudo mount -a
Change ownership to you: 
Code:
sudo chown -R derouge:derouge /second_drive
Set permissions: 
Code:
sudo chmod -R 755 /second_drive

---

### Post by volmark on 2008-06-28
> **MJN said:**
> As Koenn was likely steering towards, you need to lay a filesystem on the partition before it can be mounted (the ID of 83 alone is insufficient).

Hence, for an ext3 FS run [B]sudo mkfs -t ext3 /dev/sdb1

[/B]Mathew

sudo mkfs -t ext3 /dev/sdb1 worked perfectly for me. I could mount the second HD drive manually, and remount it with “mount –a” after editing of fstab.
Unfortunately after rebooting my HD drives were mutually changed: primary HD drive that was /dev/sda1 became /div/sdb1 (and respectively other logical drives) and /dev/sdb1 became /dev/sda1.
Strange …

---

### Post by windependence on 2008-06-28
I know this is a cross post since I answered you ni your other post but anyway read this thread:

[http://ubuntuforums.org/showthread.php?t=836542](http://ubuntuforums.org/showthread.php?t=836542)

-Tim

---

