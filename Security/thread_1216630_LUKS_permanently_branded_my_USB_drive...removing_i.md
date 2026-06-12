---
title: "LUKS permanently branded my USB drive...removing it?"
date: 2009-07-18
forum: Security
---

### Post by AntsLoveSoda on 2009-07-18
Hey All!

At one point, I used cryptsetup with LUKS to encrypt an entire USB stick.  Now, I'm trying to get it back to it's original state (a FAT partition).  But after removing the partition with fdisk, and creating a new one, no matter what I do, it still acts like it's encrypted when I plug it in.

I even tried using fdisk through a failsafe terminal.  I can't get rid of the encryption it seems.  It's almost like the LUKS partition headers won't go away, and it has permanetly branded this USB drive.  Any thoughts? :confused:

Thanks!

---

### Post by unutbu on 2009-07-18
Please post 
```

sudo fdisk -l
``` and if there is more than one drive, indicate which is the LUKS-encrypted drive you wish to reformat.

---

### Post by AntsLoveSoda on 2009-07-18
This is the section showing the information for the USB drive...
```

Disk /dev/sdb: 2004 MB, 2004877312 bytes
62 heads, 62 sectors/track, 1018 cylinders
Units = cylinders of 3844 * 512 = 1968128 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1018     1956565    c  W95 FAT32 (LBA)

```Even stranger, it shows in fdisk what the partition is *supposed* to be (what I changed it to), but Ubuntu still acts like it's a LUKS formatted drive...and mounts still as ext3.

---

### Post by unutbu on 2009-07-18
Each partition has a type or ID. 
Each partition (primary or logical) can have a filesystem inside it.
Each filesystem has a type (such as ext3 or FAT).

What you are seeing here is the partition type, not the filesystem type:
```

/dev/sdb1               1        1018     1956565    c  W95 FAT32 (LBA)
```

When Linux mounts a partition, it ignores the partition type and instead tries to 
recognize the filesystem type within the partition.

So I believe you have a LUKS-encrypted filesystem inside sdb1. You've changed the partition type, but perhaps you haven't formated the filesystem within sdb1 yet.

To do this, you could use GParted (System>Admin>"Partition Editor") to delete sdb1 and create a new sdb1 with a FAT32 filesystem within it. Make sure you choose the option to reformat. (Really, you shouldn't even need to delete sdb1. I just forget exactly how to create a filesystem using GParted.)

If my vague GParted directions don't work, you can always open a terminal and type
```

sudo mkdosfs -n "VOLUME-NAME" /dev/sdb1
```
This will put a new filesystem inside the sdb1 partition, with what (I think) Windows would call a "drive" label "VOLUME-NAME".

---

### Post by AntsLoveSoda on 2009-07-18
Oh beautiful, worked perfectly!

I was always under the impression that simply deleting a partition would take care of that (I knew a format would need to be done, but I thought deleting the partition would void out any data that was originally there.)

And yes, you're correct with the drive label information.

Thanks for the help, unutbu!

---

### Post by HermanAB on 2009-07-19
Howdy,

You can always restore a disk to virgin state by zapping it with zeros:
$ sudo dd if=/dev/zero of=/dev/sdX

After that you need to create a partition with Fdisk.  Note that Windoze will only work with an extended partition on a USB device, so you have to create an extended partition and then create the file system inside that.  If it only needs to work on Linux, then you don't need to create a partition - you can format the raw disk.

So on Linux, this works:
mkfs.vfat /dev/sdb

On Windoze, you need to create a partition first:
echo -e -n "n\n1\n\nw\n"|fdisk /dev/sdb
mkfs.vfat -n LABEL /dev/sdb1

---

### Post by AntsLoveSoda on 2009-07-19
That's funny -- the 'dd' command crossed my mind at one time, and I thought "I wonder what would happen if I....naaah," because I thought I would just mess it up further.  Good to know that trick though.

I probably will need to use it on Windoze at some point.  Mainly, just trying to return it to the "universal usage" state (Linux, Windoze, Mac, picture printer terminals at stores, printers, etc).

Thanks for pointing that out!

---

