---
title: "VMware Kernel Module updater not installed"
date: 2014-07-17
forum: Virtualisation
---

### Post by bahtiyar on 2014-07-17
&#305; am using ubuntu 12.04 linux 13.10

Vmware workstation not start up.  it set up kernel module updater and then some problem is given picture

---

### Post by JohnAreBee on 2014-07-20
> **bahtiyar said:**
> &#305; am using ubuntu 12.04 linux 13.10

Vmware workstation not start up.  it set up kernel module updater and then some problem is given picture

Give me some more detailed info please,
**System Build** *(run this in terminal post output)*: lsb_release -a 
**Kernel Build** *(run this in terminal post output)*: uname -a
**VM Workstation Build** *(run this in terminal post output)*: vmware -v

---

### Post by bahtiyar on 2014-07-23
:~$  lsb_release -a 
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.4 LTS
Release:	12.04
Codename:	precise




 ~$  uname -aLinux biochemistry-CASPER-NIRVANA 3.13.0-32-generic #57~precise1-Ubuntu SMP Tue Jul 15 03:51:20 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


~$ vmware -v
VMware Workstation 10.0.1 build-1379776

---

### Post by cecilieaux on 2014-07-25
> Before you can run VMware, several modules must be compiled and loaded into the running kernel

The it starts compiling them four things:

Stopping VMware services OK

Virtual Network Device  ... gets a red ! (CRASH)

Reunning Depmod OK

Starting VMware services ... gets a red ! (CRASH)

Then it says

> Unable to start services.

See log file /tmp/vmware-root/vmware-modconfig-5606.log for details.

This, of course, requires root!!!!> 

2014-07-25T20:02:02.160-05:00| vthread-3| I120: Log for VMware Workstation pid=5606 version=10.0.1 build=build-1379776 option=Release
2014-07-25T20:02:02.160-05:00| vthread-3| I120: The process is 32-bit.
2014-07-25T20:02:02.160-05:00| vthread-3| I120: Host codepage=UTF-8 encoding=UTF-8
2014-07-25T20:02:02.160-05:00| vthread-3| I120: Host is Linux 3.13.0-32-generic Ubuntu 14.04.1 LTS
2014-07-25T20:02:02.160-05:00| vthread-3| I120: Msg_Reset:
2014-07-25T20:02:02.160-05:00| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/usr/lib/vmware/settings": No such file or directory.
2014-07-25T20:02:02.160-05:00| vthread-3| I120: ----------------------------------------
2014-07-25T20:02:02.160-05:00| vthread-3| I120: PREF Optional preferences file not found at /usr/lib/vmware/settings. Using default values.
2014-07-25T20:02:02.160-05:00| vthread-3| I120: Msg_Reset:
2014-07-25T20:02:02.160-05:00| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/root/.vmware/config": No such file or directory.
2014-07-25T20:02:02.160-05:00| vthread-3| I120: ----------------------------------------
2014-07-25T20:02:02.160-05:00| vthread-3| I120: PREF Optional preferences file not found at /root/.vmware/config. Using default values.
2014-07-25T20:02:02.160-05:00| vthread-3| I120: PREF Unable to check permissions for preferences file.
2014-07-25T20:02:02.160-05:00| vthread-3| I120: Msg_Reset:
2014-07-25T20:02:02.160-05:00| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/root/.vmware/preferences": No such file or directory.
2014-07-25T20:02:02.160-05:00| vthread-3| I120: ----------------------------------------
2014-07-25T20:02:02.160-05:00| vthread-3| I120: PREF Failed to load user preferences.
2014-07-25T20:02:02.161-05:00| vthread-3| W110: Logging to /tmp/vmware-root/vmware-modconfig-5606.log
2014-07-25T20:02:02.180-05:00| vthread-3| I120: Obtaining info using the running kernel.
2014-07-25T20:02:02.180-05:00| vthread-3| I120: Created new pathsHash.
2014-07-25T20:02:02.180-05:00| vthread-3| I120: Setting header path for 3.13.0-32-generic to "/lib/modules/3.13.0-32-generic/build/include".
2014-07-25T20:02:02.180-05:00| vthread-3| I120: Validating path "/lib/modules/3.13.0-32-generic/build/include" for kernel release "3.13.0-32-generic".
2014-07-25T20:02:02.180-05:00| vthread-3| I120: Failed to find /lib/modules/3.13.0-32-generic/build/include/linux/version.h
2014-07-25T20:02:02.180-05:00| vthread-3| I120: /lib/modules/3.13.0-32-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2014-07-25T20:02:02.180-05:00| vthread-3| I120: using /usr/bin/gcc-4.8 for preprocess check
2014-07-25T20:02:02.186-05:00| vthread-3| I120: Preprocessed UTS_RELEASE, got value "3.13.0-32-generic".
2014-07-25T20:02:02.187-05:00| vthread-3| I120: The header path "/lib/modules/3.13.0-32-generic/build/include" for the kernel "3.13.0-32-generic" is valid.  Whoohoo!
2014-07-25T20:02:02.280-05:00| vthread-3| I120: Reading in info for the vmmon module.
2014-07-25T20:02:02.280-05:00| vthread-3| I120: Reading in info for the vmnet module.
2014-07-25T20:02:02.280-05:00| vthread-3| I120: Reading in info for the vmblock module.
2014-07-25T20:02:02.280-05:00| vthread-3| I120: Reading in info for the vmci module.
2014-07-25T20:02:02.280-05:00| vthread-3| I120: Reading in info for the vsock module.
2014-07-25T20:02:02.280-05:00| vthread-3| I120: Setting vsock to depend on vmci.
2014-07-25T20:02:02.280-05:00| vthread-3| I120: Invoking modinfo on "vmmon".
2014-07-25T20:02:02.282-05:00| vthread-3| I120: "/sbin/modinfo" exited with status 0.
2014-07-25T20:02:02.282-05:00| vthread-3| I120: Invoking modinfo on "vmnet".
2014-07-25T20:02:02.283-05:00| vthread-3| I120: "/sbin/modinfo" exited with status 256.
2014-07-25T20:02:02.283-05:00| vthread-3| I120: Invoking modinfo on "vmblock".
2014-07-25T20:02:02.285-05:00| vthread-3| I120: "/sbin/modinfo" exited with status 256.
2014-07-25T20:02:02.285-05:00| vthread-3| I120: Invoking modinfo on "vmci".
2014-07-25T20:02:02.286-05:00| vthread-3| I120: "/sbin/modinfo" exited with status 256.
2014-07-25T20:02:02.286-05:00| vthread-3| I120: Invoking modinfo on "vsock".
2014-07-25T20:02:02.288-05:00| vthread-3| I120: "/sbin/modinfo" exited with status 0.
2014-07-25T20:02:02.305-05:00| vthread-3| I120: to be installed: vmnet status: 0
2014-07-25T20:02:02.323-05:00| vthread-3| I120: Obtaining info using the running kernel.
2014-07-25T20:02:02.323-05:00| vthread-3| I120: Setting header path for 3.13.0-32-generic to "/lib/modules/3.13.0-32-generic/build/include".
2014-07-25T20:02:02.323-05:00| vthread-3| I120: Validating path "/lib/modules/3.13.0-32-generic/build/include" for kernel release "3.13.0-32-generic".
2014-07-25T20:02:02.323-05:00| vthread-3| I120: Failed to find /lib/modules/3.13.0-32-generic/build/include/linux/version.h
2014-07-25T20:02:02.323-05:00| vthread-3| I120: /lib/modules/3.13.0-32-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2014-07-25T20:02:02.323-05:00| vthread-3| I120: using /usr/bin/gcc-4.8 for preprocess check
2014-07-25T20:02:02.329-05:00| vthread-3| I120: Preprocessed UTS_RELEASE, got value "3.13.0-32-generic".
2014-07-25T20:02:02.329-05:00| vthread-3| I120: The header path "/lib/modules/3.13.0-32-generic/build/include" for the kernel "3.13.0-32-generic" is valid.  Whoohoo!
2014-07-25T20:02:02.422-05:00| vthread-3| I120: Kernel header path retrieved from FileEntry: /lib/modules/3.13.0-32-generic/build/include
2014-07-25T20:02:02.422-05:00| vthread-3| I120: Update kernel header path to /lib/modules/3.13.0-32-generic/build/include
2014-07-25T20:02:02.422-05:00| vthread-3| I120: Validating path "/lib/modules/3.13.0-32-generic/build/include" for kernel release "3.13.0-32-generic".
2014-07-25T20:02:02.422-05:00| vthread-3| I120: Failed to find /lib/modules/3.13.0-32-generic/build/include/linux/version.h
2014-07-25T20:02:02.422-05:00| vthread-3| I120: /lib/modules/3.13.0-32-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2014-07-25T20:02:02.422-05:00| vthread-3| I120: using /usr/bin/gcc-4.8 for preprocess check
2014-07-25T20:02:02.428-05:00| vthread-3| I120: Preprocessed UTS_RELEASE, got value "3.13.0-32-generic".
2014-07-25T20:02:02.429-05:00| vthread-3| I120: The header path "/lib/modules/3.13.0-32-generic/build/include" for the kernel "3.13.0-32-generic" is valid.  Whoohoo!
2014-07-25T20:02:02.430-05:00| vthread-3| I120: Found compiler at "/usr/bin/gcc"
2014-07-25T20:02:02.432-05:00| vthread-3| I120: Got gcc version "4.8".
2014-07-25T20:02:02.432-05:00| vthread-3| I120: The GCC version matches the kernel GCC minor version like a glove.
2014-07-25T20:02:02.433-05:00| vthread-3| I120: Using user supplied compiler "/usr/bin/gcc".
2014-07-25T20:02:02.435-05:00| vthread-3| I120: Got gcc version "4.8".
2014-07-25T20:02:02.435-05:00| vthread-3| I120: The GCC version matches the kernel GCC minor version like a glove.
2014-07-25T20:02:02.439-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel "3.13.0-32-generic".
2014-07-25T20:02:02.439-05:00| vthread-3| I120: No matching PBM set was found for kernel "3.13.0-32-generic".
2014-07-25T20:02:02.439-05:00| vthread-3| I120: The GCC version matches the kernel GCC minor version like a glove.
2014-07-25T20:02:02.439-05:00| vthread-3| I120: Validating path "/lib/modules/3.13.0-32-generic/build/include" for kernel release "3.13.0-32-generic".
2014-07-25T20:02:02.439-05:00| vthread-3| I120: Failed to find /lib/modules/3.13.0-32-generic/build/include/linux/version.h
2014-07-25T20:02:02.439-05:00| vthread-3| I120: /lib/modules/3.13.0-32-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2014-07-25T20:02:02.439-05:00| vthread-3| I120: using /usr/bin/gcc-4.8 for preprocess check
2014-07-25T20:02:02.445-05:00| vthread-3| I120: Preprocessed UTS_RELEASE, got value "3.13.0-32-generic".
2014-07-25T20:02:02.445-05:00| vthread-3| I120: The header path "/lib/modules/3.13.0-32-generic/build/include" for the kernel "3.13.0-32-generic" is valid.  Whoohoo!
2014-07-25T20:02:02.470-05:00| vthread-3| I120: The GCC version matches the kernel GCC minor version like a glove.
2014-07-25T20:02:02.471-05:00| vthread-3| I120: Validating path "/lib/modules/3.13.0-32-generic/build/include" for kernel release "3.13.0-32-generic".
2014-07-25T20:02:02.471-05:00| vthread-3| I120: Failed to find /lib/modules/3.13.0-32-generic/build/include/linux/version.h
2014-07-25T20:02:02.471-05:00| vthread-3| I120: /lib/modules/3.13.0-32-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2014-07-25T20:02:02.471-05:00| vthread-3| I120: using /usr/bin/gcc-4.8 for preprocess check
2014-07-25T20:02:02.477-05:00| vthread-3| I120: Preprocessed UTS_RELEASE, got value "3.13.0-32-generic".
2014-07-25T20:02:02.477-05:00| vthread-3| I120: The header path "/lib/modules/3.13.0-32-generic/build/include" for the kernel "3.13.0-32-generic" is valid.  Whoohoo!
2014-07-25T20:02:02.477-05:00| vthread-3| I120: Using temp dir "/tmp".
2014-07-25T20:02:02.478-05:00| vthread-3| I120: Obtaining info using the running kernel.
2014-07-25T20:02:02.478-05:00| vthread-3| I120: Setting header path for 3.13.0-32-generic to "/lib/modules/3.13.0-32-generic/build/include".
2014-07-25T20:02:02.478-05:00| vthread-3| I120: Validating path "/lib/modules/3.13.0-32-generic/build/include" for kernel release "3.13.0-32-generic".
2014-07-25T20:02:02.478-05:00| vthread-3| I120: Failed to find /lib/modules/3.13.0-32-generic/build/include/linux/version.h
2014-07-25T20:02:02.478-05:00| vthread-3| I120: /lib/modules/3.13.0-32-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2014-07-25T20:02:02.478-05:00| vthread-3| I120: using /usr/bin/gcc-4.8 for preprocess check
2014-07-25T20:02:02.484-05:00| vthread-3| I120: Preprocessed UTS_RELEASE, got value "3.13.0-32-generic".
2014-07-25T20:02:02.484-05:00| vthread-3| I120: The header path "/lib/modules/3.13.0-32-generic/build/include" for the kernel "3.13.0-32-generic" is valid.  Whoohoo!
2014-07-25T20:02:02.576-05:00| vthread-3| I120: Invoking modinfo on "vmnet".
2014-07-25T20:02:02.579-05:00| vthread-3| I120: "/sbin/modinfo" exited with status 256.
2014-07-25T20:02:04.099-05:00| vthread-3| I120: Setting destination path for vmnet to "/lib/modules/3.13.0-32-generic/misc/vmnet.ko".
2014-07-25T20:02:04.108-05:00| vthread-3| I120: Extracting the vmnet source from "/usr/lib/vmware/modules/source/vmnet.tar".
2014-07-25T20:02:04.155-05:00| vthread-3| I120: Successfully extracted the vmnet source.
2014-07-25T20:02:04.155-05:00| vthread-3| I120: Building module with command "/usr/bin/make -j2 -C /tmp/modconfig-IqrjJX/vmnet-only auto-build HEADER_DIR=/lib/modules/3.13.0-32-generic/build/include CC=/usr/bin/gcc IS_GCC_3=no"
2014-07-25T20:02:13.364-05:00| vthread-3| W110: Failed to build vmnet.  Failed to execute the build command.

So, here we are ... and VMware bites the dust

---

