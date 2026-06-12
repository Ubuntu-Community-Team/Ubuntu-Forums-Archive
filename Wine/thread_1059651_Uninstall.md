---
title: "Uninstall"
date: 2009-02-04
forum: Wine
---

### Post by RedSingularity on 2009-02-04
How can i clear the Uninstall area of wine?  It still has the option to remove things like ventrillo and Crysis but i removed them already.  What is the problem?

---

### Post by cogadh on 2009-02-04
Some apps, usually ones that are installed from a MSI instead of an EXE, will leave significant traces behind, like an uninstaller entry. You can get rid of them by manually removing all traces of the app from the Wine registry, then manually deleting any leftover files in the installation directory. 

You could also just delete your entire .wine directory, but that would eliminate any other apps you may have installed. If those apps that are leftover in the unistaller are the only things you had installed, its probably the easiest way to get rid of them.

---

### Post by RedSingularity on 2009-02-04
If i delete the .wine directory will it effect future program installations?  Or will it "remake" itself when i install some new software in wine?

---

### Post by RedSingularity on 2009-02-04
Oh never mind.  It worked!  Thanks a lot!!

---

### Post by cogadh on 2009-02-04
It will automatically recreate itself the next time you run anything in Wine. It is usually best to create it by running the Wine configuration first, rather than having it created when you try to install something (Wine really should be configured before it is used).

EDIT - Ack! Simultaneous post!

---

