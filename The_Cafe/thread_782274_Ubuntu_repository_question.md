---
title: "Ubuntu repository question"
date: 2008-05-04
forum: The Cafe
---

### Post by Ozor Mox on 2008-05-04
So I've been experimenting recently with installing a command-line Ubuntu system from the alternate CD, and creating a custom desktop. Thing is, a lot of the problems I'm running in to seem to be a result of Ubuntu-customised packages. For example, installing xorg and gnome-core to get a basic desktop works fine, except there are some broken panel buttons for things that aren't installed yet, like Evolution, help and volume controls. If I install Xfce, I get a plain desktop with a completely unconfigured panel that I have to add a clock, taskbar, application list etc. to.

Now I see that Ubuntu has some pre-configured packages with 'ubuntu' on the end, so I presume this causes the problems with GNOME. But how come if I do a Debian net install and then install any of the desktops (GNOME, KDE, Xfce...), they are all set up properly with Debian wallpaper and configured panels and such? Is it not possible to do this with Ubuntu, and get a working desktop but no pre-installed applications?

Just trying to understand how these packages work.

---

### Post by jrusso2 on 2008-05-04
I think its because Ubuntu uses a lot of modified Meta packages which installs a number of things at once, where as Debian installs one thing at a time.

---

### Post by WastingBody on 2008-05-04
Gentoo has the same problem when you build a light system. When you first boot into the system it has those launchers that have no installed program associated with them.

---

### Post by swoll1980 on 2008-05-04
> **jrusso2 said:**
> I think its because Ubuntu uses a lot of modified Meta packages which installs a number of things at once, where as Debian installs one thing at a time.

ubuntu-desktop

---

### Post by Ozor Mox on 2008-05-05
> **swoll1980 said:**
> ubuntu-desktop

As far as I know, that's the same as installing Ubuntu normally. Everything works great if you do that, but install a command-line system and then packages xorg, gdm and gnome-core as recommended for a minimal installation. You'll get an error when GDM starts saying it can't find the Human theme, lots of shortcuts will be broken on the panels, the artwork will be missing. Do it with a Debian net install, and everything will work. Quite odd I thought, but then I know that Ubuntu is designed to be a full desktop out of the box, unlike Debian.

---

