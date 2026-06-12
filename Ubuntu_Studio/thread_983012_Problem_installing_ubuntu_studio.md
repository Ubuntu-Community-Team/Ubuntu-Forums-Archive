---
title: "Problem installing ubuntu studio"
date: 2008-11-15
forum: Ubuntu Studio
---

### Post by awaycaboose on 2008-11-15
Hi

I'm trying to install ubuntu studio on my laptop along side standard ubuntu 8.10 everything seemed to go ok and ubuntu boots up just fine however when I boot ubuntu studio there is no GUI only a command line to enter username and password. Doing this gives access to the system but still no GUI.

Any help would be greatly appreciated as I'm still very new to the whole ubuntu world but am enjoying it greatly so far and will enjoy it even more if I can start to use my laptop for music production again :).

---

### Post by Chusho on 2008-11-30
I have the same problem too,i would really appreciate it if someone help us.

---

### Post by awaycaboose on 2008-11-30
Hey bud, I've since discovered this [http://linux.about.com/od/linux101/l/blnewbie4_3_1.htm]("http://linux.about.com/od/linux101/l/blnewbie4_3_1.htm"). Not sure if it'll solve your problem with studio as I did a fresh install of Hardy Heron and installed all of the music production software which I wanted. So far it seems to all be running fine and from what I've read studio is essentialy the same setup in one easy to install package.

Hope this helps :)

---

### Post by markbuntu on 2008-11-30
If you are using the nvidia or ati drivers for your graphics card the ubuntustudio linux-rt kernel will fail to install them properly and as a consequence the x server will fail to start when booting ito the rt kernel. 

The best thing you can do if this happens to you is to reboot into failsafe mode and reconfigure x to use the VESA driver. This is a semi-automatic process.

 If you can get to the login screen, choose Gnome-failsafe in the change session option. If you are using the ati fglrx driver you can reinstall it and you should be OK. 

be sure to select the linux-restricted-modules-rt when selecting the packages for the rt kernel. If you are using nvidia drivers, they will fail without this package.

If you are about to install UbutuStudio, be sure to set Desktop Visual Effects to none before installing the rt kernel. You can do this by right clicking on the screen and selecting the appropriate options. This will prevent compiz from failing with the VESA drivers.

---

