---
title: "Upgrade to 11.04, VMWare workstation will not compile"
date: 2011-09-08
forum: Virtualisation
---

### Post by bcdudley on 2011-09-08
I just ran the upgrade from 10.04 => 10.10 => 11.04. When I tried to run VMWare Workstation, I got the message I normally get when the Kernel is updated that VMWare must be recompiled. I let it go through and it errors out with "Unable to build kernel module".

Here is the log file:

```
Sep 08 15:16:24.649: app-140237000587040| Log for VMware Workstation pid=13185 version=7.1.0 build=build-261024 option=Release
Sep 08 15:16:24.649: app-140237000587040| The process is 64-bit.
Sep 08 15:16:24.649: app-140237000587040| Host codepage=UTF-8 encoding=UTF-8
Sep 08 15:16:24.649: app-140237000587040| Logging to /tmp/vmware-root/setup-13185.log
Sep 08 15:16:24.792: app-140237000587040| modconf query interface initialized
Sep 08 15:16:24.792: app-140237000587040| modconf library initialized
Sep 08 15:16:24.819: app-140237000587040| Your GCC version: 4.5
Sep 08 15:16:24.825: app-140237000587040| Your GCC version: 4.5
Sep 08 15:16:24.839: app-140237000587040| Your GCC version: 4.5
Sep 08 15:16:24.854: app-140237000587040| Your GCC version: 4.5
Sep 08 15:16:24.867: app-140237000587040| Your GCC version: 4.5
Sep 08 15:16:24.905: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:24.907: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:24.909: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:24.912: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:24.914: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:24.929: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:24.931: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:24.933: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:24.936: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:24.938: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:24.942: app-140237000587040| Your GCC version: 4.5
Sep 08 15:16:24.953: app-140237000587040| Your GCC version: 4.5
Sep 08 15:16:24.990: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:24.994: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:24.999: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:25.002: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:25.004: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:25.009: app-140237000587040| Your GCC version: 4.5
Sep 08 15:16:25.020: app-140237000587040| Your GCC version: 4.5
Sep 08 15:16:25.067: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:25.069: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:25.072: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:25.074: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:25.076: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:25.468: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:25.468: app-140237000587040| Building module vmmon.
Sep 08 15:16:25.487: app-140237000587040| Extracting the sources of the vmmon module.
Sep 08 15:16:25.536: app-140237000587040| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.38-11-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.5.2
Sep 08 15:16:29.287: app-140237000587040| Failed to compile module vmmon!
Sep 08 15:17:22.433: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:17:22.441: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:17:22.448: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:17:22.456: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:17:22.461: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:17:22.466: app-140237000587040| Your GCC version: 4.5
Sep 08 15:17:22.477: app-140237000587040| Your GCC version: 4.5
Sep 08 15:17:22.533: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:17:22.541: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:17:22.543: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:17:22.546: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:17:22.550: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:17:22.786: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:17:22.787: app-140237000587040| Building module vmmon.
Sep 08 15:17:22.787: app-140237000587040| Extracting the sources of the vmmon module.
Sep 08 15:17:22.802: app-140237000587040| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.38-11-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.5.2
Sep 08 15:17:23.706: app-140237000587040| Failed to compile module vmmon!
```Any suggestions. I tried installing build-essential, but it did not help.

---

### Post by bcdudley on 2011-09-08
I figured it out. I upgraded from 7.10 to 7.14 and it started working.

---

### Post by dcstar on 2011-09-27
> **bcdudley said:**
> I figured it out. I upgraded from 7.10 to 7.14 and it started working.

Then mark the thread (read below).

---

### Post by voltage on 2011-10-01
hi, can share with me how to install VMWare Workstation to 11.04 ?

thanks 

> **bcdudley said:**
> I just ran the upgrade from 10.04 => 10.10 => 11.04. When I tried to run VMWare Workstation, I got the message I normally get when the Kernel is updated that VMWare must be recompiled. I let it go through and it errors out with "Unable to build kernel module".

Here is the log file:

```
Sep 08 15:16:24.649: app-140237000587040| Log for VMware Workstation pid=13185 version=7.1.0 build=build-261024 option=Release
Sep 08 15:16:24.649: app-140237000587040| The process is 64-bit.
Sep 08 15:16:24.649: app-140237000587040| Host codepage=UTF-8 encoding=UTF-8
Sep 08 15:16:24.649: app-140237000587040| Logging to /tmp/vmware-root/setup-13185.log
Sep 08 15:16:24.792: app-140237000587040| modconf query interface initialized
Sep 08 15:16:24.792: app-140237000587040| modconf library initialized
Sep 08 15:16:24.819: app-140237000587040| Your GCC version: 4.5
Sep 08 15:16:24.825: app-140237000587040| Your GCC version: 4.5
Sep 08 15:16:24.839: app-140237000587040| Your GCC version: 4.5
Sep 08 15:16:24.854: app-140237000587040| Your GCC version: 4.5
Sep 08 15:16:24.867: app-140237000587040| Your GCC version: 4.5
Sep 08 15:16:24.905: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:24.907: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:24.909: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:24.912: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:24.914: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:24.929: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:24.931: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:24.933: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:24.936: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:24.938: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:24.942: app-140237000587040| Your GCC version: 4.5
Sep 08 15:16:24.953: app-140237000587040| Your GCC version: 4.5
Sep 08 15:16:24.990: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:24.994: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:24.999: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:25.002: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:25.004: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:25.009: app-140237000587040| Your GCC version: 4.5
Sep 08 15:16:25.020: app-140237000587040| Your GCC version: 4.5
Sep 08 15:16:25.067: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:25.069: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:25.072: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:25.074: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:25.076: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:25.468: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:16:25.468: app-140237000587040| Building module vmmon.
Sep 08 15:16:25.487: app-140237000587040| Extracting the sources of the vmmon module.
Sep 08 15:16:25.536: app-140237000587040| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.38-11-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.5.2
Sep 08 15:16:29.287: app-140237000587040| Failed to compile module vmmon!
Sep 08 15:17:22.433: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:17:22.441: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:17:22.448: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:17:22.456: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:17:22.461: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:17:22.466: app-140237000587040| Your GCC version: 4.5
Sep 08 15:17:22.477: app-140237000587040| Your GCC version: 4.5
Sep 08 15:17:22.533: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:17:22.541: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:17:22.543: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:17:22.546: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:17:22.550: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:17:22.786: app-140237000587040| Trying to find a suitable PBM set for kernel 2.6.38-11-generic.
Sep 08 15:17:22.787: app-140237000587040| Building module vmmon.
Sep 08 15:17:22.787: app-140237000587040| Extracting the sources of the vmmon module.
Sep 08 15:17:22.802: app-140237000587040| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.38-11-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.5.2
Sep 08 15:17:23.706: app-140237000587040| Failed to compile module vmmon!
```Any suggestions. I tried installing build-essential, but it did not help.

---

