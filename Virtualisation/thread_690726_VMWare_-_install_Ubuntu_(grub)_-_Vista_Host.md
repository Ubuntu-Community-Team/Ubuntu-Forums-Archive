---
title: "VMWare - install Ubuntu (grub) - Vista Host"
date: 2008-02-07
forum: Virtualisation
---

### Post by superjacent on 2008-02-07
Hope someone can help.   I was dual booting between Vista and Ubuntu but was getting sick and tired of shutting down one to access the other.   

In Vista I installed VMWare Server and then created a virtual drive on my second hard-drive for the  Ubuntu system.   Unbuntu installed but in the process I disabled the loading of Grub.   Wasn't too sure if that would effect my existing dual booting Grub.

When re-starting the VMWare server and selecting Ubuntu, all I end up with is an empty black screen.   I am able to use a bootable Super Grub disk - and gain access to Unbuntu.

My question is - if I can gain access to my virtual Unbuntu - how do I set up Grub from there. 

Would it be easier to go through the install process again, but this time - what settings are required for Grub.   When clicking the 'Advanced' button at the relevant screen, the default (from memory) is hd0 - surely this would wipe out my existing Grub (which I don't want to do - just yet).

Any advice greatly appreciated.

---

### Post by davidgutu on 2008-04-26
I was also looking for the same. Somebody please help

---

### Post by himdel on 2009-07-08
Ubuntu's grub is broken in vmware, if you install grub from a debian repository, and do a grub-install /dev/sda (where sda is your harddrive), it will boot fine.

---

### Post by odysseusjak on 2009-07-08
I use Virtualbox instead and it works perfectly.  I have Vista Ultimate as the host and then, using Virtualbox I have XP and Ubuntu 9.04.

---

