---
title: "How Do You Get the Wacom Tablet Controls (Calibration, Buttons, etc.)?"
date: 2015-02-12
forum: Ubuntu Studio
---

### Post by info29 on 2015-02-12
Hi Everyone...I'm completely new here. I'm completely new to Linux as  well, so I'm probably going to have a lot of questions (of course I'll  be searching the forums first before I ask).

Anyway, my first  question is, is there a way to get the Wacom Tablet controls that are  found in the regular Ubuntu 14.10 Control Center to the Ubuntu Studio  settings? It seems like those controls are much more fitting to be in  the Studio as well.

[ATTACH=CONFIG]259943[/ATTACH]

I've been going back and forth between the  regular Ubuntu distro and then Studio. On my machine, Studio runs a bit  faster and I like majority of the applications included as I do graphic  design on the side. However, I do like the Wacom control panel of the  regular distro, because I can't find a way to calibrate my Wacom tablet  inside Ubuntu Studio.

So is there a away to get that in the studio? And any reason why Studio does not have that?

Many thanks everyone.

-brian

---

### Post by CrocoDuck on 2015-02-13
Hi! Not into graphics and I am not currently using ubuntu at moment, so maybe I won't be of much help. I suspect that app to be part of the GNOME desktop applets/tools. It should be available in software center, you just have to discover the actual name of the package and install it. Maybe [this]("http://libregraphicsworld.org/blog/entry/peter-hutterer-on-the-gnome-applet-for-wacom-tablets") can help. Keep an eye on the dependencies you will pull in installing the package, you may wish to avoid to install too many dependencies from other DEs to maintain the system responsive. I suspect that Studio does not have it by default just because it uses XFCE instead of UNITY, which is a graphical shell for GNOME. The default graphical tools for each DE are included and probably XFCE lacks a graphical configuration tool... but you can install software based on other DEs as well if you wish... or go the manual way editing conf files.

---

### Post by bhilmers2 on 2015-02-13
CrocoDuck has it right. You can install the **unity-control-center** package from the repository. This should be the first entry when searching "wacom" in Ubuntu Software Cetner. Alternatively, on the command line:
```
sudo apt-get install unity-control-center
```
Now keep in mind, Ubuntu Studio will not make a menu item for this. You have just installed an alternative to Settings Manager. You can launch the Unity Settings Manager from the terminal my typing **unity-control-center** (or press Alt+F2 and type it), look for Wacom Tablet, open it and adjust the settings your desire. If you think you will open this control panel often you can create a entry in the main menu or create a launcher (we can help with that if you can't figure it out).

Now as to why this isn't already in Ubuntu Studio, a distro aimed at creative types, well, that's a little more complicated. Right now Ubuntu Studio has kind of an "all things to all people" approach, but in practice that doesn't work very well because of massive fragmentation in the Linux ecosystem. However, the distro gets better with every release, so I stick with it.


*Edit:* If you install from the software center, be sure to look over the optional packages carefully. Also, I think this package changes some of the panel widgets because it's part of the Unity DE.

---

### Post by info29 on 2015-02-16
Thank you both so very much. I've been playing around between the regular distro and the Studio. But like I said the only thing missing for me was the wacom settings. Now that it's in there thanks largely in part to you both. I believe I'll be using the Studio for now on. I really do hope that Ubuntu Studio get's it's own Wacom settings with calibration and button reassignments. I mean it has a very strong midi and audio support for sure, but a distro aimed at the creative professionals without strong wacom support, just doesn't make sense. 

Again, many-many thanks for the help.

---

