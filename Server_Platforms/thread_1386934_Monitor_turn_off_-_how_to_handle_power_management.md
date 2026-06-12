---
title: "Monitor turn off - how to handle power management"
date: 2010-01-21
forum: Server Platforms
---

### Post by Diubidone on 2010-01-21
Hi all,

I have an Ubuntu Server with minimal gnome display and a Nagios monitoring server on it. I would need the monitor to stay always on but I can't figure out how to configure the power management with the terminal (Bash shell).

Anyone can give me a hint?

---

### Post by gobbledigook on 2010-01-21
try [_**this**_]("http://ubuntuforums.org/showthread.php?t=278693") thread... about post #5 :)

---

### Post by doas777 on 2010-01-21
if the monitor is actually going into standby, look to see if you have a file at /etc/X11/xorg.conf. in it look for a setting called "DPMS" and set it to false. 

hopefully that will do it, but prolly not, since no one uses xorg.conf anymore.

---

