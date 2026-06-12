---
title: "USB disks won't work on server install"
date: 2007-02-23
forum: Server Platforms
---

### Post by scottishnarn on 2007-02-23
I have a 6.10 server install which works fine apart from the fact that usb disks won't mount. The same disks mount fine in a normal desktop ubuntu version, so I figured it must be a package that is not installed in the deault server install. Does anyone know which packages I need to install to get it working. I'd rather not do a complete desktop install on this server system.

Thanks

---

### Post by Nythain on 2007-02-23
sounds like a possible kernel issue... not sure if the server kernel has the modules required for usb devices like the generic used in the desktop distros... if anyone else has more help, yay, cause i've been thinking of switching to server for minimal base start and will suffer this same problem

---

### Post by jtc on 2007-02-23
When you say the USB-drive won't mount, do you then mean it won't automount or that it won't mount when you try to do it manually?

---

### Post by scottishnarn on 2007-02-23
It certainly won't automount. I tried to mount it manually, but I can't remember the commands I used, I think I might have tried ```
mount /dev/usbdisk /media/usbdisk
``` of course making sure /media/usbdisk existed. Ideally I'd like it to automount, but if it doesn't I can just add the mount and umount commands to the backup script, since I'm using it for backups anyway.

---

### Post by jtc on 2007-02-23
What error message do you receive?

---

### Post by scottishnarn on 2007-02-24
I can manually mount I need to use ```
sudo mount /dev/sdb1 /media/usbdisk
```but it won't automount. I'm also a little worried that the disk will always be found at /dev/sdb1 and not /dev/sdc1 or something else.

---

### Post by jdevora on 2007-05-01
In [http://ubuntuforums.org/showthread.php?t=356478&highlight=automount](http://ubuntuforums.org/showthread.php?t=356478&highlight=automount) I just read that you have to use the package ivman

Cheers
 JD

---

