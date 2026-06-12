---
title: "Ubuntu GNOME ubiquity bug"
date: 2013-04-05
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2013-04-05
Both Jeremy Bicha and I encountered a new ubiquity bug while testing the Beta 2 candidates:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1164592](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1164592)

As you can see there it really only effects the "install alongside" option, but it's kind of hard to explain, and it's already been suggested that it may be a duplicate of this:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1080701](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1080701)

I'm fairly certain that it's not a dupe so I'm stealing some electronic ink to post some screenshots for comparison with Lubuntu RR Beta 2 images. In both cases I started with a very simple setup:

```
lubuntu@lubuntu:~$ sudo parted -l
Model: ATA WDC WD800JB-00JJ (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  77.9GB  77.9GB  primary   ext4            boot
 2      77.9GB  80.0GB  2137MB  extended
 5      77.9GB  80.0GB  2136MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!           
```

In both cases you need to simply select "Install alongside":

 [ATTACH=CONFIG]240962[/ATTACH]

Then with Lubuntu things work as expected, you're presented with the option to resize as you wish, and Install now is active:

[ATTACH=CONFIG]240963[/ATTACH]

Then after clicking on Install now you're asked to confirm:

[ATTACH=CONFIG]240964[/ATTACH]

But with Ubuntu GNOME only the Quit button appears to be active and you're not able to advance beyond that screen:

[ATTACH=CONFIG]240965[/ATTACH]

After waiting and waiting for a long time clicking on Quit does not even appear to do anything but if I click on the X in the upper right-hand corner I do get this:

[ATTACH=CONFIG]240966[/ATTACH]

Hopefully my pics will be worth a few thousand words.

---

### Post by dino99 on 2013-04-05
could it that Ubiquity be disturbed by /dev/sr0 ? Maybe set the cdrom off inside the bios (if possible) or unplug it to see if ubiquity react differently.

[http://superuser.com/questions/272657/whats-the-difference-between-dev-hdc-dev-sr0-dev-cdrom](http://superuser.com/questions/272657/whats-the-difference-between-dev-hdc-dev-sr0-dev-cdrom)

---

