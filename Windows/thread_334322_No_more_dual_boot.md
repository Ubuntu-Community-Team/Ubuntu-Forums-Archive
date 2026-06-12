---
title: "No more dual boot?"
date: 2007-01-08
forum: Windows
---

### Post by Synapse Void on 2007-01-08
So I'm thinking of going full Linux and eliminating my NTFS partition.  Most of my software (engineering apps) isn't available in native Linux format but runs fine under WINE.  Is it possible to install Windows apps directly to a linux partition without the need for 'Windows first' installations?  I'm hoping to be 'Microsoft free' in the near future but don't know if it's practical.  Any tips from those who have gone through the same thing would be greatly appreciated.

---

### Post by teaker1s on 2007-01-08
? just use gparted to delete windows partition and resize linux.
then install your windows programs in wine.

may be worth keeping windows if you want to update any hardware firmware in the future;)

---

### Post by BoyOfDestiny on 2007-01-09
> **Synapse Void said:**
> So I'm thinking of going full Linux and eliminating my NTFS partition.  Most of my software (engineering apps) isn't available in native Linux format but runs fine under WINE.  Is it possible to install Windows apps directly to a linux partition without the need for 'Windows first' installations?  I'm hoping to be 'Microsoft free' in the near future but don't know if it's practical.  Any tips from those who have gone through the same thing would be greatly appreciated.

Hmm, depends on the apps I'd guess, and how far wine continues to progress... 
How fast is your machine? You could run windows in virtual machine, like QEMU. If you have a rig that supports hardware virtualiziation tech, you could use it plus kvm (support is feisty fawn - the next ubuntu) and run apps near native speeds... 

Either way, easy to fall back on, if you just have to use windows for something...

---

