---
title: "Problem with vmware installation on ubuntu hardy"
date: 2009-03-27
forum: Virtualisation
---

### Post by rado3105 on 2009-03-27
> None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Your kernel was built with "gcc" version "4.2.3", while you are trying to use 
"/usr/bin/gcc" version "4.2.4". This configuration is not recommended and 
VMware Server may crash if you'll continue. Please try to use exactly same 
compiler as one used for building your kernel. Do you want to go with compiler 
"/usr/bin/gcc" version "4.2.4" anyway? [no]

I did it anyway, but after compiling, and writing vmware in terminal, it showed me this:

> r-c@r-c-desktop:~$ vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)


I installed it using this mannual:
[http://ubuntu-tutorials.com/2008/11/01/vmware-server-107-on-ubuntu-810-intrepid-2627-7-generic/](http://ubuntu-tutorials.com/2008/11/01/vmware-server-107-on-ubuntu-810-intrepid-2627-7-generic/)

---

### Post by Herman on 2009-03-27
Try using VirtualBox instead, you can install it through 'Applications'-->'Add/Remove'. [http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by rado3105 on 2009-03-27
I heard that wmware is much more better, it is faster and eat less system power. Is any way to install vmware?

---

### Post by baizon on 2009-03-27
Which version of VMWare do you try to install?
But i suggest VirtualBox too. VMWare is better for commercial use, because its "heavy" (VMWare: ~550MB, VirtualBox: ~35MB).

---

### Post by rado3105 on 2009-03-27
VMware-server-1.0.7-108231.tar.gz

I also patched it:
vmware-update-2.6.27-5.5.7-2.tar.gz

---

### Post by baizon on 2009-03-28
Try VMWare 1.0.8. It seems he could not find the right gcc compiler for VMWare. What did the installation-log  said?

---

### Post by bodhi.zazen on 2009-03-28
This question is answered im my how to install vmware which is listed in the guides in the sticky. :twisted:

The sitkcy is here : [http://ubuntuforums.org/showthread.php?t=973756](http://ubuntuforums.org/showthread.php?t=973756)

There is a reason for it being a sticky and you might want to look at the stickies in the future :p .

The vmware guide is here : 

[http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

---

