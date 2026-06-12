---
title: "uninstalling X, wm."
date: 2008-12-22
forum: Server Platforms
---

### Post by caymahallesi on 2008-12-22
hi guys I need your comment on below ideas.

I have ubuntu server version installed on my one of old-home-computer.

I am trying to learn the server software and using the desktop sometimes makes me really tired and frastrated, because the system is very slow running on p41.3ghz cpu and 350mb ram. when I logout of WindowsManager (like gnome) I am still using 150-160mb of ram. so, I was wondering since I was able to install webmin, ssh and firestarter on the server, now I can get rid of WM to save on hdd and memory space.

So, I am going to run sudo apt-get autoremove ubuntu-desktop, xfce4 command to remove these WM. 

please let me know what you think about this my planned actions. Is it worth removeing these WM, xorg etc.

---

### Post by kerry_s on 2008-12-22
ubuntu-desktop is just a meta-package, it will not uninstall anything.

ubuntu ties everything together once you start uninstalling it will snowball. i would just start over with just the server install since now you know what to do.

---

