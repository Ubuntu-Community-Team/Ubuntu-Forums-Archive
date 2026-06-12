---
title: "HP ML115 iLO 100c KVM Console Problem"
date: 2011-03-28
forum: Server Platforms
---

### Post by alexharrington on 2011-03-28
Hi there

I have an HP ML115 G5 with an iLO 100c card which provides remote KVM services over IP.

The server POSTs fine, and I can run utilities like memtest fine over the KVM Java applet, but when I boot in to Ubuntu the console output is broken up.

I'm running the latest firmware for the iLO card. We don't have this problem with the iLO2 cards built in to the larger DL360/DL380 servers we have.

I've tried changing the console resolution (640x480, 800x600, 1024x768) in the grub configuration however all except 640x480 just give a black screen where the console should be.

Has anyone seen this before or have any suggestions on fixing it?

Thanks

Alex

---

### Post by alexharrington on 2011-03-28
I stumbled across this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/605481](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/605481)

Which suggests a kernel parameter as a work around. I edited /etc/default/grub

and changed the line as follows:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet vga16fb.modeset=0"
```

and then ran:
```
sudo update-grub
```

And it's working.

Sorry for the noise!

---

