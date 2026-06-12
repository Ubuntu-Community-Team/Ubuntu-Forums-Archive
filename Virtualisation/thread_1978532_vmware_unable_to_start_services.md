---
title: "vmware unable to start services"
date: 2012-05-11
forum: Virtualisation
---

### Post by Hexno on 2012-05-11
I keep getting an error when trying to install and run vmware workstation 8 64bit for linux.

I'm using the latest Kubuntu installed through the wubi.exe program.

Linux ubuntu 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

See the attached image file, it looks like I'm having issues with compiling the kernel module for the network interface. Log file below:

```

2012-05-11T22:27:30.537-05:00| vthread-3| I120: Log for VMware Workstation pid=10783 version=8.0.3 build=build-703057 option=Release
2012-05-11T22:27:30.537-05:00| vthread-3| I120: The process is 64-bit.
2012-05-11T22:27:30.537-05:00| vthread-3| I120: Host codepage=UTF-8 encoding=UTF-8
2012-05-11T22:27:30.537-05:00| vthread-3| I120: Host is Linux 3.2.0-23-generic Ubuntu 12.04 LTS
2012-05-11T22:27:30.536-05:00| vthread-3| I120: Msg_Reset:
2012-05-11T22:27:30.536-05:00| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/usr/lib/vmware/settings": No such file or directory.
2012-05-11T22:27:30.536-05:00| vthread-3| I120: ----------------------------------------
2012-05-11T22:27:30.536-05:00| vthread-3| I120: PREF Optional preferences file not found at /usr/lib/vmware/settings. Using default values.
2012-05-11T22:27:30.536-05:00| vthread-3| I120: Msg_Reset:
2012-05-11T22:27:30.536-05:00| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/root/.vmware/config": No such file or directory.
2012-05-11T22:27:30.536-05:00| vthread-3| I120: ----------------------------------------
2012-05-11T22:27:30.536-05:00| vthread-3| I120: PREF Optional preferences file not found at /root/.vmware/config. Using default values.
2012-05-11T22:27:30.536-05:00| vthread-3| I120: Msg_Reset:
2012-05-11T22:27:30.536-05:00| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/root/.vmware/preferences": No such file or directory.
2012-05-11T22:27:30.536-05:00| vthread-3| I120: ----------------------------------------
2012-05-11T22:27:30.536-05:00| vthread-3| I120: PREF Failed to load user preferences.
2012-05-11T22:27:30.537-05:00| vthread-3| W110: Logging to /tmp/vmware-root/modconfig-10783.log
2012-05-11T22:27:30.595-05:00| vthread-3| I120: modconf query interface initialized
2012-05-11T22:27:30.595-05:00| vthread-3| I120: modconf library initialized
2012-05-11T22:27:30.637-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:27:30.641-05:00| vthread-3| I120: Validating path /lib/modules/preferred/build/include for kernel release 3.2.0-23-generic
2012-05-11T22:27:30.641-05:00| vthread-3| I120: Failed to find /lib/modules/preferred/build/include/linux/version.h
2012-05-11T22:27:30.641-05:00| vthread-3| I120: Failed version test: /lib/modules/preferred/build/include/linux/version.h not found.
2012-05-11T22:27:30.641-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic
2012-05-11T22:27:30.643-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:27:30.654-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:27:30.678-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic is valid.
2012-05-11T22:27:30.678-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic
2012-05-11T22:27:30.681-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:27:30.690-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:27:30.716-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic is valid.
2012-05-11T22:27:30.740-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:30.743-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:30.746-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:30.749-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:30.752-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:30.774-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:30.777-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:30.780-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:30.783-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:30.786-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:30.789-05:00| vthread-3| I120: Validating path /lib/modules/preferred/build/include for kernel release 3.2.0-23-generic
2012-05-11T22:27:30.789-05:00| vthread-3| I120: Failed to find /lib/modules/preferred/build/include/linux/version.h
2012-05-11T22:27:30.789-05:00| vthread-3| I120: Failed version test: /lib/modules/preferred/build/include/linux/version.h not found.
2012-05-11T22:27:30.789-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic
2012-05-11T22:27:30.791-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:27:30.802-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:27:30.831-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic is valid.
2012-05-11T22:27:30.855-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:30.858-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:30.861-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:30.864-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:30.867-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:30.870-05:00| vthread-3| I120: Validating path /lib/modules/preferred/build/include for kernel release 3.2.0-23-generic
2012-05-11T22:27:30.870-05:00| vthread-3| I120: Failed to find /lib/modules/preferred/build/include/linux/version.h
2012-05-11T22:27:30.870-05:00| vthread-3| I120: Failed version test: /lib/modules/preferred/build/include/linux/version.h not found.
2012-05-11T22:27:30.870-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic
2012-05-11T22:27:30.872-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:27:30.884-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:27:30.906-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic is valid.
2012-05-11T22:27:30.947-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:30.950-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:30.953-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:30.956-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:30.959-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:31.494-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:31.494-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic
2012-05-11T22:27:31.496-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:27:31.506-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:27:31.530-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic is valid.
2012-05-11T22:27:31.530-05:00| vthread-3| I120: Building module vmmon.
2012-05-11T22:27:31.531-05:00| vthread-3| I120: Extracting the sources of the vmmon module.
2012-05-11T22:27:31.543-05:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-23-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-05-11T22:27:32.826-05:00| vthread-3| I120: Installing module vmmon from /tmp/vmware-root/modules/vmmon.o to /lib/modules/3.2.0-23-generic/misc.
2012-05-11T22:27:32.826-05:00| vthread-3| I120: Registering file: /usr/lib/vmware-installer/2.0/vmware-installer --register-file vmware-vmx regular /lib/modules/3.2.0-23-generic/misc/vmmon.ko
2012-05-11T22:27:33.724-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:33.724-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic
2012-05-11T22:27:33.726-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:27:33.737-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:27:33.761-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic is valid.
2012-05-11T22:27:33.762-05:00| vthread-3| I120: Building module vmnet.
2012-05-11T22:27:33.762-05:00| vthread-3| I120: Extracting the sources of the vmnet module.
2012-05-11T22:27:33.772-05:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmnet-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-23-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-05-11T22:27:39.374-05:00| vthread-3| I120: Failed to compile module vmnet!
2012-05-11T22:27:39.378-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:39.378-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic
2012-05-11T22:27:39.380-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:27:39.391-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:27:39.414-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic is valid.
2012-05-11T22:27:39.414-05:00| vthread-3| I120: Building module vmblock.
2012-05-11T22:27:39.414-05:00| vthread-3| I120: Extracting the sources of the vmblock module.
2012-05-11T22:27:39.426-05:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmblock-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-23-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-05-11T22:27:41.190-05:00| vthread-3| I120: Installing module vmblock from /tmp/vmware-root/modules/vmblock.o to /lib/modules/3.2.0-23-generic/misc.
2012-05-11T22:27:41.190-05:00| vthread-3| I120: Registering file: /usr/lib/vmware-installer/2.0/vmware-installer --register-file vmware-vmx regular /lib/modules/3.2.0-23-generic/misc/vmblock.ko
2012-05-11T22:27:42.011-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:42.011-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic
2012-05-11T22:27:42.013-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:27:42.023-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:27:42.052-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic is valid.
2012-05-11T22:27:42.052-05:00| vthread-3| I120: Building module vmci.
2012-05-11T22:27:42.052-05:00| vthread-3| I120: Extracting the sources of the vmci module.
2012-05-11T22:27:42.065-05:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-23-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-05-11T22:27:48.862-05:00| vthread-3| I120: Installing module vmci from /tmp/vmware-root/modules/vmci.o to /lib/modules/3.2.0-23-generic/misc.
2012-05-11T22:27:48.862-05:00| vthread-3| I120: Registering file: /usr/lib/vmware-installer/2.0/vmware-installer --register-file vmware-vmx regular /lib/modules/3.2.0-23-generic/misc/vmci.ko
2012-05-11T22:27:49.688-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:49.688-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic
2012-05-11T22:27:49.690-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:27:49.698-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:27:49.721-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic is valid.
2012-05-11T22:27:49.721-05:00| vthread-3| I120: Building module vmci.
2012-05-11T22:27:49.721-05:00| vthread-3| I120: Extracting the sources of the vmci module.
2012-05-11T22:27:49.736-05:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-23-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-05-11T22:27:50.210-05:00| vthread-3| I120: Building module vsock.
2012-05-11T22:27:50.210-05:00| vthread-3| I120: Extracting the sources of the vsock module.
2012-05-11T22:27:50.222-05:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vsock-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-23-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-05-11T22:27:51.762-05:00| vthread-3| I120: Installing module vsock from /tmp/vmware-root/modules/vsock.o to /lib/modules/3.2.0-23-generic/misc.
2012-05-11T22:27:51.763-05:00| vthread-3| I120: Registering file: /usr/lib/vmware-installer/2.0/vmware-installer --register-file vmware-vmx regular /lib/modules/3.2.0-23-generic/misc/vsock.ko
2012-05-11T22:49:19.632-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:49:19.635-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:49:19.638-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:49:19.641-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:49:19.643-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:49:19.646-05:00| vthread-3| I120: Validating path /lib/modules/preferred/build/include for kernel release 3.2.0-23-generic
2012-05-11T22:49:19.646-05:00| vthread-3| I120: Failed to find /lib/modules/preferred/build/include/linux/version.h
2012-05-11T22:49:19.646-05:00| vthread-3| I120: Failed version test: /lib/modules/preferred/build/include/linux/version.h not found.
2012-05-11T22:49:19.646-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic
2012-05-11T22:49:19.648-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:49:19.658-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:49:19.687-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic is valid.
2012-05-11T22:49:19.729-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:49:19.732-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:49:19.735-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:49:19.738-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:49:19.740-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:49:20.284-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:49:20.284-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic
2012-05-11T22:49:20.287-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:49:20.298-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:49:20.322-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic is valid.
2012-05-11T22:49:20.322-05:00| vthread-3| I120: Building module vmmon.
012-05-11T22:49:20.322-05:00| vthread-3| I120: Extracting the sources of the vmmon module.
2012-05-11T22:49:20.338-05:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-23-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-05-11T22:49:20.982-05:00| vthread-3| I120: Installing module vmmon from /tmp/vmware-root/modules/vmmon.o to /lib/modules/3.2.0-23-generic/misc.
2012-05-11T22:49:20.983-05:00| vthread-3| I120: Registering file: /usr/lib/vmware-installer/2.0/vmware-installer --register-file vmware-vmx regular /lib/modules/3.2.0-23-generic/misc/vmmon.ko
2012-05-11T22:49:21.883-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:49:21.883-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic
2012-05-11T22:49:21.886-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:49:21.897-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:49:21.919-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic is valid.
2012-05-11T22:49:21.919-05:00| vthread-3| I120: Building module vmnet.
2012-05-11T22:49:21.919-05:00| vthread-3| I120: Extracting the sources of the vmnet module.
2012-05-11T22:49:21.930-05:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmnet-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-23-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-05-11T22:49:22.886-05:00| vthread-3| I120: Failed to compile module vmnet!
2012-05-11T22:49:22.889-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:49:22.889-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic
2012-05-11T22:49:22.891-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:49:22.897-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:49:22.924-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic is valid.
2012-05-11T22:49:22.924-05:00| vthread-3| I120: Building module vmblock.
2012-05-11T22:49:22.924-05:00| vthread-3| I120: Extracting the sources of the vmblock module.
2012-05-11T22:49:22.939-05:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmblock-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-23-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-05-11T22:49:24.343-05:00| vthread-3| I120: Installing module vmblock from /tmp/vmware-root/modules/vmblock.o to /lib/modules/3.2.0-23-generic/misc.
2012-05-11T22:49:24.344-05:00| vthread-3| I120: Registering file: /usr/lib/vmware-installer/2.0/vmware-installer --register-file vmware-vmx regular /lib/modules/3.2.0-23-generic/misc/vmblock.ko
2012-05-11T22:49:25.330-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:49:25.330-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic
2012-05-11T22:49:25.333-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:49:25.343-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:49:25.371-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic is valid.
2012-05-11T22:49:25.371-05:00| vthread-3| I120: Building module vmci.
2012-05-11T22:49:25.372-05:00| vthread-3| I120: Extracting the sources of the vmci module.
2012-05-11T22:49:25.387-05:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-23-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-05-11T22:49:25.916-05:00| vthread-3| I120: Installing module vmci from /tmp/vmware-root/modules/vmci.o to /lib/modules/3.2.0-23-generic/misc.
2012-05-11T22:49:25.916-05:00| vthread-3| I120: Registering file: /usr/lib/vmware-installer/2.0/vmware-installer --register-file vmware-vmx regular /lib/modules/3.2.0-23-generic/misc/vmci.ko
2012-05-11T22:49:26.885-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:49:26.885-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic
2012-05-11T22:49:26.888-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:49:26.896-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:49:26.924-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic is valid.
2012-05-11T22:49:26.924-05:00| vthread-3| I120: Building module vmci.
2012-05-11T22:49:26.924-05:00| vthread-3| I120: Extracting the sources of the vmci module.
2012-05-11T22:49:26.939-05:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-23-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-05-11T22:49:27.453-05:00| vthread-3| I120: Building module vsock.
2012-05-11T22:49:27.453-05:00| vthread-3| I120: Extracting the sources of the vsock module.
2012-05-11T22:49:27.469-05:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vsock-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-23-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-05-11T22:49:28.212-05:00| vthread-3| I120: Installing module vsock from /tmp/vmware-root/modules/vsock.o to /lib/modules/3.2.0-23-generic/misc.
2012-05-11T22:49:28.213-05:00| vthread-3| I120: Registering file: /usr/lib/vmware-installer/2.0/vmware-installer --register-file vmware-vmx regular /lib/modules/3.2.0-23-generic/misc/vsock.ko

```

---

### Post by kako13 on 2012-05-12
Also, I have the same issue as you and has been unable to find a solution so far.

> **Hexno said:**
> I keep getting an error when trying to install and run vmware workstation 8 64bit for linux.

I'm using the latest Kubuntu installed through the wubi.exe program.

Linux ubuntu 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

See the attached image file, it looks like I'm having issues with compiling the kernel module for the network interface. Log file below:

```

2012-05-11T22:27:30.537-05:00| vthread-3| I120: Log for VMware Workstation pid=10783 version=8.0.3 build=build-703057 option=Release
2012-05-11T22:27:30.537-05:00| vthread-3| I120: The process is 64-bit.
2012-05-11T22:27:30.537-05:00| vthread-3| I120: Host codepage=UTF-8 encoding=UTF-8
2012-05-11T22:27:30.537-05:00| vthread-3| I120: Host is Linux 3.2.0-23-generic Ubuntu 12.04 LTS
2012-05-11T22:27:30.536-05:00| vthread-3| I120: Msg_Reset:
2012-05-11T22:27:30.536-05:00| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/usr/lib/vmware/settings": No such file or directory.
2012-05-11T22:27:30.536-05:00| vthread-3| I120: ----------------------------------------
2012-05-11T22:27:30.536-05:00| vthread-3| I120: PREF Optional preferences file not found at /usr/lib/vmware/settings. Using default values.
2012-05-11T22:27:30.536-05:00| vthread-3| I120: Msg_Reset:
2012-05-11T22:27:30.536-05:00| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/root/.vmware/config": No such file or directory.
2012-05-11T22:27:30.536-05:00| vthread-3| I120: ----------------------------------------
2012-05-11T22:27:30.536-05:00| vthread-3| I120: PREF Optional preferences file not found at /root/.vmware/config. Using default values.
2012-05-11T22:27:30.536-05:00| vthread-3| I120: Msg_Reset:
2012-05-11T22:27:30.536-05:00| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/root/.vmware/preferences": No such file or directory.
2012-05-11T22:27:30.536-05:00| vthread-3| I120: ----------------------------------------
2012-05-11T22:27:30.536-05:00| vthread-3| I120: PREF Failed to load user preferences.
2012-05-11T22:27:30.537-05:00| vthread-3| W110: Logging to /tmp/vmware-root/modconfig-10783.log
2012-05-11T22:27:30.595-05:00| vthread-3| I120: modconf query interface initialized
2012-05-11T22:27:30.595-05:00| vthread-3| I120: modconf library initialized
2012-05-11T22:27:30.637-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:27:30.641-05:00| vthread-3| I120: Validating path /lib/modules/preferred/build/include for kernel release 3.2.0-23-generic
2012-05-11T22:27:30.641-05:00| vthread-3| I120: Failed to find /lib/modules/preferred/build/include/linux/version.h
2012-05-11T22:27:30.641-05:00| vthread-3| I120: Failed version test: /lib/modules/preferred/build/include/linux/version.h not found.
2012-05-11T22:27:30.641-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic
2012-05-11T22:27:30.643-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:27:30.654-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:27:30.678-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic is valid.
2012-05-11T22:27:30.678-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic
2012-05-11T22:27:30.681-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:27:30.690-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:27:30.716-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic is valid.
2012-05-11T22:27:30.740-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:30.743-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:30.746-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:30.749-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:30.752-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:30.774-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:30.777-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:30.780-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:30.783-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:30.786-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:30.789-05:00| vthread-3| I120: Validating path /lib/modules/preferred/build/include for kernel release 3.2.0-23-generic
2012-05-11T22:27:30.789-05:00| vthread-3| I120: Failed to find /lib/modules/preferred/build/include/linux/version.h
2012-05-11T22:27:30.789-05:00| vthread-3| I120: Failed version test: /lib/modules/preferred/build/include/linux/version.h not found.
2012-05-11T22:27:30.789-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic
2012-05-11T22:27:30.791-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:27:30.802-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:27:30.831-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic is valid.
2012-05-11T22:27:30.855-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:30.858-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:30.861-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:30.864-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:30.867-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:30.870-05:00| vthread-3| I120: Validating path /lib/modules/preferred/build/include for kernel release 3.2.0-23-generic
2012-05-11T22:27:30.870-05:00| vthread-3| I120: Failed to find /lib/modules/preferred/build/include/linux/version.h
2012-05-11T22:27:30.870-05:00| vthread-3| I120: Failed version test: /lib/modules/preferred/build/include/linux/version.h not found.
2012-05-11T22:27:30.870-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic
2012-05-11T22:27:30.872-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:27:30.884-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:27:30.906-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic is valid.
2012-05-11T22:27:30.947-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:30.950-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:30.953-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:30.956-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:30.959-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:31.494-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:31.494-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic
2012-05-11T22:27:31.496-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:27:31.506-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:27:31.530-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic is valid.
2012-05-11T22:27:31.530-05:00| vthread-3| I120: Building module vmmon.
2012-05-11T22:27:31.531-05:00| vthread-3| I120: Extracting the sources of the vmmon module.
2012-05-11T22:27:31.543-05:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-23-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-05-11T22:27:32.826-05:00| vthread-3| I120: Installing module vmmon from /tmp/vmware-root/modules/vmmon.o to /lib/modules/3.2.0-23-generic/misc.
2012-05-11T22:27:32.826-05:00| vthread-3| I120: Registering file: /usr/lib/vmware-installer/2.0/vmware-installer --register-file vmware-vmx regular /lib/modules/3.2.0-23-generic/misc/vmmon.ko
2012-05-11T22:27:33.724-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:33.724-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic
2012-05-11T22:27:33.726-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:27:33.737-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:27:33.761-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic is valid.
2012-05-11T22:27:33.762-05:00| vthread-3| I120: Building module vmnet.
2012-05-11T22:27:33.762-05:00| vthread-3| I120: Extracting the sources of the vmnet module.
2012-05-11T22:27:33.772-05:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmnet-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-23-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-05-11T22:27:39.374-05:00| vthread-3| I120: Failed to compile module vmnet!
2012-05-11T22:27:39.378-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:39.378-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic
2012-05-11T22:27:39.380-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:27:39.391-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:27:39.414-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic is valid.
2012-05-11T22:27:39.414-05:00| vthread-3| I120: Building module vmblock.
2012-05-11T22:27:39.414-05:00| vthread-3| I120: Extracting the sources of the vmblock module.
2012-05-11T22:27:39.426-05:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmblock-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-23-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-05-11T22:27:41.190-05:00| vthread-3| I120: Installing module vmblock from /tmp/vmware-root/modules/vmblock.o to /lib/modules/3.2.0-23-generic/misc.
2012-05-11T22:27:41.190-05:00| vthread-3| I120: Registering file: /usr/lib/vmware-installer/2.0/vmware-installer --register-file vmware-vmx regular /lib/modules/3.2.0-23-generic/misc/vmblock.ko
2012-05-11T22:27:42.011-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:42.011-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic
2012-05-11T22:27:42.013-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:27:42.023-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:27:42.052-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic is valid.
2012-05-11T22:27:42.052-05:00| vthread-3| I120: Building module vmci.
2012-05-11T22:27:42.052-05:00| vthread-3| I120: Extracting the sources of the vmci module.
2012-05-11T22:27:42.065-05:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-23-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-05-11T22:27:48.862-05:00| vthread-3| I120: Installing module vmci from /tmp/vmware-root/modules/vmci.o to /lib/modules/3.2.0-23-generic/misc.
2012-05-11T22:27:48.862-05:00| vthread-3| I120: Registering file: /usr/lib/vmware-installer/2.0/vmware-installer --register-file vmware-vmx regular /lib/modules/3.2.0-23-generic/misc/vmci.ko
2012-05-11T22:27:49.688-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:27:49.688-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic
2012-05-11T22:27:49.690-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:27:49.698-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:27:49.721-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic is valid.
2012-05-11T22:27:49.721-05:00| vthread-3| I120: Building module vmci.
2012-05-11T22:27:49.721-05:00| vthread-3| I120: Extracting the sources of the vmci module.
2012-05-11T22:27:49.736-05:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-23-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-05-11T22:27:50.210-05:00| vthread-3| I120: Building module vsock.
2012-05-11T22:27:50.210-05:00| vthread-3| I120: Extracting the sources of the vsock module.
2012-05-11T22:27:50.222-05:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vsock-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-23-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-05-11T22:27:51.762-05:00| vthread-3| I120: Installing module vsock from /tmp/vmware-root/modules/vsock.o to /lib/modules/3.2.0-23-generic/misc.
2012-05-11T22:27:51.763-05:00| vthread-3| I120: Registering file: /usr/lib/vmware-installer/2.0/vmware-installer --register-file vmware-vmx regular /lib/modules/3.2.0-23-generic/misc/vsock.ko
2012-05-11T22:49:19.632-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:49:19.635-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:49:19.638-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:49:19.641-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:49:19.643-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:49:19.646-05:00| vthread-3| I120: Validating path /lib/modules/preferred/build/include for kernel release 3.2.0-23-generic
2012-05-11T22:49:19.646-05:00| vthread-3| I120: Failed to find /lib/modules/preferred/build/include/linux/version.h
2012-05-11T22:49:19.646-05:00| vthread-3| I120: Failed version test: /lib/modules/preferred/build/include/linux/version.h not found.
2012-05-11T22:49:19.646-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic
2012-05-11T22:49:19.648-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:49:19.658-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:49:19.687-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic is valid.
2012-05-11T22:49:19.729-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:49:19.732-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:49:19.735-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:49:19.738-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:49:19.740-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:49:20.284-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:49:20.284-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic
2012-05-11T22:49:20.287-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:49:20.298-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:49:20.322-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic is valid.
2012-05-11T22:49:20.322-05:00| vthread-3| I120: Building module vmmon.
012-05-11T22:49:20.322-05:00| vthread-3| I120: Extracting the sources of the vmmon module.
2012-05-11T22:49:20.338-05:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-23-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-05-11T22:49:20.982-05:00| vthread-3| I120: Installing module vmmon from /tmp/vmware-root/modules/vmmon.o to /lib/modules/3.2.0-23-generic/misc.
2012-05-11T22:49:20.983-05:00| vthread-3| I120: Registering file: /usr/lib/vmware-installer/2.0/vmware-installer --register-file vmware-vmx regular /lib/modules/3.2.0-23-generic/misc/vmmon.ko
2012-05-11T22:49:21.883-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:49:21.883-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic
2012-05-11T22:49:21.886-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:49:21.897-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:49:21.919-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic is valid.
2012-05-11T22:49:21.919-05:00| vthread-3| I120: Building module vmnet.
2012-05-11T22:49:21.919-05:00| vthread-3| I120: Extracting the sources of the vmnet module.
2012-05-11T22:49:21.930-05:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmnet-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-23-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-05-11T22:49:22.886-05:00| vthread-3| I120: Failed to compile module vmnet!
2012-05-11T22:49:22.889-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:49:22.889-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic
2012-05-11T22:49:22.891-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:49:22.897-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:49:22.924-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic is valid.
2012-05-11T22:49:22.924-05:00| vthread-3| I120: Building module vmblock.
2012-05-11T22:49:22.924-05:00| vthread-3| I120: Extracting the sources of the vmblock module.
2012-05-11T22:49:22.939-05:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmblock-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-23-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-05-11T22:49:24.343-05:00| vthread-3| I120: Installing module vmblock from /tmp/vmware-root/modules/vmblock.o to /lib/modules/3.2.0-23-generic/misc.
2012-05-11T22:49:24.344-05:00| vthread-3| I120: Registering file: /usr/lib/vmware-installer/2.0/vmware-installer --register-file vmware-vmx regular /lib/modules/3.2.0-23-generic/misc/vmblock.ko
2012-05-11T22:49:25.330-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:49:25.330-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic
2012-05-11T22:49:25.333-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:49:25.343-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:49:25.371-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic is valid.
2012-05-11T22:49:25.371-05:00| vthread-3| I120: Building module vmci.
2012-05-11T22:49:25.372-05:00| vthread-3| I120: Extracting the sources of the vmci module.
2012-05-11T22:49:25.387-05:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-23-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-05-11T22:49:25.916-05:00| vthread-3| I120: Installing module vmci from /tmp/vmware-root/modules/vmci.o to /lib/modules/3.2.0-23-generic/misc.
2012-05-11T22:49:25.916-05:00| vthread-3| I120: Registering file: /usr/lib/vmware-installer/2.0/vmware-installer --register-file vmware-vmx regular /lib/modules/3.2.0-23-generic/misc/vmci.ko
2012-05-11T22:49:26.885-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-11T22:49:26.885-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic
2012-05-11T22:49:26.888-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:49:26.896-05:00| vthread-3| I120: Your GCC version: 4.6
2012-05-11T22:49:26.924-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic is valid.
2012-05-11T22:49:26.924-05:00| vthread-3| I120: Building module vmci.
2012-05-11T22:49:26.924-05:00| vthread-3| I120: Extracting the sources of the vmci module.
2012-05-11T22:49:26.939-05:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-23-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-05-11T22:49:27.453-05:00| vthread-3| I120: Building module vsock.
2012-05-11T22:49:27.453-05:00| vthread-3| I120: Extracting the sources of the vsock module.
2012-05-11T22:49:27.469-05:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vsock-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-23-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-05-11T22:49:28.212-05:00| vthread-3| I120: Installing module vsock from /tmp/vmware-root/modules/vsock.o to /lib/modules/3.2.0-23-generic/misc.
2012-05-11T22:49:28.213-05:00| vthread-3| I120: Registering file: /usr/lib/vmware-installer/2.0/vmware-installer --register-file vmware-vmx regular /lib/modules/3.2.0-23-generic/misc/vsock.ko

```

---

### Post by kako13 on 2012-05-12
Actually I found the solution: [http://weltall.heliohost.org/wordpress/2012/01/26/vmware-workstation-8-0-2-player-4-0-2-fix-for-linux-kernel-3-2-and-3-3/](http://weltall.heliohost.org/wordpress/2012/01/26/vmware-workstation-8-0-2-player-4-0-2-fix-for-linux-kernel-3-2-and-3-3/).

If you are using the version 8.0.3 remember to modify the script accordingly.

---

### Post by Timserver on 2012-05-26
Im still having problems, but im not sure i changed the script in the correct matter sinds im a total noob :)

```
2012-05-27T01:27:54.046+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-27T01:27:54.049+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-27T01:27:54.052+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-27T01:27:54.055+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-27T01:27:54.058+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-27T01:27:54.062+01:00| vthread-3| I120: Validating path /lib/modules/preferred/build/include for kernel release 3.2.0-23-generic
2012-05-27T01:27:54.062+01:00| vthread-3| I120: Failed to find /lib/modules/preferred/build/include/linux/version.h
2012-05-27T01:27:54.062+01:00| vthread-3| I120: Failed version test: /lib/modules/preferred/build/include/linux/version.h not found.
2012-05-27T01:27:54.062+01:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic
2012-05-27T01:27:54.066+01:00| vthread-3| I120: Your GCC version: 4.6
2012-05-27T01:27:54.078+01:00| vthread-3| I120: Your GCC version: 4.6
2012-05-27T01:27:54.113+01:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic is valid.
2012-05-27T01:27:54.139+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-27T01:27:54.143+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-27T01:27:54.146+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-27T01:27:54.149+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-27T01:27:54.152+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-27T01:27:54.155+01:00| vthread-3| I120: Validating path /lib/modules/preferred/build/include for kernel release 3.2.0-23-generic
2012-05-27T01:27:54.155+01:00| vthread-3| I120: Failed to find /lib/modules/preferred/build/include/linux/version.h
2012-05-27T01:27:54.155+01:00| vthread-3| I120: Failed version test: /lib/modules/preferred/build/include/linux/version.h not found.
2012-05-27T01:27:54.155+01:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic
2012-05-27T01:27:54.159+01:00| vthread-3| I120: Your GCC version: 4.6
2012-05-27T01:27:54.171+01:00| vthread-3| I120: Your GCC version: 4.6
2012-05-27T01:27:54.206+01:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-generic/build/include for kernel release 3.2.0-23-generic is valid.
2012-05-27T01:27:54.255+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-27T01:27:54.258+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-27T01:27:54.261+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-27T01:27:54.264+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-27T01:27:54.267+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-27T01:27:54.445+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-generic.
2012-05-27T01:27:54.445+01:00| vthread-3| I120: Can't get required utilities make, tar, echo, grep, rmmod, insmod
2012-05-27T01:27:54.445+01:00| vthread-3| W110: Could not prepare build system.
```

Anyone have any ideas?

---

### Post by nb505 on 2012-06-15
Yeah.... I'm also having the exact same issue. I've tried the patch but it doesn't work, and I've scoured google for hours with no working solutions. :confused:

---

### Post by JuhazOne on 2012-06-28
The second last line suggests the problem: "Can't get required utilities make, tar, echo, grep, rmmod, insmod". Why this happens is beyond me - I imagine that these utils (except make) should be installed by default. Try checking if the utils are present in your system and the permissions are ok... Try posting here the results of running:

```
ls -l /usr/bin/make /bin/tar /bin/echo /bin/grep /sbin/rmmod /sbin/insmod
```

---

