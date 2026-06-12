---
title: "Auto mounting Easy SATA drive"
date: 2011-08-05
forum: Server Platforms
---

### Post by manthony121 on 2011-08-05
I am looking towards backing up critical data from my network onto a hot swappable SATA HDD.  So, I installed an Antec "Easy SATA" bay into my case, plugged in a drive and.....nothing.  A little digging showed that I had to change the BIOS setting for SATA drives to "AHCI" (it had been set to "IDE"). I made the change, and the system booted normally.  Once again, I plugged in the drive, and the system recognized it immediately, as evidenced by "fdisk -l".  However, none of the partitions are mounted.

So, how would I write a script, or modify /etc/fstab, so that the partitions on the plugged in drive are recognized and automatically mounted when the drive is inserted?

---

### Post by ruffEdgz on 2011-08-05
If you see partitions that you wish to be mounted on boot, it would be wise to read this article about fstab:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

There are many options to choose from but here is a basic EXAMPLE (only) of what a new entry in your fstab would look like:
```

/dev/sdb1       /new/mounted/dir         ext4          defaults      0 0

```
The '**/dev/sdb1'** is the partition I would like to mount, **'/new/mounted/dir'** is the mounting point on your file system, **'ext4'** is the filesystem type,** 'defaults'** are the mount options (read more about by typing in 'man mount'), and **'0 0'** is the number for your DUMP and FSCK PASS which you will normally use 0 0 in majority of situations (not all).

Hope this helps.

---

### Post by manthony121 on 2011-08-05
I was actually looking for more of a "hot swap" option, similar to the way a USB storage device is automatically mounted when it is plugged in.

---

### Post by ruffEdgz on 2011-08-05
oh well, your going to have to use probably udev rules for that sort of thing.

[http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221)

I found something that was used back in 2006 and the idea is the same, the commands have been changed to get that information (I.E. udevadm is the command you will be using to trace the hardware information you need).

It's not totally the same but I needed to do this for my laptop whenever I plug in my USB wireless mouse and disable the touchpad: [http://thisisbryan.com/2011/06/10/linux-disable-touchpad-when-other-mouse-is-found/](http://thisisbryan.com/2011/06/10/linux-disable-touchpad-when-other-mouse-is-found/)

Hope this helps.

::UPDATE:: Found some of the other websites I used when getting my USB mouse rule to work on my laptop:

[http://manpages.ubuntu.com/manpages/karmic/man7/udev.7.html](http://manpages.ubuntu.com/manpages/karmic/man7/udev.7.html)
[http://hackaday.com/2009/09/18/how-to-write-udev-rules/](http://hackaday.com/2009/09/18/how-to-write-udev-rules/)

---

### Post by rubylaser on 2011-08-05
I always use fstab for consistent mounts, or just mount by hand, or via script, but if you want automount, here's a quick [howto]("http://sudocode.blogspot.com/2009/02/automount-usb-disks-in-ubuntu-server.html").

---

### Post by manthony121 on 2011-08-07
> **rubylaser said:**
> I always use fstab for consistent mounts, or just mount by hand, or via script, but if you want automount, here's a quick [howto]("http://sudocode.blogspot.com/2009/02/automount-usb-disks-in-ubuntu-server.html").

Useful link; thank you.  Despite not having the usbmount package installed, my system (Ubuntu 11.04) mounts USB storage devices automatically, anyway.  I assume that the usbmount package functionality is now incorporated into the kernel or other packages?

It looks like it will take some digging to be able to adapt the usbmount scripts to work with a sata interface.  If anyone already knows how to do this, I would very much like to know.

---

### Post by hyper2hottie on 2011-08-07
usb devices are mounted by gnome-volume-manager.

---

