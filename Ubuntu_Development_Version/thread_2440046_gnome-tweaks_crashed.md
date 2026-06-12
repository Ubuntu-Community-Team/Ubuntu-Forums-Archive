---
title: "gnome-tweaks crashed"
date: 2020-04-05
forum: Ubuntu Development Version
---

### Post by corradoventu on 2020-04-05
on gnome-tweaks - extensions - desktop icons: click on configuration wheel -> crash

[https://bugs.launchpad.net/ubuntu/+source/gnome-tweaks/+bug/1870796](https://bugs.launchpad.net/ubuntu/+source/gnome-tweaks/+bug/1870796)

---

### Post by VMC on 2020-04-05
Also transparency no longer works on Gnome 3.36:
[https://github.com/rockon999/dynamic-panel-transparency/issues/111](https://github.com/rockon999/dynamic-panel-transparency/issues/111)

Gnome 3.36 may be the reason your gnome-tweaks failed. My gnome-tweaks didn't crash, but failed to work as before.

---

### Post by mc4man on 2020-04-05
> **corradoventu said:**
> on gnome-tweaks - extensions - desktop icons: click on configuration wheel -> crash

[https://bugs.launchpad.net/ubuntu/+source/gnome-tweaks/+bug/1870796](https://bugs.launchpad.net/ubuntu/+source/gnome-tweaks/+bug/1870796)

Is something leading you to believe you can control the package installed desktop-icon extension  thru gnome-tweaks? 
I don't believe it has ever been able to control the ubuntu packaged extension(s).., it/they can be configured lightly in dconf, or disabled entirely by removing the package(s).

---

### Post by P-I H on 2020-04-06
Tweaks has been updated today, and in this version it's possible to click on the configuration wheel for "Desktop icons" and adjust icon size and if personal folder icon and trash icon shall be shown or not. Tested in ubuntu-wayland.

---

### Post by corradoventu on 2020-04-07
Desktop icons and other extensions can be managed also from the new app 'Extensions'

---

