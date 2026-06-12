---
title: "System partition smaller than recovery image"
date: 2009-03-31
forum: Virtualisation
---

### Post by ubantuwannabe on 2009-03-31
My laptop is nc4400. Operating System is originally Windows XP.

Before I reformat the disk totally to ubuntu 8.10, I made two recovery disk (dvd) using the menu in windows xp.

next I install vmware 2.0 on ubuntu 8.10

and follow [http://www.lucidtips.com/2009/01/20/installing-vmware-server-and-windows-xp-on-ubuntu/](http://www.lucidtips.com/2009/01/20/installing-vmware-server-and-windows-xp-on-ubuntu/)

as instructed.

while I was installing windows Xp on the virtual system, I encountered the following error:

System Partition is samller than the recovery image, and hence windows xp installation is stop.

How should I resolve this issue?

thanks

---

### Post by Jose Catre-Vandis on 2009-03-31
So you are trying to load the image of your original hard disk install into a VM? Good luck, Xp will complain bitterly about the changes in hardware, and you might need to reactivate if OEM.

Did you reduce the size of your XP partition before burning to DVD? The recovery images will try to restore to the same sized partition (e.g. your entire hard drive) hence the error.

You might need to put your XP back on, sort out the partition size, clean out anything you don't need, so there is enough space in the VM.

Alternately you might need to create a VM with a bigger virtual hard disk, so that your recovery image fits.

Been a while since I played with VMware, as i am a VirtualBox junkie ;^)

---

### Post by Mark20 on 2009-03-31
One alternative would be to dual boot - have Ubuntu AND XP installed on your computer.  Then create a virtual machine in Ubuntu which accesses the physical install of XP.  Meaning that all of your data would already be there, and any time you change something in your virtual machine it will be changing the windows partition as opposed to a vmware file. This way you would never have to boot into Windows, but you could still access all of your files via this virtual machine.

I have this setup at work and it's awesome!  There's a really good guide [here]("http://imrannazar.com/Running-a-Windows-Partition-in-VMware") if you're interested.

Mark

---

