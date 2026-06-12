---
title: "How to patch VMware Player 3.1.5 for 32bits machine with new Kernel"
date: 2013-03-07
forum: Virtualisation
---

### Post by WhiteHatGuy on 2013-03-07
Hi


Sorry for my spelling and grammar errors, english is not my native launguage. Also I didnt know where to ask on this forum. I thought virtualization was the right place.


I need to run VMware-Player-3.1.5-491717.i386 in lubuntu. It has to be that version only, cause my motherboard architecture is 32bits. Thats why I cant use newer versions of vmware player.


I download this patch: vmware workstation 7.1.5 / player 3.1.5 fix for linux 3.2+ (patch by Ariel), I extracted and put in in my home folder.


From this website:


[http://weltall.heliohost.org/wordpress/2012/01/26/vmware-workstation-8-0-2-player-4-0-2-fix-for-linux-kernel-3-2-and-3-3/](http://weltall.heliohost.org/wordpress/2012/01/26/vmware-workstation-8-0-2-player-4-0-2-fix-for-linux-kernel-3-2-and-3-3/)


My steps:


1) Ok, so I already install VMware-Player-3.1.5-491717.i386


2) If I start VMware-Player-3.1.5-491717.i386 I get this error message:


VMware Kernel Module Updater, before you can run VMWare, several modules must be compiled and loaded into the running kernel.


3) Ok so time to use the patch


4) I put on terminal this commands:


a) sudo apt-get install build-essential linux-headers-`uname -r` 


b) chmod +x VMware-Player-3.1.5-491717.i386.bundle 
     
     sudo ./VMware-Player-3.1.5-491717.i386.bundle 


c) sudo apt-get install patch 


d) sudo ./patch-modules_3.2.0.sh 


5) It finish the hole process succesfully and it patch it. But when I try to run vmware player, I still get the same error. Before with old kernel it worked properly and I was able to run it with no problems. But with new Lubuntu kernel, now I get the error message, and wont get away.
(VMware Kernel Module Updater, before you can run VMWare, several modules must be compiled and loaded into the running kernel)




6) I noticed that the patch I download has 2 files:


a) patch-modules_3.2.0.sh


b) vmware-715-kernel32.patch


I am able to run patch-modules_3.2.0.sh properly, and I am able to install it succesfully, but I dont know how to install or run vmware-715-kernel32.patch.


I getting the feeling that, this is why I am getting the errors message, because I havent install properly the vmware-715-kernel32.patch






Any ideas of what command I need to run in the terminal in order to run vmware-715-kernel32.patch, and been able to patch the kernel succesfully?


Thanks

---

