---
title: "Error Unable to start services... Lubuntu 16.04 X64"
date: 2018-03-12
forum: Virtualisation
---

### Post by cdoublejj on 2018-03-12
Normally it installs and update and i'm on my way but, for some reason i get this error.

[https://imgur.com/fRUEfOu](https://imgur.com/fRUEfOu)

```
2018-03-12T07:36:19.898-05:00| vthread-4| I125: Log for VMware Workstation pid=20806 version=12.5.8 build=build-7098237 option=Release2018-03-12T07:36:19.898-05:00| vthread-4| I125: The process is 64-bit.
2018-03-12T07:36:19.898-05:00| vthread-4| I125: Host codepage=UTF-8 encoding=UTF-8
2018-03-12T07:36:19.898-05:00| vthread-4| I125: Host is Linux 4.13.0-36-generic Ubuntu 16.04.4 LTS
2018-03-12T07:36:19.898-05:00| vthread-4| I125: DictionaryLoad: Cannot open file "/usr/lib/vmware/settings": No such file or directory.
2018-03-12T07:36:19.898-05:00| vthread-4| I125: PREF Optional preferences file not found at /usr/lib/vmware/settings. Using default values.
2018-03-12T07:36:19.898-05:00| vthread-4| I125: DictionaryLoad: Cannot open file "/root/.vmware/config": No such file or directory.
2018-03-12T07:36:19.898-05:00| vthread-4| I125: PREF Optional preferences file not found at /root/.vmware/config. Using default values.
2018-03-12T07:36:19.898-05:00| vthread-4| I125: PREF Unable to check permissions for preferences file.
2018-03-12T07:36:19.898-05:00| vthread-4| I125: DictionaryLoad: Cannot open file "/root/.vmware/preferences": No such file or directory.
2018-03-12T07:36:19.898-05:00| vthread-4| I125: PREF Failed to load user preferences.
2018-03-12T07:36:19.950-05:00| vthread-4| W115: Logging to /tmp/vmware-root/vmware-20806.log
2018-03-12T07:36:19.964-05:00| vthread-4| I125: Obtaining info using the running kernel.
2018-03-12T07:36:19.965-05:00| vthread-4| I125: Created new pathsHash.
2018-03-12T07:36:19.965-05:00| vthread-4| I125: Setting header path for 4.13.0-36-generic to "/lib/modules/4.13.0-36-generic/build/include".
2018-03-12T07:36:19.965-05:00| vthread-4| I125: Validating path "/lib/modules/4.13.0-36-generic/build/include" for kernel release "4.13.0-36-generic".
2018-03-12T07:36:19.965-05:00| vthread-4| I125: Failed to find /lib/modules/4.13.0-36-generic/build/include/linux/version.h
2018-03-12T07:36:19.965-05:00| vthread-4| I125: /lib/modules/4.13.0-36-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2018-03-12T07:36:19.965-05:00| vthread-4| I125: using /usr/bin/gcc for preprocess check
2018-03-12T07:36:19.971-05:00| vthread-4| I125: Preprocessed UTS_RELEASE, got value "4.13.0-36-generic".
2018-03-12T07:36:19.971-05:00| vthread-4| I125: The header path "/lib/modules/4.13.0-36-generic/build/include" for the kernel "4.13.0-36-generic" is valid.  Whoohoo!
2018-03-12T07:36:20.142-05:00| vthread-4| I125: found symbol version file /lib/modules/4.13.0-36-generic/build/Module.symvers
2018-03-12T07:36:20.142-05:00| vthread-4| I125: Reading symbol versions from /lib/modules/4.13.0-36-generic/build/Module.symvers.
2018-03-12T07:36:20.161-05:00| vthread-4| I125: Read 22205 symbol versions
2018-03-12T07:36:20.162-05:00| vthread-4| I125: Reading in info for the vmmon module.
2018-03-12T07:36:20.162-05:00| vthread-4| I125: Reading in info for the vmnet module.
2018-03-12T07:36:20.162-05:00| vthread-4| I125: Reading in info for the vmblock module.
2018-03-12T07:36:20.162-05:00| vthread-4| I125: Reading in info for the vmci module.
2018-03-12T07:36:20.162-05:00| vthread-4| I125: Reading in info for the vsock module.
2018-03-12T07:36:20.162-05:00| vthread-4| I125: Setting vsock to depend on vmci.
2018-03-12T07:36:20.162-05:00| vthread-4| I125: Invoking modinfo on "vmmon".
2018-03-12T07:36:20.164-05:00| vthread-4| I125: "/sbin/modinfo" exited with status 256.
2018-03-12T07:36:20.164-05:00| vthread-4| I125: Invoking modinfo on "vmnet".
2018-03-12T07:36:20.166-05:00| vthread-4| I125: "/sbin/modinfo" exited with status 256.
2018-03-12T07:36:20.166-05:00| vthread-4| I125: Invoking modinfo on "vmblock".
2018-03-12T07:36:20.169-05:00| vthread-4| I125: "/sbin/modinfo" exited with status 256.
2018-03-12T07:36:20.169-05:00| vthread-4| I125: Invoking modinfo on "vmci".
2018-03-12T07:36:20.171-05:00| vthread-4| I125: "/sbin/modinfo" exited with status 256.
2018-03-12T07:36:20.171-05:00| vthread-4| I125: Invoking modinfo on "vsock".
2018-03-12T07:36:20.173-05:00| vthread-4| I125: "/sbin/modinfo" exited with status 0.
2018-03-12T07:36:20.187-05:00| vthread-4| I125: to be installed: vmmon status: 0
2018-03-12T07:36:20.187-05:00| vthread-4| I125: to be installed: vmnet status: 0
2018-03-12T07:36:20.202-05:00| vthread-4| I125: Obtaining info using the running kernel.
2018-03-12T07:36:20.202-05:00| vthread-4| I125: Setting header path for 4.13.0-36-generic to "/lib/modules/4.13.0-36-generic/build/include".
2018-03-12T07:36:20.202-05:00| vthread-4| I125: Validating path "/lib/modules/4.13.0-36-generic/build/include" for kernel release "4.13.0-36-generic".
2018-03-12T07:36:20.202-05:00| vthread-4| I125: Failed to find /lib/modules/4.13.0-36-generic/build/include/linux/version.h
2018-03-12T07:36:20.202-05:00| vthread-4| I125: /lib/modules/4.13.0-36-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2018-03-12T07:36:20.202-05:00| vthread-4| I125: using /usr/bin/gcc for preprocess check
2018-03-12T07:36:20.208-05:00| vthread-4| I125: Preprocessed UTS_RELEASE, got value "4.13.0-36-generic".
2018-03-12T07:36:20.208-05:00| vthread-4| I125: The header path "/lib/modules/4.13.0-36-generic/build/include" for the kernel "4.13.0-36-generic" is valid.  Whoohoo!
2018-03-12T07:36:20.382-05:00| vthread-4| I125: found symbol version file /lib/modules/4.13.0-36-generic/build/Module.symvers
2018-03-12T07:36:20.382-05:00| vthread-4| I125: Reading symbol versions from /lib/modules/4.13.0-36-generic/build/Module.symvers.
2018-03-12T07:36:20.401-05:00| vthread-4| I125: Read 22205 symbol versions
2018-03-12T07:36:20.401-05:00| vthread-4| I125: Kernel header path retrieved from FileEntry: /lib/modules/4.13.0-36-generic/build/include
2018-03-12T07:36:20.401-05:00| vthread-4| I125: Update kernel header path to /lib/modules/4.13.0-36-generic/build/include
2018-03-12T07:36:20.401-05:00| vthread-4| I125: Validating path "/lib/modules/4.13.0-36-generic/build/include" for kernel release "4.13.0-36-generic".
2018-03-12T07:36:20.401-05:00| vthread-4| I125: Failed to find /lib/modules/4.13.0-36-generic/build/include/linux/version.h
2018-03-12T07:36:20.401-05:00| vthread-4| I125: /lib/modules/4.13.0-36-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2018-03-12T07:36:20.401-05:00| vthread-4| I125: using /usr/bin/gcc for preprocess check
2018-03-12T07:36:20.408-05:00| vthread-4| I125: Preprocessed UTS_RELEASE, got value "4.13.0-36-generic".
2018-03-12T07:36:20.408-05:00| vthread-4| I125: The header path "/lib/modules/4.13.0-36-generic/build/include" for the kernel "4.13.0-36-generic" is valid.  Whoohoo!
2018-03-12T07:36:20.409-05:00| vthread-4| I125: Found compiler at "/usr/bin/gcc"
2018-03-12T07:36:20.412-05:00| vthread-4| I125: Got gcc version "5.4.0".
2018-03-12T07:36:20.412-05:00| vthread-4| I125: The GCC version matches the kernel GCC minor version like a glove.
2018-03-12T07:36:20.413-05:00| vthread-4| I125: Using user supplied compiler "/usr/bin/gcc".
2018-03-12T07:36:20.415-05:00| vthread-4| I125: Got gcc version "5.4.0".
2018-03-12T07:36:20.415-05:00| vthread-4| I125: The GCC version matches the kernel GCC minor version like a glove.
2018-03-12T07:36:20.417-05:00| vthread-4| I125: Trying to find a suitable PBM set for kernel "4.13.0-36-generic".
2018-03-12T07:36:20.417-05:00| vthread-4| I125: No matching PBM set was found for kernel "4.13.0-36-generic".
2018-03-12T07:36:20.417-05:00| vthread-4| I125: The GCC version matches the kernel GCC minor version like a glove.
2018-03-12T07:36:20.413-05:00| vthread-4| I125: Using user supplied compiler "/usr/bin/gcc".
2018-03-12T07:36:20.415-05:00| vthread-4| I125: Got gcc version "5.4.0".
2018-03-12T07:36:20.415-05:00| vthread-4| I125: The GCC version matches the kernel GCC minor version like a glove.
2018-03-12T07:36:20.417-05:00| vthread-4| I125: Trying to find a suitable PBM set for kernel "4.13.0-36-generic".
2018-03-12T07:36:20.417-05:00| vthread-4| I125: No matching PBM set was found for kernel "4.13.0-36-generic".
2018-03-12T07:36:20.417-05:00| vthread-4| I125: The GCC version matches the kernel GCC minor version like a glove.
2018-03-12T07:36:20.417-05:00| vthread-4| I125: Validating path "/lib/modules/4.13.0-36-generic/build/include" for kernel release "4.13.0-36-generic".
2018-03-12T07:36:20.417-05:00| vthread-4| I125: Failed to find /lib/modules/4.13.0-36-generic/build/include/linux/version.h
2018-03-12T07:36:20.417-05:00| vthread-4| I125: /lib/modules/4.13.0-36-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2018-03-12T07:36:20.417-05:00| vthread-4| I125: using /usr/bin/gcc for preprocess check
2018-03-12T07:36:20.424-05:00| vthread-4| I125: Preprocessed UTS_RELEASE, got value "4.13.0-36-generic".
2018-03-12T07:36:20.424-05:00| vthread-4| I125: The header path "/lib/modules/4.13.0-36-generic/build/include" for the kernel "4.13.0-36-generic" is valid.  Whoohoo!
2018-03-12T07:36:20.425-05:00| vthread-4| I125: The GCC version matches the kernel GCC minor version like a glove.
2018-03-12T07:36:20.425-05:00| vthread-4| I125: Validating path "/lib/modules/4.13.0-36-generic/build/include" for kernel release "4.13.0-36-generic".
2018-03-12T07:36:20.425-05:00| vthread-4| I125: Failed to find /lib/modules/4.13.0-36-generic/build/include/linux/version.h
2018-03-12T07:36:20.425-05:00| vthread-4| I125: /lib/modules/4.13.0-36-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2018-03-12T07:36:20.425-05:00| vthread-4| I125: using /usr/bin/gcc for preprocess check
2018-03-12T07:36:20.432-05:00| vthread-4| I125: Preprocessed UTS_RELEASE, got value "4.13.0-36-generic".
2018-03-12T07:36:20.432-05:00| vthread-4| I125: The header path "/lib/modules/4.13.0-36-generic/build/include" for the kernel "4.13.0-36-generic" is valid.  Whoohoo!
2018-03-12T07:36:20.432-05:00| vthread-4| I125: Using temp dir "/tmp".
2018-03-12T07:36:20.433-05:00| vthread-4| I125: Obtaining info using the running kernel.
2018-03-12T07:36:20.433-05:00| vthread-4| I125: Setting header path for 4.13.0-36-generic to "/lib/modules/4.13.0-36-generic/build/include".
2018-03-12T07:36:20.433-05:00| vthread-4| I125: Validating path "/lib/modules/4.13.0-36-generic/build/include" for kernel release "4.13.0-36-generic".
2018-03-12T07:36:20.433-05:00| vthread-4| I125: Failed to find /lib/modules/4.13.0-36-generic/build/include/linux/version.h
2018-03-12T07:36:20.433-05:00| vthread-4| I125: /lib/modules/4.13.0-36-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2018-03-12T07:36:20.433-05:00| vthread-4| I125: using /usr/bin/gcc for preprocess check
2018-03-12T07:36:20.441-05:00| vthread-4| I125: Preprocessed UTS_RELEASE, got value "4.13.0-36-generic".
2018-03-12T07:36:20.441-05:00| vthread-4| I125: The header path "/lib/modules/4.13.0-36-generic/build/include" for the kernel "4.13.0-36-generic" is valid.  Whoohoo!
2018-03-12T07:36:20.611-05:00| vthread-4| I125: found symbol version file /lib/modules/4.13.0-36-generic/build/Module.symvers
2018-03-12T07:36:20.611-05:00| vthread-4| I125: Reading symbol versions from /lib/modules/4.13.0-36-generic/build/Module.symvers.
2018-03-12T07:36:20.630-05:00| vthread-4| I125: Read 22205 symbol versions
2018-03-12T07:36:20.630-05:00| vthread-4| I125: Invoking modinfo on "vmmon".
2018-03-12T07:36:20.633-05:00| vthread-4| I125: "/sbin/modinfo" exited with status 256.
2018-03-12T07:36:20.633-05:00| vthread-4| I125: Invoking modinfo on "vmnet".
2018-03-12T07:36:20.636-05:00| vthread-4| I125: "/sbin/modinfo" exited with status 256.
2018-03-12T07:36:21.020-05:00| vthread-4| I125: Setting destination path for vmmon to "/lib/modules/4.13.0-36-generic/misc/vmmon.ko".
2018-03-12T07:36:21.020-05:00| vthread-4| I125: Extracting the vmmon source from "/usr/lib/vmware/modules/source/vmmon.tar".
2018-03-12T07:36:21.031-05:00| vthread-4| I125: Successfully extracted the vmmon source.
2018-03-12T07:36:21.031-05:00| vthread-4| I125: Building module with command "/usr/bin/make -j4 -C /tmp/modconfig-xfzVg2/vmmon-only auto-build HEADER_DIR=/lib/modules/4.13.0-36-generic/build/include CC=/usr/bin/gcc IS_GCC_3=no"
2018-03-12T07:36:23.395-05:00| vthread-4| I125: Successfully built vmmon.  Module is currently at "/tmp/modconfig-xfzVg2/vmmon.o".
2018-03-12T07:36:23.395-05:00| vthread-4| I125: Found the vmmon symvers file at "/tmp/modconfig-xfzVg2/vmmon-only/Module.symvers".
2018-03-12T07:36:23.395-05:00| vthread-4| I125: Installing vmmon from /tmp/modconfig-xfzVg2/vmmon.o to /lib/modules/4.13.0-36-generic/misc/vmmon.ko.
2018-03-12T07:36:23.395-05:00| vthread-4| I125: Registering file "/lib/modules/4.13.0-36-generic/misc/vmmon.ko".
2018-03-12T07:36:23.772-05:00| vthread-4| I125: "/usr/lib/vmware-installer/2.1.0/vmware-installer" exited with status 0.
2018-03-12T07:36:23.773-05:00| vthread-4| I125: Registering file "/usr/lib/vmware/symvers/vmmon-4.13.0-36-generic".
2018-03-12T07:36:24.027-05:00| vthread-4| I125: "/usr/lib/vmware-installer/2.1.0/vmware-installer" exited with status 0.
2018-03-12T07:36:24.029-05:00| vthread-4| I125: Setting destination path for vmnet to "/lib/modules/4.13.0-36-generic/misc/vmnet.ko".
2018-03-12T07:36:24.029-05:00| vthread-4| I125: Extracting the vmnet source from "/usr/lib/vmware/modules/source/vmnet.tar".
2018-03-12T07:36:24.034-05:00| vthread-4| I125: Successfully extracted the vmnet source.
2018-03-12T07:36:24.034-05:00| vthread-4| I125: Building module with command "/usr/bin/make -j4 -C /tmp/modconfig-xfzVg2/vmnet-only auto-build HEADER_DIR=/lib/modules/4.13.0-36-generic/build/include CC=/usr/bin/gcc IS_GCC_3=no"
2018-03-12T07:36:24.038-05:00| vthread-4| W115: Failed to build vmnet.  Failed to execute the build command.
(END)
```

EDIT: reinstalling didn't help

---

### Post by cdoublejj on 2018-03-12
Solution: [https://gist.github.com/ukos-git/e656c47025dd55b4836a980a34811637](https://gist.github.com/ukos-git/e656c47025dd55b4836a980a34811637)

---

