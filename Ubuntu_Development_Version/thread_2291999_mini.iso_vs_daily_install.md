---
title: "mini.iso vs daily install"
date: 2015-08-24
forum: Ubuntu Development Version
---

### Post by dino99 on 2015-08-24
Today i've tested a wily mini.iso install with ubuntu-desktop
but got a configuring language ( OS us + kbd fr) issue. Resulting to unreable titles, shrinked words, missing letters, etc
switching the installed languages for global & regional does not help.
get the same result with an unity or gnome-shell session: its something related to utf-8 and ansi-x conflicts.
affect both 'nouveau' & nvidia-355 drivers; so it might be a problem with configuring locales.

Wonder if the daily built also have that issue.
Looks like it is due to a too old installer used.

---

### Post by sudodus on 2015-08-24
The current wily mini.iso is three weeks old according to the information at [http://cdimages.ubuntu.com/netboot/](http://cdimages.ubuntu.com/netboot/)

**mini.iso 31-Jul-2015 12:04**

What happens when you update/upgrade a system installed from it before installing ubuntu-desktop?

---

### Post by dino99 on 2015-08-24
Sadly i've selected to install ubuntu-desktop when the installer have asked to; an the problem first appeared with the unity session. Then i've installed gnome-shell, and got the same garbage. After doing a lot of tweaks, i still have that problem; so i've closed that session, and booted an other installation.
That issue have been discussed and reported also, some affecting qemu, some nvidia, some blaming a too old installer.
I will wait some days, upgrade again to know if that can be fixed; otherwise i will do an other fresh install, maybe a daily one that time.

---

