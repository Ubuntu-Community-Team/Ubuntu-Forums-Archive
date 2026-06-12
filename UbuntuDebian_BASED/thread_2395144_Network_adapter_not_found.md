---
title: "Network adapter not found"
date: 2018-06-27
forum: Ubuntu/Debian BASED
---

### Post by cyber2go on 2018-06-27
Hi everyone,

I am trying to install the drivers for my internal wifi adapter (Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network Adapter)

I've downloaded the drivers but when I try to install with the command 'make' I get the following error: make
/bin/sh: 1: bc: not found
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.16.0-kali2-amd64/build M=/rtl8821ce  modules
make[1]: *** /lib/modules/4.16.0-kali2-amd64/build: No such file or directory.  Stop.
Makefile:1902: recipe for target 'modules' failed
make: *** [modules] Error 2

Ps; I was able to install it on ubuntu 180.04LTS but I now switched to Kali linux and now I get this error when I try to install the drivers.

Do any of you maybe have a solution for me or just can tell be what the error mean?

---

### Post by oldos2er on 2018-06-27
Moved to Other OS, Ubuntu/Debian BASED.

---

