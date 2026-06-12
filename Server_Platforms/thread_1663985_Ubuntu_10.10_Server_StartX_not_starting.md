---
title: "Ubuntu 10.10 Server StartX not starting"
date: 2011-01-10
forum: Server Platforms
---

### Post by sentinelace on 2011-01-10
I ran "sudo apt-get install ubuntu-desktop". Now it starts to boot but all I have is a mouse. I cannot access anything on the desktop. Any ideas?

---

### Post by stlsaint on 2011-01-10
Thats because more is required to ensure that gnome is started.
You need to install xserver also
```
x-window-system-core xserver-xorg
``` 

Then you install either gnome or the entire ubuntu desktop environment:

Option: Gnome
Package=gnome-desktop-environment

Option: Ubuntu Desktop
Package: Ubuntu desktop environment

Then i think you must run: 
```
/etc/init.d/gdm start
```

Possibly a reboot may be required. I am unsure of the entirety of the process as i dont install a GUI on my servers but a quick google will get you further.:popcorn:

---

### Post by pspkicks316 on 2011-01-10
Once you install GDM, it should symlink to your rcX.d folders and run at startup. To only have X run when you want, I believe you just need to remove GDM (or remove the symlinks with 'sudo rc.update -f gdm remove' or something along those lines). That's what I did, so that I can start X as needed.

---

### Post by sentinelace on 2011-01-10
That worked!  Thanks.

---

