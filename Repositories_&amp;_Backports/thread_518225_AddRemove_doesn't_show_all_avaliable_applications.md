---
title: "Add\Remove doesn't show all avaliable applications"
date: 2007-08-05
forum: Repositories &amp; Backports
---

### Post by TuxIsCute on 2007-08-05
When using Add\Remove, not all applications available in archive.Ubuntu.com are show for installation.  I was looking for DopeWars and DGen.  Both of these applications show up in Synaptic Package Manager and I can install them from there.  However, this doesn't get them to show in the correct places in the main menu.  They should be shown in Games.  Why don't these programs show up in the regular Add\Remove!?

---

### Post by 2rB on 2007-08-05
Probably because its not made an Ubuntu-version of them.
If you see in synaptic, they dont have the Ubunto-logo.

Dont know if this is the correct answer, as Im quite new to Linux / Ubuntu - but it seems logical to me.

So you probably have to make the shortcut manualy.

---

### Post by AlexenderReez on 2007-08-05
> **TuxIsCute said:**
> When using Add\Remove, not all applications available in archive.Ubuntu.com are show for installation.  I was looking for DopeWars and DGen.  Both of these applications show up in Synaptic Package Manager and I can install them from there.  However, this doesn't get them to show in the correct places in the main menu.  They should be shown in Games.  Why don't these programs show up in the regular Add\Remove!?

there is 'show' kind of option there....it won't appears any universal software unless you change that to all available application view.

some software doesn't give error in gnome menu,you need manually add using edit menu or ---> 

> sudo gedit /usr/share/applications/<application name>

> [Desktop Entry]
Name=<name>
Comment=<description >
Exec=<command to launch>
Icon= its icon
Terminal=false
Type=Application
Categories=Application;System;

---

### Post by UbuWu on 2007-08-05
Most likely because they don't have a .desktop file. This is the file that describes the menu item. The list of programs for add/remove is made basically by scanning all available packages for .desktop files.

Btw. if this is the case you should file a bug in launchpad about these packages not having a .desktop file. You can probably even manage yourself to write one for it and add it to the bug report. For examples look in /usr/share/applications on your system.

---

