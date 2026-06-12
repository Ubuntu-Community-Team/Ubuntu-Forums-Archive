---
title: "virtualization integration"
date: 2007-05-26
forum: Windows
---

### Post by corvax on 2007-05-26
Not sure if this is the proper place for this  but......Id like to see somthing  using zen or kqemu or any free open  virtualization implimentations  in ubuntu that would let you install xp vista etc etc and customize it so that any windows apps games etc that  are installed  create a shortcut  in the menu or on desktop or both  (your choice?) in ubuntu and  when clicked on within the linux environment from the desktop etc launches the app/game etc full sceen within xp or vista  in vm  and make running windows apps from he linux desktop seem seemless. What im talking about is integration here. 
what do you guys think?

---

### Post by Cyvros on 2007-05-29
You can do that already with [Wine](http://www.winehq.org/) (should be in the repos) - in GNOME and Xfce (not sure about KDE), it adds shortcuts for Windows apps you install with it directly into the Applications menu. Also helpful if you're dual-booting and need to boot a Windows-installed app from inside a Linux distro.

VirtualBox (currently just normal virtualisation) is supposed to have a similar feature in addition to general virtual machines at some point in the future.

---

### Post by 3rdalbum on 2007-05-30
Wine now supports the Portland Project and the Freedesktop standards for menus, so KDE adds a "Wine" menu much the same as XFCE and Gnome.

There would be fairly significant technical barriers to doing this with virtualisation, and I'm a novice in this so I'm sure there are more problems than what I can see. Basically, if you see this as being a good feature, best learn C and program it yourself.

---

### Post by Cyvros on 2007-05-31
> **3rdalbum said:**
> Wine now supports the Portland Project and the Freedesktop standards for menus, so KDE adds a "Wine" menu much the same as XFCE and Gnome.

There would be fairly significant technical barriers to doing this with virtualisation, and I'm a novice in this so I'm sure there are more problems than what I can see. Basically, if you see this as being a good feature, best learn C and program it yourself.

Nice - it's good to know that they're compatible with the three big DEs.


Even if you're using one of the *box WMs, it's fairly easy to add it to your menu file - I'd assume it'd be just as easy, if not easier, for other WMs like Enlightenment.

---

