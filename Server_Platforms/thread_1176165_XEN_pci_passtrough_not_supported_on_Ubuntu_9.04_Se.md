---
title: "XEN pci passtrough not supported on Ubuntu 9.04 Server?"
date: 2009-06-02
forum: Server Platforms
---

### Post by princeofpersia on 2009-06-02
Greetings, 

  The current "virtual" linux kernel (2.6.28-11-server), distributed with Ubuntu 9.04 Server seems to lack PCI passtrough. 

*#grep CONFIG_XEN_PCIDEV_FRONTEND /boot/config-2.6.28-11-server*

returns nothing and on boot the following error message is printed

[I]#dmesg | grep XENBUS.*pci
[    0.751235] XENBUS: Device with no driver: device/pci/0
[/I]
What disturbs me is that I can't compile the support either. I tried the standard debian procedure for building the kernel, having executed something like

cp /boot/config-2.6.28-11-server /usr/src/linux/.config
echo "[I]CONFIG_XEN_PCIDEV_FRONTEND=y"  >> .config

[/I]After the compilation, the .config file was sorted (at least different lines were changed their place) and the option was missing. Results were the same - the new kernel booted under xen, but no PCI passtrough. Did I screwed up or it's just not supported?

---

