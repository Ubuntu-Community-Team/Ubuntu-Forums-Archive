---
title: "vmware showing unable to start services on ubuntu 16,10"
date: 2017-02-23
forum: Virtualisation
---

### Post by anisubhra on 2017-02-23
This is the log files output i have got

```
2017-02-23T20:16:35.267+05:30| vthread-4| I125: Log for VMware Workstation pid=5248 version=12.1.1 build=build-3770994 option=Release
2017-02-23T20:16:35.267+05:30| vthread-4| I125: The process is 64-bit.
2017-02-23T20:16:35.267+05:30| vthread-4| I125: Host codepage=UTF-8 encoding=UTF-8
2017-02-23T20:16:35.267+05:30| vthread-4| I125: Host is Linux 4.8.0-37-generic Ubuntu 16.10
2017-02-23T20:16:35.267+05:30| vthread-4| I125: DictionaryLoad: Cannot open file "/usr/lib/vmware/settings": No such file or directory.
2017-02-23T20:16:35.267+05:30| vthread-4| I125: PREF Optional preferences file not found at /usr/lib/vmware/settings. Using default values.
2017-02-23T20:16:35.267+05:30| vthread-4| I125: DictionaryLoad: Cannot open file "/root/.vmware/config": No such file or directory.
2017-02-23T20:16:35.267+05:30| vthread-4| I125: PREF Optional preferences file not found at /root/.vmware/config. Using default values.
2017-02-23T20:16:35.267+05:30| vthread-4| I125: PREF Unable to check permissions for preferences file.
2017-02-23T20:16:35.267+05:30| vthread-4| I125: DictionaryLoad: Cannot open file "/root/.vmware/preferences": No such file or directory.
2017-02-23T20:16:35.267+05:30| vthread-4| I125: PREF Failed to load user preferences.
2017-02-23T20:16:35.335+05:30| vthread-4| W115: Logging to /tmp/vmware-root/vmware-5248.log
2017-02-23T20:16:35.426+05:30| vthread-4| I125: Obtaining info using the running kernel.
2017-02-23T20:16:35.426+05:30| vthread-4| I125: Created new pathsHash.
2017-02-23T20:16:35.426+05:30| vthread-4| I125: Setting header path for 4.8.0-37-generic to "/lib/modules/4.8.0-37-generic/build/include".
2017-02-23T20:16:35.426+05:30| vthread-4| I125: Validating path "/lib/modules/4.8.0-37-generic/build/include" for kernel release "4.8.0-37-generic".
2017-02-23T20:16:35.426+05:30| vthread-4| I125: Failed to find /lib/modules/4.8.0-37-generic/build/include/linux/version.h
2017-02-23T20:16:35.426+05:30| vthread-4| I125: /lib/modules/4.8.0-37-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2017-02-23T20:16:35.426+05:30| vthread-4| I125: using /usr/bin/gcc for preprocess check
2017-02-23T20:16:35.440+05:30| vthread-4| I125: Preprocessed UTS_RELEASE, got value "4.8.0-37-generic".
2017-02-23T20:16:35.440+05:30| vthread-4| I125: The header path "/lib/modules/4.8.0-37-generic/build/include" for the kernel "4.8.0-37-generic" is valid.  Whoohoo!
2017-02-23T20:16:35.685+05:30| vthread-4| I125: found symbol version file /lib/modules/4.8.0-37-generic/build/Module.symvers
2017-02-23T20:16:35.685+05:30| vthread-4| I125: Reading symbol versions from /lib/modules/4.8.0-37-generic/build/Module.symvers.
2017-02-23T20:16:35.715+05:30| vthread-4| I125: Read 20864 symbol versions
2017-02-23T20:16:35.716+05:30| vthread-4| I125: Reading in info for the vmmon module.
2017-02-23T20:16:35.716+05:30| vthread-4| I125: Reading in info for the vmnet module.
2017-02-23T20:16:35.716+05:30| vthread-4| I125: Reading in info for the vmblock module.
2017-02-23T20:16:35.716+05:30| vthread-4| I125: Reading in info for the vmci module.
2017-02-23T20:16:35.716+05:30| vthread-4| I125: Reading in info for the vsock module.
2017-02-23T20:16:35.716+05:30| vthread-4| I125: Setting vsock to depend on vmci.
2017-02-23T20:16:35.716+05:30| vthread-4| I125: Invoking modinfo on "vmmon".
2017-02-23T20:16:35.719+05:30| vthread-4| I125: "/sbin/modinfo" exited with status 256.
2017-02-23T20:16:35.719+05:30| vthread-4| I125: Invoking modinfo on "vmnet".
2017-02-23T20:16:35.723+05:30| vthread-4| I125: "/sbin/modinfo" exited with status 256.
2017-02-23T20:16:35.723+05:30| vthread-4| I125: Invoking modinfo on "vmblock".
2017-02-23T20:16:35.726+05:30| vthread-4| I125: "/sbin/modinfo" exited with status 256.
2017-02-23T20:16:35.726+05:30| vthread-4| I125: Invoking modinfo on "vmci".
2017-02-23T20:16:35.729+05:30| vthread-4| I125: "/sbin/modinfo" exited with status 256.
2017-02-23T20:16:35.729+05:30| vthread-4| I125: Invoking modinfo on "vsock".
2017-02-23T20:16:35.732+05:30| vthread-4| I125: "/sbin/modinfo" exited with status 0.
2017-02-23T20:16:35.750+05:30| vthread-4| I125: to be installed: vmmon status: 0
2017-02-23T20:16:35.750+05:30| vthread-4| I125: to be installed: vmnet status: 0
2017-02-23T20:16:35.775+05:30| vthread-4| I125: Obtaining info using the running kernel.
2017-02-23T20:16:35.775+05:30| vthread-4| I125: Setting header path for 4.8.0-37-generic to "/lib/modules/4.8.0-37-generic/build/include".
2017-02-23T20:16:35.775+05:30| vthread-4| I125: Validating path "/lib/modules/4.8.0-37-generic/build/include" for kernel release "4.8.0-37-generic".
2017-02-23T20:16:35.776+05:30| vthread-4| I125: Failed to find /lib/modules/4.8.0-37-generic/build/include/linux/version.h
2017-02-23T20:16:35.776+05:30| vthread-4| I125: /lib/modules/4.8.0-37-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2017-02-23T20:16:35.776+05:30| vthread-4| I125: using /usr/bin/gcc for preprocess check
2017-02-23T20:16:35.784+05:30| vthread-4| I125: Preprocessed UTS_RELEASE, got value "4.8.0-37-generic".
2017-02-23T20:16:35.784+05:30| vthread-4| I125: The header path "/lib/modules/4.8.0-37-generic/build/include" for the kernel "4.8.0-37-generic" is valid.  Whoohoo!
2017-02-23T20:16:36.038+05:30| vthread-4| I125: found symbol version file /lib/modules/4.8.0-37-generic/build/Module.symvers
2017-02-23T20:16:36.038+05:30| vthread-4| I125: Reading symbol versions from /lib/modules/4.8.0-37-generic/build/Module.symvers.
2017-02-23T20:16:36.068+05:30| vthread-4| I125: Read 20864 symbol versions
2017-02-23T20:16:36.068+05:30| vthread-4| I125: Kernel header path retrieved from FileEntry: /lib/modules/4.8.0-37-generic/build/include
2017-02-23T20:16:36.068+05:30| vthread-4| I125: Update kernel header path to /lib/modules/4.8.0-37-generic/build/include
2017-02-23T20:16:36.068+05:30| vthread-4| I125: Validating path "/lib/modules/4.8.0-37-generic/build/include" for kernel release "4.8.0-37-generic".
2017-02-23T20:16:36.068+05:30| vthread-4| I125: Failed to find /lib/modules/4.8.0-37-generic/build/include/linux/version.h
2017-02-23T20:16:36.068+05:30| vthread-4| I125: /lib/modules/4.8.0-37-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2017-02-23T20:16:36.068+05:30| vthread-4| I125: using /usr/bin/gcc for preprocess check
2017-02-23T20:16:36.080+05:30| vthread-4| I125: Preprocessed UTS_RELEASE, got value "4.8.0-37-generic".
2017-02-23T20:16:36.080+05:30| vthread-4| I125: The header path "/lib/modules/4.8.0-37-generic/build/include" for the kernel "4.8.0-37-generic" is valid.  Whoohoo!
2017-02-23T20:16:36.082+05:30| vthread-4| I125: Found compiler at "/usr/bin/gcc"
2017-02-23T20:16:36.087+05:30| vthread-4| I125: Got gcc version "6.2.0".
2017-02-23T20:16:36.087+05:30| vthread-4| I125: The GCC version matches the kernel GCC minor version like a glove.
2017-02-23T20:16:36.087+05:30| vthread-4| I125: Using user supplied compiler "/usr/bin/gcc".
2017-02-23T20:16:36.092+05:30| vthread-4| I125: Got gcc version "6.2.0".
2017-02-23T20:16:36.092+05:30| vthread-4| I125: The GCC version matches the kernel GCC minor version like a glove.
2017-02-23T20:16:36.093+05:30| vthread-4| I125: Trying to find a suitable PBM set for kernel "4.8.0-37-generic".
2017-02-23T20:16:36.093+05:30| vthread-4| I125: No matching PBM set was found for kernel "4.8.0-37-generic".
2017-02-23T20:16:36.094+05:30| vthread-4| I125: The GCC version matches the kernel GCC minor version like a glove.
2017-02-23T20:16:36.094+05:30| vthread-4| I125: Validating path "/lib/modules/4.8.0-37-generic/build/include" for kernel release "4.8.0-37-generic".
2017-02-23T20:16:36.094+05:30| vthread-4| I125: Failed to find /lib/modules/4.8.0-37-generic/build/include/linux/version.h
2017-02-23T20:16:36.094+05:30| vthread-4| I125: /lib/modules/4.8.0-37-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2017-02-23T20:16:36.094+05:30| vthread-4| I125: using /usr/bin/gcc for preprocess check
2017-02-23T20:16:36.106+05:30| vthread-4| I125: Preprocessed UTS_RELEASE, got value "4.8.0-37-generic".
2017-02-23T20:16:36.106+05:30| vthread-4| I125: The header path "/lib/modules/4.8.0-37-generic/build/include" for the kernel "4.8.0-37-generic" is valid.  Whoohoo!
2017-02-23T20:16:36.108+05:30| vthread-4| I125: The GCC version matches the kernel GCC minor version like a glove.
2017-02-23T20:16:36.108+05:30| vthread-4| I125: Validating path "/lib/modules/4.8.0-37-generic/build/include" for kernel release "4.8.0-37-generic".
2017-02-23T20:16:36.108+05:30| vthread-4| I125: Failed to find /lib/modules/4.8.0-37-generic/build/include/linux/version.h
2017-02-23T20:16:36.108+05:30| vthread-4| I125: /lib/modules/4.8.0-37-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2017-02-23T20:16:36.108+05:30| vthread-4| I125: using /usr/bin/gcc for preprocess check
2017-02-23T20:16:36.118+05:30| vthread-4| I125: Preprocessed UTS_RELEASE, got value "4.8.0-37-generic".
2017-02-23T20:16:36.118+05:30| vthread-4| I125: The header path "/lib/modules/4.8.0-37-generic/build/include" for the kernel "4.8.0-37-generic" is valid.  Whoohoo!
2017-02-23T20:16:36.118+05:30| vthread-4| I125: Using temp dir "/tmp".
2017-02-23T20:16:36.120+05:30| vthread-4| I125: Obtaining info using the running kernel.
2017-02-23T20:16:36.120+05:30| vthread-4| I125: Setting header path for 4.8.0-37-generic to "/lib/modules/4.8.0-37-generic/build/include".
2017-02-23T20:16:36.120+05:30| vthread-4| I125: Validating path "/lib/modules/4.8.0-37-generic/build/include" for kernel release "4.8.0-37-generic".
2017-02-23T20:16:36.120+05:30| vthread-4| I125: Failed to find /lib/modules/4.8.0-37-generic/build/include/linux/version.h
2017-02-23T20:16:36.120+05:30| vthread-4| I125: /lib/modules/4.8.0-37-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2017-02-23T20:16:36.120+05:30| vthread-4| I125: using /usr/bin/gcc for preprocess check
2017-02-23T20:16:36.128+05:30| vthread-4| I125: Preprocessed UTS_RELEASE, got value "4.8.0-37-generic".
2017-02-23T20:16:36.128+05:30| vthread-4| I125: The header path "/lib/modules/4.8.0-37-generic/build/include" for the kernel "4.8.0-37-generic" is valid.  Whoohoo!
2017-02-23T20:16:36.371+05:30| vthread-4| I125: found symbol version file /lib/modules/4.8.0-37-generic/build/Module.symvers
2017-02-23T20:16:36.371+05:30| vthread-4| I125: Reading symbol versions from /lib/modules/4.8.0-37-generic/build/Module.symvers.
2017-02-23T20:16:36.402+05:30| vthread-4| I125: Read 20864 symbol versions
2017-02-23T20:16:36.402+05:30| vthread-4| I125: Invoking modinfo on "vmmon".
2017-02-23T20:16:36.405+05:30| vthread-4| I125: "/sbin/modinfo" exited with status 256.
2017-02-23T20:16:36.405+05:30| vthread-4| I125: Invoking modinfo on "vmnet".
2017-02-23T20:16:36.410+05:30| vthread-4| I125: "/sbin/modinfo" exited with status 256.
2017-02-23T20:16:36.686+05:30| vthread-4| I125: Setting destination path for vmmon to "/lib/modules/4.8.0-37-generic/misc/vmmon.ko".
2017-02-23T20:16:36.687+05:30| vthread-4| I125: Extracting the vmmon source from "/usr/lib/vmware/modules/source/vmmon.tar".
2017-02-23T20:16:36.716+05:30| vthread-4| I125: Successfully extracted the vmmon source.
2017-02-23T20:16:36.716+05:30| vthread-4| I125: Building module with command "/usr/bin/make -j4 -C /tmp/modconfig-xCF3fp/vmmon-only auto-build HEADER_DIR=/lib/modules/4.8.0-37-generic/build/include CC=/usr/bin/gcc IS_GCC_3=no"
2017-02-23T20:16:39.492+05:30| vthread-4| W115: Failed to build vmmon.  Failed to execute the build command.
2017-02-23T20:16:39.495+05:30| vthread-4| I125: Setting destination path for vmnet to "/lib/modules/4.8.0-37-generic/misc/vmnet.ko".
2017-02-23T20:16:39.495+05:30| vthread-4| I125: Extracting the vmnet source from "/usr/lib/vmware/modules/source/vmnet.tar".
2017-02-23T20:16:39.501+05:30| vthread-4| I125: Successfully extracted the vmnet source.
2017-02-23T20:16:39.502+05:30| vthread-4| I125: Building module with command "/usr/bin/make -j4 -C /tmp/modconfig-xCF3fp/vmnet-only auto-build HEADER_DIR=/lib/modules/4.8.0-37-generic/build/include CC=/usr/bin/gcc IS_GCC_3=no"
2017-02-23T20:16:41.881+05:30| vthread-4| W115: Failed to build vmnet.  Failed to execute the build command.
```

---

### Post by howefield on 2017-02-23
Thread moved to the "*Virtualisation*" forum.

---

