---
title: "Physical location of menu bar launchers"
date: 2008-09-09
forum: Security
---

### Post by summersab on 2008-09-09
So, I have an idea to integrate the Menu Bar into the Cario Dock using sub menus. However, in order to do so, I really need to know the ins and outs of the Menu Bar that is standard with Ubuntu. You know - the Applications, Places, System bar. Where are those icons mapped from? Now, I know that there is a folder (/usr/share/applications) that stores all icons for GUI applications, and the code for these launchers specify where the icons are to go in the Menu Bar. However, what program makes this magic happen? For instance, when a new package is installed, the icon appears in the Menu Bar appropriately. What code makes this happen and how? I need to know this in order to make a Cario Dock menu bar that dynamically updates to fit the current set of installed programs. Thanks!

---

### Post by koenn on 2008-09-09
it's probably a gnome feature, so you might want to read the gnome manuals : [http://library.gnome.org/admin/](http://library.gnome.org/admin/)

there's also an installable program called 'menu' that does something quite like what you describe. maybe investigate that as well.

---

