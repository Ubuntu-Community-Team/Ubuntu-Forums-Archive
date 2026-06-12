---
title: "Mate now installable (and bootable) in Utopic"
date: 2014-04-29
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2014-04-29
Just install 'mate-session-manager':

```
lance@lance-desktop:~$ **sudo apt-get install mate-session-manager**
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  caja caja-common libcaja-extension1 libmarco-private0 libmate-desktop-2-17
  libmate-menu2 libmate-panel-applet-4-1 libmateweather-common libmateweather1
  libunique-1.0-0 marco marco-common mate-desktop mate-desktop-common
  mate-menus mate-panel mate-panel-common mate-polkit mate-polkit-common menu
  menu-xdg
Suggested packages:
  meld engrampa menu-l10n gksu kdebase-bin kdebase-runtime ktsuss sux
Recommended packages:
  mate-settings-daemon
[B][COLOR="#FF0000"]The following NEW packages will be installed:
  caja caja-common libcaja-extension1 libmarco-private0 libmate-desktop-2-17
  libmate-menu2 libmate-panel-applet-4-1 libmateweather-common libmateweather1
  libunique-1.0-0 marco marco-common mate-desktop mate-desktop-common
  mate-menus mate-panel mate-panel-common mate-polkit mate-polkit-common
  mate-session-manager menu menu-xdg
0 upgraded, 22 newly installed, 0 to remove and 124 not upgraded.
Need to get 20.9 MB of archives.
After this operation, 64.2 MB of additional disk space will be used[/COLOR][/B].
```

Seems rough around the edges but I may be missing some recommends ;)

---

### Post by kansasnoob on 2014-05-20
The meta-package 'mate-desktop-environment' is now in the Utopic repos:

> mate-desktop-environment (1.8.0+2) unstable; urgency=low

  * debian/control:
    + Meta:package m-d-e-core breaks old (<< 1.8.0) m-d-e meta packages.

 -- Mike Gabriel <sunweaver@debian.org>  Mon, 12 May 2014 12:49:22 +0200

mate-desktop-environment (1.8.0+1) unstable; urgency=low

  * Initial upload to Debian. (Closes: #746731, #743401).

 -- Mike Gabriel <sunweaver@debian.org>  Sun, 11 May 2014 21:47:04 +0200


I'll have to try a fresh install soon to see how complete it is.

---

### Post by ventrical on 2014-05-20
And away we go .. ! :)

---

### Post by ventrical on 2014-05-20
It is very kluncky right now :)  I have it on a high end machine and there is no smooth scrolling for ff .. etc.. missing icons ..slow,.. can't shut down , hitting log off will shut down .. etc..

---

### Post by ventrical on 2014-05-20
It also brought in something (???) that now causes a horizontal tear between the window titlebar and the window in a Unity session.  Just horrible.

---

