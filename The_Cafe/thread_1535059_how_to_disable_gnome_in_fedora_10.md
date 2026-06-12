---
title: "how to disable gnome in fedora 10?"
date: 2010-07-20
forum: The Cafe
---

### Post by legolas_w on 2010-07-20
Hi,

I have a server VM with fedora 10g, I am wondering how I can disable its gnome desktop from loading and eating memory and my time.

Thanks.

---

### Post by kaldor on 2010-07-20
Why not just uninstall GNOME completely? 

If it's for a server, just put a basic WM on it if you ever need a GUI.

---

### Post by Dragonbite on 2010-07-20
Isn't there a runlevel (3? 5?) which does not start X until you run "startx"?

---

### Post by RiceMonster on 2010-07-20
> **Dragonbite said:**
> Isn't there a runlevel (3? 5?) which does not start X until you run "startx"?

Yes. If you change the runlevel in /etc/inittab gdm will not start, and neither will gnome when you log in.

Just edit /etc/inittab and change "id:5:initdefault:" to "id:3:initdefault:"

---

