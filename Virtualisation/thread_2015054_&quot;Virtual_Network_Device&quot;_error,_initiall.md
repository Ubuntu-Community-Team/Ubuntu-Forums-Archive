---
title: "&quot;Virtual Network Device&quot; error, initially opening VMware Player"
date: 2012-07-02
forum: Virtualisation
---

### Post by groovydaddy on 2012-07-02
I'm not sure what's going on...  I've installed VMware Player and VMware Workstation on Ubuntu Linux many times for many different people.  I've never encountered this error.  Has anyone else encountered this error?  Any suggestions?

If it matters, I'm running Ubuntu Studio 12.04 LTS 64-bit.  Thanks.

---

### Post by groovydaddy on 2012-07-02
The log file reads:

2012-07-02T21:26:32.100-05:00| vthread-3| I120: Log for VMware Workstation pid=10225 version=8.0.4 build=build-744019 option=Release
2012-07-02T21:26:32.100-05:00| vthread-3| I120: The process is 64-bit.
2012-07-02T21:26:32.100-05:00| vthread-3| I120: Host codepage=UTF-8 encoding=UTF-8
2012-07-02T21:26:32.100-05:00| vthread-3| I120: Host is Linux 3.2.0-23-lowlatency Ubuntu 12.04 LTS
2012-07-02T21:26:32.099-05:00| vthread-3| I120: Msg_Reset:
2012-07-02T21:26:32.099-05:00| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/usr/lib/vmware/settings": No such file or directory.
2012-07-02T21:26:32.099-05:00| vthread-3| I120: ----------------------------------------
2012-07-02T21:26:32.099-05:00| vthread-3| I120: PREF Optional preferences file not found at /usr/lib/vmware/settings. Using default values.
2012-07-02T21:26:32.100-05:00| vthread-3| I120: Msg_Reset:
2012-07-02T21:26:32.100-05:00| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/root/.vmware/config": No such file or directory.
2012-07-02T21:26:32.100-05:00| vthread-3| I120: ----------------------------------------
2012-07-02T21:26:32.100-05:00| vthread-3| I120: PREF Optional preferences file not found at /root/.vmware/config. Using default values.
2012-07-02T21:26:32.100-05:00| vthread-3| I120: Msg_Reset:
2012-07-02T21:26:32.100-05:00| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/root/.vmware/preferences": No such file or directory.
2012-07-02T21:26:32.100-05:00| vthread-3| I120: ----------------------------------------
2012-07-02T21:26:32.100-05:00| vthread-3| I120: PREF Failed to load user preferences.
2012-07-02T21:26:32.101-05:00| vthread-3| W110: Logging to /tmp/vmware-root/modconfig-10225.log
2012-07-02T21:26:32.171-05:00| vthread-3| I120: modconf query interface initialized
2012-07-02T21:26:32.171-05:00| vthread-3| I120: modconf library initialized
2012-07-02T21:26:32.231-05:00| vthread-3| I120: Your GCC version: 4.6
2012-07-02T21:26:32.236-05:00| vthread-3| I120: Validating path /lib/modules/preferred/build/include for kernel release 3.2.0-23-lowlatency
2012-07-02T21:26:32.236-05:00| vthread-3| I120: Failed to find /lib/modules/preferred/build/include/linux/version.h
2012-07-02T21:26:32.236-05:00| vthread-3| I120: Failed version test: /lib/modules/preferred/build/include/linux/version.h not found.
2012-07-02T21:26:32.236-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-lowlatency/build/include for kernel release 3.2.0-23-lowlatency
2012-07-02T21:26:32.239-05:00| vthread-3| I120: Your GCC version: 4.6
2012-07-02T21:26:32.254-05:00| vthread-3| I120: Your GCC version: 4.6
2012-07-02T21:26:32.287-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-lowlatency/build/include for kernel release 3.2.0-23-lowlatency is valid.
2012-07-02T21:26:32.287-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-lowlatency/build/include for kernel release 3.2.0-23-lowlatency
2012-07-02T21:26:32.291-05:00| vthread-3| I120: Your GCC version: 4.6
2012-07-02T21:26:32.301-05:00| vthread-3| I120: Your GCC version: 4.6
2012-07-02T21:26:32.326-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-lowlatency/build/include for kernel release 3.2.0-23-lowlatency is valid.
2012-07-02T21:26:32.361-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-lowlatency.
2012-07-02T21:26:32.366-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-lowlatency.
2012-07-02T21:26:32.371-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-lowlatency.
2012-07-02T21:26:32.376-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-lowlatency.
2012-07-02T21:26:32.381-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-lowlatency.
2012-07-02T21:26:32.414-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-lowlatency.
2012-07-02T21:26:32.419-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-lowlatency.
2012-07-02T21:26:32.424-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-lowlatency.
2012-07-02T21:26:32.429-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-lowlatency.
2012-07-02T21:26:32.434-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-lowlatency.
2012-07-02T21:26:32.438-05:00| vthread-3| I120: Validating path /lib/modules/preferred/build/include for kernel release 3.2.0-23-lowlatency
2012-07-02T21:26:32.438-05:00| vthread-3| I120: Failed to find /lib/modules/preferred/build/include/linux/version.h
2012-07-02T21:26:32.438-05:00| vthread-3| I120: Failed version test: /lib/modules/preferred/build/include/linux/version.h not found.
2012-07-02T21:26:32.438-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-lowlatency/build/include for kernel release 3.2.0-23-lowlatency
2012-07-02T21:26:32.441-05:00| vthread-3| I120: Your GCC version: 4.6
2012-07-02T21:26:32.456-05:00| vthread-3| I120: Your GCC version: 4.6
2012-07-02T21:26:32.489-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-lowlatency/build/include for kernel release 3.2.0-23-lowlatency is valid.
2012-07-02T21:26:32.516-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-lowlatency.
2012-07-02T21:26:32.521-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-lowlatency.
2012-07-02T21:26:32.526-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-lowlatency.
2012-07-02T21:26:32.531-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-lowlatency.
2012-07-02T21:26:32.536-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-lowlatency.
2012-07-02T21:26:32.540-05:00| vthread-3| I120: Validating path /lib/modules/preferred/build/include for kernel release 3.2.0-23-lowlatency
2012-07-02T21:26:32.540-05:00| vthread-3| I120: Failed to find /lib/modules/preferred/build/include/linux/version.h
2012-07-02T21:26:32.540-05:00| vthread-3| I120: Failed version test: /lib/modules/preferred/build/include/linux/version.h not found.
2012-07-02T21:26:32.540-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-lowlatency/build/include for kernel release 3.2.0-23-lowlatency
2012-07-02T21:26:32.543-05:00| vthread-3| I120: Your GCC version: 4.6
2012-07-02T21:26:32.558-05:00| vthread-3| I120: Your GCC version: 4.6
2012-07-02T21:26:32.590-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-lowlatency/build/include for kernel release 3.2.0-23-lowlatency is valid.
2012-07-02T21:26:32.651-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-lowlatency.
2012-07-02T21:26:32.657-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-lowlatency.
2012-07-02T21:26:32.662-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-lowlatency.
2012-07-02T21:26:32.667-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-lowlatency.
2012-07-02T21:26:32.672-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-lowlatency.
2012-07-02T21:26:32.970-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-lowlatency.
2012-07-02T21:26:32.971-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-lowlatency/build/include for kernel release 3.2.0-23-lowlatency
2012-07-02T21:26:32.974-05:00| vthread-3| I120: Your GCC version: 4.6
2012-07-02T21:26:32.984-05:00| vthread-3| I120: Your GCC version: 4.6
2012-07-02T21:26:33.016-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-lowlatency/build/include for kernel release 3.2.0-23-lowlatency is valid.
2012-07-02T21:26:33.016-05:00| vthread-3| I120: Building module vmmon.
2012-07-02T21:26:33.016-05:00| vthread-3| I120: Extracting the sources of the vmmon module.
2012-07-02T21:26:33.030-05:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-23-lowlatency/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-07-02T21:26:36.490-05:00| vthread-3| I120: Installing module vmmon from /tmp/vmware-root/modules/vmmon.o to /lib/modules/3.2.0-23-lowlatency/misc.
2012-07-02T21:26:36.491-05:00| vthread-3| I120: Registering file: /usr/lib/vmware-installer/2.0/vmware-installer --register-file vmware-vmx regular /lib/modules/3.2.0-23-lowlatency/misc/vmmon.ko
2012-07-02T21:26:37.668-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-lowlatency.
2012-07-02T21:26:37.668-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-lowlatency/build/include for kernel release 3.2.0-23-lowlatency
2012-07-02T21:26:37.674-05:00| vthread-3| I120: Your GCC version: 4.6
2012-07-02T21:26:37.684-05:00| vthread-3| I120: Your GCC version: 4.6
2012-07-02T21:26:37.710-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-lowlatency/build/include for kernel release 3.2.0-23-lowlatency is valid.
2012-07-02T21:26:37.710-05:00| vthread-3| I120: Building module vmnet.
2012-07-02T21:26:37.710-05:00| vthread-3| I120: Extracting the sources of the vmnet module.
2012-07-02T21:26:37.719-05:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmnet-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-23-lowlatency/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-07-02T21:26:40.457-05:00| vthread-3| I120: Failed to compile module vmnet!
2012-07-02T21:26:40.463-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-lowlatency.
2012-07-02T21:26:40.463-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-lowlatency/build/include for kernel release 3.2.0-23-lowlatency
2012-07-02T21:26:40.465-05:00| vthread-3| I120: Your GCC version: 4.6
2012-07-02T21:26:40.481-05:00| vthread-3| I120: Your GCC version: 4.6
2012-07-02T21:26:40.523-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-lowlatency/build/include for kernel release 3.2.0-23-lowlatency is valid.
2012-07-02T21:26:40.523-05:00| vthread-3| I120: Building module vmblock.
2012-07-02T21:26:40.523-05:00| vthread-3| I120: Extracting the sources of the vmblock module.
2012-07-02T21:26:40.541-05:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmblock-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-23-lowlatency/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-07-02T21:26:46.038-05:00| vthread-3| I120: Installing module vmblock from /tmp/vmware-root/modules/vmblock.o to /lib/modules/3.2.0-23-lowlatency/misc.
2012-07-02T21:26:46.039-05:00| vthread-3| I120: Registering file: /usr/lib/vmware-installer/2.0/vmware-installer --register-file vmware-vmx regular /lib/modules/3.2.0-23-lowlatency/misc/vmblock.ko
2012-07-02T21:26:47.157-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-lowlatency.
2012-07-02T21:26:47.157-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-lowlatency/build/include for kernel release 3.2.0-23-lowlatency
2012-07-02T21:26:47.160-05:00| vthread-3| I120: Your GCC version: 4.6
2012-07-02T21:26:47.176-05:00| vthread-3| I120: Your GCC version: 4.6
2012-07-02T21:26:47.207-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-lowlatency/build/include for kernel release 3.2.0-23-lowlatency is valid.
2012-07-02T21:26:47.207-05:00| vthread-3| I120: Building module vmci.
2012-07-02T21:26:47.207-05:00| vthread-3| I120: Extracting the sources of the vmci module.
2012-07-02T21:26:47.220-05:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-23-lowlatency/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-07-02T21:26:50.228-05:00| vthread-3| I120: Installing module vmci from /tmp/vmware-root/modules/vmci.o to /lib/modules/3.2.0-23-lowlatency/misc.
2012-07-02T21:26:50.228-05:00| vthread-3| I120: Registering file: /usr/lib/vmware-installer/2.0/vmware-installer --register-file vmware-vmx regular /lib/modules/3.2.0-23-lowlatency/misc/vmci.ko
2012-07-02T21:26:51.421-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-23-lowlatency.
2012-07-02T21:26:51.422-05:00| vthread-3| I120: Validating path /lib/modules/3.2.0-23-lowlatency/build/include for kernel release 3.2.0-23-lowlatency
2012-07-02T21:26:51.427-05:00| vthread-3| I120: Your GCC version: 4.6
2012-07-02T21:26:51.440-05:00| vthread-3| I120: Your GCC version: 4.6
2012-07-02T21:26:51.465-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-23-lowlatency/build/include for kernel release 3.2.0-23-lowlatency is valid.
2012-07-02T21:26:51.465-05:00| vthread-3| I120: Building module vmci.
2012-07-02T21:26:51.465-05:00| vthread-3| I120: Extracting the sources of the vmci module.
2012-07-02T21:26:51.477-05:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-23-lowlatency/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-07-02T21:26:52.019-05:00| vthread-3| I120: Building module vsock.
2012-07-02T21:26:52.019-05:00| vthread-3| I120: Extracting the sources of the vsock module.
2012-07-02T21:26:52.038-05:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vsock-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-23-lowlatency/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-07-02T21:26:54.996-05:00| vthread-3| I120: Installing module vsock from /tmp/vmware-root/modules/vsock.o to /lib/modules/3.2.0-23-lowlatency/misc.
2012-07-02T21:26:54.997-05:00| vthread-3| I120: Registering file: /usr/lib/vmware-installer/2.0/vmware-installer --register-file vmware-vmx regular /lib/modules/3.2.0-23-lowlatency/misc/vsock.ko

---

### Post by RikoW on 2012-07-06
Hi,

there seems to be a long standing incompatibility with the Ubuntu kernels and recent releases of VMware. I can't unterstand, how VMware can afford not to fix that themselves. Anyway, you need to patch the VMware modules:

[http://weltall.heliohost.org/wordpress/2012/01/26/vmware-workstation-8-0-2-player-4-0-2-fix-for-linux-kernel-3-2-and-3-3/]("http://weltall.heliohost.org/wordpress/2012/01/26/vmware-workstation-8-0-2-player-4-0-2-fix-for-linux-kernel-3-2-and-3-3/")

This says for VMware WS8.0.2, but I applied it to most recent release (WS8.0.4, Player 4.0.4) and it still works.

Good luck,

         Riko

---

### Post by fjgaude on 2012-07-12
It would seem VMware corporation simply doesn't expect people to update Linux kernels beyond for what their software works. <sigh>

---

### Post by dcstar on 2012-07-24
> **fjgaude said:**
> It would seem VMware corporation simply doesn't expect people to update Linux kernels beyond for what their software works. <sigh>

All it means is that VMware - a commercial operation - do not immediately update their products once a new Linux version is released, but they do eventually. Supporting the bleeding edge of Linux is probably a trivial low-priority task for them.

The patches for this particular have been available for ages and are easily found and implemented by most Linux users sophisticated enough to utilise Virtualisation.

I am quite happy that VMware allow me to use - for free - such powerful products like Player and ESXi and any inconvenience of waiting a few months after a new Ubuntu release to use VMware products "out of the box" is trivial.

---

