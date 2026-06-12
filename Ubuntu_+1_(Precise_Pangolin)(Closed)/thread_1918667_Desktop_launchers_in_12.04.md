---
title: "Desktop launchers in 12.04?"
date: 2012-02-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by siriusbg on 2012-02-01
Hi, I just wanted to ask whether there'll be a possibility to place launchers on the desktop. I really miss this option in 11.10 and as far as I have read there was no discussion concerning this matter. Thanks!

---

### Post by Hreinsi on 2012-02-01
> **siriusbg said:**
> Hi, I just wanted to ask whether there'll be a possibility to place launchers on the desktop. I really miss this option in 11.10 and as far as I have read there was no discussion concerning this matter. Thanks!

Can you drag them from Dash to desktop works for me in 3D

---

### Post by mc4man on 2012-02-01
> **siriusbg said:**
> Hi, I just wanted to ask whether there'll be a possibility to place launchers on the desktop. I really miss this option in 11.10 and as far as I have read there was no discussion concerning this matter. Thanks!
Pretty much discussed ect. when it first disappeared (the create desktop launcher

Do a site search, there are numerous threads concerning using previous type methods or just find an example on how to create your own - a launcher is just a .desktop file, what it does depends on how you structure it

here's one thread
[http://ubuntuforums.org/showthread.php?t=1815051](http://ubuntuforums.org/showthread.php?t=1815051)

---

### Post by Hreinsi on 2012-02-01
I used this in 11.10 but in  12.04 I can drag from dash but newer use desktop icons.

[http://shuffleos.com/3708/how-to-create-desktop-launchers-right-click-context-menu-ubuntu-11-10/](http://shuffleos.com/3708/how-to-create-desktop-launchers-right-click-context-menu-ubuntu-11-10/)

---

### Post by TerryNewton on 2012-02-01
On my 12.04 test system I use the gnome-desktop-item-edit utility from the gnome-panel package, run using this CreateLauncher script put in the ~/.gnome2/nautilus-scripts directory...

```

#!/bin/bash
gnome-desktop-item-edit --create-new $(pwd) &

```

Once in place and made executable, Scripts|CreateLauncher then it brings up a dialog very similar to Gnome 2 where the icon name, command, icon, etc can be specified. Of course desktop icons have to be enabled, if not gnome-tweak-tool can fix that. If you can right-click the desktop and make a file then icons are enabled.

---

### Post by EgoGratis on 2012-02-06
I agree. Decision to retire this functionality from Gnome 3 was premature and plain wrong. Some time has passed now and i didn't get use to not have this functionality on my desktop OS.

I think not having "desktop manager" as first class citizen as a part of desktop experience is wrong. Nobody does nothing anymore AFAIK to improve the way desktop is managed in Gnome? To use it just for wallpaper is wrong and we (users) should not be treated in this way. We don't deserve it!

I think not just desktop launchers but the whole desktop manager is still needed for desktop usage an i hope developers come to their senses and make some progress in this area too in the future! It's like having something that is plain wrong and doing nothing about it! I will say it again: WRONG!

---

### Post by EgoGratis on 2012-02-06
XFCE (4.10) developers are making some progress in desktop management and could it be used by Ubuntu (Gnome) in the future too:

[http://wiki.xfce.org/releng/4.10/roadmap/thunar#replace_xfdesktop_by_adding_a_thunarx_interface_for_desktop_extensions](http://wiki.xfce.org/releng/4.10/roadmap/thunar#replace_xfdesktop_by_adding_a_thunarx_interface_for_desktop_extensions)

Could the plugin be used with Nautilus too? Should Ubuntu use XFCE desktop manager in the future because Gnome developers think of the desktop as just wallpaper stand?

---

