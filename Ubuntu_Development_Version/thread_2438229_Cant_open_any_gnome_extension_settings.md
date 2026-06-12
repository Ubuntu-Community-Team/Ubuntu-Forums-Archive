---
title: "Cant open any gnome extension settings"
date: 2020-03-07
forum: Ubuntu Development Version
---

### Post by izznogooood on 2020-03-07
Hei guys!

I can't seem to open any extension settings. Nothing happens when I press the cogwheel in extensions menu in gnome-tweaks. On top of that the new gnome extensions app is completely blank.


gnome session
xorg
nvidia

---

### Post by kurt18947 on 2020-03-08
Same here with 20.04, no extensions are listed in current version.  Some extensions are working for me, others are not.

---

### Post by P-I H on 2020-03-08
This might be related.

I have the "Dash to panel extension" installed.
There are some problems see
[https://github.com/home-sweet-gnome/dash-to-panel/issues/878](https://github.com/home-sweet-gnome/dash-to-panel/issues/878)

In one of the comments it's noted that that extensions settings need gnome 3.35.92 to work. Focal Fossa has gnome 3.35.91.
The comment
[COLOR=#24292E][FONT=-apple-system]"It is working fine on Fedora Rawhide 3.35.92, but the bug you mentioned about the extension preferences was also present on 3.35.91 before the update. What is the output of [/FONT][/COLOR]gnome-shell --version[COLOR=#24292E][FONT=-apple-system] on your system? My guess is that Ubuntu 20.04 isn't yet updated to 3.35.92. Thanks!"[/FONT][/COLOR]

---

### Post by dino99 on 2020-03-08
Waiting for an upstream fix first
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1866146](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1866146)

---

