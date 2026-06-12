---
title: "[SOLVED] Install VMWare Player in Ubuntu 8.04 LTS"
date: 2008-08-20
forum: Server Platforms
---

### Post by flouran on 2008-08-20
Hi Guys,
I wanted to install VMWare Player on Ubuntu 8.04 so that I could run the NST (Network Security Toolkit) v 1.8.0 on VMWare. I downloaded the .tar.gz file from [http://www.vmware.com/products/player/]("http://www.vmware.com/products/player/")
,and when I untarred it and tried to run, vmware-install.pl, and followed the instructions, when I was asked where the C headers for the current Linux kernel version I was running (2.6.24-19-generic), it said it couldn't find the directory, /usr/src/linux/include.

Does anyone know where the C headers for the current kernel version I am running are located in Ubuntu?
Also, does anyone know any good guides where I could install VMWare Player on Ubuntu 8.04 LTS? I've searched Google for guides, and they don't work (I even tried: [http://ubuntuforums.org/showthread.php?t=832753]("http://ubuntuforums.org/showthread.php?t=832753"), but to no avail)! And, if someone knows how to do this from experience I am happy to hear from them as well. Please help!!

---

### Post by eggdeng on 2008-08-20
```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by windependence on 2008-08-20
He may also need to install gcc, gcc+, make, and the Kernel source.

[http://www.howtoforge.com/installing-vmware-server-on-ubuntu-8.04](http://www.howtoforge.com/installing-vmware-server-on-ubuntu-8.04)

[http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

Why not just install VMware server 1.06?

-Tim

---

### Post by flouran on 2008-08-20
Thank you very much!
However, I installed QEmu instead, which works just as fine as VMWare.

---

