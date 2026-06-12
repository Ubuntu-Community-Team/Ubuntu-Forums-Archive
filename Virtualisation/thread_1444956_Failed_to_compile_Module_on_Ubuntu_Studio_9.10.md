---
title: "Failed to compile Module on Ubuntu Studio 9.10"
date: 2010-04-02
forum: Virtualisation
---

### Post by lexlinux on 2010-04-02
Hi all...i am hoping you guys can help me out, I am a noob into this.

I have downloaded and installed latest version 3.01 of VMware Player, installation seemed successful.
However, attempting to run vmware brings a dialog box saying that it  needs to update kernel modules.

"before you can run VMware, several modules must be compiled and loaded  into the running kernel."

the following error appear (/tmp/vmware-root/setup-3248.log):
Please see also the attached screenshot.

Anyone can share their expertise, knowledge and experience would be great. 


---start of file ----
Apr 01 20:55:35.170: app-3078584000| Log for VMware Workstation pid=3248 version=7.0.1 build=build-227600 option=Release
Apr 01 20:55:35.170: app-3078584000| The process is 32-bit.
Apr 01 20:55:35.170: app-3078584000| Host codepage=UTF-8 encoding=UTF-8
Apr 01 20:55:35.170: app-3078584000| Logging to /tmp/vmware-root/setup-3248.log
Apr 01 20:55:35.414: app-3078584000| modconf query interface initialized
Apr 01 20:55:35.415: app-3078584000| modconf library initialized
Apr 01 20:55:35.461: app-3078584000| Your GCC version: 4.4
Apr 01 20:55:35.470: app-3078584000| Your GCC version: 4.4
Apr 01 20:55:35.483: app-3078584000| Your GCC version: 4.4
Apr 01 20:55:35.501: app-3078584000| Your GCC version: 4.4
Apr 01 20:55:35.514: app-3078584000| Your GCC version: 4.4
Apr 01 20:55:35.557: app-3078584000| Trying to find a suitable PBM set for kernel 2.6.31-9-rt.
Apr 01 20:55:35.562: app-3078584000| Trying to find a suitable PBM set for kernel 2.6.31-9-rt.
Apr 01 20:55:35.568: app-3078584000| Trying to find a suitable PBM set for kernel 2.6.31-9-rt.
Apr 01 20:55:35.573: app-3078584000| Trying to find a suitable PBM set for kernel 2.6.31-9-rt.
Apr 01 20:55:35.578: app-3078584000| Trying to find a suitable PBM set for kernel 2.6.31-9-rt.
Apr 01 20:55:35.605: app-3078584000| Trying to find a suitable PBM set for kernel 2.6.31-9-rt.
Apr 01 20:55:35.610: app-3078584000| Trying to find a suitable PBM set for kernel 2.6.31-9-rt.
Apr 01 20:55:35.615: app-3078584000| Trying to find a suitable PBM set for kernel 2.6.31-9-rt.
Apr 01 20:55:35.621: app-3078584000| Trying to find a suitable PBM set for kernel 2.6.31-9-rt.
Apr 01 20:55:35.626: app-3078584000| Trying to find a suitable PBM set for kernel 2.6.31-9-rt.
Apr 01 20:55:35.633: app-3078584000| Your GCC version: 4.4
Apr 01 20:55:35.647: app-3078584000| Your GCC version: 4.4
Apr 01 20:55:35.694: app-3078584000| Trying to find a suitable PBM set for kernel 2.6.31-9-rt.
Apr 01 20:55:35.699: app-3078584000| Trying to find a suitable PBM set for kernel 2.6.31-9-rt.
Apr 01 20:55:35.705: app-3078584000| Trying to find a suitable PBM set for kernel 2.6.31-9-rt.
Apr 01 20:55:35.710: app-3078584000| Trying to find a suitable PBM set for kernel 2.6.31-9-rt.
Apr 01 20:55:35.715: app-3078584000| Trying to find a suitable PBM set for kernel 2.6.31-9-rt.
Apr 01 20:55:35.722: app-3078584000| Your GCC version: 4.4
Apr 01 20:55:35.736: app-3078584000| Your GCC version: 4.4
Apr 01 20:55:35.798: app-3078584000| Trying to find a suitable PBM set for kernel 2.6.31-9-rt.
Apr 01 20:55:35.804: app-3078584000| Trying to find a suitable PBM set for kernel 2.6.31-9-rt.
Apr 01 20:55:35.809: app-3078584000| Trying to find a suitable PBM set for kernel 2.6.31-9-rt.
Apr 01 20:55:35.815: app-3078584000| Trying to find a suitable PBM set for kernel 2.6.31-9-rt.
Apr 01 20:55:35.820: app-3078584000| Trying to find a suitable PBM set for kernel 2.6.31-9-rt.
Apr 01 20:55:36.387: app-3078584000| Trying to find a suitable PBM set for kernel 2.6.31-9-rt.
Apr 01 20:55:36.388: app-3078584000| Building module vmmon.
Apr 01 20:55:36.399: app-3078584000| Extracting the sources of the vmmon module.
Apr 01 20:55:36.508: app-3078584000| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.31-9-rt/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.1
Apr 01 20:55:46.451: app-3078584000| Installing module vmmon from /tmp/vmware-root/modules/vmmon.o.
Apr 01 20:55:46.468: app-3078584000| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.31-9-rt/misc/vmmon.o
Apr 01 20:55:48.822: app-3078584000| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.31-9-rt/misc/vmmon.ko
Apr 01 20:55:58.520: app-3078584000| Trying to find a suitable PBM set for kernel 2.6.31-9-rt.
Apr 01 20:55:58.520: app-3078584000| Building module vmnet.
Apr 01 20:55:58.520: app-3078584000| Extracting the sources of the vmnet module.
Apr 01 20:55:58.550: app-3078584000| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmnet-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.31-9-rt/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.1
Apr 01 20:56:03.645: app-3078584000| Failed to compile module vmnet!
Apr 01 20:56:03.655: app-3078584000| Trying to find a suitable PBM set for kernel 2.6.31-9-rt.
Apr 01 20:56:03.655: app-3078584000| Building module vmblock.
Apr 01 20:56:03.655: app-3078584000| Extracting the sources of the vmblock module.
Apr 01 20:56:03.706: app-3078584000| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmblock-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.31-9-rt/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.1
Apr 01 20:56:08.695: app-3078584000| Installing module vmblock from /tmp/vmware-root/modules/vmblock.o.
Apr 01 20:56:08.696: app-3078584000| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.31-9-rt/misc/vmblock.o
Apr 01 20:56:09.542: app-3078584000| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.31-9-rt/misc/vmblock.ko
Apr 01 20:56:10.962: app-3078584000| Trying to find a suitable PBM set for kernel 2.6.31-9-rt.
Apr 01 20:56:10.962: app-3078584000| Building module vmci.
Apr 01 20:56:10.962: app-3078584000| Extracting the sources of the vmci module.
Apr 01 20:56:11.000: app-3078584000| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.31-9-rt/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.1
Apr 01 20:56:12.016: app-3078584000| Failed to compile module vmci!
Apr 01 20:56:12.025: app-3078584000| Trying to find a suitable PBM set for kernel 2.6.31-9-rt.
Apr 01 20:56:12.026: app-3078584000| Building module vmci.
Apr 01 20:56:12.026: app-3078584000| Extracting the sources of the vmci module.
Apr 01 20:56:12.043: app-3078584000| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.31-9-rt/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.1
Apr 01 20:56:13.017: app-3078584000| Failed to compile module vmci!
----end---

Thank you.

---

