---
title: "VNC to lightdm"
date: 2013-01-23
forum: Virtualisation
---

### Post by pmatos on 2013-01-23
Hello,

I would like to be able to access my family PC from my other xubuntu/windows PCs, however I want to get to the login screen, not to an open session.

I followed [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC) unsuccessfully. 

I run on my family PC:
```
sudo x11vnc -xkb -safer -localhost -nopw -once -auth /var/run/lightdm/root/:0 -display :0
```

Unfortunately, when I connect from vncviewer in another PC into my PC, I see and have control over my wifes session while she's on the PC. While this had some funny applications while I was testing it, it was not what I wanted. I expected to see the lightdm login screen.

How can I get x11vnc to connect to lightdm and show me the login screen instead of my wifes session?

Thanks.

---

