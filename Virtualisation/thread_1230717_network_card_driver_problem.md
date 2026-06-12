---
title: "network card driver problem"
date: 2009-08-03
forum: Virtualisation
---

### Post by sirajrathore on 2009-08-03
Hi
 
i am running ubuntu 8.04 server kernel 2.6.24 on Intel 64bit dual processor machine.i had intel PRO/1000 PT quad port network interface which was working fine.
i installed openvz stable release with kernel 2.6.18-14-ovz-amd64-smp.This enviromnent did not detect the interface.i downloaded the driver from intel website.it is e1000e-1.0.2.5 for linux.when i did 'make
install' to install this driver following error has been shown.
----------------------------
Makefile:70 Linux source not found in any of these locations
Makefile:72 Install the appropriate kernel development package,e.g.
Makefile:73 kernel-devel,for building kernel modules and try again.
Stop
----------------------------
i searched on the web for the same error.i found some suggestions.it was suggested to install 'linux-kernel-devel' and gcc packages. i installed it but the same error is still there.
 
can anyone help please.
 
 
Regards
Siraj

---

