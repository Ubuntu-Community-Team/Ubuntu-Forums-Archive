---
title: "Can't uninstall a program"
date: 2011-02-16
forum: Wine
---

### Post by GeoffAk on 2011-02-16
Hello.  I am trying to uninstall "Sonos Desktop Controller" and can't seem to do so.  When I click "Remove" in Add/Remove Programs the screen simply flashes and the program is still there...nothing happens.  Any ideas?

---

### Post by handy on 2011-02-16
It sounds like at least a part of "Sonos Desktop Controller" is still running. If you install htop, you may be able to work out what is running & kill the process, it is worth installing htop for other reasons anyway. ;) 

If all else fails, you could manually uninstall it by going into "~/.wine/drive_c/Program Files/<program folder>" & delete the <program folder> of whatever you want to remove.

You will then have to manually remove the menu listing from Gnome or KDE, whichever desktop you are using.

---

### Post by GeoffAk on 2011-02-16
I installed htop, but didn't see any part of it running.  I removed the directory under "~/.wine/drive_c/Program Files/" and also the GNOME menu listing.  Now when I try to install it again, it runs through the installation and says it completed, but nothing shows up under "Program Files".  It's like it didn't even install.  What should I do from here?

---

### Post by handy on 2011-02-17
What was wrong with your initial installation?

---

### Post by GeoffAk on 2011-02-17
A newer version was released, which made the software obsolete and unable to control my sound system.  It has a built-in upgrader (no need to reinstall), but for some reason this never worked in Wine, so I would always reinstall, but now this doesn't work either.  It's also possible the built-in upgrader created the situation I'm in now :(

---

### Post by handy on 2011-02-17
> **GeoffAk said:**
> A newer version was released, which made the software obsolete and unable to control my sound system.  It has a built-in upgrader (no need to reinstall), but for some reason this never worked in Wine, so I would always reinstall, but now this doesn't work either.  It's also possible the built-in upgrader created the situation I'm in now :(

Hmm. I'm sorry but you need someone who has a good deal more knowledge than I do on this subject. They have a forum over on the Wine site:

[http://forum.winehq.org/](http://forum.winehq.org/)

Perhaps it could provide your quickest solution as I think that your situation is complex.

---

