---
title: "How to boot from GRUB's command line"
date: 2015-02-09
forum: Tutorials
---

### Post by Gvarelov on 2015-02-09
Not very many tutorials out there treating booting and GRUB, and even those that are, choose to skip at a very important step: booting from command line.
Typical scenario (a nightmare for the user) is when for reasons unknown and to which user hasn't contributed, upon startup user gets thrown at GRUB's command line. Or worse, at BusyBox/initramfs command prompt. It is very important to understand how GRUB works and which commands it executes. I'll choose to spare the reader of the story about BIOS and stages.
At OS install time or when you reinstall GRUB, GRUB's utility grub-install creates a core image, and as a part of that image assigns a value to the variable "prefix". This variable points to the location of /boot/grub or in the case of most recent Ubuntus, /grub directory. This location is very important, as assignments of other variables are done relative to the value of "prefix". Like for example the location of "root". Once "prefix" and "root" are set, GRUB locates and loads the "normal" module, again using the location given in "prefix" as a pointer to where the normal module might be found. After the normal module is successfully loaded, GRUB runs the "normal" command after which boot menu is presented to user or the computer boots the default kernel straight away.
Those few tutorials that deal with booting from command line rely on locating "linux" and "initrd" and issuing the "boot" command. While that may have worked at the time of writing of those tutorials, and it might make sense, it isn't working as straight as it is described and as a result you might be thrown at initramfs prompt which may require some more command line effort and search.
So, at GRUB command line, issue:
```
grub> insmod normal
grub> normal
```
and given path of "prefix" is correct, you should be able to proceed to normal boot.

---

