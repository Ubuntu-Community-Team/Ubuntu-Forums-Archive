---
title: "Creating a static cdrom automount point."
date: 2011-03-14
forum: Server Platforms
---

### Post by RyanRahl on 2011-03-14
I have an Ubuntu server running Samba and I would like to share out the cdrom drive to the network. I made a share of the /media directory and it seems to work fine when I insert USB drives and I am able to browse and work with files. However, when I insert a cdrom it automatically mounts to /media/<volume name> and I get a permission denied error when I attempt to access it over the network. I am assuming this is happening because the permissions do not include the execute bit and being a read only file system I can not change this. I made the directory /media/cdrom and manually mounted the cdrom to it and I can successfully access it over the network just like the USB drives. So my question is: Is there a way to make the cdrom automatically mount and unmount to /media/cdrom when I insert and eject disks instead of to /media/<volume name>? Or maybe just have the permissions automatically set so Samba users can open it instead of just see it.

---

### Post by egpetrich on 2011-03-15
I can't offer you a turnkey solution, but I may be able to point you in the right direction.

There's a tutorial thread on [how to run a script when a USB device is plugged in]("http://ubuntuforums.org/showthread.php?t=502864"). One part of the thread describes a way to create a static entry in "/dev/" for a particular USB device. Assuming that the "udev" rules are what create your automount, you might be able to create a custom rule to do what you want when a CD is inserted into the drive.

---

