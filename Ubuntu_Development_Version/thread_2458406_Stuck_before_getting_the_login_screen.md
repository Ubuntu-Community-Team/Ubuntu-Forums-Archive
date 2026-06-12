---
title: "Stuck before getting the login screen"
date: 2021-02-24
forum: Ubuntu Development Version
---

### Post by dino99 on 2021-02-24
When starting Hirsute, without "quiet splash", the booting process goes well until ending to a black empty screen; the mouse and keyboard don't work at all.
Starting the recovery mode, startx ends with an "oops, we got a problem" message.

Looks like a wayland/xwayland problem, and the x11 fallback does not work either. Is there a key word to start wayland manually ?

Problem is pointed to glib 2.67.4 (proposed) [https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/1916701](https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/1916701)

No problem with the previous 2.66.4 version 
wait & see :(

---

### Post by zika on 2021-02-24
There is way to use *multi-user.target* and then do ```
startx
``` Add ```
systemd.unit=multi-user.target
``` in Grub_command_line to do it for that boot. For permanent use just *edit /etc/default/grub* and do ```
update-grub
```afterwards...
You could, also, alternatively, use ```
systemctl set-default multi-user.target
``` in boot-recovery mode but that is, also, permanent, until next change...

There seems to be some trouble with Wayland and Gnome, Settings are not working also and Log-Out leads to hang.
Luckily I have my daily i3 in X11 and just have tried Gnome for the sake of this thread...

---

### Post by dino99 on 2021-02-24
New version coming with a fix
[https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/1916701/comments/7](https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/1916701/comments/7)

---

