---
title: "apt-get upgrade results in seg fault"
date: 2011-02-03
forum: Server Platforms
---

### Post by MarisO on 2011-02-03
I did apt-get upgrade on my 10.4 server and this is what happened:

Setting up grub-pc (1.98-1ubuntu10) ...
Installation finished. No error reported.
touch: cannot touch `/boot/grub/grub.cfg': Read-only file system
rm: cannot remove `/tmp/grub.nPwxFV8A3o': Read-only file system
debconf: DbDriver "config": could not write /var/cache/debconf/config.dat-new: Read-only file system
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libpam-ck-connector (0.4.1-3ubuntu2) ...
touch: cannot touch `/var/lib/update-notifier/dpkg-run-stamp': Read-only file system
sh: cannot create /var/lib/update-notifier/updates-available: Read-only file system
[1]    11563 segmentation fault  sudo apt-get upgrade

why is it saying "Read-only file system" ?
Is my SSD drive faulty ?

---

### Post by ibuclaw on 2011-02-03
Looks like /boot is mounted as ro, I would not find this unusual on a server.
To put it in the shortest way possible, temporarily remount as rw, upgrade, then reboot. :)

```
mount -o remount,rw /boot
```
You may require extra options depending on default mount settings of that partition.

Regards

---

