---
title: "Running Adobe from Ubuntu but from a windows partiton?"
date: 2009-08-04
forum: Wine
---

### Post by MasterNetra on 2009-08-04
I was wondering if anyone knew a way to get it to where wine can launch a Adobe product, such as dreamweaver from a windows partition. I mean I am able to add/edit/remove files from the partition. Why not get wine to run windows stuff from it?

---

### Post by doas777 on 2009-08-04
prolly won't work.
adobe apps write extensively to the windows registery. Wine has it's own registery, so you need to install the apps in wine. if they are already installed in windows, you will not be able to run them, except in windows, unless you also install them into wine (at which point you now have two full instances of the same program installed at the same time.)

would work fine with a stand-alone application, but photoshop and dreamweaver (yuck) will want to get their dirty litte fingers in the os itself.

---

### Post by theGlitch on 2009-08-04
You could try mapping a virtual machine's hard drive to your windows partition. Just a theory though, haven't tried it. If you do try, I'd suggest VirtualBox.

---

### Post by ajgreeny on 2009-08-04
No idea about adobe products, but you can certainly run the executables of some applications already installed in windows using wine, either by navigating to the windows folder in nautilus and double clicking on the program.exe file or by right clicking and choosing "Open with wine".  I have done it in the past with small apps such as IrfanView, a terrific freeware picture viewer and editor which I used in XP.  A lot of other applications would simply refuse to open.

---

### Post by alex.rayu on 2009-08-04
Will not work. There are settings and security codes in the Windows partition and registry. And wine will try to use its own registry not the one from the Windows partition.

---

