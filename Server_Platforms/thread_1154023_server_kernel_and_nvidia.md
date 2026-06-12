---
title: "server kernel and nvidia"
date: 2009-05-09
forum: Server Platforms
---

### Post by deathguppie on 2009-05-09
I don't know if this is the right place to put this but I hoped there would be more knowledge on the subject poking around on this thread.

I have over 4 gigs of ram but the system only identifies 3 , as you all know well, on my kubuntu desktop system.

However I am an open source character modeler, and I need my full amount of ram.  The only problem is that I *must* have a working nvidia driver in order to use the extra ram.  (I need it for blender sculpt mode).  But the only kernel with PAE is the server kernel, and there is no nvidia driver for that kernel.

Anyway the last time I tried this I ended up trying to install the nvidia driver from source and hosed my system trying to get it to work.. 

Has anyone successfully done this?

---

### Post by aurelieng on 2009-05-09
Why not using Kubuntu AMD64 ? Alternatively, you can boot the server kernel (with PAE) and try to install the binary NVIDIA driver from the official NVIDIA website ?

You can also have a look at these threads : [http://ubuntuforums.org/showthread.php?t=957430](http://ubuntuforums.org/showthread.php?t=957430) and [http://ubuntuforums.org/showthread.php?t=893443](http://ubuntuforums.org/showthread.php?t=893443)

---

### Post by deathguppie on 2009-05-09
Actually checking /proc/cpuinfo tells me that pae is built in to the regular kernel.. only my bios (ati 790) does not have an option for turning on a hardware memory hole.  

Strange since it is an am2+ motherboard

I set enable-pae ht=on in menu.lst but no go.

64bit is not an option because I need some game stuff that does not work in 64bit.

---

### Post by aurelieng on 2009-05-10
/proc/cpuinfo refers to your CPU, not to the kernel. If you have a 32bits kernel with PAE, you should see your 4Gb or RAM. Otherwise, your kernel has not PAE enabled and/or your BIOS does not allow it (I seriously doubt about that).

---

