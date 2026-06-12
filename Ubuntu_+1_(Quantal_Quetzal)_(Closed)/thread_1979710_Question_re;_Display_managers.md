---
title: "Question re; Display managers"
date: 2012-05-14
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Miykel on 2012-05-14
Is there a way I could change between several display managers ???
Regards Miykel

---

### Post by ronacc on 2012-05-14
Install them and they will be available at login from the session menu .

---

### Post by Miykel on 2012-05-14
Thanks Ronacc; I may be on a different tangent here, what I meant was, sat, lightdm or gdm,that kind thing.
Regards Miykel

---

### Post by jfernyhough on 2012-05-14
When you install a second DM dpkg will prompt you to choose which loads by default. You can change it by running $ sudo dpkg-reconfigure lightdm (or $ sudo dpkg-reconfigure gdm) and choosing the DM you want. It doesn't seem to matter which one you reconfigure, you get the list of all currently installed.

---

### Post by ronacc on 2012-05-14
just open synaptic and install them ,I just installed lxde and lubuntu ( searched on lxde in synaptic and installed everthing that came up, ) I now have on my login session menu , Gnome  (Gnome-shell) , gnome classic , Gnome/openbox , LXDE , lubuntu , lubuntu Netbook , openbox ,Ubuntu ( unity 3D ) , unity 2D  .  I have also had Gnome and KDE on the same install .

---

### Post by zombifier25 on 2012-05-14
> **ronacc said:**
> just open synaptic and install them ,I just installed lxde and lubuntu ( searched on lxde in synaptic and installed everthing that came up, ) I now have on my login session menu , Gnome  (Gnome-shell) , gnome classic , Gnome/openbox , LXDE , lubuntu , lubuntu Netbook , openbox ,Ubuntu ( unity 3D ) , unity 2D  .  I have also had Gnome and KDE on the same install .

You're not reading do you? :popcorn: OP was asking for LightDM/GDM/KDM/etc which jfernyhough answered nicely.

---

### Post by Miykel on 2012-05-14
Thanks so much jfernyhough, thats exactly what I was looking for, and thanks to everyone else for the help
Kind Regards Miykel

---

