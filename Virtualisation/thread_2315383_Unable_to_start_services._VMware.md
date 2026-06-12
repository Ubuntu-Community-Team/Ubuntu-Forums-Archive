---
title: "Unable to start services. VMware"
date: 2016-02-28
forum: Virtualisation
---

### Post by Liiz_Tit on 2016-02-28
Help Please.
code: 
[HTML]Unable to start services.

See log file /tmp/vmware-root/vmware-4293.log for details[/HTML]
uname -a
[HTML]
Linux LiizTit 4.2.0-30-generic #35~14.04.1-Ubuntu SMP Fri Feb 19 14:48:13 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

[/HTML]
 file log: gedit /tmp/vmware-root/vmware-4293.log
[HTML]2016-02-28T20:44:25.503+07:00| vthread-4| I120: Log for VMware Workstation pid=4293 version=11.1.2 build=build-2780323 option=Release
2016-02-28T20:44:25.503+07:00| vthread-4| I120: The process is 64-bit.
2016-02-28T20:44:25.503+07:00| vthread-4| I120: Host codepage=UTF-8 encoding=UTF-8
2016-02-28T20:44:25.503+07:00| vthread-4| I120: Host is Linux 4.2.0-30-generic Ubuntu 14.04.4 LTS
2016-02-28T20:44:25.502+07:00| vthread-4| I120: DictionaryLoad: Cannot open file "/usr/lib/vmware/settings": No such file or directory.
2016-02-28T20:44:25.502+07:00| vthread-4| I120: Msg_Reset:
2016-02-28T20:44:25.502+07:00| vthread-4| I120: [msg.dictionary.load.openFailed] Cannot open file "/usr/lib/vmware/settings": No such file or directory.
2016-02-28T20:44:25.502+07:00| vthread-4| I120: ----------------------------------------
2016-02-28T20:44:25.502+07:00| vthread-4| I120: PREF Optional preferences file not found at /usr/lib/vmware/settings. Using default values.
2016-02-28T20:44:25.503+07:00| vthread-4| I120: DictionaryLoad: Cannot open file "/root/.vmware/config": No such file or directory.
2016-02-28T20:44:25.503+07:00| vthread-4| I120: Msg_Reset:
2016-02-28T20:44:25.503+07:00| vthread-4| I120: [msg.dictionary.load.openFailed] Cannot open file "/root/.vmware/config": No such file or directory.
2016-02-28T20:44:25.503+07:00| vthread-4| I120: ----------------------------------------
2016-02-28T20:44:25.503+07:00| vthread-4| I120: PREF Optional preferences file not found at /root/.vmware/config. Using default values.
2016-02-28T20:44:25.503+07:00| vthread-4| I120: PREF Unable to check permissions for preferences file.
2016-02-28T20:44:25.503+07:00| vthread-4| I120: DictionaryLoad: Cannot open file "/root/.vmware/preferences": No such file or directory.
2016-02-28T20:44:25.503+07:00| vthread-4| I120: Msg_Reset:
2016-02-28T20:44:25.503+07:00| vthread-4| I120: [msg.dictionary.load.openFailed] Cannot open file "/root/.vmware/preferences": No such file or directory.
2016-02-28T20:44:25.503+07:00| vthread-4| I120: ----------------------------------------
2016-02-28T20:44:25.503+07:00| vthread-4| I120: PREF Failed to load user preferences.
2016-02-28T20:44:25.546+07:00| vthread-4| W110: Logging to /tmp/vmware-root/vmware-4293.log
2016-02-28T20:44:25.554+07:00| vthread-4| I120: Obtaining info using the running kernel.
2016-02-28T20:44:25.554+07:00| vthread-4| I120: Created new pathsHash.
2016-02-28T20:44:25.554+07:00| vthread-4| I120: Setting header path for 4.2.0-30-generic to "/lib/modules/4.2.0-30-generic/build/include".
2016-02-28T20:44:25.554+07:00| vthread-4| I120: Validating path "/lib/modules/4.2.0-30-generic/build/include" for kernel release "4.2.0-30-generic".
2016-02-28T20:44:25.554+07:00| vthread-4| I120: Failed to find /lib/modules/4.2.0-30-generic/build/include/linux/version.h
2016-02-28T20:44:25.554+07:00| vthread-4| I120: /lib/modules/4.2.0-30-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2016-02-28T20:44:25.554+07:00| vthread-4| I120: using /usr/bin/gcc-4.8 for preprocess check
2016-02-28T20:44:25.559+07:00| vthread-4| I120: Preprocessed UTS_RELEASE, got value "4.2.0-30-generic".
2016-02-28T20:44:25.559+07:00| vthread-4| I120: The header path "/lib/modules/4.2.0-30-generic/build/include" for the kernel "4.2.0-30-generic" is valid.  Whoohoo!
2016-02-28T20:44:25.722+07:00| vthread-4| I120: found symbol version file /lib/modules/4.2.0-30-generic/build/Module.symvers
2016-02-28T20:44:25.722+07:00| vthread-4| I120: Reading symbol versions from /lib/modules/4.2.0-30-generic/build/Module.symvers.
2016-02-28T20:44:25.744+07:00| vthread-4| I120: Read 19472 symbol versions
2016-02-28T20:44:25.744+07:00| vthread-4| I120: Reading in info for the vmmon module.
2016-02-28T20:44:25.744+07:00| vthread-4| I120: Reading in info for the vmnet module.
2016-02-28T20:44:25.744+07:00| vthread-4| I120: Reading in info for the vmblock module.
2016-02-28T20:44:25.744+07:00| vthread-4| I120: Reading in info for the vmci module.
2016-02-28T20:44:25.744+07:00| vthread-4| I120: Reading in info for the vsock module.
2016-02-28T20:44:25.744+07:00| vthread-4| I120: Setting vsock to depend on vmci.
2016-02-28T20:44:25.744+07:00| vthread-4| I120: Invoking modinfo on "vmmon".
2016-02-28T20:44:25.747+07:00| vthread-4| I120: "/sbin/modinfo" exited with status 0.
2016-02-28T20:44:25.747+07:00| vthread-4| I120: Invoking modinfo on "vmnet".
2016-02-28T20:44:25.749+07:00| vthread-4| I120: "/sbin/modinfo" exited with status 256.
2016-02-28T20:44:25.749+07:00| vthread-4| I120: Invoking modinfo on "vmblock".
2016-02-28T20:44:25.750+07:00| vthread-4| I120: "/sbin/modinfo" exited with status 256.
2016-02-28T20:44:25.750+07:00| vthread-4| I120: Invoking modinfo on "vmci".
2016-02-28T20:44:25.752+07:00| vthread-4| I120: "/sbin/modinfo" exited with status 256.
2016-02-28T20:44:25.752+07:00| vthread-4| I120: Invoking modinfo on "vsock".
2016-02-28T20:44:25.754+07:00| vthread-4| I120: "/sbin/modinfo" exited with status 0.
2016-02-28T20:44:25.769+07:00| vthread-4| I120: to be installed: vmnet status: 0
2016-02-28T20:44:25.782+07:00| vthread-4| I120: Obtaining info using the running kernel.
2016-02-28T20:44:25.782+07:00| vthread-4| I120: Setting header path for 4.2.0-30-generic to "/lib/modules/4.2.0-30-generic/build/include".
2016-02-28T20:44:25.782+07:00| vthread-4| I120: Validating path "/lib/modules/4.2.0-30-generic/build/include" for kernel release "4.2.0-30-generic".
2016-02-28T20:44:25.782+07:00| vthread-4| I120: Failed to find /lib/modules/4.2.0-30-generic/build/include/linux/version.h
2016-02-28T20:44:25.782+07:00| vthread-4| I120: /lib/modules/4.2.0-30-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2016-02-28T20:44:25.782+07:00| vthread-4| I120: using /usr/bin/gcc-4.8 for preprocess check
2016-02-28T20:44:25.788+07:00| vthread-4| I120: Preprocessed UTS_RELEASE, got value "4.2.0-30-generic".
2016-02-28T20:44:25.788+07:00| vthread-4| I120: The header path "/lib/modules/4.2.0-30-generic/build/include" for the kernel "4.2.0-30-generic" is valid.  Whoohoo!
2016-02-28T20:44:25.959+07:00| vthread-4| I120: found symbol version file /lib/modules/4.2.0-30-generic/build/Module.symvers
2016-02-28T20:44:25.959+07:00| vthread-4| I120: Reading symbol versions from /lib/modules/4.2.0-30-generic/build/Module.symvers.
2016-02-28T20:44:25.981+07:00| vthread-4| I120: Read 19472 symbol versions
2016-02-28T20:44:25.982+07:00| vthread-4| I120: Kernel header path retrieved from FileEntry: /lib/modules/4.2.0-30-generic/build/include
2016-02-28T20:44:25.982+07:00| vthread-4| I120: Update kernel header path to /lib/modules/4.2.0-30-generic/build/include
2016-02-28T20:44:25.982+07:00| vthread-4| I120: Validating path "/lib/modules/4.2.0-30-generic/build/include" for kernel release "4.2.0-30-generic".
2016-02-28T20:44:25.982+07:00| vthread-4| I120: Failed to find /lib/modules/4.2.0-30-generic/build/include/linux/version.h
2016-02-28T20:44:25.982+07:00| vthread-4| I120: /lib/modules/4.2.0-30-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2016-02-28T20:44:25.982+07:00| vthread-4| I120: using /usr/bin/gcc-4.8 for preprocess check
2016-02-28T20:44:25.987+07:00| vthread-4| I120: Preprocessed UTS_RELEASE, got value "4.2.0-30-generic".
2016-02-28T20:44:25.987+07:00| vthread-4| I120: The header path "/lib/modules/4.2.0-30-generic/build/include" for the kernel "4.2.0-30-generic" is valid.  Whoohoo!
2016-02-28T20:44:25.988+07:00| vthread-4| I120: Found compiler at "/usr/bin/gcc"
2016-02-28T20:44:25.990+07:00| vthread-4| I120: Got gcc version "4.8".
2016-02-28T20:44:25.990+07:00| vthread-4| I120: The GCC version matches the kernel GCC minor version like a glove.
2016-02-28T20:44:25.990+07:00| vthread-4| I120: Using user supplied compiler "/usr/bin/gcc".
2016-02-28T20:44:25.992+07:00| vthread-4| I120: Got gcc version "4.8".
2016-02-28T20:44:25.992+07:00| vthread-4| I120: The GCC version matches the kernel GCC minor version like a glove.
2016-02-28T20:44:25.996+07:00| vthread-4| I120: Trying to find a suitable PBM set for kernel "4.2.0-30-generic".
2016-02-28T20:44:25.996+07:00| vthread-4| I120: No matching PBM set was found for kernel "4.2.0-30-generic".
2016-02-28T20:44:25.996+07:00| vthread-4| I120: The GCC version matches the kernel GCC minor version like a glove.
2016-02-28T20:44:25.996+07:00| vthread-4| I120: Validating path "/lib/modules/4.2.0-30-generic/build/include" for kernel release "4.2.0-30-generic".
2016-02-28T20:44:25.996+07:00| vthread-4| I120: Failed to find /lib/modules/4.2.0-30-generic/build/include/linux/version.h
2016-02-28T20:44:25.996+07:00| vthread-4| I120: /lib/modules/4.2.0-30-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2016-02-28T20:44:25.996+07:00| vthread-4| I120: using /usr/bin/gcc-4.8 for preprocess check
2016-02-28T20:44:26.002+07:00| vthread-4| I120: Preprocessed UTS_RELEASE, got value "4.2.0-30-generic".
2016-02-28T20:44:26.002+07:00| vthread-4| I120: The header path "/lib/modules/4.2.0-30-generic/build/include" for the kernel "4.2.0-30-generic" is valid.  Whoohoo!
2016-02-28T20:44:26.003+07:00| vthread-4| I120: The GCC version matches the kernel GCC minor version like a glove.
2016-02-28T20:44:26.003+07:00| vthread-4| I120: Validating path "/lib/modules/4.2.0-30-generic/build/include" for kernel release "4.2.0-30-generic".
2016-02-28T20:44:26.003+07:00| vthread-4| I120: Failed to find /lib/modules/4.2.0-30-generic/build/include/linux/version.h
2016-02-28T20:44:26.003+07:00| vthread-4| I120: /lib/modules/4.2.0-30-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2016-02-28T20:44:26.003+07:00| vthread-4| I120: using /usr/bin/gcc-4.8 for preprocess check
2016-02-28T20:44:26.008+07:00| vthread-4| I120: Preprocessed UTS_RELEASE, got value "4.2.0-30-generic".
2016-02-28T20:44:26.008+07:00| vthread-4| I120: The header path "/lib/modules/4.2.0-30-generic/build/include" for the kernel "4.2.0-30-generic" is valid.  Whoohoo!
2016-02-28T20:44:26.008+07:00| vthread-4| I120: Using temp dir "/tmp".
2016-02-28T20:44:26.009+07:00| vthread-4| I120: Obtaining info using the running kernel.
2016-02-28T20:44:26.009+07:00| vthread-4| I120: Setting header path for 4.2.0-30-generic to "/lib/modules/4.2.0-30-generic/build/include".
2016-02-28T20:44:26.009+07:00| vthread-4| I120: Validating path "/lib/modules/4.2.0-30-generic/build/include" for kernel release "4.2.0-30-generic".
2016-02-28T20:44:26.009+07:00| vthread-4| I120: Failed to find /lib/modules/4.2.0-30-generic/build/include/linux/version.h
2016-02-28T20:44:26.009+07:00| vthread-4| I120: /lib/modules/4.2.0-30-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2016-02-28T20:44:26.009+07:00| vthread-4| I120: using /usr/bin/gcc-4.8 for preprocess check
2016-02-28T20:44:26.015+07:00| vthread-4| I120: Preprocessed UTS_RELEASE, got value "4.2.0-30-generic".
2016-02-28T20:44:26.015+07:00| vthread-4| I120: The header path "/lib/modules/4.2.0-30-generic/build/include" for the kernel "4.2.0-30-generic" is valid.  Whoohoo!
2016-02-28T20:44:26.217+07:00| vthread-4| I120: found symbol version file /lib/modules/4.2.0-30-generic/build/Module.symvers
2016-02-28T20:44:26.217+07:00| vthread-4| I120: Reading symbol versions from /lib/modules/4.2.0-30-generic/build/Module.symvers.
2016-02-28T20:44:26.241+07:00| vthread-4| I120: Read 19472 symbol versions
2016-02-28T20:44:26.241+07:00| vthread-4| I120: Invoking modinfo on "vmnet".
2016-02-28T20:44:26.243+07:00| vthread-4| I120: "/sbin/modinfo" exited with status 256.
2016-02-28T20:44:26.764+07:00| vthread-4| I120: Setting destination path for vmnet to "/lib/modules/4.2.0-30-generic/misc/vmnet.ko".
2016-02-28T20:44:26.764+07:00| vthread-4| I120: Extracting the vmnet source from "/usr/lib/vmware/modules/source/vmnet.tar".
2016-02-28T20:44:26.769+07:00| vthread-4| I120: Successfully extracted the vmnet source.
2016-02-28T20:44:26.769+07:00| vthread-4| I120: Building module with command "/usr/bin/make -j4 -C /tmp/modconfig-tew7OY/vmnet-only auto-build HEADER_DIR=/lib/modules/4.2.0-30-generic/build/include CC=/usr/bin/gcc IS_GCC_3=no"
2016-02-28T20:44:29.852+07:00| vthread-4| W110: Failed to build vmnet.  Failed to execute the build command.[/HTML]

VMware-Workstation-Full-11.1.2-2780323.x86_64.bundle
help me please!

---

### Post by MAFoElffen on 2016-02-28
So-- 
- What was the VM Guest? (and what is the host?)
- Was is an Easy install or Manual Installation? 
- Was that after an guest install or on an existing or on an exisiting VM that has been running.

---

