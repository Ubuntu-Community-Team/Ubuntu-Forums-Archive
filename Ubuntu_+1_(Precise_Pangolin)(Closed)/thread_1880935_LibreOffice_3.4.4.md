---
title: "LibreOffice 3.4.4"
date: 2011-11-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2011-11-14
The newest LibreOffice release 3.4.4 is already available from Oneiric-updates repos.
So it will be soon in Precise too.

Of course, the Oneiric branch LibreOffice may very well be installed at this time into Precise.
All the dependencies are exactly the same as with the latest Precise version (3.4.3).

Here:
[https://launchpad.net/ubuntu/oneiric/+source/libreoffice/1:3.4.4-0ubuntu1](https://launchpad.net/ubuntu/oneiric/+source/libreoffice/1:3.4.4-0ubuntu1)

---

### Post by wgarcia on 2011-11-15
One of the less developed aspects of Unity is the integration with LibreOffice. There is a bug opened:

[https://bugs.launchpad.net/unity-2d/+bug/842566](https://bugs.launchpad.net/unity-2d/+bug/842566)

This has really to be high priority for Precise, shipping a desktop with the main office suit badly integrated is really a problem.

---

### Post by dino99 on 2011-11-15
Everyone knows that unity is very young and still a work in progress, with its bugs and lack of settings/features. But using unity is only your choice as you can be logged without it, using gnome-session-fallback or gnome-shell for example.

---

### Post by Harry33 on 2011-11-15
> **wgarcia said:**
> One of the less developed aspects of Unity is the integration with LibreOffice. There is a bug opened:

[https://bugs.launchpad.net/unity-2d/+bug/842566](https://bugs.launchpad.net/unity-2d/+bug/842566)

This has really to be high priority for Precise, shipping a desktop with the main office suit badly integrated is really a problem.

Well that seems to be a Unity bug, not a LO one.

---

### Post by kaldor on 2011-11-15
The LibreOffice integration is pretty well known. Currently, you can install the *lo-menubar* package. Apparently it's not stable enough, but I have never had a problem and I've been using it since the Natty betas.

I think they should just include the appmenu by default for 12.04. More people will use it on launch, and then by 12.04.1 it may be largely fixed.

---

### Post by wgarcia on 2011-11-15
Instead in my case with lo-menubar I get some LO windows without menu, or that stay in the background, or not well integrated in the launcher. And according to the bug I quote I'm not the only one.

---

### Post by kaldor on 2011-11-15
> **wgarcia said:**
> Instead in my case with lo-menubar I get some LO windows without menu, or that stay in the background, or not well integrated in the launcher. And according to the bug I quote I'm not the only one.

No such appmenu issues here. The launcher integration is crap, however.

---

### Post by vasa1 on 2011-11-15
> **kaldor said:**
> The LibreOffice integration is pretty well known. Currently, you can install the *lo-menubar* package. Apparently it's not stable enough, but I have never had a problem and I've been using it since the Natty betas.

I think they should just include the appmenu by default for 12.04. More people will use it on launch, and then by 12.04.1 it may be largely fixed.

There is this bug as well:
[https://bugs.launchpad.net/ubuntu/+source/lo-menubar/+bug/760879](https://bugs.launchpad.net/ubuntu/+source/lo-menubar/+bug/760879)
"Window" is not part of the menu and menu-related keyboard short cuts don't work. While the first has a workaround, nothing is clear about the second.

---

