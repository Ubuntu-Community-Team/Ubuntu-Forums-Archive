---
title: "Oracle VirtualBox"
date: 2012-09-20
forum: Virtualisation
---

### Post by Lucius Ferus on 2012-09-20
For Virtualbox install i'm not understanding very well what's a chroot 64 bit environnment, wich they say is necessary on Linux. I've got a 32 bit system and after reeding the  Ubuntu Debootstrap documentation, i still don't know if it is the correct way for this Virtualbox. Once is mentionned the creation of a 32 bit environment in a 64 bit System, as un example. I'm trying to do the opposite; is it possible? And necessary? My target is to install Backtrack 5.
I'm thankfull for any tip. Cheers.

---

### Post by Cheesemill on 2012-09-20
If you are running a 32-bit system then you can only run 32-bit VM's.

Just download the 32-bit BackTrack .iso file and point your new VM to it.

---

### Post by afz12 on 2012-09-20
Hi Lucius

I have another notebook that runs XP 32 bit. I downloaded the extension pack from
[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads) as

Oracle_VM_VirtualBox_Extension_Pack-4.2.0-80737.vbox-extpack

and then 
VirtualBox-4.2.0-80737-Win.exe

from the same page. The install goes well using the Ubuntu Software Centre as the install option. After this, the extension pack is installed using Virtualbox as the install option. I suspect the operation will be similar for other 32 bit OS'

When you run Virtualbox, you only need to change a few settings such as memory allocation and location of shared folders. Then you can install 32 bit V-Machines easily. Once installed and running, the next step in to "add guest additions" and go through the steps - this shows up in v-box settings. THis procedure seems to work each time I've used it. The only problem you may have is USB support - you may need to use a terminal command for this.

However, if your host is 32 bit, I wonder if the virtualization will be a bit slow? OS' usually run best "natively" and perhaps about 1/2 as fast in Virtualbox. If you have a fast machine (i7 64 bit for example) then any OS will probably run fine. Good luck.

---

