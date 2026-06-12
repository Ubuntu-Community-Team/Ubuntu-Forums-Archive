---
title: "Xen and Ubuntu Server 11.04"
date: 2011-06-19
forum: Server Platforms
---

### Post by ahhyes on 2011-06-19
Hi Guys,

Is there a way to get Xen PV-on-HVM drivers for Linux HVM guests working on ubuntu server, according to:

[http://wiki.xensource.com/xenwiki/XenLinuxPVonHVMdrivers](http://wiki.xensource.com/xenwiki/XenLinuxPVonHVMdrivers)

> Xen PV-on-HVM drivers were merged to upstream kernel.org Linux 2.6.36, and various optimizations added in Linux 2.6.37. 

I am using Ubuntu server on my Xen HVM VPS. It would be nice to use the PV drivers for HVM to take advantage of performance improvements (so it doesnt need to use the Qemu emulation layer and can use Xenbus/netfront etc)

I am running a custom kernel 2.6.39.1 and have enabled Xen support in the kernel (under "Processor type and features" -> "Paravirtualized guest support" -> "Xen guest support"

However it appears this is not working, it's not using the PV-on-HVM drivers.

> root@srv:/usr/src/linux# dmesg | grep -i xen
Linux version 2.6.39.1-customserver-xen (root@srv.mydomain.net) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) ) #1 SMP PREEMPT Sun Jun 19 16:41:16 EST 2011
DMI: Xen HVM domU, BIOS 3.4.3 01/22/2011
ACPI: RSDP 00000000000ea020 00024 (v02    Xen)
ACPI: XSDT 00000000fc006060 00034 (v01    Xen      HVM 00000000 HVML 00000000)
ACPI: FACP 00000000fc005ee0 000F4 (v04    Xen      HVM 00000000 HVML 00000000)
ACPI: DSDT 00000000fc002c40 0321F (v02    Xen      HVM 00000000 INTL 20090220)
ACPI: APIC 00000000fc005fe0 00080 (v02    Xen      HVM 00000000 HVML 00000000)
XENFS: not registering filesystem on non-xen platform

> root@srv:/usr/src/linux# lspci | grep -i xen
00:03.0 Unassigned class [ff80]: XenSource, Inc. Xen Platform Device (rev 01)

is there extra kernel params needed to make this work?

Any info to point me in the right direction appreciated. :)

Thanks

---

### Post by ahhyes on 2011-06-20
*bump*

---

