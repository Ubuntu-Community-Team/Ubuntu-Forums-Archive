---
title: "chroot -&gt; udev, X unconfigured"
date: 2012-02-09
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Ibidem on 2012-02-09
```
root@Caracal:/# dpkg --configure udev xserver-xorg-core Setting up udev (175-0ubuntu4) ... runlevel:/var/run/utmp: No such file or directory start: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused invoke-rc.d: initscript udev, action "restart" failed. dpkg: error processing udev (--configure):  subprocess installed post-installation script returned error exit status 1 dpkg: dependency problems prevent configuration of xserver-xorg-core:  xserver-xorg-core depends on udev (>= 149); however:   Package udev is not configured yet. dpkg: error processing xserver-xorg-core (--configure):  dependency problems - leaving unconfigured Errors were encountered while processing:  udev  xserver-xorg-core 
``` Chrooted from Debian (Squeeze + some updates), with /sys, /proc, /dev, /dev/pts, and resolv.conf mounted.  I blame Upstart.  Really, the Ubuntu developers need to redesign some part of it from the ground up; if a chroot breaks upgrades, the design is completely wrong. Will probably take booting in text mode to fix it.

---

### Post by Ibidem on 2012-02-09
X was broken on first boot (why doesn't xdm respect 'text'?) but booting in recovery mode, logging in as root, and running aptitude fixes it.

---

