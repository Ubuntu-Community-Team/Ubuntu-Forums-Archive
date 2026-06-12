---
title: "Question about VirtualBox..."
date: 2010-11-19
forum: Virtualisation
---

### Post by camn on 2010-11-19
Is is possible to use a physical partition on your HD instead of a virtual HD (I heard you can do this in VMware, but that's a pain to install)? I need to install Windows on my laptop for some programs that don't work right in Wine, but I don't have any CDs to burn the ISO...

---

### Post by lmarmisa on 2010-11-19
You do not need to burn any CD. You can select the iso file.

---

### Post by msandoy on 2010-11-19
I can't say if it is possible to use a physical partition on your drive, but I do not see why you would prefer that. The easy way/smallest waste of space, is to use a dynamically expanding disk image. If you need to swap files between VM and physical machine, just make a permanent shareed folder. Connect it as a networkdrive in VM, and drop files back and forth. You can also use ordinary filesharing if you use bridged network adapter.

---

### Post by camn on 2010-11-20
> **msandoy said:**
> I can't say if it is possible to use a physical partition on your drive, but I do not see why you would prefer that. The easy way/smallest waste of space, is to use a dynamically expanding disk image. If you need to swap files between VM and physical machine, just make a permanent shareed folder. Connect it as a networkdrive in VM, and drop files back and forth. You can also use ordinary filesharing if you use bridged network adapter.

My computer sucks and is REALLY slow in a VM...

---

### Post by msandoy on 2010-11-20
That is one of the beauty's of using a VM, you do not need to shut down the VM every time, just exit the VM window, and choose save state. Then the next time you need to do some work in the other OS, it's up and running in just seconds. Don't forget to also install the virtualbox addons, since those actually improoves both performance and adds features like better integration with the desktop.

---

### Post by camn on 2010-11-21
> **msandoy said:**
> That is one of the beauty's of using a VM, you do not need to shut down the VM every time, just exit the VM window, and choose save state. Then the next time you need to do some work in the other OS, it's up and running in just seconds. Don't forget to also install the virtualbox addons, since those actually improoves both performance and adds features like better integration with the desktop.

Seriously, my computer CAN'T run things in virtual machines. It's too slow to actually do anything.

---

### Post by msandoy on 2010-11-21
Ok, but you started this thread, asking about virtualbox.
If I understand you correct, you need to install windows, but your computer is too slow to run anything in virtualbox. You do not have a cd, to burn the ISO file. Then my suggestion is, use gparted to resize your partition, creating enough space for windows. Use one of the existing utilities online for creating a bootable USB with windows ISO. Install windows side by side with Ubuntu, and restore Grub.

Be sure to read up on how to restore Grub, before proseeding to install windows, since that removes the startup menu.

---

### Post by camn on 2010-11-22
> **msandoy said:**
> Ok, but you started this thread, asking about virtualbox.
If I understand you correct, you need to install windows, but your computer is too slow to run anything in virtualbox. You do not have a cd, to burn the ISO file. Then my suggestion is, use gparted to resize your partition, creating enough space for windows. Use one of the existing utilities online for creating a bootable USB with windows ISO. Install windows side by side with Ubuntu, and restore Grub.

Be sure to read up on how to restore Grub, before proseeding to install windows, since that removes the startup menu.

Because I heard that you could use VMWare to install to a physical partition, instead of a virtual HD. I wouldn't really run the VM, just use it to install. I was wondering if that was possible with Virtual Box since VMWare is such a pain to install.

---

### Post by rkham11 on 2010-11-22
installing a virtual machine really is not all that difficult. and I don't know anything about physically partitioning from the virtualBox software
If you want to run windows on your computer with out using virtualBox or VM ware, then you will have to physically partition your drive from an OS that is not running from that drive during the time of the partitioning. (i.e  ubuntu or GParted live CD) then you will need to install windows to that partition and configure your boot loader. If your out of CDs then you probably cant do any of this. 

This is all much more difficult then just using virtualBox

---

