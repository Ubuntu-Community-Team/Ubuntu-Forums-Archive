---
title: "Request: Just a few packages ;)"
date: 2005-06-23
forum: Ubuntu Backports
---

### Post by XDevHald on 2005-06-23
> 
ORBit-2.0 >= 2.4.0 
gdk-pixbuf-2.0 >= 2.1.0 
gtk+-2.0 >= 2.5.4 
libgnome-2.0 >= 2.1.1 
libgnomeui-2.0 >= 2.5.4 
gnome-desktop-2.0 >= 2.9.91 
gnome-vfs-2.0 >= 2.9.1 
libglade-2.0 >= 2.5.0 
gconf-2.0 >= 2.6.1 
libgnome-menu >= 2.11.1
 

Not that bad, but this is so I can install gnome-panel 2.11.3

---

### Post by jdong on 2005-06-23
Half of those are libraries.. which I'm less than willing to backport and put in the official tree.

Perhaps try using ubp-build to build them yourself? Googling "ubp-build" will get you a copy of the script.

Add deb-src lines for Breezy to your sources.list, update, then python ubp-build.py <PACKAGENAME>


It'll build, stopping in between to ask for changelog (Change version to include ~5.04ubp1 to make upgrading easy). When it reaches "Backports or Extras?", CTRL+C out of it, then look in ~/ubp-compile-temp for your debs :)

---

### Post by XDevHald on 2005-06-23
Ah, even better :D

Cheers!

---

