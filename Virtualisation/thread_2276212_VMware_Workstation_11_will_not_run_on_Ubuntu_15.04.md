---
title: "VMware Workstation 11 will not run on Ubuntu 15.04 (Kernel 3.19.0-15-generic)"
date: 2015-04-30
forum: Virtualisation
---

### Post by sub sexy on 2015-04-30
I recently did a clean upgrade to Ubuntu 15.04 and after installing VMware I am unable to run it. When I launch VMware I receive a  message stating several modules must be compiled first. I select install and got an error stating it was unable to start services. Below are the details of my machine,screenshots and the error logs. Any help would be greatly appreciated. I am not new to Ubuntu but very new to VMware so please be as descriptiveas possible with the answer. Appreciate the help in advance. 

VMware Workstation 11

# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 15.04
Release:	15.04
Codename:	vivid

# uname -a
Linux gareth-Inspiron-7720 3.19.0-15-generic #15-Ubuntu SMP Thu Apr 16 23:32:37 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

# vmware -v
VMware Workstation 11.1.0 build-2496824

# vmplayer --version
VMware Player 7.1.0 build-2496824

Logs from /tmp/vmware-root/vmware10423.log

2015-04-30T15:55:23.790-04:00| vthread-4| I120: Log for VMware Workstation pid=10423 version=11.1.0 build=build-2496824 option=Release
2015-04-30T15:55:23.790-04:00| vthread-4| I120: The process is 64-bit.
2015-04-30T15:55:23.790-04:00| vthread-4| I120: Host codepage=UTF-8 encoding=UTF-8
2015-04-30T15:55:23.790-04:00| vthread-4| I120: Host is Linux 3.19.0-15-generic Ubuntu 15.04
2015-04-30T15:55:23.790-04:00| vthread-4| I120: DictionaryLoad: Cannot open file "/usr/lib/vmware/settings": No such file or directory.
2015-04-30T15:55:23.790-04:00| vthread-4| I120: Msg_Reset:
2015-04-30T15:55:23.790-04:00| vthread-4| I120: [msg.dictionary.load.openFailed] Cannot open file "/usr/lib/vmware/settings": No such file or directory.
2015-04-30T15:55:23.790-04:00| vthread-4| I120: ----------------------------------------
2015-04-30T15:55:23.790-04:00| vthread-4| I120: PREF Optional preferences file not found at /usr/lib/vmware/settings. Using default values.
2015-04-30T15:55:23.790-04:00| vthread-4| I120: DictionaryLoad: Cannot open file "/home/gareth/.vmware/config": No such file or directory.
2015-04-30T15:55:23.790-04:00| vthread-4| I120: Msg_Reset:
2015-04-30T15:55:23.790-04:00| vthread-4| I120: [msg.dictionary.load.openFailed] Cannot open file "/home/gareth/.vmware/config": No such file or directory.
2015-04-30T15:55:23.790-04:00| vthread-4| I120: ----------------------------------------
2015-04-30T15:55:23.790-04:00| vthread-4| I120: PREF Optional preferences file not found at /home/gareth/.vmware/config. Using default values.
2015-04-30T15:55:23.790-04:00| vthread-4| I120: PREF Unable to check permissions for preferences file.
2015-04-30T15:55:23.790-04:00| vthread-4| I120: DictionaryLoad: Cannot open file "/home/gareth/.vmware/preferences": No such file or directory.
2015-04-30T15:55:23.790-04:00| vthread-4| I120: Msg_Reset:
2015-04-30T15:55:23.790-04:00| vthread-4| I120: [msg.dictionary.load.openFailed] Cannot open file "/home/gareth/.vmware/preferences": No such file or directory.
2015-04-30T15:55:23.790-04:00| vthread-4| I120: ----------------------------------------
2015-04-30T15:55:23.790-04:00| vthread-4| I120: PREF Failed to load user preferences.
2015-04-30T15:55:23.830-04:00| vthread-4| W110: Logging to /tmp/vmware-root/vmware-10423.log
2015-04-30T15:55:23.851-04:00| vthread-4| I120: Obtaining info using the running kernel.
2015-04-30T15:55:23.851-04:00| vthread-4| I120: Created new pathsHash.
2015-04-30T15:55:23.851-04:00| vthread-4| I120: Setting header path for 3.19.0-15-generic to "/lib/modules/3.19.0-15-generic/build/include".
2015-04-30T15:55:23.851-04:00| vthread-4| I120: Validating path "/lib/modules/3.19.0-15-generic/build/include" for kernel release "3.19.0-15-generic".
2015-04-30T15:55:23.851-04:00| vthread-4| I120: Failed to find /lib/modules/3.19.0-15-generic/build/include/linux/version.h
2015-04-30T15:55:23.851-04:00| vthread-4| I120: /lib/modules/3.19.0-15-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2015-04-30T15:55:23.851-04:00| vthread-4| I120: using /usr/bin/gcc-4.9 for preprocess check
2015-04-30T15:55:23.857-04:00| vthread-4| I120: Preprocessed UTS_RELEASE, got value "3.19.0-15-generic".
2015-04-30T15:55:23.858-04:00| vthread-4| I120: The header path "/lib/modules/3.19.0-15-generic/build/include" for the kernel "3.19.0-15-generic" is valid.  Whoohoo!
2015-04-30T15:55:24.043-04:00| vthread-4| I120: found symbol version file /lib/modules/3.19.0-15-generic/build/Module.symvers
2015-04-30T15:55:24.043-04:00| vthread-4| I120: Reading symbol versions from /lib/modules/3.19.0-15-generic/build/Module.symvers.
2015-04-30T15:55:24.061-04:00| vthread-4| I120: Read 18818 symbol versions
2015-04-30T15:55:24.061-04:00| vthread-4| I120: Reading in info for the vmmon module.
2015-04-30T15:55:24.061-04:00| vthread-4| I120: Reading in info for the vmnet module.
2015-04-30T15:55:24.061-04:00| vthread-4| I120: Reading in info for the vmblock module.
2015-04-30T15:55:24.061-04:00| vthread-4| I120: Reading in info for the vmci module.
2015-04-30T15:55:24.061-04:00| vthread-4| I120: Reading in info for the vsock module.
2015-04-30T15:55:24.061-04:00| vthread-4| I120: Setting vsock to depend on vmci.
2015-04-30T15:55:24.061-04:00| vthread-4| I120: Invoking modinfo on "vmmon".
2015-04-30T15:55:24.064-04:00| vthread-4| I120: "/sbin/modinfo" exited with status 0.
2015-04-30T15:55:24.064-04:00| vthread-4| I120: Invoking modinfo on "vmnet".
2015-04-30T15:55:24.066-04:00| vthread-4| I120: "/sbin/modinfo" exited with status 256.
2015-04-30T15:55:24.066-04:00| vthread-4| I120: Invoking modinfo on "vmblock".
2015-04-30T15:55:24.067-04:00| vthread-4| I120: "/sbin/modinfo" exited with status 256.
2015-04-30T15:55:24.067-04:00| vthread-4| I120: Invoking modinfo on "vmci".
2015-04-30T15:55:24.069-04:00| vthread-4| I120: "/sbin/modinfo" exited with status 256.
2015-04-30T15:55:24.070-04:00| vthread-4| I120: Invoking modinfo on "vsock".
2015-04-30T15:55:24.072-04:00| vthread-4| I120: "/sbin/modinfo" exited with status 0.
2015-04-30T15:55:24.095-04:00| vthread-4| I120: to be installed: vmnet status: 0
2015-04-30T15:55:24.113-04:00| vthread-4| I120: Obtaining info using the running kernel.
2015-04-30T15:55:24.113-04:00| vthread-4| I120: Setting header path for 3.19.0-15-generic to "/lib/modules/3.19.0-15-generic/build/include".
2015-04-30T15:55:24.113-04:00| vthread-4| I120: Validating path "/lib/modules/3.19.0-15-generic/build/include" for kernel release "3.19.0-15-generic".
2015-04-30T15:55:24.113-04:00| vthread-4| I120: Failed to find /lib/modules/3.19.0-15-generic/build/include/linux/version.h
2015-04-30T15:55:24.113-04:00| vthread-4| I120: /lib/modules/3.19.0-15-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2015-04-30T15:55:24.113-04:00| vthread-4| I120: using /usr/bin/gcc-4.9 for preprocess check
2015-04-30T15:55:24.121-04:00| vthread-4| I120: Preprocessed UTS_RELEASE, got value "3.19.0-15-generic".
2015-04-30T15:55:24.121-04:00| vthread-4| I120: The header path "/lib/modules/3.19.0-15-generic/build/include" for the kernel "3.19.0-15-generic" is valid.  Whoohoo!
2015-04-30T15:55:24.308-04:00| vthread-4| I120: found symbol version file /lib/modules/3.19.0-15-generic/build/Module.symvers
2015-04-30T15:55:24.308-04:00| vthread-4| I120: Reading symbol versions from /lib/modules/3.19.0-15-generic/build/Module.symvers.
2015-04-30T15:55:24.326-04:00| vthread-4| I120: Read 18818 symbol versions
2015-04-30T15:55:24.327-04:00| vthread-4| I120: Kernel header path retrieved from FileEntry: /lib/modules/3.19.0-15-generic/build/include
2015-04-30T15:55:24.327-04:00| vthread-4| I120: Update kernel header path to /lib/modules/3.19.0-15-generic/build/include
2015-04-30T15:55:24.327-04:00| vthread-4| I120: Validating path "/lib/modules/3.19.0-15-generic/build/include" for kernel release "3.19.0-15-generic".
2015-04-30T15:55:24.327-04:00| vthread-4| I120: Failed to find /lib/modules/3.19.0-15-generic/build/include/linux/version.h
2015-04-30T15:55:24.327-04:00| vthread-4| I120: /lib/modules/3.19.0-15-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2015-04-30T15:55:24.327-04:00| vthread-4| I120: using /usr/bin/gcc-4.9 for preprocess check
2015-04-30T15:55:24.335-04:00| vthread-4| I120: Preprocessed UTS_RELEASE, got value "3.19.0-15-generic".
2015-04-30T15:55:24.335-04:00| vthread-4| I120: The header path "/lib/modules/3.19.0-15-generic/build/include" for the kernel "3.19.0-15-generic" is valid.  Whoohoo!
2015-04-30T15:55:24.336-04:00| vthread-4| I120: Found compiler at "/usr/bin/gcc"
2015-04-30T15:55:24.341-04:00| vthread-4| I120: Got gcc version "4.9.2".
2015-04-30T15:55:24.341-04:00| vthread-4| I120: The GCC version matches the kernel GCC minor version like a glove.
2015-04-30T15:55:24.341-04:00| vthread-4| I120: Using user supplied compiler "/usr/bin/gcc".
2015-04-30T15:55:24.345-04:00| vthread-4| I120: Got gcc version "4.9.2".
2015-04-30T15:55:24.345-04:00| vthread-4| I120: The GCC version matches the kernel GCC minor version like a glove.
2015-04-30T15:55:24.351-04:00| vthread-4| I120: Trying to find a suitable PBM set for kernel "3.19.0-15-generic".
2015-04-30T15:55:24.351-04:00| vthread-4| I120: No matching PBM set was found for kernel "3.19.0-15-generic".
2015-04-30T15:55:24.351-04:00| vthread-4| I120: The GCC version matches the kernel GCC minor version like a glove.
2015-04-30T15:55:24.351-04:00| vthread-4| I120: Validating path "/lib/modules/3.19.0-15-generic/build/include" for kernel release "3.19.0-15-generic".
2015-04-30T15:55:24.351-04:00| vthread-4| I120: Failed to find /lib/modules/3.19.0-15-generic/build/include/linux/version.h
2015-04-30T15:55:24.351-04:00| vthread-4| I120: /lib/modules/3.19.0-15-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2015-04-30T15:55:24.351-04:00| vthread-4| I120: using /usr/bin/gcc-4.9 for preprocess check
2015-04-30T15:55:24.360-04:00| vthread-4| I120: Preprocessed UTS_RELEASE, got value "3.19.0-15-generic".
2015-04-30T15:55:24.361-04:00| vthread-4| I120: The header path "/lib/modules/3.19.0-15-generic/build/include" for the kernel "3.19.0-15-generic" is valid.  Whoohoo!
2015-04-30T15:55:24.363-04:00| vthread-4| I120: The GCC version matches the kernel GCC minor version like a glove.
2015-04-30T15:55:24.363-04:00| vthread-4| I120: Validating path "/lib/modules/3.19.0-15-generic/build/include" for kernel release "3.19.0-15-generic".
2015-04-30T15:55:24.363-04:00| vthread-4| I120: Failed to find /lib/modules/3.19.0-15-generic/build/include/linux/version.h
2015-04-30T15:55:24.363-04:00| vthread-4| I120: /lib/modules/3.19.0-15-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2015-04-30T15:55:24.363-04:00| vthread-4| I120: using /usr/bin/gcc-4.9 for preprocess check
2015-04-30T15:55:24.373-04:00| vthread-4| I120: Preprocessed UTS_RELEASE, got value "3.19.0-15-generic".
2015-04-30T15:55:24.373-04:00| vthread-4| I120: The header path "/lib/modules/3.19.0-15-generic/build/include" for the kernel "3.19.0-15-generic" is valid.  Whoohoo!
2015-04-30T15:55:24.373-04:00| vthread-4| I120: Using temp dir "/tmp".
2015-04-30T15:55:24.374-04:00| vthread-4| I120: Obtaining info using the running kernel.
2015-04-30T15:55:24.374-04:00| vthread-4| I120: Setting header path for 3.19.0-15-generic to "/lib/modules/3.19.0-15-generic/build/include".
2015-04-30T15:55:24.374-04:00| vthread-4| I120: Validating path "/lib/modules/3.19.0-15-generic/build/include" for kernel release "3.19.0-15-generic".
2015-04-30T15:55:24.374-04:00| vthread-4| I120: Failed to find /lib/modules/3.19.0-15-generic/build/include/linux/version.h
2015-04-30T15:55:24.374-04:00| vthread-4| I120: /lib/modules/3.19.0-15-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2015-04-30T15:55:24.374-04:00| vthread-4| I120: using /usr/bin/gcc-4.9 for preprocess check
2015-04-30T15:55:24.382-04:00| vthread-4| I120: Preprocessed UTS_RELEASE, got value "3.19.0-15-generic".
2015-04-30T15:55:24.382-04:00| vthread-4| I120: The header path "/lib/modules/3.19.0-15-generic/build/include" for the kernel "3.19.0-15-generic" is valid.  Whoohoo!
2015-04-30T15:55:24.548-04:00| vthread-4| I120: found symbol version file /lib/modules/3.19.0-15-generic/build/Module.symvers
2015-04-30T15:55:24.548-04:00| vthread-4| I120: Reading symbol versions from /lib/modules/3.19.0-15-generic/build/Module.symvers.
2015-04-30T15:55:24.566-04:00| vthread-4| I120: Read 18818 symbol versions
2015-04-30T15:55:24.566-04:00| vthread-4| I120: Invoking modinfo on "vmnet".
2015-04-30T15:55:24.568-04:00| vthread-4| I120: "/sbin/modinfo" exited with status 256.
2015-04-30T15:55:24.879-04:00| vthread-4| I120: Setting destination path for vmnet to "/lib/modules/3.19.0-15-generic/misc/vmnet.ko".
2015-04-30T15:55:24.879-04:00| vthread-4| I120: Extracting the vmnet source from "/usr/lib/vmware/modules/source/vmnet.tar".
2015-04-30T15:55:24.888-04:00| vthread-4| I120: Successfully extracted the vmnet source.
2015-04-30T15:55:24.888-04:00| vthread-4| I120: Building module with command "/usr/bin/make -j8 -C /tmp/modconfig-mFz0An/vmnet-only auto-build HEADER_DIR=/lib/modules/3.19.0-15-generic/build/include CC=/usr/bin/gcc IS_GCC_3=no"
2015-04-30T15:55:26.778-04:00| vthread-4| W110: Failed to build vmnet.  Failed to execute the build command.

[http://ubuntuforums.org/asset.php?fid=258261&uid=537256&d=1430448900](http://ubuntuforums.org/asset.php?fid=258261&uid=537256&d=1430448900)

---

### Post by sammiev on 2015-04-30
I'm waiting for an update from VMware but there maybe a work around [here]("http://ubuntuforums.org/showthread.php?t=2275220"). 

I tried it but tried a lot of other things first that may of caused this way to fail. 

I have noticed it worked for others.

I will try it again on the weekend when I have more time.

---

### Post by sammiev on 2015-05-02
Removed my install of VMware and tried a fresh install of VMware tonight and applied the fix from this post [here]("http://ubuntuforums.org/showthread.php?t=2275220").

All went well and VMware does work well with 15.04 with the latest kernel.

---

### Post by sub sexy on 2015-05-06
Thanks sammiev. This worked for me as well after a clean install. Thanks a million for the information

---

### Post by sammiev on 2015-05-06
> **sub sexy said:**
> Thanks sammiev. This worked for me as well after a clean install. Thanks a million for the information

Hi,

Glad it worked out for you.

Can you please mark the thread as solved.

Above your 1st post select -Thread Tools - then solved. :)

---

