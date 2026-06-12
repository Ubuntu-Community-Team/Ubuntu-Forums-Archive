---
title: "File Sharing between multiple OS"
date: 2012-05-07
forum: Tutorials
---

### Post by rahuldroy on 2012-05-07
A lot of people tend to dual (sometimes triple or more) boot their systems. I personally dual boot windows 7 for University purposes and LUbuntu for everything else. I sometimes triple boot just to test a new OS out...

This raises a problem when it comes to file sharing between the OSes. I want to share with you how I have addressed this -

- **Create a separate pMartition just for Data**
[INDENT]This partition is used just for all my data, including dropbox, documents, pictures etc.
I gave it UUID DATA
File System is NTFS as this is supported by Windows, Linux, Mac Osx, BSD etc.
It is highly recommended this be done before any OS is installed. My Current set-up is as follows - 
Windows Partition (43GB) *
Ubuntu Partition (76GB) *
DATA Partition(107GB)
Swap (2GB)
Test OS Partition (21GB)

* - My primary OSes 
This is my partition set-up, this doesn't mean that you should have exactly the same set-up. You should have a set-up that suits you. You can do this in Gparted live CD or most live CD distributions.[/INDENT]

- **Linking local directories with folders in the partition **(example for Desktop folder only, applicable to most other folders)

**Ubuntu (Unity with Nautilus)**-
[INDENT]Make sure your DATA  partition is mounted automatically at start-up. This can be done by ntfs-config
[INDENT]sudo nano ~/.config/user-dirs.dirs
[/INDENT]Change the paths there. This is how I have set-up my desktop link - 
[INDENT]XDG_DESKTOP_DIR="/media/DATA/Desktop"
[/INDENT][/INDENT]
**Lubuntu (LXDE with PCManFM)**- 
[INDENT]Slighly different to ubuntu LXDE uses pcmanfm instead of Nautilus. The previous method didn't work unfortunately.
Delete the Desktop folder 
Go to terminal and type in - 
[INDENT]ln -s /media/DATA/Desktop Desktop[/INDENT]
		the previous command creates a symbolic link between the Desktop folder in your home directory with the desktop folder inside your data partition.[/INDENT]

**Windows** - 
[INDENT]Open windows explorer and navigate to Desktop Folder.
Right click the desktop folder
Click on the location tab
Click Move and select target folder
Click apply[/INDENT]

---

