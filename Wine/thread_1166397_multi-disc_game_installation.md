---
title: "multi-disc game installation"
date: 2009-05-21
forum: Wine
---

### Post by goostmaster on 2009-05-21
I am trying to install W40k: Dawn of War on my computer. there are 4 discs, and i believe wine installs it by unpacking the .CAB files (labeled DawnOfWar1, DawnOfWar2, DawnOfWar3, DawnOfWar4) on each disc and copying the unpacked files.   First things first, I pop in the CD, go to the terminal and enter:   wine /home/goosty/.wine/dosdevices/D:/DawnOfWar.exe  which begins the installation process. After it finishes unpacking DawnOfWar1, it asks me to switch out disks. I open up a second terminal and enter:  wine eject -a  which ejects the disk. I put in the new disk, close the drive, and once it mounts, press the retry button, which continues the installation. A few seconds later it crashes, stating that a fatal error has occurred, and that it did not even begin to unpack DawnOfWar2. Does anybody know what I'm doing wrong?

---

### Post by KhaaL on 2009-05-21
sounds weird, could you paste the contents from the console upon the crash?

---

### Post by goostmaster on 2009-05-21
oh sorry, i was unclear. the installer crashes, i.e. it stops working and immediately quits, stating that a fatal error has occured.

---

