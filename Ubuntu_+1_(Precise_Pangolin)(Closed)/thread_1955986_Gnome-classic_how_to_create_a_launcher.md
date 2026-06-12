---
title: "Gnome-classic: how to create a launcher ?"
date: 2012-04-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by dino99 on 2012-04-10
with gtk2 it was easy to create a launcher on the desktop. But now with gnome-session-fallback, right-click on the desktop dont let you create one sadly, hopes this feature setting back asap. Its important for entering a command on a borked panel.

---

### Post by lucazade on 2012-04-10
installing alacarte?
then moving .desktop file from .local/share/applications/*.desktop to the desktop folder.

---

### Post by alex2e1gzy on 2012-04-10
A quick google came up with:

> gnome-desktop-item-edit ~/Desktop/ --create-new

From [http://www.ubuntugeek.com/how-to-create-desktop-launchers-in-ubuntu-11-10oneiric.html](http://www.ubuntugeek.com/how-to-create-desktop-launchers-in-ubuntu-11-10oneiric.html)

---

### Post by dino99 on 2012-04-10
> **alex2e1gzy said:**
> A quick google came up with:



From [http://www.ubuntugeek.com/how-to-create-desktop-launchers-in-ubuntu-11-10oneiric.html](http://www.ubuntugeek.com/how-to-create-desktop-launchers-in-ubuntu-11-10oneiric.html)

i've already found workarounds, thanks :)

but as Ubuntu is designed for Humans, then the great gnome devs thinking that a simple right-click is too easy, should stop smoking.

---

### Post by Yellow Pasque on 2012-04-10
> **dino99 said:**
> i've already found workarounds, thanks :)

but as Ubuntu is designed for Humans, then the great gnome devs thinking that a simple right-click is too easy, should stop smoking.
Gnome devs don't want you to use gnome-fallback (especially if your hardware is capable of running gnome-shell) and it's obvious they don't want to put time/effort into it. They're actually going to kill gnome-fallback once llvmpipe 3D sofware driver becomes prevalent.

I highly recommend switching to xfce/xubuntu (where creating a desktop launcher is still intuitive/easy).

---

### Post by ssam on 2012-04-10
another option if you are happy with gnome2 is to install mate [http://mate-desktop.org/]("http://mate-desktop.org/")

---

### Post by JHCKX on 2012-04-10
In Gnome-fallback, you can select a program from the menus, then Ctrl-click and drag it to the desktop or one of the panels. Simple enough and I found the solution without Google. Still, a right-click is even simpler.

---

