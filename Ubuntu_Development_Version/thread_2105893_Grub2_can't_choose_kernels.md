---
title: "Grub2 can't choose kernels"
date: 2013-01-17
forum: Ubuntu Development Version
---

### Post by jerrylamos on 2013-01-17
Grub2 does not allow choice of "mainline kernel" vs. stock Ubuntu kernel.

In:

ttps://wiki.ubuntu.com/Kernel/MainlineBuilds?action=show&redirect=KernelMainlineBuilds

it says:

"The mainline kernels have their own ABI namespace so they install side by side with the stock Ubuntu kernels (each kernel has a separate directory under /lib/modules/VERSION for example). This means that you can keep several mainline and Ubuntu stock kernels installed at the same time and select the one you need from the GRUB boot menu."

Here's from /boot:

initrd.img-3.8.0-030800rc3-generic
initrd.img-3.8.0-0-generic

Now in fact /boot/grub/grub.cfg does show entries for both kernels, but the Grub2 menu on boot does not show the stock Ubuntu kernel or allow choosing it.

How do I get Grub2 boot menu to display all the kernels that are in grub.cfg?

Thanks....

---

### Post by dino99 on 2013-01-17
i propose that you purge grub-pc via synaptic, then reinstall it. Here on i386, i've both the stock & vanilla kernels, and i can choose the one i want into grub menu without trouble (as usual)

---

### Post by jerrylamos on 2013-01-17
Well synaptic grub-pc complete removal did, but then on install got the following message and refuses to mark for installation: 

grub-pc:
 Depends: grub-gfxpayload-lists but it is not going to be installed

and won't install.  

I try installing grub-gfxpayload-lists 

grub-gfxpayload-lists:
 Depends: grub-pc (>= 1.99~20101210-1ubuntu2)

and refuses to mark for installation.

So I went back to sudo apt-get install grub-pc grub-gfxpayload-lists.

Maybe it will boot?

Yes it did, same problem, only allows one boot image on the partition while there are two.  Launchpad Bug #1100958

---

