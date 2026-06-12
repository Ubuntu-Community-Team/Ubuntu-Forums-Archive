---
title: "Ubuntu 18.04 Desktop Dock"
date: 2018-04-08
forum: Ubuntu Development Version
---

### Post by jonesyp on 2018-04-08
I'm adding shortcuts to my desktop and have done this by firstly installing gnome-panel with:

```
sudo apt-get install --no-install-recommends gnome-panel
```

Then running in terminal:

```
gnome-desktop-item-edit ~/Desktop/ --create-new

```

This all works fine and the shortcut appears on my desktop with the chosen Icon.  The problem is that when I run the application the icon I choose does not appear in the launcher.  See image below:

[IMG]https://s14.postimg.org/p92yy4ee9/Fuse.png[/IMG]

How can I make the desktop Icon appear in the Dock?

Thanks
Peter

---

### Post by vanadium on 2018-04-10
Desktop launchers are not really supported anymore. If you use this icon a lot, you would rather add it permanently to the dock at the left. Other frequently used applications will readily appear in the software overview you obtain with the grid icon or with the hotkey Win+a, and thus be two actions away.

If you prefer differently, then indeed you'll either need to heavily customize the system, or move to a desktop such as mate or xfce that still do support launchers on the desktop. Consider that this approach has its drawbacks: these icons tend to be hidden behind your work. They may be less accessible than a click on the program grid icon, and for sure require you to disrupt your current work space in order to access them.

---

### Post by monkeybrain20122 on 2018-04-10
> **jonesyp said:**
> 
How can I make the desktop Icon appear in the Dock?



Put you .desktop file in ~/.local/share/applications. Then you'll find it in the dash, ten right click to add to favourites (or something like that..)

---

