---
title: "Linuxmintdebian"
date: 2011-01-15
forum: The Cafe
---

### Post by Timmer1240 on 2011-01-15
Im trying to install linuxmint debian in virtualbox but the installer ALWAYS stops when copying opt/firefox/limozjs.so anyone know what I could be doing wrong?I checked the md5 of the iso and its ok Im getting frustrated with it!Same thing happened when I tryed to install the new crunchbang statler and linux squeeze Im having bad luck with debian!

---

### Post by Timmer1240 on 2011-01-15
I got it figured out learned a lessen in partitioning and didnt have the i/o cache on the host enabled now I just got to figure out how to install the guest additions now!If a person never has problems you never learn anything!

---

### Post by kaldor on 2011-01-15
For the guest additions, boot up your Mint Debian VM and when loaded, click machine > install guest additions.

I can't remember the exact location, but you'll figure it out; it's on one of the VM's dropdown menus. 

A .iso will mount as a software CD on your LMDE desktop. Browse the folder, and run in terminal the one that matches your machine.

---

### Post by Tibuda on 2011-01-15
> **kaldor said:**
> For the guest additions, boot up your Mint Debian VM and when loaded, click machine > install guest additions.

I can't remember the exact location, but you'll figure it out; it's on one of the VM's dropdown menus. 

A .iso will mount as a software CD on your LMDE desktop. Browse the folder, and run in terminal the one that matches your machine.

I guess you should run the guest additions installer as root. I cant' remember.

---

### Post by Timmer1240 on 2011-01-15
Yes I had to go into filesystem media cdrom open in terminal and enter sudo sh ./VBoxLinuxAdditions-x86.run enter my password and MAGIC!Im still not to good with the terminal but its a must in some instances! And Im really liking this distro might have to jump to this seems really nice!

---

