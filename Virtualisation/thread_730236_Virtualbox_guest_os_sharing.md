---
title: "Virtualbox guest os sharing"
date: 2008-03-20
forum: Virtualisation
---

### Post by coninsan on 2008-03-20
Hi

Ive just installed winxp in virtualbox, but now comes the aperantly tricky part.
i need to transfer files from my host os, ubuntu gutsy, to winxp so i can install some programs i need.
But i can not get the shared folders to work, i cant get ANY files from ubuntu to Xp as it is now.
Does anyone know how to get it to work?

---

### Post by sumguy231 on 2008-03-20
Have you installed the Virtualbox guest additions on Windows XP? You'll need them to set up shared folders. Once you have them installed, they should probably just work.

---

### Post by coninsan on 2008-03-20
ive just installed the adds you mentioned, but i can not find the shared folders in xp. 
i am getting a bit frustrated about this right now :(

---

### Post by bodhi.zazen on 2008-03-20
Or use a network file share : samba, scp, ftp, http, nfs

Or put the files on a USB drive and mount the USB on windows.

Put the file into an .iso and mount the .iso as a CD on windows.

---

### Post by cybergalvez on 2008-03-20
> **coninsan said:**
> ive just installed the adds you mentioned, but i can not find the shared folders in xp. 
i am getting a bit frustrated about this right now :(

in the lower right hand corner of your virtualbox you will find some icons, one looks like a folder icon, right click on that icon, it will bring up a folder sharing dialog box.  Select what folders host folders you want to share, then within XP you mount them as windows shares, //VBOXSRV/sharname

Jose

---

### Post by coninsan on 2008-03-20
i would like to mount my external drive as a usb in windows, but i have no idea howto... :(

---

### Post by markharding557 on 2008-03-20
> **coninsan said:**
> ive just installed the adds you mentioned, but i can not find the shared folders in xp. 
i am getting a bit frustrated about this right now :(

1/in vb make sure you have enabled shared folders and selected the folders you want to share.
2/in winxp open mycomputer_tools_map networkdrive,a box will come up,set the drive letter you want and browse for your shared folder it should be in virtualbox shared folders click ok and you should see your shared folder as a network drive in mycomputer

---

### Post by coninsan on 2008-03-20
seriously i dont not know how to get to mycomputer_tools_map networkdrive, my winxp is in danish and it is s***

so i am lost right now...

---

### Post by markharding557 on 2008-03-20
you can change language/locale in control panel_regional and language options it has a globe type icon.
never given windows advice before on here

---

