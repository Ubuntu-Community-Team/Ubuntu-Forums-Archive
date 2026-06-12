---
title: "VMWare Workstation 7 - Ubuntu 10.04 64-Bit"
date: 2011-07-27
forum: Virtualisation
---

### Post by KirmesBude on 2011-07-27
The Installation of VMWare worked flawless, but whenever i start VMWare it says i need to compile some things.
I click install and get a triangle at network device and then it cant initialize the VMWare services.

```
Jul 27 21:58:23.007: app-140224205801216| Log for VMware Workstation pid=14757 version=7.0.0 build=build-203739 option=Release
Jul 27 21:58:23.007: app-140224205801216| The process is 64-bit.
Jul 27 21:58:23.007: app-140224205801216| Host codepage=UTF-8 encoding=UTF-8
Jul 27 21:58:23.007: app-140224205801216| Logging to /tmp/vmware-root/setup-14757.log
Jul 27 21:58:23.098: app-140224205801216| modconf query interface initialized
Jul 27 21:58:23.098: app-140224205801216| modconf library initialized
Jul 27 21:58:23.118: app-140224205801216| Your GCC version: 4.4
Jul 27 21:58:23.121: app-140224205801216| Your GCC version: 4.4
Jul 27 21:58:23.127: app-140224205801216| Your GCC version: 4.4
Jul 27 21:58:23.135: app-140224205801216| Your GCC version: 4.4
Jul 27 21:58:23.147: app-140224205801216| Your GCC version: 4.4
Jul 27 21:58:23.166: app-140224205801216| Trying to find a suitable PBM set for kernel 2.6.32-33-generic.
Jul 27 21:58:23.167: app-140224205801216| Trying to find a suitable PBM set for kernel 2.6.32-33-generic.
Jul 27 21:58:23.168: app-140224205801216| Trying to find a suitable PBM set for kernel 2.6.32-33-generic.
Jul 27 21:58:23.170: app-140224205801216| Trying to find a suitable PBM set for kernel 2.6.32-33-generic.
Jul 27 21:58:23.172: app-140224205801216| Trying to find a suitable PBM set for kernel 2.6.32-33-generic.
Jul 27 21:58:23.182: app-140224205801216| Trying to find a suitable PBM set for kernel 2.6.32-33-generic.
Jul 27 21:58:23.183: app-140224205801216| Trying to find a suitable PBM set for kernel 2.6.32-33-generic.
Jul 27 21:58:23.184: app-140224205801216| Trying to find a suitable PBM set for kernel 2.6.32-33-generic.
Jul 27 21:58:23.186: app-140224205801216| Trying to find a suitable PBM set for kernel 2.6.32-33-generic.
Jul 27 21:58:23.188: app-140224205801216| Trying to find a suitable PBM set for kernel 2.6.32-33-generic.
Jul 27 21:58:23.190: app-140224205801216| Your GCC version: 4.4
Jul 27 21:58:23.196: app-140224205801216| Your GCC version: 4.4
Jul 27 21:58:23.222: app-140224205801216| Trying to find a suitable PBM set for kernel 2.6.32-33-generic.
Jul 27 21:58:23.224: app-140224205801216| Trying to find a suitable PBM set for kernel 2.6.32-33-generic.
Jul 27 21:58:23.225: app-140224205801216| Trying to find a suitable PBM set for kernel 2.6.32-33-generic.
Jul 27 21:58:23.227: app-140224205801216| Trying to find a suitable PBM set for kernel 2.6.32-33-generic.
Jul 27 21:58:23.228: app-140224205801216| Trying to find a suitable PBM set for kernel 2.6.32-33-generic.
Jul 27 21:58:23.231: app-140224205801216| Your GCC version: 4.4
Jul 27 21:58:23.237: app-140224205801216| Your GCC version: 4.4
Jul 27 21:58:23.263: app-140224205801216| Trying to find a suitable PBM set for kernel 2.6.32-33-generic.
Jul 27 21:58:23.264: app-140224205801216| Trying to find a suitable PBM set for kernel 2.6.32-33-generic.
Jul 27 21:58:23.265: app-140224205801216| Trying to find a suitable PBM set for kernel 2.6.32-33-generic.
Jul 27 21:58:23.267: app-140224205801216| Trying to find a suitable PBM set for kernel 2.6.32-33-generic.
Jul 27 21:58:23.268: app-140224205801216| Trying to find a suitable PBM set for kernel 2.6.32-33-generic.
Jul 27 21:58:23.438: app-140224205801216| Trying to find a suitable PBM set for kernel 2.6.32-33-generic.
Jul 27 21:58:23.439: app-140224205801216| Building module vmmon.
Jul 27 21:58:23.439: app-140224205801216| Extracting the sources of the vmmon module.
Jul 27 21:58:23.447: app-140224205801216| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-33-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Jul 27 21:58:27.383: app-140224205801216| Installing module vmmon from /tmp/vmware-root/modules/vmmon.o.
Jul 27 21:58:27.383: app-140224205801216| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.32-33-generic/misc/vmmon.o
Jul 27 21:58:27.798: app-140224205801216| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.32-33-generic/misc/vmmon.ko
Jul 27 21:58:28.475: app-140224205801216| Trying to find a suitable PBM set for kernel 2.6.32-33-generic.
Jul 27 21:58:28.475: app-140224205801216| Building module vmnet.
Jul 27 21:58:28.475: app-140224205801216| Extracting the sources of the vmnet module.
Jul 27 21:58:28.482: app-140224205801216| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmnet-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-33-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Jul 27 21:58:32.432: app-140224205801216| Failed to compile module vmnet!
Jul 27 21:58:32.437: app-140224205801216| Trying to find a suitable PBM set for kernel 2.6.32-33-generic.
Jul 27 21:58:32.437: app-140224205801216| Building module vmblock.
Jul 27 21:58:32.437: app-140224205801216| Extracting the sources of the vmblock module.
Jul 27 21:58:32.444: app-140224205801216| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmblock-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-33-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Jul 27 21:58:35.288: app-140224205801216| Installing module vmblock from /tmp/vmware-root/modules/vmblock.o.
Jul 27 21:58:35.288: app-140224205801216| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.32-33-generic/misc/vmblock.o
Jul 27 21:58:35.649: app-140224205801216| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.32-33-generic/misc/vmblock.ko
Jul 27 21:58:36.341: app-140224205801216| Trying to find a suitable PBM set for kernel 2.6.32-33-generic.
Jul 27 21:58:36.342: app-140224205801216| Building module vmci.
Jul 27 21:58:36.342: app-140224205801216| Extracting the sources of the vmci module.
Jul 27 21:58:36.349: app-140224205801216| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-33-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Jul 27 21:58:37.380: app-140224205801216| Failed to compile module vmci!
Jul 27 21:58:37.383: app-140224205801216| Trying to find a suitable PBM set for kernel 2.6.32-33-generic.
Jul 27 21:58:37.384: app-140224205801216| Building module vmci.
Jul 27 21:58:37.384: app-140224205801216| Extracting the sources of the vmci module.
Jul 27 21:58:37.391: app-140224205801216| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-33-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Jul 27 21:58:37.846: app-140224205801216| Failed to compile module vmci!
```

---

