---
title: "[solved] vmware workstation 12 on kernel 4.10.0-33-generic  (ubuntu 16.04)"
date: 2017-08-28
forum: Virtualisation
---

### Post by voriain on 2017-08-28
Hello   I just tried starting vmware-workstation for the first time in a few months. Looks like there are problems with the newer kernel, as I have updates according as updates came along.     The ouput of  uname -ar is Linux lp 4.10.0-33-generic #37~16.04.1-Ubuntu SMP Fri Aug 11 14:07:24 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux     I attach screenshots of the messages that I get.   The following is the  log file produced.     ```
2017-08-28T14:57:37.263+01:00| vthread-4| I125: Log for VMware Workstation pid=3673 version=12.5.0 build=build-4352439 option=Release 2017-08-28T14:57:37.263+01:00| vthread-4| I125: The process is 64-bit. 2017-08-28T14:57:37.263+01:00| vthread-4| I125: Host codepage=UTF-8 encoding=UTF-8 2017-08-28T14:57:37.263+01:00| vthread-4| I125: Host is Linux 4.10.0-33-generic Ubuntu 16.04.3 LTS 2017-08-28T14:57:37.263+01:00| vthread-4| I125: DictionaryLoad: Cannot open file "/usr/lib/vmware/settings": No such file or directory. 2017-08-28T14:57:37.263+01:00| vthread-4| I125: PREF Optional preferences file not found at /usr/lib/vmware/settings. Using default values. 2017-08-28T14:57:37.263+01:00| vthread-4| I125: DictionaryLoad: Cannot open file "/root/.vmware/config": No such file or directory. 2017-08-28T14:57:37.263+01:00| vthread-4| I125: PREF Optional preferences file not found at /root/.vmware/config. Using default values. 2017-08-28T14:57:37.263+01:00| vthread-4| I125: PREF Unable to check permissions for preferences file. 2017-08-28T14:57:37.263+01:00| vthread-4| I125: DictionaryLoad: Cannot open file "/root/.vmware/preferences": No such file or directory. 2017-08-28T14:57:37.263+01:00| vthread-4| I125: PREF Failed to load user preferences. 2017-08-28T14:57:37.301+01:00| vthread-4| W115: Logging to /tmp/vmware-root/vmware-3673.log 2017-08-28T14:57:37.314+01:00| vthread-4| I125: Obtaining info using the running kernel. 2017-08-28T14:57:37.314+01:00| vthread-4| I125: Created new pathsHash. 2017-08-28T14:57:37.314+01:00| vthread-4| I125: Setting header path for 4.10.0-33-generic to "/lib/modules/4.10.0-33-generic/build/include". 2017-08-28T14:57:37.314+01:00| vthread-4| I125: Validating path "/lib/modules/4.10.0-33-generic/build/include" for kernel release "4.10.0-33-generic". 2017-08-28T14:57:37.314+01:00| vthread-4| I125: Failed to find /lib/modules/4.10.0-33-generic/build/include/linux/version.h 2017-08-28T14:57:37.314+01:00| vthread-4| I125: /lib/modules/4.10.0-33-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead. 2017-08-28T14:57:37.314+01:00| vthread-4| I125: using /usr/bin/gcc for preprocess check 2017-08-28T14:57:37.320+01:00| vthread-4| I125: Preprocessed UTS_RELEASE, got value "4.10.0-33-generic". 2017-08-28T14:57:37.320+01:00| vthread-4| I125: The header path "/lib/modules/4.10.0-33-generic/build/include" for the kernel "4.10.0-33-generic" is valid.  Whoohoo! 2017-08-28T14:57:37.432+01:00| vthread-4| I125: found symbol version file /lib/modules/4.10.0-33-generic/build/Module.symvers 2017-08-28T14:57:37.432+01:00| vthread-4| I125: Reading symbol versions from /lib/modules/4.10.0-33-generic/build/Module.symvers. 2017-08-28T14:57:37.449+01:00| vthread-4| I125: Read 21375 symbol versions 2017-08-28T14:57:37.449+01:00| vthread-4| I125: Reading in info for the vmmon module. 2017-08-28T14:57:37.449+01:00| vthread-4| I125: Reading in info for the vmnet module. 2017-08-28T14:57:37.449+01:00| vthread-4| I125: Reading in info for the vmblock module. 2017-08-28T14:57:37.449+01:00| vthread-4| I125: Reading in info for the vmci module. 2017-08-28T14:57:37.449+01:00| vthread-4| I125: Reading in info for the vsock module. 2017-08-28T14:57:37.449+01:00| vthread-4| I125: Setting vsock to depend on vmci. 2017-08-28T14:57:37.449+01:00| vthread-4| I125: Invoking modinfo on "vmmon". 2017-08-28T14:57:37.450+01:00| vthread-4| I125: "/sbin/modinfo" exited with status 256. 2017-08-28T14:57:37.450+01:00| vthread-4| I125: Invoking modinfo on "vmnet". 2017-08-28T14:57:37.452+01:00| vthread-4| I125: "/sbin/modinfo" exited with status 256. 2017-08-28T14:57:37.452+01:00| vthread-4| I125: Invoking modinfo on "vmblock". 2017-08-28T14:57:37.453+01:00| vthread-4| I125: "/sbin/modinfo" exited with status 256. 2017-08-28T14:57:37.453+01:00| vthread-4| I125: Invoking modinfo on "vmci". 2017-08-28T14:57:37.454+01:00| vthread-4| I125: "/sbin/modinfo" exited with status 256. 2017-08-28T14:57:37.454+01:00| vthread-4| I125: Invoking modinfo on "vsock". 2017-08-28T14:57:37.455+01:00| vthread-4| I125: "/sbin/modinfo" exited with status 0. 2017-08-28T14:57:37.466+01:00| vthread-4| I125: to be installed: vmmon status: 0 2017-08-28T14:57:37.466+01:00| vthread-4| I125: to be installed: vmnet status: 0 2017-08-28T14:57:37.587+01:00| vthread-4| I125: Obtaining info using the running kernel. 2017-08-28T14:57:37.587+01:00| vthread-4| I125: Setting header path for 4.10.0-33-generic to "/lib/modules/4.10.0-33-generic/build/include". 2017-08-28T14:57:37.587+01:00| vthread-4| I125: Validating path "/lib/modules/4.10.0-33-generic/build/include" for kernel release "4.10.0-33-generic". 2017-08-28T14:57:37.587+01:00| vthread-4| I125: Failed to find /lib/modules/4.10.0-33-generic/build/include/linux/version.h 2017-08-28T14:57:37.587+01:00| vthread-4| I125: /lib/modules/4.10.0-33-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead. 2017-08-28T14:57:37.587+01:00| vthread-4| I125: using /usr/bin/gcc for preprocess check 2017-08-28T14:57:37.594+01:00| vthread-4| I125: Preprocessed UTS_RELEASE, got value "4.10.0-33-generic". 2017-08-28T14:57:37.595+01:00| vthread-4| I125: The header path "/lib/modules/4.10.0-33-generic/build/include" for the kernel "4.10.0-33-generic" is valid.  Whoohoo! 2017-08-28T14:57:37.708+01:00| vthread-4| I125: found symbol version file /lib/modules/4.10.0-33-generic/build/Module.symvers 2017-08-28T14:57:37.708+01:00| vthread-4| I125: Reading symbol versions from /lib/modules/4.10.0-33-generic/build/Module.symvers. 2017-08-28T14:57:37.725+01:00| vthread-4| I125: Read 21375 symbol versions 2017-08-28T14:57:37.725+01:00| vthread-4| I125: Kernel header path retrieved from FileEntry: /lib/modules/4.10.0-33-generic/build/include 2017-08-28T14:57:37.725+01:00| vthread-4| I125: Update kernel header path to /lib/modules/4.10.0-33-generic/build/include 2017-08-28T14:57:37.725+01:00| vthread-4| I125: Validating path "/lib/modules/4.10.0-33-generic/build/include" for kernel release "4.10.0-33-generic". 2017-08-28T14:57:37.725+01:00| vthread-4| I125: Failed to find /lib/modules/4.10.0-33-generic/build/include/linux/version.h 2017-08-28T14:57:37.725+01:00| vthread-4| I125: /lib/modules/4.10.0-33-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead. 2017-08-28T14:57:37.725+01:00| vthread-4| I125: using /usr/bin/gcc for preprocess check 2017-08-28T14:57:37.731+01:00| vthread-4| I125: Preprocessed UTS_RELEASE, got value "4.10.0-33-generic". 2017-08-28T14:57:37.731+01:00| vthread-4| I125: The header path "/lib/modules/4.10.0-33-generic/build/include" for the kernel "4.10.0-33-generic" is valid.  Whoohoo! 2017-08-28T14:57:37.732+01:00| vthread-4| I125: Found compiler at "/usr/bin/gcc" 2017-08-28T14:57:37.734+01:00| vthread-4| I125: Got gcc version "5.4.0". 2017-08-28T14:57:37.734+01:00| vthread-4| I125: The GCC version matches the kernel GCC minor version like a glove. 2017-08-28T14:57:37.734+01:00| vthread-4| I125: Using user supplied compiler "/usr/bin/gcc". 2017-08-28T14:57:37.736+01:00| vthread-4| I125: Got gcc version "5.4.0". 2017-08-28T14:57:37.736+01:00| vthread-4| I125: The GCC version matches the kernel GCC minor version like a glove. 2017-08-28T14:57:37.737+01:00| vthread-4| I125: Trying to find a suitable PBM set for kernel "4.10.0-33-generic". 2017-08-28T14:57:37.737+01:00| vthread-4| I125: No matching PBM set was found for kernel "4.10.0-33-generic". 2017-08-28T14:57:37.737+01:00| vthread-4| I125: The GCC version matches the kernel GCC minor version like a glove. 2017-08-28T14:57:37.737+01:00| vthread-4| I125: Validating path "/lib/modules/4.10.0-33-generic/build/include" for kernel release "4.10.0-33-generic". 2017-08-28T14:57:37.737+01:00| vthread-4| I125: Failed to find /lib/modules/4.10.0-33-generic/build/include/linux/version.h 2017-08-28T14:57:37.737+01:00| vthread-4| I125: /lib/modules/4.10.0-33-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead. 2017-08-28T14:57:37.737+01:00| vthread-4| I125: using /usr/bin/gcc for preprocess check 2017-08-28T14:57:37.743+01:00| vthread-4| I125: Preprocessed UTS_RELEASE, got value "4.10.0-33-generic". 2017-08-28T14:57:37.743+01:00| vthread-4| I125: The header path "/lib/modules/4.10.0-33-generic/build/include" for the kernel "4.10.0-33-generic" is valid.  Whoohoo! 2017-08-28T14:57:37.743+01:00| vthread-4| I125: The GCC version matches the kernel GCC minor version like a glove. 2017-08-28T14:57:37.744+01:00| vthread-4| I125: Validating path "/lib/modules/4.10.0-33-generic/build/include" for kernel release "4.10.0-33-generic". 2017-08-28T14:57:37.744+01:00| vthread-4| I125: Failed to find /lib/modules/4.10.0-33-generic/build/include/linux/version.h 2017-08-28T14:57:37.744+01:00| vthread-4| I125: /lib/modules/4.10.0-33-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead. 2017-08-28T14:57:37.744+01:00| vthread-4| I125: using /usr/bin/gcc for preprocess check 2017-08-28T14:57:37.750+01:00| vthread-4| I125: Preprocessed UTS_RELEASE, got value "4.10.0-33-generic". 2017-08-28T14:57:37.750+01:00| vthread-4| I125: The header path "/lib/modules/4.10.0-33-generic/build/include" for the kernel "4.10.0-33-generic" is valid.  Whoohoo! 2017-08-28T14:57:37.750+01:00| vthread-4| I125: Using temp dir "/tmp". 2017-08-28T14:57:37.751+01:00| vthread-4| I125: Obtaining info using the running kernel. 2017-08-28T14:57:37.751+01:00| vthread-4| I125: Setting header path for 4.10.0-33-generic to "/lib/modules/4.10.0-33-generic/build/include". 2017-08-28T14:57:37.752+01:00| vthread-4| I125: Validating path "/lib/modules/4.10.0-33-generic/build/include" for kernel release "4.10.0-33-generic". 2017-08-28T14:57:37.752+01:00| vthread-4| I125: Failed to find /lib/modules/4.10.0-33-generic/build/include/linux/version.h 2017-08-28T14:57:37.752+01:00| vthread-4| I125: /lib/modules/4.10.0-33-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead. 2017-08-28T14:57:37.752+01:00| vthread-4| I125: using /usr/bin/gcc for preprocess check 2017-08-28T14:57:37.758+01:00| vthread-4| I125: Preprocessed UTS_RELEASE, got value "4.10.0-33-generic". 2017-08-28T14:57:37.758+01:00| vthread-4| I125: The header path "/lib/modules/4.10.0-33-generic/build/include" for the kernel "4.10.0-33-generic" is valid.  Whoohoo! 2017-08-28T14:57:37.874+01:00| vthread-4| I125: found symbol version file /lib/modules/4.10.0-33-generic/build/Module.symvers 2017-08-28T14:57:37.874+01:00| vthread-4| I125: Reading symbol versions from /lib/modules/4.10.0-33-generic/build/Module.symvers. 2017-08-28T14:57:37.891+01:00| vthread-4| I125: Read 21375 symbol versions 2017-08-28T14:57:37.891+01:00| vthread-4| I125: Invoking modinfo on "vmmon". 2017-08-28T14:57:37.892+01:00| vthread-4| I125: "/sbin/modinfo" exited with status 256. 2017-08-28T14:57:37.892+01:00| vthread-4| I125: Invoking modinfo on "vmnet". 2017-08-28T14:57:37.894+01:00| vthread-4| I125: "/sbin/modinfo" exited with status 256. 2017-08-28T14:57:38.851+01:00| vthread-4| I125: Setting destination path for vmmon to "/lib/modules/4.10.0-33-generic/misc/vmmon.ko". 2017-08-28T14:57:38.851+01:00| vthread-4| I125: Extracting the vmmon source from "/usr/lib/vmware/modules/source/vmmon.tar". 2017-08-28T14:57:38.917+01:00| vthread-4| I125: Successfully extracted the vmmon source. 2017-08-28T14:57:38.917+01:00| vthread-4| I125: Building module with command "/usr/bin/make -j8 -C /tmp/modconfig-PBD1on/vmmon-only auto-build HEADER_DIR=/lib/modules/4.10.0-33-generic/build/include CC=/usr/bin/gcc IS_GCC_3=no" 2017-08-28T14:57:47.823+01:00| vthread-4| W115: Failed to build vmmon.  Failed to execute the build command. 2017-08-28T14:57:47.824+01:00| vthread-4| I125: Setting destination path for vmnet to "/lib/modules/4.10.0-33-generic/misc/vmnet.ko". 2017-08-28T14:57:47.824+01:00| vthread-4| I125: Extracting the vmnet source from "/usr/lib/vmware/modules/source/vmnet.tar". 2017-08-28T14:57:47.883+01:00| vthread-4| I125: Successfully extracted the vmnet source. 2017-08-28T14:57:47.883+01:00| vthread-4| I125: Building module with command "/usr/bin/make -j8 -C /tmp/modconfig-PBD1on/vmnet-only auto-build HEADER_DIR=/lib/modules/4.10.0-33-generic/build/include CC=/usr/bin/gcc IS_GCC_3=no" 2017-08-28T14:57:52.713+01:00| vthread-4| W115: Failed to build vmnet.  Failed to execute the build command.
```     Can anyone help?

---

### Post by sp40140 on 2017-08-29
There is no issue with new kernel. I am running same one as you and my vmware 12 workstation player works fine.
May be you can re-start your machine and try again and see if that fixes your issue.

---

### Post by jonasre on 2017-08-31
I've got the same issue here. I'm using Ubuntu 17.04 and workstation 12.

---

### Post by voriain on 2017-08-31
I restarted my laptop a few times now.
I ensured that I'm using the most recent version of Vmware Workstation (12.5).
Still nothing doing. Problem persists.

---

### Post by flyklr on 2017-08-31
I'm having the same problem with Ubuntu 16.04.

I've rebooted my VM and laptop multiple times and have tried using both the NAT settings and Bridged settings that had worked with the previous kernel.

---

### Post by sp40140 on 2017-08-31
Do you guys have same errors in the log file?

---

### Post by cowpicket on 2017-09-15
Hi, I was having the exact same problem. 

Using Ubuntu 16.04.3, [COLOR=#000000][FONT=&amp]4.10.0-33-generic [/FONT][/COLOR]and VMWare Workstation 12.5.1. 

This was output from the log file:

```

2017-09-15T14:44:00.800-04:00| vthread-4| I125: Log for VMware Workstation pid=2555 version=12.5.1 build=build-4542065 option=Release
2017-09-15T14:44:00.800-04:00| vthread-4| I125: The process is 64-bit.
2017-09-15T14:44:00.800-04:00| vthread-4| I125: Host codepage=UTF-8 encoding=UTF-8
2017-09-15T14:44:00.800-04:00| vthread-4| I125: Host is Linux 4.10.0-33-generic Ubuntu 16.04.3 LTS
2017-09-15T14:44:00.800-04:00| vthread-4| I125: DictionaryLoad: Cannot open file "/usr/lib/vmware/settings": No such file or directory.
2017-09-15T14:44:00.800-04:00| vthread-4| I125: PREF Optional preferences file not found at /usr/lib/vmware/settings. Using default values.
2017-09-15T14:44:00.800-04:00| vthread-4| I125: DictionaryLoad: Cannot open file "/root/.vmware/config": No such file or directory.
2017-09-15T14:44:00.800-04:00| vthread-4| I125: PREF Optional preferences file not found at /root/.vmware/config. Using default values.
2017-09-15T14:44:00.800-04:00| vthread-4| I125: PREF Unable to check permissions for preferences file.
2017-09-15T14:44:00.800-04:00| vthread-4| I125: DictionaryLoad: Cannot open file "/root/.vmware/preferences": No such file or directory.
2017-09-15T14:44:00.800-04:00| vthread-4| I125: PREF Failed to load user preferences.
2017-09-15T14:44:00.857-04:00| vthread-4| W115: Logging to /tmp/vmware-root/vmware-2555.log
2017-09-15T14:44:00.869-04:00| vthread-4| I125: Obtaining info using the running kernel.
2017-09-15T14:44:00.869-04:00| vthread-4| I125: Created new pathsHash.
2017-09-15T14:44:00.869-04:00| vthread-4| I125: Setting header path for 4.10.0-33-generic to "/lib/modules/4.10.0-33-generic/build/include".
2017-09-15T14:44:00.869-04:00| vthread-4| I125: Validating path "/lib/modules/4.10.0-33-generic/build/include" for kernel release "4.10.0-33-generic".
2017-09-15T14:44:00.869-04:00| vthread-4| I125: Failed to find /lib/modules/4.10.0-33-generic/build/include/linux/version.h
2017-09-15T14:44:00.869-04:00| vthread-4| I125: /lib/modules/4.10.0-33-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2017-09-15T14:44:00.869-04:00| vthread-4| I125: using /usr/bin/gcc for preprocess check
2017-09-15T14:44:00.876-04:00| vthread-4| I125: Preprocessed UTS_RELEASE, got value "4.10.0-33-generic".
2017-09-15T14:44:00.876-04:00| vthread-4| I125: The header path "/lib/modules/4.10.0-33-generic/build/include" for the kernel "4.10.0-33-generic" is valid.  Whoohoo!
2017-09-15T14:44:01.044-04:00| vthread-4| I125: found symbol version file /lib/modules/4.10.0-33-generic/build/Module.symvers
2017-09-15T14:44:01.044-04:00| vthread-4| I125: Reading symbol versions from /lib/modules/4.10.0-33-generic/build/Module.symvers.
2017-09-15T14:44:01.073-04:00| vthread-4| I125: Read 21375 symbol versions
2017-09-15T14:44:01.073-04:00| vthread-4| I125: Reading in info for the vmmon module.
2017-09-15T14:44:01.073-04:00| vthread-4| I125: Reading in info for the vmnet module.
2017-09-15T14:44:01.073-04:00| vthread-4| I125: Reading in info for the vmblock module.
2017-09-15T14:44:01.073-04:00| vthread-4| I125: Reading in info for the vmci module.
2017-09-15T14:44:01.073-04:00| vthread-4| I125: Reading in info for the vsock module.
2017-09-15T14:44:01.073-04:00| vthread-4| I125: Setting vsock to depend on vmci.
2017-09-15T14:44:01.073-04:00| vthread-4| I125: Invoking modinfo on "vmmon".
2017-09-15T14:44:01.075-04:00| vthread-4| I125: "/sbin/modinfo" exited with status 256.
2017-09-15T14:44:01.075-04:00| vthread-4| I125: Invoking modinfo on "vmnet".
2017-09-15T14:44:01.076-04:00| vthread-4| I125: "/sbin/modinfo" exited with status 256.
2017-09-15T14:44:01.076-04:00| vthread-4| I125: Invoking modinfo on "vmblock".
2017-09-15T14:44:01.078-04:00| vthread-4| I125: "/sbin/modinfo" exited with status 256.
2017-09-15T14:44:01.078-04:00| vthread-4| I125: Invoking modinfo on "vmci".
2017-09-15T14:44:01.080-04:00| vthread-4| I125: "/sbin/modinfo" exited with status 256.
2017-09-15T14:44:01.080-04:00| vthread-4| I125: Invoking modinfo on "vsock".
2017-09-15T14:44:01.082-04:00| vthread-4| I125: "/sbin/modinfo" exited with status 0.
2017-09-15T14:44:01.101-04:00| vthread-4| I125: to be installed: vmmon status: 0
2017-09-15T14:44:01.102-04:00| vthread-4| I125: to be installed: vmnet status: 0
2017-09-15T14:44:01.123-04:00| vthread-4| I125: Obtaining info using the running kernel.
2017-09-15T14:44:01.123-04:00| vthread-4| I125: Setting header path for 4.10.0-33-generic to "/lib/modules/4.10.0-33-generic/build/include".
2017-09-15T14:44:01.123-04:00| vthread-4| I125: Validating path "/lib/modules/4.10.0-33-generic/build/include" for kernel release "4.10.0-33-generic".
2017-09-15T14:44:01.123-04:00| vthread-4| I125: Failed to find /lib/modules/4.10.0-33-generic/build/include/linux/version.h
2017-09-15T14:44:01.123-04:00| vthread-4| I125: /lib/modules/4.10.0-33-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2017-09-15T14:44:01.123-04:00| vthread-4| I125: using /usr/bin/gcc for preprocess check
2017-09-15T14:44:01.129-04:00| vthread-4| I125: Preprocessed UTS_RELEASE, got value "4.10.0-33-generic".
2017-09-15T14:44:01.129-04:00| vthread-4| I125: The header path "/lib/modules/4.10.0-33-generic/build/include" for the kernel "4.10.0-33-generic" is valid.  Whoohoo!
2017-09-15T14:44:01.294-04:00| vthread-4| I125: found symbol version file /lib/modules/4.10.0-33-generic/build/Module.symvers
2017-09-15T14:44:01.294-04:00| vthread-4| I125: Reading symbol versions from /lib/modules/4.10.0-33-generic/build/Module.symvers.
2017-09-15T14:44:01.322-04:00| vthread-4| I125: Read 21375 symbol versions
2017-09-15T14:44:01.322-04:00| vthread-4| I125: Kernel header path retrieved from FileEntry: /lib/modules/4.10.0-33-generic/build/include
2017-09-15T14:44:01.322-04:00| vthread-4| I125: Update kernel header path to /lib/modules/4.10.0-33-generic/build/include
2017-09-15T14:44:01.322-04:00| vthread-4| I125: Validating path "/lib/modules/4.10.0-33-generic/build/include" for kernel release "4.10.0-33-generic".
2017-09-15T14:44:01.322-04:00| vthread-4| I125: Failed to find /lib/modules/4.10.0-33-generic/build/include/linux/version.h
2017-09-15T14:44:01.322-04:00| vthread-4| I125: /lib/modules/4.10.0-33-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2017-09-15T14:44:01.322-04:00| vthread-4| I125: using /usr/bin/gcc for preprocess check
2017-09-15T14:44:01.328-04:00| vthread-4| I125: Preprocessed UTS_RELEASE, got value "4.10.0-33-generic".
2017-09-15T14:44:01.328-04:00| vthread-4| I125: The header path "/lib/modules/4.10.0-33-generic/build/include" for the kernel "4.10.0-33-generic" is valid.  Whoohoo!
2017-09-15T14:44:01.329-04:00| vthread-4| I125: Found compiler at "/usr/bin/gcc"
2017-09-15T14:44:01.332-04:00| vthread-4| I125: Got gcc version "5.4.0".
2017-09-15T14:44:01.332-04:00| vthread-4| I125: The GCC version matches the kernel GCC minor version like a glove.
2017-09-15T14:44:01.332-04:00| vthread-4| I125: Using user supplied compiler "/usr/bin/gcc".
2017-09-15T14:44:01.335-04:00| vthread-4| I125: Got gcc version "5.4.0".
2017-09-15T14:44:01.335-04:00| vthread-4| I125: The GCC version matches the kernel GCC minor version like a glove.
2017-09-15T14:44:01.336-04:00| vthread-4| I125: Trying to find a suitable PBM set for kernel "4.10.0-33-generic".
2017-09-15T14:44:01.336-04:00| vthread-4| I125: No matching PBM set was found for kernel "4.10.0-33-generic".
2017-09-15T14:44:01.336-04:00| vthread-4| I125: The GCC version matches the kernel GCC minor version like a glove.
2017-09-15T14:44:01.336-04:00| vthread-4| I125: Validating path "/lib/modules/4.10.0-33-generic/build/include" for kernel release "4.10.0-33-generic".
2017-09-15T14:44:01.336-04:00| vthread-4| I125: Failed to find /lib/modules/4.10.0-33-generic/build/include/linux/version.h
2017-09-15T14:44:01.336-04:00| vthread-4| I125: /lib/modules/4.10.0-33-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2017-09-15T14:44:01.336-04:00| vthread-4| I125: using /usr/bin/gcc for preprocess check
2017-09-15T14:44:01.342-04:00| vthread-4| I125: Preprocessed UTS_RELEASE, got value "4.10.0-33-generic".
2017-09-15T14:44:01.342-04:00| vthread-4| I125: The header path "/lib/modules/4.10.0-33-generic/build/include" for the kernel "4.10.0-33-generic" is valid.  Whoohoo!
2017-09-15T14:44:01.343-04:00| vthread-4| I125: The GCC version matches the kernel GCC minor version like a glove.
2017-09-15T14:44:01.343-04:00| vthread-4| I125: Validating path "/lib/modules/4.10.0-33-generic/build/include" for kernel release "4.10.0-33-generic".
2017-09-15T14:44:01.344-04:00| vthread-4| I125: Failed to find /lib/modules/4.10.0-33-generic/build/include/linux/version.h
2017-09-15T14:44:01.344-04:00| vthread-4| I125: /lib/modules/4.10.0-33-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2017-09-15T14:44:01.344-04:00| vthread-4| I125: using /usr/bin/gcc for preprocess check
2017-09-15T14:44:01.349-04:00| vthread-4| I125: Preprocessed UTS_RELEASE, got value "4.10.0-33-generic".
2017-09-15T14:44:01.349-04:00| vthread-4| I125: The header path "/lib/modules/4.10.0-33-generic/build/include" for the kernel "4.10.0-33-generic" is valid.  Whoohoo!
2017-09-15T14:44:01.349-04:00| vthread-4| I125: Using temp dir "/tmp".
2017-09-15T14:44:01.351-04:00| vthread-4| I125: Obtaining info using the running kernel.
2017-09-15T14:44:01.351-04:00| vthread-4| I125: Setting header path for 4.10.0-33-generic to "/lib/modules/4.10.0-33-generic/build/include".
2017-09-15T14:44:01.351-04:00| vthread-4| I125: Validating path "/lib/modules/4.10.0-33-generic/build/include" for kernel release "4.10.0-33-generic".
2017-09-15T14:44:01.351-04:00| vthread-4| I125: Failed to find /lib/modules/4.10.0-33-generic/build/include/linux/version.h
2017-09-15T14:44:01.351-04:00| vthread-4| I125: /lib/modules/4.10.0-33-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2017-09-15T14:44:01.351-04:00| vthread-4| I125: using /usr/bin/gcc for preprocess check
2017-09-15T14:44:01.358-04:00| vthread-4| I125: Preprocessed UTS_RELEASE, got value "4.10.0-33-generic".
2017-09-15T14:44:01.358-04:00| vthread-4| I125: The header path "/lib/modules/4.10.0-33-generic/build/include" for the kernel "4.10.0-33-generic" is valid.  Whoohoo!
2017-09-15T14:44:01.520-04:00| vthread-4| I125: found symbol version file /lib/modules/4.10.0-33-generic/build/Module.symvers
2017-09-15T14:44:01.520-04:00| vthread-4| I125: Reading symbol versions from /lib/modules/4.10.0-33-generic/build/Module.symvers.
2017-09-15T14:44:01.548-04:00| vthread-4| I125: Read 21375 symbol versions
2017-09-15T14:44:01.548-04:00| vthread-4| I125: Invoking modinfo on "vmmon".
2017-09-15T14:44:01.550-04:00| vthread-4| I125: "/sbin/modinfo" exited with status 256.
2017-09-15T14:44:01.550-04:00| vthread-4| I125: Invoking modinfo on "vmnet".
2017-09-15T14:44:01.553-04:00| vthread-4| I125: "/sbin/modinfo" exited with status 256.
2017-09-15T14:44:01.997-04:00| vthread-4| I125: Setting destination path for vmmon to "/lib/modules/4.10.0-33-generic/misc/vmmon.ko".
2017-09-15T14:44:01.998-04:00| vthread-4| I125: Extracting the vmmon source from "/usr/lib/vmware/modules/source/vmmon.tar".
2017-09-15T14:44:02.016-04:00| vthread-4| I125: Successfully extracted the vmmon source.
2017-09-15T14:44:02.016-04:00| vthread-4| I125: Building module with command "/usr/bin/make -j4 -C /tmp/modconfig-2tJIvO/vmmon-only auto-build HEADER_DIR=/lib/modules/4.10.0-33-generic/build/include CC=/usr/bin/gcc IS_GCC_3=no"
2017-09-15T14:44:04.133-04:00| vthread-4| W115: Failed to build vmmon.  Failed to execute the build command.
2017-09-15T14:44:04.135-04:00| vthread-4| I125: Setting destination path for vmnet to "/lib/modules/4.10.0-33-generic/misc/vmnet.ko".
2017-09-15T14:44:04.135-04:00| vthread-4| I125: Extracting the vmnet source from "/usr/lib/vmware/modules/source/vmnet.tar".
2017-09-15T14:44:04.144-04:00| vthread-4| I125: Successfully extracted the vmnet source.
2017-09-15T14:44:04.144-04:00| vthread-4| I125: Building module with command "/usr/bin/make -j4 -C /tmp/modconfig-2tJIvO/vmnet-only auto-build HEADER_DIR=/lib/modules/4.10.0-33-generic/build/include CC=/usr/bin/gcc IS_GCC_3=no"
2017-09-15T14:44:05.801-04:00| vthread-4| W115: Failed to build vmnet.  Failed to execute the build command.

```

After a much searching and not finding any answers I simply downloaded the installer from VMWare website (12.5.7) and did a clean install. The installer also takes care of the uninstalling of the previous version. In all it took about 5 minutes, very painless, and now it's working.

Note: I did receive an alert notifying me of a newer version available for upgrade but I have ignored it for the time being.

---

### Post by voriain on 2017-09-22
I downloaded the latest from [https://www.vmware.com/products/workstation/workstation-evaluation.html](https://www.vmware.com/products/workstation/workstation-evaluation.html) and it worked.

---

### Post by kilaka on 2018-01-11
Uninstalled, downloaded and installing the latest version of vmware workstation 12.
Still didn't work for me.
Still getting the error: `Failed to build vmnet.  Failed to execute the build command.` from the log file :(
Ubuntu 16.04.
Kernel: 4.13.0-26.
VmWare: 12.5.9-7535481. Released on 2018-01-10,

---

### Post by chadb4184 on 2018-01-25
> **kilaka said:**
> Uninstalled, downloaded and installing the latest version of vmware workstation 12.
Still didn't work for me.
Still getting the error: `Failed to build vmnet.  Failed to execute the build command.` from the log file :(
Ubuntu 16.04.
Kernel: 4.13.0-26.
VmWare: 12.5.9-7535481. Released on 2018-01-10,

I am getting the same.

I have tried re-installing, as well. Still getting the same 'Failed to build vmnet. Failed to execute the build command.'

Ubuntu 16.04
Kernel: 4.13.0-26
VmWare: 12.5.9-7535481 64-bit

---

