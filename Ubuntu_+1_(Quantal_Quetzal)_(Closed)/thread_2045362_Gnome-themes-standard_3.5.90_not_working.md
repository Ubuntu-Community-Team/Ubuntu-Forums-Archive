---
title: "Gnome-themes-standard_3.5.90 not working"
date: 2012-08-21
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Harry33 on 2012-08-21
The newest gnome-themes-standard (3.5.90-0ubuntu1) does not work correctly.
In Gnome-shell DE the theming looks terrible now.

Downgrading to the previous version (3.5.5) solves the issue for now.

---

### Post by dino99 on 2012-08-21
confirmed

[https://bugs.launchpad.net/ubuntu/+source/gnome-themes-standard/+bug/1039389](https://bugs.launchpad.net/ubuntu/+source/gnome-themes-standard/+bug/1039389)

---

### Post by Harry33 on 2012-08-22
The newest version 3.5.90.1-0ubuntu2 does not work correctly either.

The visual theming problem is evident when using a GTK+2 application,
such as thunderbird, firefox or synaptic.
Synaptic looks definitely very bad.

---

### Post by dino99 on 2012-08-22
adwaita look has changed a little bit, but i cant complaint about that new one. What do mean by "look quite bad" now ?

---

### Post by Harry33 on 2012-08-22
> **dino99 said:**
> adwaita look has changed a little bit, but i cant complaint about that new one. What do mean by "look quite bad" now ?

There is no problem if I use a GTK+3 application, like nautilus.
But, try Thunderbird or Synaptic.
For me, the toolbar buttons for example look bad and icon colors are not correct.

I will check later if this is because I do not have gtk2-engines-pixbuf installed.

---

### Post by dino99 on 2012-08-22
> **Harry33 said:**
> 

I will check later if this is because I do not have gtk2-engines-pixbuf installed.

i have it installed and its mandatory now

---

### Post by Harry33 on 2012-08-22
> **dino99 said:**
> i have it installed and its mandatory now

Not mandatory, it is recommended.
If gnome-themes-standard really needs it, it should depend on it.

---

### Post by Harry33 on 2012-08-22
OK, installing gtk2-engines-pixbuf along with gtk2-engines fixes this issue.

---

