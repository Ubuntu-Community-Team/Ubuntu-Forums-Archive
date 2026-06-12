---
title: "Is it possible to install TomBoy notes (Gnome) on Slackware/Zenwalk?"
date: 2007-07-09
forum: Slackware and derivatives
---

### Post by wrycatcher on 2007-07-09
I would love to use TomBoy notes (a post it application developed for Gnome, also bundled with Ubuntu) with my Zenwalk distro.  I believe it's *technically *possible, but my fear is that I will need to compile and install some sort of Gnome package designed for Slackware-based distros.  I've read some negative reviews of such packages.   I don't even know if I **need** a Gnome package, but I suspect I might...anyone out there familiar with TomBoy's requirements and how I could get it working in Zenwalk?

If so, please take a moment to kindly show a slackware newbie the ropes...thanks!

---

### Post by saulgoode on 2007-07-09
It appears that Tomboy is not dependent upon any Gnome libraries, but it does use the MONO framework and requires the GDI+, GTK-SHARP, and GTK-SHARP2 libraries.

If you are lucky, you will have these packages (*mono, libgdiplus, gtk-sharp,* and *gtk-sharp2*) installed -- you can look in your '/var/log/packages' directory for them. It is quite possible they will not be installed (they are not part of the SW distribution). You should check to see if Zenwalk has these packages in their repositories (I don't use Zenwalk). 

If not, I could assist you in learning how to compile them if you wish to go that route.

---

### Post by wrycatcher on 2007-08-01
moved to subthread

---

### Post by wrycatcher on 2007-08-01
It appears I'll have to install from source as I do not see them installed and they are not present in the Zenwalk repositories (using Netpkg to browse). I guess what is the best way to install those dependent things (mono, gtk-sharp, etc.) from source?

---

