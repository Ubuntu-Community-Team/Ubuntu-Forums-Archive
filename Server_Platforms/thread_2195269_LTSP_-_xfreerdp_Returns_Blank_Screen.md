---
title: "LTSP - xfreerdp Returns Blank Screen"
date: 2013-12-23
forum: Server Platforms
---

### Post by laptopdude90 on 2013-12-23
I'm having trouble setting up LTSP with my Windows RDP server. When I enable xfreerdp, all I get is a black screen with a mouse.
Here is my /var/lib/tftpboot/ltsp/i386/lts.conf:

SCREEN_07 = "xfreerdp -f --ignore-certificate --no-nla 192.168.1.96"

However, if I boot the thin client into Ubuntu and run that command, it works fine. If I run that command on the server, it also works fine.
In /opt/ltsp/i386/usr/share/ltsp/xinitrc, I have export HOME=${HOME:-/root} right under . /usr/share/ltsp/ltsp-client-functions.

---

