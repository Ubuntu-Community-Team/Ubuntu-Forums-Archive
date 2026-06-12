---
title: "Can't uninstall wine"
date: 2010-07-17
forum: Wine
---

### Post by ucal on 2010-07-17
I originally installed 1.2rc4 from source, then wanted to upgrade through the repos to 1.2 stable (which i think is technically 1.2rc7?).  I couldn't initially figure out how to uninstall wine when it was installed from source, so I just installed from the repos without uninstalling the previous version (bad idea, I know).  Now, even though my version number says 1.2rc7, I can't uninstall any of my programs installed previously, though they do launch.  If I attempt to uninstall wine from the repos, the menu entries persist.  Even stranger, if I delete the .wine folder, and then try to configure wine, it rebuilds the folder.  This is when wine is technically uninstalled.  

Honestly, I just want to start over with a blank slate >_>

---

### Post by Weekendpartier on 2010-07-17
**Can't Uninstall Wine**
Have you tried using Synaptic Package Manager under the system menu?  Or you can also try in the applications menu Ubuntu Software Center - both have remove features.  Finally, if you know the command - you could remove it from terminal - - I believe the command is basic like:
sudo apt-get remove wine

I believe these should work in completely removing wine.

---

### Post by ucal on 2010-07-17
> **Weekendpartier said:**
> **Can't Uninstall Wine**
Have you tried using Synaptic Package Manager under the system menu?  Or you can also try in the applications menu Ubuntu Software Center - both have remove features.  Finally, if you know the command - you could remove it from terminal - - I believe the command is basic like:
sudo apt-get remove wine

I believe these should work in completely removing wine.

That's the problem though.  When I run that command, the menu icons persist, and the program seemingly does as well, because deleting the .wine folder causes it to rebuild the folder and then run perfectly.

---

### Post by dino99 on 2010-07-17
look into /usr/share/app*

---

### Post by asdfoo on 2010-07-18
to uninstall from source you just run:  make uninstall

---

