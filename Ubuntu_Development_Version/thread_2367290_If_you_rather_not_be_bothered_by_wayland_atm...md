---
title: "If you rather not be bothered by wayland atm.."
date: 2017-07-28
forum: Ubuntu Development Version
---

### Post by mc4man on 2017-07-28
Then simply - 
```
sudo nano /etc/gdm3/custom.conf
```
Remove the comment marked in red below, save, reboot.
```
# GDM configuration storage
#
# See /usr/share/gdm/gdm.schemas for a list of available options.

[daemon]
# Uncoment the line below to force the login screen to use Xorg
[COLOR="#FF0000"]#[/COLOR]WaylandEnable=false
```

May need to be redone on gdm3 updates..

---

