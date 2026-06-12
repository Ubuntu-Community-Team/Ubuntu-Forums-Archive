---
title: "Ubuntu VMWare guest from physical partition can't start."
date: 2008-02-21
forum: Virtualisation
---

### Post by john.wheeler on 2008-02-21
I have installed Ubuntu 7.10 on a separate partition on my Mac Book Pro, which after some problems with display settings, now works fine.

I would like to run the same Ubuntu installation as a VMWare virtual machine running under Mac OS (using VMWare Fusion).

I have created a new Ubuntu VM from the raw Ubuntu disk partition.

Unfortunately this fails to boot, only getting as far as "running local boot scripts (/etc/rc.local) " 

My guess is that the hardware configuration under VMWare is incompatible with the physical Ubuntu installation. I suspect it might be something to do with the Mac's NVidia video card. I had to download extra drivers to get the native Ubuntu 7.10 to run properly, and obviously the VM image doesn't have these.

Does anyone have any advice on how to get an Ubuntu VMWare guest running on a Mac Book Pro?

Thanks for any help you can give me.

John Wheel

---

### Post by Tye on 2008-03-07
G'day john

i used to only get as far as "running local boot scripts (/etc/rc.local) "
in my ubuntu server
the solution i found was to just press enter and i was at the command propt

i hope this helps

---

### Post by mvan83 on 2008-03-28
If you think it's the nvidia driver, you should edit your xorg.conf file in the guest OS and change the driver to "vmware" instead of "nv" or "nvidia". If you have specific options set in that section near "nvidia" they should probably be commented out.

---

