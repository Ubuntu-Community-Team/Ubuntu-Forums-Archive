---
title: "Integrate menu-file-browser-applet"
date: 2007-11-03
forum: Ubuntu Brainstorm
---

### Post by teasum on 2007-11-03
One feature I always missed from my XP days was having a menu for a given drive or folder that I could navigate in order to find files, instead of having to use the file manager.  In Ubuntu, there is a gnome-panel applet called "menu-file-browser-applet" which works well enough for me, but lacks polish and integration.  For example, selecting preferences from the context menu opens a text config file (.mfbarc) in gedit, rather than a preferences dialog, the background of the menu is fixed as opaque, and the menu name(s) actually don't line up with the existing menu bar.  

As this applet provides basic functionality, I would nominate it for integration into Hardy, if possible.  Here's a link to a page with more information: [http://code.google.com/p/gnome-menu-file-browser-applet/]("http://code.google.com/p/gnome-menu-file-browser-applet/")  The technical aspects of this is beyond me, but I think having this applet as a regular package or integrated by default would be great.

---

### Post by 23meg on 2007-11-03
I've filed a needs-packaging bug:

[https://bugs.launchpad.net/ubuntu/+bug/159765](https://bugs.launchpad.net/ubuntu/+bug/159765)

---

### Post by rytmisk on 2007-11-06
I tried this - installed it from the .deb package from the google project site and it worked fine. Bit if I try to change the directory (I do not use my home directory for anything really) I can't figure out how. If I right click on the edge of the applet and press "Preferences" a box saying "use Gconf for now" pops up. And then I open gconf-editor and try to find the right place to change settings, but fail miserably... 

Help anyone?
Ketil

---

### Post by 23meg on 2007-11-06
/apps/panel/applets/applet_x, where x is the applet number it has on your system.

---

### Post by rytmisk on 2007-11-06
Thanks!!

---

