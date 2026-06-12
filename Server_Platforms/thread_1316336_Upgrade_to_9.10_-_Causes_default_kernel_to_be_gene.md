---
title: "Upgrade to 9.10 - Causes default kernel to be generic kernel"
date: 2009-11-05
forum: Server Platforms
---

### Post by danooch13 on 2009-11-05
Hello,

Ever since the upgrade from 9.04 to 9.10, I have been noticing a few differences, not that they are bad, but I feel they should be mentioned.

With ubuntu 9.10 server, does any notice what there default kernel is in menu.lst?

This is mine:
```
title           Ubuntu 9.10, kernel 2.6.31-14-generic-pae
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.31-14-generic-pae root=/dev/mapper/sil_ajaiahaafcai1 ro quiet splash apm=off nomodeset
initrd          /boot/initrd.img-2.6.31-14-generic-pae

title           Ubuntu 9.10, kernel 2.6.31-14-generic-pae (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.31-14-generic-pae root=/dev/mapper/sil_ajaiahaafcai1 ro  single
initrd          /boot/initrd.img-2.6.31-14-generic-pae

title           Ubuntu 9.10, kernel 2.6.31-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.31-14-generic root=/dev/mapper/sil_ajaiahaafcai1 ro quiet splash
initrd          /boot/initrd.img-2.6.31-14-generic


```

Notice how it is using the generic kernel as opposed to the server one.

Why would the generic be the default after the upgrade?

Thanks

---

### Post by crouz on 2009-11-07
I've got both the generic-pae, generic and server in the menu.lst after upgrade to 9.10 but it is the generic-pae that is used by default.

The server is older than the generic ones:
generic and generic-pae are 2.6.31.14
server is 2.6.28.11.

Maybe this is the reason for having the generic-pae as default? It seems rather odd though...

---

### Post by sc0g on 2009-11-17
I have this kernel installed as well (linux-image-2.6.31-14-generic-pae).

**How much RAM does your system have? Mine has 4GB.**

This is all I could find about it: [http://packages.ubuntu.com/karmic/linux-image-2.6.31-14-generic-pae](http://packages.ubuntu.com/karmic/linux-image-2.6.31-14-generic-pae)

> Supports Generic processors.

Geared toward 32 bit desktop systems with more then 4GB RAM.

---

### Post by Ama Zing on 2009-11-18
Yep same for me after the amazing one step up-grade from Hardy 8.04 CLI the default menu opt has become the **2.6.31-14 **Generic-pae kernel with autostart of X i/o CLI.
No complaints either despite of some fail messages during upgrade - evryting runs as in prev version :D
Maybe [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension) is part of the reason. Guess prev Server kernels had PAE build-in to access more than 4GB memory on 32-bit CPU. But headless Servers might get in trouble I guess after this update and an admin ignoring the new start menu of the box.
 
__________________
:idea: To Bug or not Debug that is the Q

---

### Post by me_name on 2009-11-20
..me too 
The PAE is default too but only have 768mB RAM...
Have (in grub + boot):
2.6.31-14-generic-pae
2.6.31-14-generic
and 2.6.28-16-server from 9.04
Synaptic shows:
linux-image-server installed ver: 2.6.31.14.27
and
linux-server installed ver: 2.6.31.14.27
as installed.. :confused:
when did cli upgrade it did have some errors wrt kernels, but went by too fast & can't find any logs.
..could I mark linux-image-server & linux-server for re-installation?

TIA + Cheers.

---

### Post by me_name on 2009-12-03
..bump..
Still no linux-server..
Just done sudo apt-get update & upgrade, says:
The following packages have been kept back:
linux-generic linux-generic-pae linux-image-generic linux-image-generic-pae

in x, ran Update Manager, it updated above.

wtf's happening?

Where's me server kernel.. :cry:

---

### Post by me_name on 2009-12-03
In synaptic:
removed linux-image-server
installed linux-image-server
..still not in grub menu.lst

---

