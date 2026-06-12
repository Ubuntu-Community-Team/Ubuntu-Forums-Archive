---
title: "ubuntu 14.04 ltsp 5.5.1 xrandr 1.4.1"
date: 2016-09-16
forum: Server Platforms
---

### Post by dvador on 2016-09-16
Hi

In lts.conf, I put :

[AA:BB:CC:8D:45:46]
XRANDR_COMMAND_0="xrandr --output LVDS --mode 800x600 --output VGA-0 --mode 800x600 --same-as LVDS"

On the thinclient, only the login windows is affected (resolution changed and cloning screens), the xsession after login is unchanged (one screen and 1280x800)


If after login, I make in localapps xterm (on the thinclient)



xrandr --output LVDS --mode 800x600 --output VGA-0 --mode 800x600 --same-as LVDS


Résolution switching and clonage are effective

If in lts.conf, I put

[AA:BB:CC:8D:45:46]
XRANDR_COMMAND_0="xrandr --newmode 832x624 41.00 832 864 944 1056 624 627 631 649 -hsync +vsync"
or
[AA:BB:CC:8D:45:46]
XRANDR_COMMAND_0="xrandr --addmode LVDS 832x624"

On the thinclient, after login, the newmod or addmod are here. So the xrandr_command_0 in lts.conf is effective (but not for mode and same-as !)



I have not monitors.xml in the /home/$user/.config
I have not .config/monitors.xml in the /var/lib/lightdm/


All work fine in ubuntu 12.04, ltsp 5.3.7, xrandr 1.3.5


Thanks


DV

---

