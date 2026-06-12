---
title: "Linux kernel question"
date: 2011-04-04
forum: Server Platforms
---

### Post by MAFoElffen on 2011-04-04
Help please.

Okay. In Ubuntu Server 10.04, the kernel naming convention went sort of like "vmlinuz-2.6.32.21-server" for servers and "vmlinuz-2.6.32.21-generic" for desktops... Kernel numbers changing for the kernel version, but last signifying whether it was a desktop or a server version of the kernel... Right?  At least as much as I've noticed with my 64bit installs.

I recently got a 32bit test server up on Ubuntu 10.10 and I think I'm either confused, maybe things might be different in 10.10 versions or my prior assumptions were wrong?  

On this test machine, I installed Ubuntu Server 10.10 32bit.  After the install, I upgraded packages, then I installed kubuntu-desktop, xubuntu-desktop and ubuntu-desktop (in that order).  I know the implied resource and security issues-- but this was a test machine to work something out.

My observation on this machine is that I cannot find a kernel image on it with "...-server".  All the versions of kernel images are "...-generic"   All my previous installs of Ubuntu Server have been 64bit installs... and I just assumed all server kernels had "...-server" as the naming convention.

 - Is this different for 10.10?  

 - Is this a difference in the 32bit server/64bit server kernel?  

 - Did my installs of the GUI's somehow change to the desktop kernel?  If so, all my testing in now invalidated- as I'm supposed to be testing on the "server kernel."  

 - Am I just lost?

Please, anyone know?

---

### Post by arrrghhh on 2011-04-04
My 32-bit install of 10.04 has 'generic' in the name... No 'server' to be found.

I think this is how it goes for 32-bit - I think the 64-bit kernel has some special server stuff in it, but the 32-bit one only has PAE additional.

Someone correct me if I'm wrong, but I believe this is how it works ;).

---

### Post by BkkBonanza on 2011-04-04
I may be wrong but at some point I think they decided to name them with "-pae" for server versions now. I recall reading that the main difference was that server versions had pae active whereas desktop didn't. Though I'm not sure about that I know that all my recent server kernels have the "-pae" suffix instead of "-server".

Edit: Just checked the configs and 32 bit has pae for server but not for desktop and 64 bit doesn't care about that (named server and generic). Seems to be that way back to Karmic anyway as before that aren't listed here:

[http://kernel.ubuntu.com/~kernel-ppa/configs/maverick/](http://kernel.ubuntu.com/~kernel-ppa/configs/maverick/)

---

