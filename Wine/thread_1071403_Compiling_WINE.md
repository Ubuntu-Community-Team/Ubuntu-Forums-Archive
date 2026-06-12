---
title: "Compiling WINE?"
date: 2009-02-16
forum: Wine
---

### Post by alex.rayu on 2009-02-16
I have compiled wine a number of times, but I have a question concerning it.

When I compile wine, it evidently creates files in the system folders skipping the deb database. So, later, if I remove wine, or install a version from the debs, do these files get overwritten? Or do they hang in there and clutter the system folder?

---

### Post by Dizzle7677 on 2009-02-16
Depends on where you put them in the first place with the prefix & exec-prefix in your configure settings. The default is to install them to /usr/local (ie. /usr/local/bin/wine) for source configures/installs. Most likely it's put in /usr (ie./usr/bin/wine)for debs. If you do a 'make uninstall' from where you compiled it you wouldn't have to worry about the system getting confused as it were. 'which wine' is a handy command...

---

### Post by alex.rayu on 2009-02-17
Thank you. So, it IS possible for them to be multiplied. I almost always delete the sources after compiling.

---

