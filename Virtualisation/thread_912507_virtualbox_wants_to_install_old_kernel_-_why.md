---
title: "virtualbox wants to install old kernel - why?"
date: 2008-09-06
forum: Virtualisation
---

### Post by eisam on 2008-09-06
hi folks,

I'm thinking of a virtual machine solution for playing with alternative and/or non-stable linux distros on an ubuntu host (with an x86 machine).

basically, before i decided to run ubuntu, i was trying several (at one point as many as 12) distros in different partitions on my hard disk, each with its own grub entries, and some with their own separate /home or /boot partitions (because that's what the installer defaulted to). this had several disadvantages - it was confusing, messy and i had to hand-maintain grub's menu.lst or grub.conf. so, now that i'm thinking of playing with other versions of ubuntu (xubuntu, kubuntu, gobuntu, intrepid) and trying to improve my command-line-foo with a minimalist distro, i thought it might be best to try virtualisation. 

i'd thought to use virtualbox - at first glance it's the one most oriented to desktop stuff. however, aptitude wants to install linux-image-2.6.24-16-386 although i currently have 2.6.24.19 on hardy. is this going to be a problem? will i have to boot with that kernel to use the guest machines? will there be any other issues?

thanks,
E

(i'm completely new to virtualisation (and pretty new to linux) so please keep that in mind when responding to my idiocy...)

---

### Post by dark_phantom on 2008-09-06
When you're installing VirtualBox OSE, the free version, then it will also install modules dependent on the kernel it was built for.  So, in short it should be fine to see messages that refer to an older kernel.


When you install the non-free version, everytime you update your kernel you will have to rebuild VirtualBox.  Don't worry about this last paragraph if you're installing VB through synaptic.

I hope this clears your concerns.

---

### Post by w3rt on 2008-09-07
I suggest installing it via synaptic, that way you know it will be the latest version

---

