---
title: "installing from multiple cds"
date: 2010-08-02
forum: Wine
---

### Post by awesome guy on 2010-08-02
Hello people,

I am trying to install Rome Total War using Crossover. The game comes on 3 cds, which is the problem. I put the first cd in the drive and start the install, but when it asks me to put the second cd in the drive I can't unmount the first cd because it is still in use (by wineserver). I also can't mount the second cd in another place, because the installer doesn't show me an option to load from a different location than the first cd. 

I have tried just ejecting the first disc by pressing the button on my case, but when I put in the second disc it isn't recognized anywhere and I have to reboot (obviously aborting the installation). 

I have also tried to force the unmount with various commands, but it kept saying that it can't unmount because it's busy. I found out wineserver is using it (which I guess has something to do with the installer), so I killed it. I then was able to unmount and mount the second disc, but because I had killed wineserver I was unable to continue the installation. 

Any ideas on how to work around all this? Help would be GREATLY appreciated :D

---

### Post by utnubuuser on 2010-08-02
Go to WineHQ and check if there are any instructions specific to that game...

---

### Post by Sef on 2010-08-02
Moved to WINE forum.

---

### Post by cogadh on 2010-08-03
Open a terminal and use the "wine eject" command to remove the first disk, then you should be able to put in the second disk and it will mount itself. Note that this doesn't always work because of how Ubuntu handles the mounting of disks now. In the past, Ubuntu had an fstab entry for all drives, including CD/DVD drives, which provided a fixed mount point for Wine/Crossover to access. Now Ubuntu's automount process uses a dynamically created mount point based on the disk's label, which sometimes causes problems for multi-disk installs with Wine. You can create your own fstab entry that will correct this problem.

---

### Post by Butthead on 2010-08-03
I don't know if this helps any, but I install all my Windows games in Dolphin.  Put the game disk in, wait until CD/DVD automounts it, then open it up using Dolphin.  Right click on "setup.exe" file, use Wine emulator menu choice to actually run it.  After disk is finished installing game files, go over to left side of Dolphin (where all your drives are listed at) and right click on your CD/DVD drive to "release" and then "eject" it.

Do the same for any subsequent game install disks you need to install.

---

