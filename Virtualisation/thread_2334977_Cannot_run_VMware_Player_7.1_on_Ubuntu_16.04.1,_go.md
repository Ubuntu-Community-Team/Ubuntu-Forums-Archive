---
title: "Cannot run VMware Player 7.1 on Ubuntu 16.04.1, got error message."
date: 2016-08-24
forum: Virtualisation
---

### Post by fromwin2lin on 2016-08-24
When I try to run VMware Player 7.1 on Ubuntu 16.04, I get the following error message: Unable to start services. See log file /tmp/vmware-root/vmware-18502.log for details.

Does anybody know how to fix this?

---

### Post by howefield on 2016-08-24
Thread moved to the "*Virtualisation*" forum for a better fit.

What does the log file say ?

---

### Post by ajgreeny on 2016-08-24
So what is the content of the log at **/tmp/vmware-root/vmware-18502.log**?

That might give you some clues.

---

### Post by fromwin2lin on 2016-08-24
```
2016-08-24T12:23:35.572-04:00| vthread-4| I120: Log for VMware Workstation pid=24480 version=11.1.0 build=build-2496824 option=Release
2016-08-24T12:23:35.572-04:00| vthread-4| I120: The process is 64-bit.
2016-08-24T12:23:35.572-04:00| vthread-4| I120: Host codepage=UTF-8 encoding=UTF-8
2016-08-24T12:23:35.572-04:00| vthread-4| I120: Host is Linux 4.4.0-31-generic Ubuntu 16.04.1 LTS
2016-08-24T12:23:35.571-04:00| vthread-4| I120: DictionaryLoad: Cannot open file "/usr/lib/vmware/settings": No such file or directory.
2016-08-24T12:23:35.571-04:00| vthread-4| I120: Msg_Reset:
2016-08-24T12:23:35.571-04:00| vthread-4| I120: [msg.dictionary.load.openFailed] Cannot open file "/usr/lib/vmware/settings": No such file or directory.
2016-08-24T12:23:35.572-04:00| vthread-4| I120: ----------------------------------------
2016-08-24T12:23:35.572-04:00| vthread-4| I120: PREF Optional preferences file not found at /usr/lib/vmware/settings. Using default values.
2016-08-24T12:23:35.572-04:00| vthread-4| I120: DictionaryLoad: Cannot open file "/root/.vmware/config": No such file or directory.
2016-08-24T12:23:35.572-04:00| vthread-4| I120: Msg_Reset:
2016-08-24T12:23:35.572-04:00| vthread-4| I120: [msg.dictionary.load.openFailed] Cannot open file "/root/.vmware/config": No such file or directory.
2016-08-24T12:23:35.572-04:00| vthread-4| I120: ----------------------------------------
2016-08-24T12:23:35.572-04:00| vthread-4| I120: PREF Optional preferences file not found at /root/.vmware/config. Using default values.
2016-08-24T12:23:35.572-04:00| vthread-4| I120: PREF Unable to check permissions for preferences file.
2016-08-24T12:23:35.572-04:00| vthread-4| I120: DictionaryLoad: Cannot open file "/root/.vmware/preferences": No such file or directory.
2016-08-24T12:23:35.572-04:00| vthread-4| I120: Msg_Reset:
2016-08-24T12:23:35.572-04:00| vthread-4| I120: [msg.dictionary.load.openFailed] Cannot open file "/root/.vmware/preferences": No such file or directory.
2016-08-24T12:23:35.572-04:00| vthread-4| I120: ----------------------------------------
2016-08-24T12:23:35.572-04:00| vthread-4| I120: PREF Failed to load user preferences.
2016-08-24T12:23:35.660-04:00| vthread-4| W110: Logging to /tmp/vmware-root/vmware-24480.log
2016-08-24T12:23:35.682-04:00| vthread-4| I120: Obtaining info using the running kernel.
2016-08-24T12:23:35.682-04:00| vthread-4| I120: Created new pathsHash.
2016-08-24T12:23:35.682-04:00| vthread-4| I120: Setting header path for 4.4.0-31-generic to "/lib/modules/4.4.0-31-generic/build/include".
2016-08-24T12:23:35.682-04:00| vthread-4| I120: Validating path "/lib/modules/4.4.0-31-generic/build/include" for kernel release "4.4.0-31-generic".
2016-08-24T12:23:35.682-04:00| vthread-4| I120: Failed to find /lib/modules/4.4.0-31-generic/build/include/linux/version.h
2016-08-24T12:23:35.682-04:00| vthread-4| I120: /lib/modules/4.4.0-31-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2016-08-24T12:23:35.682-04:00| vthread-4| I120: using /usr/bin/gcc for preprocess check
2016-08-24T12:23:35.694-04:00| vthread-4| I120: Preprocessed UTS_RELEASE, got value "4.4.0-31-generic".
2016-08-24T12:23:35.694-04:00| vthread-4| I120: The header path "/lib/modules/4.4.0-31-generic/build/include" for the kernel "4.4.0-31-generic" is valid.  Whoohoo!
2016-08-24T12:23:35.915-04:00| vthread-4| I120: found symbol version file /lib/modules/4.4.0-31-generic/build/Module.symvers
2016-08-24T12:23:35.915-04:00| vthread-4| I120: Reading symbol versions from /lib/modules/4.4.0-31-generic/build/Module.symvers.
2016-08-24T12:23:35.939-04:00| vthread-4| I120: Read 18767 symbol versions
2016-08-24T12:23:35.940-04:00| vthread-4| I120: Reading in info for the vmmon module.
2016-08-24T12:23:35.940-04:00| vthread-4| I120: Reading in info for the vmnet module.
2016-08-24T12:23:35.940-04:00| vthread-4| I120: Reading in info for the vmblock module.
2016-08-24T12:23:35.940-04:00| vthread-4| I120: Reading in info for the vmci module.
2016-08-24T12:23:35.940-04:00| vthread-4| I120: Reading in info for the vsock module.
2016-08-24T12:23:35.940-04:00| vthread-4| I120: Setting vsock to depend on vmci.
2016-08-24T12:23:35.940-04:00| vthread-4| I120: Invoking modinfo on "vmmon".
2016-08-24T12:23:35.942-04:00| vthread-4| I120: "/sbin/modinfo" exited with status 256.
2016-08-24T12:23:35.942-04:00| vthread-4| I120: Invoking modinfo on "vmnet".
2016-08-24T12:23:35.945-04:00| vthread-4| I120: "/sbin/modinfo" exited with status 256.
2016-08-24T12:23:35.945-04:00| vthread-4| I120: Invoking modinfo on "vmblock".
2016-08-24T12:23:35.949-04:00| vthread-4| I120: "/sbin/modinfo" exited with status 256.
2016-08-24T12:23:35.949-04:00| vthread-4| I120: Invoking modinfo on "vmci".
2016-08-24T12:23:35.953-04:00| vthread-4| I120: "/sbin/modinfo" exited with status 256.
2016-08-24T12:23:35.953-04:00| vthread-4| I120: Invoking modinfo on "vsock".
2016-08-24T12:23:35.956-04:00| vthread-4| I120: "/sbin/modinfo" exited with status 0.
2016-08-24T12:23:35.975-04:00| vthread-4| I120: to be installed: vmmon status: 0
2016-08-24T12:23:35.975-04:00| vthread-4| I120: to be installed: vmnet status: 0
2016-08-24T12:23:36.000-04:00| vthread-4| I120: Obtaining info using the running kernel.
2016-08-24T12:23:36.000-04:00| vthread-4| I120: Setting header path for 4.4.0-31-generic to "/lib/modules/4.4.0-31-generic/build/include".
2016-08-24T12:23:36.000-04:00| vthread-4| I120: Validating path "/lib/modules/4.4.0-31-generic/build/include" for kernel release "4.4.0-31-generic".
2016-08-24T12:23:36.000-04:00| vthread-4| I120: Failed to find /lib/modules/4.4.0-31-generic/build/include/linux/version.h
2016-08-24T12:23:36.000-04:00| vthread-4| I120: /lib/modules/4.4.0-31-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2016-08-24T12:23:36.000-04:00| vthread-4| I120: using /usr/bin/gcc for preprocess check
2016-08-24T12:23:36.006-04:00| vthread-4| I120: Preprocessed UTS_RELEASE, got value "4.4.0-31-generic".
2016-08-24T12:23:36.006-04:00| vthread-4| I120: The header path "/lib/modules/4.4.0-31-generic/build/include" for the kernel "4.4.0-31-generic" is valid.  Whoohoo!
2016-08-24T12:23:36.195-04:00| vthread-4| I120: found symbol version file /lib/modules/4.4.0-31-generic/build/Module.symvers
2016-08-24T12:23:36.195-04:00| vthread-4| I120: Reading symbol versions from /lib/modules/4.4.0-31-generic/build/Module.symvers.
2016-08-24T12:23:36.219-04:00| vthread-4| I120: Read 18767 symbol versions
2016-08-24T12:23:36.219-04:00| vthread-4| I120: Kernel header path retrieved from FileEntry: /lib/modules/4.4.0-31-generic/build/include
2016-08-24T12:23:36.219-04:00| vthread-4| I120: Update kernel header path to /lib/modules/4.4.0-31-generic/build/include
2016-08-24T12:23:36.219-04:00| vthread-4| I120: Validating path "/lib/modules/4.4.0-31-generic/build/include" for kernel release "4.4.0-31-generic".
2016-08-24T12:23:36.219-04:00| vthread-4| I120: Failed to find /lib/modules/4.4.0-31-generic/build/include/linux/version.h
2016-08-24T12:23:36.219-04:00| vthread-4| I120: /lib/modules/4.4.0-31-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2016-08-24T12:23:36.219-04:00| vthread-4| I120: using /usr/bin/gcc for preprocess check
2016-08-24T12:23:36.226-04:00| vthread-4| I120: Preprocessed UTS_RELEASE, got value "4.4.0-31-generic".
2016-08-24T12:23:36.226-04:00| vthread-4| I120: The header path "/lib/modules/4.4.0-31-generic/build/include" for the kernel "4.4.0-31-generic" is valid.  Whoohoo!
2016-08-24T12:23:36.227-04:00| vthread-4| I120: Found compiler at "/usr/bin/gcc"
2016-08-24T12:23:36.231-04:00| vthread-4| I120: Got gcc version "5.4.0".
2016-08-24T12:23:36.231-04:00| vthread-4| I120: GCC minor version 5 does not match Kernel GCC minor version 5.  But that is ok.
2016-08-24T12:23:36.231-04:00| vthread-4| I120: Using user supplied compiler "/usr/bin/gcc".
2016-08-24T12:23:36.234-04:00| vthread-4| I120: Got gcc version "5.4.0".
2016-08-24T12:23:36.234-04:00| vthread-4| I120: GCC minor version 5 does not match Kernel GCC minor version 5.  But that is ok.
2016-08-24T12:23:36.238-04:00| vthread-4| I120: Trying to find a suitable PBM set for kernel "4.4.0-31-generic".
2016-08-24T12:23:36.238-04:00| vthread-4| I120: No matching PBM set was found for kernel "4.4.0-31-generic".
2016-08-24T12:23:36.239-04:00| vthread-4| I120: GCC minor version 5 does not match Kernel GCC minor version 5.  But that is ok.
2016-08-24T12:23:36.239-04:00| vthread-4| I120: Validating path "/lib/modules/4.4.0-31-generic/build/include" for kernel release "4.4.0-31-generic".
2016-08-24T12:23:36.239-04:00| vthread-4| I120: Failed to find /lib/modules/4.4.0-31-generic/build/include/linux/version.h
2016-08-24T12:23:36.239-04:00| vthread-4| I120: /lib/modules/4.4.0-31-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2016-08-24T12:23:36.239-04:00| vthread-4| I120: using /usr/bin/gcc for preprocess check
2016-08-24T12:23:36.246-04:00| vthread-4| I120: Preprocessed UTS_RELEASE, got value "4.4.0-31-generic".
2016-08-24T12:23:36.246-04:00| vthread-4| I120: The header path "/lib/modules/4.4.0-31-generic/build/include" for the kernel "4.4.0-31-generic" is valid.  Whoohoo!
2016-08-24T12:23:36.247-04:00| vthread-4| I120: GCC minor version 5 does not match Kernel GCC minor version 5.  But that is ok.
2016-08-24T12:23:36.247-04:00| vthread-4| I120: Validating path "/lib/modules/4.4.0-31-generic/build/include" for kernel release "4.4.0-31-generic".
2016-08-24T12:23:36.247-04:00| vthread-4| I120: Failed to find /lib/modules/4.4.0-31-generic/build/include/linux/version.h
2016-08-24T12:23:36.247-04:00| vthread-4| I120: /lib/modules/4.4.0-31-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2016-08-24T12:23:36.247-04:00| vthread-4| I120: using /usr/bin/gcc for preprocess check
2016-08-24T12:23:36.254-04:00| vthread-4| I120: Preprocessed UTS_RELEASE, got value "4.4.0-31-generic".
2016-08-24T12:23:36.254-04:00| vthread-4| I120: The header path "/lib/modules/4.4.0-31-generic/build/include" for the kernel "4.4.0-31-generic" is valid.  Whoohoo!
2016-08-24T12:23:36.254-04:00| vthread-4| I120: Using temp dir "/tmp".
2016-08-24T12:23:36.256-04:00| vthread-4| I120: Obtaining info using the running kernel.
2016-08-24T12:23:36.256-04:00| vthread-4| I120: Setting header path for 4.4.0-31-generic to "/lib/modules/4.4.0-31-generic/build/include".
2016-08-24T12:23:36.256-04:00| vthread-4| I120: Validating path "/lib/modules/4.4.0-31-generic/build/include" for kernel release "4.4.0-31-generic".
2016-08-24T12:23:36.256-04:00| vthread-4| I120: Failed to find /lib/modules/4.4.0-31-generic/build/include/linux/version.h
2016-08-24T12:23:36.256-04:00| vthread-4| I120: /lib/modules/4.4.0-31-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2016-08-24T12:23:36.256-04:00| vthread-4| I120: using /usr/bin/gcc for preprocess check
2016-08-24T12:23:36.264-04:00| vthread-4| I120: Preprocessed UTS_RELEASE, got value "4.4.0-31-generic".
2016-08-24T12:23:36.264-04:00| vthread-4| I120: The header path "/lib/modules/4.4.0-31-generic/build/include" for the kernel "4.4.0-31-generic" is valid.  Whoohoo!
2016-08-24T12:23:36.466-04:00| vthread-4| I120: found symbol version file /lib/modules/4.4.0-31-generic/build/Module.symvers
2016-08-24T12:23:36.466-04:00| vthread-4| I120: Reading symbol versions from /lib/modules/4.4.0-31-generic/build/Module.symvers.
2016-08-24T12:23:36.490-04:00| vthread-4| I120: Read 18767 symbol versions
2016-08-24T12:23:36.490-04:00| vthread-4| I120: Invoking modinfo on "vmmon".
2016-08-24T12:23:36.492-04:00| vthread-4| I120: "/sbin/modinfo" exited with status 256.
2016-08-24T12:23:36.493-04:00| vthread-4| I120: Invoking modinfo on "vmnet".
2016-08-24T12:23:36.495-04:00| vthread-4| I120: "/sbin/modinfo" exited with status 256.
2016-08-24T12:23:36.842-04:00| vthread-4| I120: Setting destination path for vmmon to "/lib/modules/4.4.0-31-generic/misc/vmmon.ko".
2016-08-24T12:23:36.842-04:00| vthread-4| I120: Extracting the vmmon source from "/usr/lib/vmware/modules/source/vmmon.tar".
2016-08-24T12:23:36.850-04:00| vthread-4| I120: Successfully extracted the vmmon source.
2016-08-24T12:23:36.850-04:00| vthread-4| I120: Building module with command "/usr/bin/make -j4 -C /tmp/modconfig-MatsIB/vmmon-only auto-build HEADER_DIR=/lib/modules/4.4.0-31-generic/build/include CC=/usr/bin/gcc IS_GCC_3=no"
2016-08-24T12:23:38.590-04:00| vthread-4| W110: Failed to build vmmon.  Failed to execute the build command.
2016-08-24T12:23:38.592-04:00| vthread-4| I120: Setting destination path for vmnet to "/lib/modules/4.4.0-31-generic/misc/vmnet.ko".
2016-08-24T12:23:38.593-04:00| vthread-4| I120: Extracting the vmnet source from "/usr/lib/vmware/modules/source/vmnet.tar".
2016-08-24T12:23:38.603-04:00| vthread-4| I120: Successfully extracted the vmnet source.
2016-08-24T12:23:38.603-04:00| vthread-4| I120: Building module with command "/usr/bin/make -j4 -C /tmp/modconfig-MatsIB/vmnet-only auto-build HEADER_DIR=/lib/modules/4.4.0-31-generic/build/include CC=/usr/bin/gcc IS_GCC_3=no"
2016-08-24T12:23:40.157-04:00| vthread-4| W110: Failed to build vmnet.  Failed to execute the build command.
```

---

