---
title: "Ubuntu Server backup to USB drive"
date: 2014-01-05
forum: Server Platforms
---

### Post by thishalll on 2014-01-05
I backup my Ubuntu Server using TAR.

```
sudo tar -cvpzf backup.tar.gz --exclude=/backup.tar.gz --one-file-system / 
```

Then I copied *backup.tar.gz* to the USB drive. I mounted USB drive to */media/usb/*

```
sudo cp backup.tar.gz /media/usb/backup.tar.gz
```


So, now I want to format entire hard drive, and restore from the file in the usb drive.

I have Ubuntu Server Installer on the USB drive, but I don't see the menu for terminal.

Where can I find it?

I don't want to make Live CD. Is there any solution for this?

---

### Post by nerdtron on 2014-01-05
That is not the way to restore a server from scratch.
The  way I would do it is to boot CloneZilla. Then clone the whole server and save it to the USB drive.
After clone is successful, you can do whatever you want to the server, then you can use Clonezilla again to restore your Ubuntu server?

But why do you want to backup-format-restore? I don't see any point/advantage?

---

### Post by pft42 on 2014-01-09
No matter where the menu entry is now, after formatting the system disk it will be gone anyway.
To run an installation you have to have a system to boot from. A formatted drive does not have one.

Rethink your whole procedure or let us know what your real intention is. This plan is broken, maybe we can give you a better one.

---

