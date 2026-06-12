---
title: "nouveau  (nvidia) &amp;  vsync"
date: 2012-06-30
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by mc4man on 2012-06-30
vsync isn't enabled for nouveau but, at least here, makes a significant difference if enabled.
To do so, -
create an /etc/X11/xorg.conf, reboot

```
Section "Device"
 Identifier "My Graphics"
 Option "GLXVBlank" "on"
EndSection

```

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1019131](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1019131)

referring
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/880707](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/880707)

---

### Post by VMC on 2012-06-30
I think you right. At lease on my 12.04 LTS, it appears to have made a difference.
The problem I've had all along, from 12.04 testing, around June 18th, was a strange delay on focus, on menu items.

After adding your vsync it appears to have been fixed. I'll know in a few days. Sometimes it appears to be working and then all of a sudden I lose focus for a couple of seconds.

Hopefully this is the cure!

---

### Post by mc4man on 2012-08-22
This has now been fixed for all current chips, but likely won't be seen  till the 3.7 kernel ( unless backported to 12.10/12.04

So as it stands only some hardware can have vsync in nouveau & has to be manually set

---

### Post by mc4man on 2012-09-27
The next nouveau package, xserver-xorg-video-nouveau (1:1.0.2-0ubuntu2),  will attempt to auto enable vsync with supported nvidia hardware.

---

