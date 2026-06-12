---
title: "No sdb in /dev/"
date: 2012-06-15
forum: Server Platforms
---

### Post by JeyPeyy on 2012-06-15
I'm trying to setup a server with my old pentium4 computer, so I upgraded to 12.04 and uninstalled all desktop environments that were installed (xfce, lxde) so I got a server setup. I'm pretty sure I could access my external hard drive through lxde, but now I can't find it. fdisk -l shows only sda* and ls /dev/sdb* gives no result. 

The hard drive is connected through an USB cable. I can see on a blue LED that it is powered, and it works on my desktop computer.

All help much appreciated!

---

### Post by volkswagner on 2012-06-15
Reboot your machine without the USB drive in place.

View dmesg while inserting the USB drive after the reboot.

```
tail -f /var/log/dmesg
```

Then insert the drive and post the output.

Also try:

```
lsusb
```

---

