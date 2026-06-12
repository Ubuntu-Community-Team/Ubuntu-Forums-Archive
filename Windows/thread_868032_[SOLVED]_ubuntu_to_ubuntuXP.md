---
title: "[SOLVED] ubuntu to ubuntu/XP"
date: 2008-07-23
forum: Windows
---

### Post by AOZ on 2008-07-23
I recently went from my ubuntu devoted machien to a dual boot with XP so i could use some software that wine couldnt handle. Anyways now im setup and all but i can't get a network connection when im using winXP or sound. So im pretty sure this is because the windows partition has no idea of the drivers i already have for my hardware. I've been looking high and low for days to find the drivers for my hardware but i can't find it anywhere. I use a Toshiba Tecra A9 laptop. Also im able to transfer files etc. from the linux partition when im using ubuntu but not when im using windows, why is this?
Thanks in advance for any help

---

### Post by neurostu on 2008-07-23
Did you reinstall XP from an XP cd or did you use recovery cds? If you did the XP cd chances are it didn't come with the drivers for your hardware... to get the drivers:
 go to Toshiba's website and search for the drivers there, download them, then install them.



As far as accessing the Ubuntu HDD in XP: windows cannot read ext2 natively, so you need to install a program to help you do that:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by DGortze380 on 2008-07-23
> **AOZ said:**
> I recently went from my ubuntu devoted machien to a dual boot with XP so i could use some software that wine couldnt handle. Anyways now im setup and all but i can't get a network connection when im using winXP or sound. So im pretty sure this is because the windows partition has no idea of the drivers i already have for my hardware. I've been looking high and low for days to find the drivers for my hardware but i can't find it anywhere. I use a Toshiba Tecra A9 laptop. Also im able to transfer files etc. from the linux partition when im using ubuntu but not when im using windows, why is this?
Thanks in advance for any help

You need to add ext3 support to windows to 'transfer' files, or use a shared partition (NTFS or FAT32). You need windows drivers for your laptop, the ubuntu drivers won't work. Try to download them from toshiba's site.

---

### Post by Het Irv on 2008-07-23
Toshiba doesn't have them on their site?
If not you could go to the Intel site if you have an Intel board.

As for the transefering of files, I know it is because Windows cannot read ext3 by default, but I don't know how to get it to read.

---

### Post by northern lights on 2008-07-23
While Ubuntu can read from and write to ntfs, the opposite is not the case. Out of the box, Windows will not read ext3.

There are however a few readers out there. For instance, check out [DiskInternals]("http://www.diskinternals.com/linux-reader/")

---

### Post by era86 on 2008-07-23
Usually you want to make the /home partition a FAT32 so both Windows and Ubuntu can read it (just for future reference). ;)

Toshiba should have the drivers available on their website for WinXP.  Just use a different comp to dload them if you don't get internet.

---

### Post by jamesrfla on 2008-07-23
Windows isn't able to transfer files from a NTFS partitions to a EXT3 partition. You can view the partition in computer management but not transfer files unless you are running Ubuntu. For the drivers try Toshiba's web site.

---

### Post by overdrank on 2008-07-23
Since this post is mostly about windows, Moved :)

---

### Post by Ptero-4 on 2008-07-23
Using fat32 is a bad idea since it doesn't retain premission information, hence breaking the configs saved to the user's home folders.
Also you need to install Ext2-IFS (opensource app) to have r/w access to your ext3 partition.

---

### Post by Themaister on 2008-07-23
I dual boot Arch with Windows (XP and Vista, which effectively makes it a triple boot, hhaha)

My / partition is quite limited, I use almost all my storage (music/video, etc) at a data partition NTFS, so both linux and windows can read it flawlessly =)

---

