---
title: "Installing Program on External Harddisk"
date: 2011-02-06
forum: Wine
---

### Post by Krabby.Linux on 2011-02-06
Hey,
I have a Problem. My Ubuntu Partition has only 1GB of free Space left. Now I want to install World of Warcraft using WINE. The Problem here is that the Downloader of WoW starts perfectly but i cant chose the Path were to download the game data ... The Partition is full and the Installer is not able do download anymore. I have an external Harddisk with 200GB of Free Space remaining. How do I install on that Disk?

I tried to Configure Wine. There is an option where I can add drives. What do I have to do so WINE is using that External Harddisk? Or is it even possible to do this ?

Thanks!!!

---

### Post by dino99 on 2011-02-06
few solutions:

- make room on your actual /home by removing garbage
- use gparted to widen /home (if non active only, so boot on partedmagic or so)
- use wineprefix, playonlinux to install a bottleneck on external drive

---

### Post by Krabby.Linux on 2011-02-06
Installed Q4Wine. There i have chosen to create a new prefix on my External hard disk. But when I am Starting the Installer he is asking me what prefix i want to use. I chose the new one. The Process starts and ends in 2-3 seconds without any messages or errors.

PS The same if i chose default prefix

---

### Post by Tweak42 on 2011-02-08
I run wow off a external usb hard disk.  I linked the wow game directory into my .wine/drive_c directory and it works as if the game is located there.

You can link directories via command line but I'm to lazy to figure out the syntax. The gui way to do this is to use nautilus.  Hit F3 to open extra pane. Navigate one pane to your .wine directory, the other to your external drive.  Now hold CTRL-SHIFT and click/drag a folder from your external drive to your .wine directory and drop. You should have a small CHAIN LINK icon appear over the folder icon when you do this.  The folder icon create should have the an redirection arrow overlaid on it.  Now the folder should behave just like it was in the .wine directory.

The advantage here is you can easily nuke your .wine folder to "reinstall" and it only breaks the link but leaves the wow folder wherever it's located.

---

