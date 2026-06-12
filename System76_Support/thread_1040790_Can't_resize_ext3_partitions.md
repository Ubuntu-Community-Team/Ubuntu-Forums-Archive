---
title: "Can't resize ext3 partitions"
date: 2009-01-15
forum: System76 Support
---

### Post by andrewdied on 2009-01-15
I am not able to resize my partitions.  My end result is I want to make a larger windows partition, which is up at /dev/sda1.  At a high level what I've tried is booting off the 8.04 and 8.10 Ubuntu disks for amd64, starting the "trial" system off the cd, starting the gnome partition editor, and used the gui to shrink the last ext3 partition.  Basically I followed the instructions in the system76 FAQ: [http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine](http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine)

The error I get is the partition is already this size.  I think this error is incorrect.  When I look at the details of what gparted is doing, it does a consistency check (e2fsck -f -y -v /dev/sda2), then tries to resize the parition (resize2fs /dev/sda2 81786914K).  Hidden in the details is a message that e2fsck -f must be run, first.  This was done the step prior, automatically.  I think the program gets confused by the e2fsck "missing" step, then when it tries to shift or shrink the partition it thinks the partition is already at the target size.

I tried running these steps by hand, again from the ubuntu install cd, not from a running install.  I got the funky message about needing to run e2fsck first (before resize2fs).  I tried using sudo, then as root itself, with -v, and without.  resize2fs just never recognized I'd run e2fsck.

I even tried using knoppix, the 5.1.1 version from 2007, which looks to be the last one released on cd.  It uses kparted, but kparted always thought the partions were busy, even though mount didn't report it mounted.

Has anyone run into this kind of thing before, or have another way to shrink the partitions?  Thanks for the help.

---

### Post by utnubuuser on 2009-01-16
I've heard of people having a bit of a time with gparted.  Try fdisk.

---

### Post by andrewdied on 2009-01-16
> **utnubuuser said:**
> I've heard of people having a bit of a time with gparted.  Try fdisk.

Does fdisk do all the fancy data moving around?  I've used fdisk from when I installed linux off floppy, but I thought that was mostly a "kill the partition and make a new one" kind of tool.

Aside: Where do you mark threads as solved?  I've never been able to figure that out.

---

### Post by jdb on 2009-01-16
> **andrewdied said:**
> Does fdisk do all the fancy data moving around?  I've used fdisk from when I installed linux off floppy, but I thought that was mostly a "kill the partition and make a new one" kind of tool.

Aside: Where do you mark threads as solved?  I've never been able to figure that out.

parted does all that stuff, but make sure everthing is backed up in case something goes wrong.

jdb

---

### Post by andrewdied on 2009-01-16
> **jdb said:**
> parted does all that stuff, but make sure everthing is backed up in case something goes wrong.


So, fdisk doesn't retain any of the existing data, then?

---

### Post by jdb on 2009-01-16
> **andrewdied said:**
> So, fdisk doesn't retain any of the existing data, then?

The way I understand it, after an fdisk the partitions are so bare they don't even have a format.
The data might be there but you'll never find it.

If someone else knows something different I'm sure we'll hear it :)

jdb

---

### Post by jbelmonte on 2009-01-16
I'm fairly certain fdisk will "f" your disk and any data. Don't do it since it sounds like you do not want to start fresh.

---

