---
title: "Can't install VMware Workstation 7.5 on Ubuntu 12.04"
date: 2012-06-03
forum: Virtualisation
---

### Post by rustybutt on 2012-06-03
My desktop is running Ubuntu 12.04, 64 bit.  I downloaded  VMware Workstation 7.5 build 491717 and it fails to compile the necessary modules.

Here's the error message:


Jun 03 12:05:51.500: app-139701756667648| Building module vmmon.
Jun 03 12:05:51.500: app-139701756667648| Extracting the sources of the vmmon module.
Jun 03 12:05:51.515: app-139701756667648| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-24-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
Jun 03 12:05:52.860: app-139701756667648| Failed to compile module vmmon!


Any suggestions?

Russ

---

