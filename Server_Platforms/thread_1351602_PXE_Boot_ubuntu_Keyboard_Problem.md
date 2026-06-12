---
title: "PXE Boot ubuntu Keyboard Problem"
date: 2009-12-10
forum: Server Platforms
---

### Post by linuxfan5246 on 2009-12-10
Hi I've set up a pxe boot server on Ubuntu 8.04 LTS on one of my client the boot menu appears but the keyboard doesn't respond here the things i've tried. my client PC is a dimension 5150

1.Updated to Latest BIOS A07
2.Tried Different Keyboard (wired and Wireless)
3.Tried pxe boot on different Machine Works fine (With both wired and wireless keyboard) 
4.Tried different usb keyboards system only supports usb 
5.tried different usb ports front and back
6.tried to turn on legacy mode in bios for keybaord to work (but it doesn't have the option to turn legacy mode on)
7.contacted dell they can't do anything thing about it

also i tried windows deployment services and that works fine with keyboard. 

can Someone please help me here i really want to get pxe booting working on my dimension 5150. i can't figure out the problem

i used this guide buy the way

[https://help.ubuntu.com/community/PXEInstallMultiDistro](https://help.ubuntu.com/community/PXEInstallMultiDistro)

---

### Post by linuxfan5246 on 2009-12-10
Bump

---

### Post by linuxfan5246 on 2009-12-12
Bump

can someone plase help me

---

### Post by tauren on 2010-03-03
I wish I could help, but I'm in the same boat.  When I boot the server from CD-ROM or hard drive, the keyboard works fine.  When I boot from PXE, the keyboard does nothing. There is no PS2 port, so I'm using a USB keyboard (tried both wired and wireless as well).  This system has Ubuntu 9.10 x86_64 server loaded on it and PXE boot loads the same.  

Hardware:
    SuperMicro Superserver 6015TW-T
    SuperMicro Super X7DWT serverboard
    Dual quad-core Xeon 5405 2GHz system, 64 bit, VT support
    32GB RAM
    Mirrored 300GB SATA

---

### Post by Sam Lars on 2011-11-28
I had this same issue. Unfortunately, I have not been able to track down a way to get the keyboard to work.
However, I did come up with a workaround.
I found the file /var/lib/tftpboot/pxelinux.cfg/default, which gives the options for the boot menu that will be loaded on PXE boot. There will be a timeout value in there, I assume 0 means no timeout. I just set it to 5, and it automatically selected the install option. If you need a different option, I think that you can edit the files referenced it the config file (menu.cfg?) or maybe the prompt option (not sure what that does) to get the menu to work the way you want.
Also, when it automatically selected the first option, it just sat there. I assumed something hadn't worked right, but I just left it. After maybe 5 minutes or more, it suddenly went into the install, and my keyboard worked again for that part.

Along other lines, kickstart could be useful in automating parts of the installation, should your keyboard not work there either.
I've been using this guide: [https://help.ubuntu.com/community/PXEInstallServer](https://help.ubuntu.com/community/PXEInstallServer)

---

