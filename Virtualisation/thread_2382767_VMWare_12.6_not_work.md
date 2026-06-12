---
title: "VMWare 12.6 not work"
date: 2018-01-17
forum: Virtualisation
---

### Post by galbron on 2018-01-17
Good morning, I bring 1 week try to install VMWare 12.6 in my system Kubuntu 16.04 LTS, but by the moment I can't.

I show you image captures, and the logs.

I attached the log:

```
2018-01-17T11:22:08.546+01:00| vthread-4| I125: Log for VMware Workstation pid=7916 version=12.5.6 build=build-5528349 option=Release
2018-01-17T11:22:08.546+01:00| vthread-4| I125: The process is 64-bit.
2018-01-17T11:22:08.546+01:00| vthread-4| I125: Host codepage=UTF-8 encoding=UTF-8
2018-01-17T11:22:08.546+01:00| vthread-4| I125: Host is Linux 4.13.0-26-generic Ubuntu 16.04.3 LTS
2018-01-17T11:22:08.546+01:00| vthread-4| I125: DictionaryLoad: Cannot open file "/usr/lib/vmware/settings": No existe el archivo o el directorio.
2018-01-17T11:22:08.546+01:00| vthread-4| I125: PREF Optional preferences file not found at /usr/lib/vmware/settings. Using default values.
2018-01-17T11:22:08.546+01:00| vthread-4| I125: DictionaryLoad: Cannot open file "/root/.vmware/config": No existe el archivo o el directorio.
2018-01-17T11:22:08.546+01:00| vthread-4| I125: PREF Optional preferences file not found at /root/.vmware/config. Using default values.
2018-01-17T11:22:08.546+01:00| vthread-4| I125: PREF Unable to check permissions for preferences file.
2018-01-17T11:22:08.546+01:00| vthread-4| I125: DictionaryLoad: Cannot open file "/root/.vmware/preferences": No existe el archivo o el directorio.
2018-01-17T11:22:08.546+01:00| vthread-4| I125: PREF Failed to load user preferences.
2018-01-17T11:22:08.585+01:00| vthread-4| W115: Logging to /tmp/vmware-root/vmware-7916.log
2018-01-17T11:22:08.593+01:00| vthread-4| I125: Obtaining info using the running kernel.
2018-01-17T11:22:08.593+01:00| vthread-4| I125: Created new pathsHash.
2018-01-17T11:22:08.593+01:00| vthread-4| I125: Setting header path for 4.13.0-26-generic to "/lib/modules/4.13.0-26-generic/build/include".
2018-01-17T11:22:08.593+01:00| vthread-4| I125: Validating path "/lib/modules/4.13.0-26-generic/build/include" for kernel release "4.13.0-26-generic".
2018-01-17T11:22:08.593+01:00| vthread-4| I125: Failed to find /lib/modules/4.13.0-26-generic/build/include/linux/version.h
2018-01-17T11:22:08.593+01:00| vthread-4| I125: /lib/modules/4.13.0-26-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2018-01-17T11:22:08.593+01:00| vthread-4| I125: using /usr/bin/gcc for preprocess check
2018-01-17T11:22:08.599+01:00| vthread-4| I125: Preprocessed UTS_RELEASE, got value "4.13.0-26-generic".
2018-01-17T11:22:08.599+01:00| vthread-4| I125: The header path "/lib/modules/4.13.0-26-generic/build/include" for the kernel "4.13.0-26-generic" is valid.  Whoohoo!
2018-01-17T11:22:08.749+01:00| vthread-4| I125: found symbol version file /lib/modules/4.13.0-26-generic/build/Module.symvers
2018-01-17T11:22:08.749+01:00| vthread-4| I125: Reading symbol versions from /lib/modules/4.13.0-26-generic/build/Module.symvers.
2018-01-17T11:22:08.769+01:00| vthread-4| I125: Read 22181 symbol versions
2018-01-17T11:22:08.769+01:00| vthread-4| I125: Reading in info for the vmmon module.
2018-01-17T11:22:08.769+01:00| vthread-4| I125: Reading in info for the vmnet module.
2018-01-17T11:22:08.769+01:00| vthread-4| I125: Reading in info for the vmblock module.
2018-01-17T11:22:08.769+01:00| vthread-4| I125: Reading in info for the vmci module.
2018-01-17T11:22:08.769+01:00| vthread-4| I125: Reading in info for the vsock module.
2018-01-17T11:22:08.769+01:00| vthread-4| I125: Setting vsock to depend on vmci.
2018-01-17T11:22:08.769+01:00| vthread-4| I125: Invoking modinfo on "vmmon".
2018-01-17T11:22:08.771+01:00| vthread-4| I125: "/sbin/modinfo" exited with status 256.
2018-01-17T11:22:08.771+01:00| vthread-4| I125: Invoking modinfo on "vmnet".
2018-01-17T11:22:08.772+01:00| vthread-4| I125: "/sbin/modinfo" exited with status 256.
2018-01-17T11:22:08.772+01:00| vthread-4| I125: Invoking modinfo on "vmblock".
2018-01-17T11:22:08.773+01:00| vthread-4| I125: "/sbin/modinfo" exited with status 256.
2018-01-17T11:22:08.773+01:00| vthread-4| I125: Invoking modinfo on "vmci".
2018-01-17T11:22:08.774+01:00| vthread-4| I125: "/sbin/modinfo" exited with status 256.
2018-01-17T11:22:08.774+01:00| vthread-4| I125: Invoking modinfo on "vsock".
2018-01-17T11:22:08.775+01:00| vthread-4| I125: "/sbin/modinfo" exited with status 0.
2018-01-17T11:22:08.794+01:00| vthread-4| I125: to be installed: vmmon status: 0
2018-01-17T11:22:08.794+01:00| vthread-4| I125: to be installed: vmnet status: 0
2018-01-17T11:22:08.817+01:00| vthread-4| I125: Obtaining info using the running kernel.
2018-01-17T11:22:08.817+01:00| vthread-4| I125: Setting header path for 4.13.0-26-generic to "/lib/modules/4.13.0-26-generic/build/include".
2018-01-17T11:22:08.817+01:00| vthread-4| I125: Validating path "/lib/modules/4.13.0-26-generic/build/include" for kernel release "4.13.0-26-generic".
2018-01-17T11:22:08.817+01:00| vthread-4| I125: Failed to find /lib/modules/4.13.0-26-generic/build/include/linux/version.h
2018-01-17T11:22:08.817+01:00| vthread-4| I125: /lib/modules/4.13.0-26-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2018-01-17T11:22:08.817+01:00| vthread-4| I125: using /usr/bin/gcc for preprocess check
2018-01-17T11:22:08.823+01:00| vthread-4| I125: Preprocessed UTS_RELEASE, got value "4.13.0-26-generic".
2018-01-17T11:22:08.823+01:00| vthread-4| I125: The header path "/lib/modules/4.13.0-26-generic/build/include" for the kernel "4.13.0-26-generic" is valid.  Whoohoo!
2018-01-17T11:22:08.970+01:00| vthread-4| I125: found symbol version file /lib/modules/4.13.0-26-generic/build/Module.symvers
2018-01-17T11:22:08.970+01:00| vthread-4| I125: Reading symbol versions from /lib/modules/4.13.0-26-generic/build/Module.symvers.
2018-01-17T11:22:08.989+01:00| vthread-4| I125: Read 22181 symbol versions
2018-01-17T11:22:08.989+01:00| vthread-4| I125: Kernel header path retrieved from FileEntry: /lib/modules/4.13.0-26-generic/build/include
2018-01-17T11:22:08.989+01:00| vthread-4| I125: Update kernel header path to /lib/modules/4.13.0-26-generic/build/include
2018-01-17T11:22:08.989+01:00| vthread-4| I125: Validating path "/lib/modules/4.13.0-26-generic/build/include" for kernel release "4.13.0-26-generic".
2018-01-17T11:22:08.989+01:00| vthread-4| I125: Failed to find /lib/modules/4.13.0-26-generic/build/include/linux/version.h
2018-01-17T11:22:08.989+01:00| vthread-4| I125: /lib/modules/4.13.0-26-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2018-01-17T11:22:08.989+01:00| vthread-4| I125: using /usr/bin/gcc for preprocess check
2018-01-17T11:22:08.995+01:00| vthread-4| I125: Preprocessed UTS_RELEASE, got value "4.13.0-26-generic".
2018-01-17T11:22:08.995+01:00| vthread-4| I125: The header path "/lib/modules/4.13.0-26-generic/build/include" for the kernel "4.13.0-26-generic" is valid.  Whoohoo!
2018-01-17T11:22:08.996+01:00| vthread-4| I125: Found compiler at "/usr/bin/gcc"
2018-01-17T11:22:08.999+01:00| vthread-4| I125: Got gcc version "5.4.0".
2018-01-17T11:22:08.999+01:00| vthread-4| I125: The GCC version matches the kernel GCC minor version like a glove.
2018-01-17T11:22:08.999+01:00| vthread-4| I125: Using user supplied compiler "/usr/bin/gcc".
2018-01-17T11:22:09.001+01:00| vthread-4| I125: Got gcc version "5.4.0".
2018-01-17T11:22:09.001+01:00| vthread-4| I125: The GCC version matches the kernel GCC minor version like a glove.
2018-01-17T11:22:09.002+01:00| vthread-4| I125: Trying to find a suitable PBM set for kernel "4.13.0-26-generic".
2018-01-17T11:22:09.002+01:00| vthread-4| I125: No matching PBM set was found for kernel "4.13.0-26-generic".
2018-01-17T11:22:09.002+01:00| vthread-4| I125: The GCC version matches the kernel GCC minor version like a glove.
2018-01-17T11:22:09.002+01:00| vthread-4| I125: Validating path "/lib/modules/4.13.0-26-generic/build/include" for kernel release "4.13.0-26-generic".
2018-01-17T11:22:09.003+01:00| vthread-4| I125: Failed to find /lib/modules/4.13.0-26-generic/build/include/linux/version.h
2018-01-17T11:22:09.003+01:00| vthread-4| I125: /lib/modules/4.13.0-26-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2018-01-17T11:22:09.003+01:00| vthread-4| I125: using /usr/bin/gcc for preprocess check
2018-01-17T11:22:09.009+01:00| vthread-4| I125: Preprocessed UTS_RELEASE, got value "4.13.0-26-generic".
2018-01-17T11:22:09.009+01:00| vthread-4| I125: The header path "/lib/modules/4.13.0-26-generic/build/include" for the kernel "4.13.0-26-generic" is valid.  Whoohoo!
2018-01-17T11:22:09.010+01:00| vthread-4| I125: The GCC version matches the kernel GCC minor version like a glove.
2018-01-17T11:22:09.010+01:00| vthread-4| I125: Validating path "/lib/modules/4.13.0-26-generic/build/include" for kernel release "4.13.0-26-generic".
2018-01-17T11:22:09.010+01:00| vthread-4| I125: Failed to find /lib/modules/4.13.0-26-generic/build/include/linux/version.h
2018-01-17T11:22:09.010+01:00| vthread-4| I125: /lib/modules/4.13.0-26-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2018-01-17T11:22:09.010+01:00| vthread-4| I125: using /usr/bin/gcc for preprocess check
2018-01-17T11:22:09.016+01:00| vthread-4| I125: Preprocessed UTS_RELEASE, got value "4.13.0-26-generic".
2018-01-17T11:22:09.016+01:00| vthread-4| I125: The header path "/lib/modules/4.13.0-26-generic/build/include" for the kernel "4.13.0-26-generic" is valid.  Whoohoo!
2018-01-17T11:22:09.016+01:00| vthread-4| I125: Using temp dir "/tmp".
2018-01-17T11:22:09.018+01:00| vthread-4| I125: Obtaining info using the running kernel.
2018-01-17T11:22:09.018+01:00| vthread-4| I125: Setting header path for 4.13.0-26-generic to "/lib/modules/4.13.0-26-generic/build/include".
2018-01-17T11:22:09.018+01:00| vthread-4| I125: Validating path "/lib/modules/4.13.0-26-generic/build/include" for kernel release "4.13.0-26-generic".
2018-01-17T11:22:09.018+01:00| vthread-4| I125: Failed to find /lib/modules/4.13.0-26-generic/build/include/linux/version.h
2018-01-17T11:22:09.018+01:00| vthread-4| I125: /lib/modules/4.13.0-26-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2018-01-17T11:22:09.018+01:00| vthread-4| I125: using /usr/bin/gcc for preprocess check
2018-01-17T11:22:09.025+01:00| vthread-4| I125: Preprocessed UTS_RELEASE, got value "4.13.0-26-generic".
2018-01-17T11:22:09.025+01:00| vthread-4| I125: The header path "/lib/modules/4.13.0-26-generic/build/include" for the kernel "4.13.0-26-generic" is valid.  Whoohoo!
2018-01-17T11:22:09.175+01:00| vthread-4| I125: found symbol version file /lib/modules/4.13.0-26-generic/build/Module.symvers
2018-01-17T11:22:09.175+01:00| vthread-4| I125: Reading symbol versions from /lib/modules/4.13.0-26-generic/build/Module.symvers.
2018-01-17T11:22:09.194+01:00| vthread-4| I125: Read 22181 symbol versions
2018-01-17T11:22:09.194+01:00| vthread-4| I125: Invoking modinfo on "vmmon".
2018-01-17T11:22:09.196+01:00| vthread-4| I125: "/sbin/modinfo" exited with status 256.
2018-01-17T11:22:09.196+01:00| vthread-4| I125: Invoking modinfo on "vmnet".
2018-01-17T11:22:09.198+01:00| vthread-4| I125: "/sbin/modinfo" exited with status 256.
2018-01-17T11:22:09.620+01:00| vthread-4| I125: Setting destination path for vmmon to "/lib/modules/4.13.0-26-generic/misc/vmmon.ko".
2018-01-17T11:22:09.620+01:00| vthread-4| I125: Extracting the vmmon source from "/usr/lib/vmware/modules/source/vmmon.tar".
2018-01-17T11:22:09.626+01:00| vthread-4| I125: Successfully extracted the vmmon source.
2018-01-17T11:22:09.626+01:00| vthread-4| I125: Building module with command "/usr/bin/make -j4 -C /tmp/modconfig-qwEGY3/vmmon-only auto-build HEADER_DIR=/lib/modules/4.13.0-26-generic/build/include CC=/usr/bin/gcc IS_GCC_3=no"
2018-01-17T11:22:11.205+01:00| vthread-4| W115: Failed to build vmmon.  Failed to execute the build command.
2018-01-17T11:22:11.207+01:00| vthread-4| I125: Setting destination path for vmnet to "/lib/modules/4.13.0-26-generic/misc/vmnet.ko".
2018-01-17T11:22:11.207+01:00| vthread-4| I125: Extracting the vmnet source from "/usr/lib/vmware/modules/source/vmnet.tar".
2018-01-17T11:22:11.211+01:00| vthread-4| I125: Successfully extracted the vmnet source.
2018-01-17T11:22:11.211+01:00| vthread-4| I125: Building module with command "/usr/bin/make -j4 -C /tmp/modconfig-qwEGY3/vmnet-only auto-build HEADER_DIR=/lib/modules/4.13.0-26-generic/build/include CC=/usr/bin/gcc IS_GCC_3=no"
2018-01-17T11:22:13.133+01:00| vthread-4| W115: Failed to build vmnet.  Failed to execute the build command.
2018-01-17T11:23:29.500+01:00| vthread-4| I125: The GCC version matches the kernel GCC minor version like a glove.
2018-01-17T11:23:29.500+01:00| vthread-4| I125: Validating path "/lib/modules/4.13.0-26-generic/build/include" for kernel release "4.13.0-26-generic".
2018-01-17T11:23:29.500+01:00| vthread-4| I125: Failed to find /lib/modules/4.13.0-26-generic/build/include/linux/version.h
2018-01-17T11:23:29.500+01:00| vthread-4| I125: /lib/modules/4.13.0-26-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2018-01-17T11:23:29.500+01:00| vthread-4| I125: using /usr/bin/gcc for preprocess check
2018-01-17T11:23:29.509+01:00| vthread-4| I125: Preprocessed UTS_RELEASE, got value "4.13.0-26-generic".
2018-01-17T11:23:29.509+01:00| vthread-4| I125: The header path "/lib/modules/4.13.0-26-generic/build/include" for the kernel "4.13.0-26-generic" is valid.  Whoohoo!
2018-01-17T11:23:29.509+01:00| vthread-4| I125: Using temp dir "/tmp".
2018-01-17T11:23:29.510+01:00| vthread-4| I125: Obtaining info using the running kernel.
2018-01-17T11:23:29.510+01:00| vthread-4| I125: Setting header path for 4.13.0-26-generic to "/lib/modules/4.13.0-26-generic/build/include".
2018-01-17T11:23:29.510+01:00| vthread-4| I125: Validating path "/lib/modules/4.13.0-26-generic/build/include" for kernel release "4.13.0-26-generic".
2018-01-17T11:23:29.510+01:00| vthread-4| I125: Failed to find /lib/modules/4.13.0-26-generic/build/include/linux/version.h
2018-01-17T11:23:29.510+01:00| vthread-4| I125: /lib/modules/4.13.0-26-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2018-01-17T11:23:29.510+01:00| vthread-4| I125: using /usr/bin/gcc for preprocess check
2018-01-17T11:23:29.519+01:00| vthread-4| I125: Preprocessed UTS_RELEASE, got value "4.13.0-26-generic".
2018-01-17T11:23:29.519+01:00| vthread-4| I125: The header path "/lib/modules/4.13.0-26-generic/build/include" for the kernel "4.13.0-26-generic" is valid.  Whoohoo!
2018-01-17T11:23:29.671+01:00| vthread-4| I125: found symbol version file /lib/modules/4.13.0-26-generic/build/Module.symvers
2018-01-17T11:23:29.671+01:00| vthread-4| I125: Reading symbol versions from /lib/modules/4.13.0-26-generic/build/Module.symvers.
2018-01-17T11:23:29.692+01:00| vthread-4| I125: Read 22181 symbol versions
2018-01-17T11:23:29.692+01:00| vthread-4| I125: Invoking modinfo on "vmmon".
2018-01-17T11:23:29.694+01:00| vthread-4| I125: "/sbin/modinfo" exited with status 256.
2018-01-17T11:23:29.694+01:00| vthread-4| I125: Invoking modinfo on "vmnet".
2018-01-17T11:23:29.696+01:00| vthread-4| I125: "/sbin/modinfo" exited with status 256.
2018-01-17T11:23:30.122+01:00| vthread-4| I125: Setting destination path for vmmon to "/lib/modules/4.13.0-26-generic/misc/vmmon.ko".
2018-01-17T11:23:30.122+01:00| vthread-4| I125: Extracting the vmmon source from "/usr/lib/vmware/modules/source/vmmon.tar".
2018-01-17T11:23:30.129+01:00| vthread-4| I125: Successfully extracted the vmmon source.
2018-01-17T11:23:30.129+01:00| vthread-4| I125: Building module with command "/usr/bin/make -j4 -C /tmp/modconfig-UubezC/vmmon-only auto-build HEADER_DIR=/lib/modules/4.13.0-26-generic/build/include CC=/usr/bin/gcc IS_GCC_3=no"
2018-01-17T11:23:31.723+01:00| vthread-4| W115: Failed to build vmmon.  Failed to execute the build command.
2018-01-17T11:23:31.725+01:00| vthread-4| I125: Setting destination path for vmnet to "/lib/modules/4.13.0-26-generic/misc/vmnet.ko".
2018-01-17T11:23:31.725+01:00| vthread-4| I125: Extracting the vmnet source from "/usr/lib/vmware/modules/source/vmnet.tar".
2018-01-17T11:23:31.729+01:00| vthread-4| I125: Successfully extracted the vmnet source.
2018-01-17T11:23:31.730+01:00| vthread-4| I125: Building module with command "/usr/bin/make -j4 -C /tmp/modconfig-UubezC/vmnet-only auto-build HEADER_DIR=/lib/modules/4.13.0-26-generic/build/include CC=/usr/bin/gcc IS_GCC_3=no"
2018-01-17T11:23:33.618+01:00| vthread-4| W115: Failed to build vmnet.  Failed to execute the build command.
```

More information

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:        16.04
Codename:       xenial

Linux radagast 4.13.0-26-generic #29~16.04.2-Ubuntu SMP Tue Jan 9 22:00:44 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

VMware Player 12.5.6 build-5528349

Thanks so much.

---

### Post by howefield on 2018-01-17
Thread moved to the "*Virtualisation*" forum for a better fit.

---

### Post by jdflammer on 2018-01-17
I'm having the same exact issue. Running on a Bonobo-WS with 16.04.

---

