---
title: "No GUI - 6.05 Server"
date: 2008-03-18
forum: Server Platforms
---

### Post by wrigley1956 on 2008-03-18
Folks,

Odd install issue - Dell Poweredge 2500 server platform w/6 SCSI drives in 3 RAID 1 configs; STD Dell video adapter, 3gb mem.

Install ok, but when booting, no GUI or control via keybd or mouse.

If I catche the screen msg, I can hit ESC to login/Menu etc...

Any way to start GUI from CMD prompt??

Thanks!

Steve

---

### Post by Wobedraggled on 2008-03-18
Server install doesn't install a gui by default.

Login and do a "sudo apt-get install xubuntu-desktop" This will get you xfce, "ubnutu-desktop" will get you gnome and "kubuntu-desktop" will get you kde.

for a server xfce should be fine.

---

### Post by lespaul_rentals on 2008-03-18
First off, there is no "6.05," only 6.06.

Second, of course it has no GUI, because it is a server install.  Servers are meant to be lightweight and dedicate their resources to background processes and daemons, not attractive desktops.  Please do not use Gnome or KDE or even Xfce to run your server.  Performance will go down greatly.  If you simply must have a GUI, install Fluxbox or just run a barebones X server.

---

