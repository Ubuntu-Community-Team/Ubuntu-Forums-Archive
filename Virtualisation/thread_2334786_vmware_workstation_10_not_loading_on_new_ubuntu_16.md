---
title: "vmware workstation 10 not loading on new ubuntu 16.04.01"
date: 2016-08-22
forum: Virtualisation
---

### Post by linux.girl on 2016-08-22
Hello everyone,

 

I  just upgraded my desktop to ubuntu LTS 16.04.01 with kerner  4.4.0-34-generic. I have vmware workstation 10 and now it is not loading  with the following errors and log, can anyone assist me please?


Failed to build vmnet.  Failed to execute the build command.
  Starting VMware services:
  Virtual machine monitor                                            failed
  Virtual machine communication interface                             done
  VM communication interface socket family                            done
  Blocking file system                                                done
  Virtual ethernet                                                   failed
  VMware Authentication Daemon                                        done


  I checked the following:


  sudo modprobe vmnet - to see if it is a secure boot issue - it isn't
  ls -al /dev/vmmon - to see if /dev/vmmon exists - it doesn't
  sudo vmware-modconfig --console --install-all - to see if it fixes it, it didn't
uninstall and reinstall - didn't help either, same error :-(

 
 
Here is the error log, appreciate any help, many thanks in advance!!!!!
 
```
 cat vmware-modconfig-16439.log 
2016-08-22T16:25:44.119+02:00|  vthread-3| I120: Log for VMware Workstation pid=16439 version=10.0.4  build=build-2249910 option=Release
2016-08-22T16:25:44.119+02:00| vthread-3| I120: The process is 64-bit.
2016-08-22T16:25:44.119+02:00| vthread-3| I120: Host codepage=UTF-8 encoding=UTF-8
2016-08-22T16:25:44.119+02:00| vthread-3| I120: Host is Linux 4.4.0-34-generic Ubuntu 16.04.1 LTS
2016-08-22T16:25:44.118+02:00| vthread-3| I120: Msg_Reset:
2016-08-22T16:25:44.118+02:00|  vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file  "/usr/lib/vmware/settings": No such file or directory.
2016-08-22T16:25:44.118+02:00| vthread-3| I120: ----------------------------------------
2016-08-22T16:25:44.118+02:00|  vthread-3| I120: PREF Optional preferences file not found at  /usr/lib/vmware/settings. Using default values.
2016-08-22T16:25:44.119+02:00| vthread-3| I120: Msg_Reset:
2016-08-22T16:25:44.119+02:00|  vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file  "/root/.vmware/config": No such file or directory.
2016-08-22T16:25:44.119+02:00| vthread-3| I120: ----------------------------------------
2016-08-22T16:25:44.119+02:00|  vthread-3| I120: PREF Optional preferences file not found at  /root/.vmware/config. Using default values.
2016-08-22T16:25:44.119+02:00| vthread-3| I120: PREF Unable to check permissions for preferences file.
2016-08-22T16:25:44.119+02:00| vthread-3| I120: Msg_Reset:
2016-08-22T16:25:44.119+02:00|  vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file  "/root/.vmware/preferences": No such file or directory.
2016-08-22T16:25:44.119+02:00| vthread-3| I120: ----------------------------------------
2016-08-22T16:25:44.119+02:00| vthread-3| I120: PREF Failed to load user preferences.
2016-08-22T16:25:44.119+02:00| vthread-3| W110: Logging to /tmp/vmware-root/vmware-modconfig-16439.log
2016-08-22T16:25:44.125+02:00| vthread-3| I120: Obtaining info using the running kernel.
2016-08-22T16:25:44.125+02:00| vthread-3| I120: Created new pathsHash.
2016-08-22T16:25:44.125+02:00|  vthread-3| I120: Setting header path for 4.4.0-34-generic to  "/lib/modules/4.4.0-34-generic/build/include".
2016-08-22T16:25:44.125+02:00|  vthread-3| I120: Validating path  "/lib/modules/4.4.0-34-generic/build/include" for kernel release  "4.4.0-34-generic".
2016-08-22T16:25:44.125+02:00| vthread-3| I120: Failed to find /lib/modules/4.4.0-34-generic/build/include/linux/version.h
2016-08-22T16:25:44.125+02:00|  vthread-3| I120:  /lib/modules/4.4.0-34-generic/build/include/linux/version.h not found,  looking for generated/uapi/linux/version.h instead.
2016-08-22T16:25:44.125+02:00| vthread-3| I120: using /usr/bin/gcc for preprocess check
2016-08-22T16:25:44.129+02:00| vthread-3| I120: Preprocessed UTS_RELEASE, got value "4.4.0-34-generic".
2016-08-22T16:25:44.129+02:00|  vthread-3| I120: The header path  "/lib/modules/4.4.0-34-generic/build/include" for the kernel  "4.4.0-34-generic" is valid.  Whoohoo!
2016-08-22T16:25:44.244+02:00| vthread-3| I120: Reading in info for the vmmon module.
2016-08-22T16:25:44.244+02:00| vthread-3| I120: Reading in info for the vmnet module.
2016-08-22T16:25:44.244+02:00| vthread-3| I120: Reading in info for the vmblock module.
2016-08-22T16:25:44.244+02:00| vthread-3| I120: Reading in info for the vmci module.
2016-08-22T16:25:44.244+02:00| vthread-3| I120: Reading in info for the vsock module.
2016-08-22T16:25:44.244+02:00| vthread-3| I120: Setting vsock to depend on vmci.
2016-08-22T16:25:44.244+02:00| vthread-3| I120: Invoking modinfo on "vmmon".
2016-08-22T16:25:44.245+02:00| vthread-3| I120: "/sbin/modinfo" exited with status 256.
2016-08-22T16:25:44.245+02:00| vthread-3| I120: Invoking modinfo on "vmnet".
2016-08-22T16:25:44.246+02:00| vthread-3| I120: "/sbin/modinfo" exited with status 256.
2016-08-22T16:25:44.246+02:00| vthread-3| I120: Invoking modinfo on "vmblock".
2016-08-22T16:25:44.247+02:00| vthread-3| I120: "/sbin/modinfo" exited with status 256.
2016-08-22T16:25:44.247+02:00| vthread-3| I120: Invoking modinfo on "vmci".
2016-08-22T16:25:44.248+02:00| vthread-3| I120: "/sbin/modinfo" exited with status 256.
2016-08-22T16:25:44.248+02:00| vthread-3| I120: Invoking modinfo on "vsock".
2016-08-22T16:25:44.249+02:00| vthread-3| I120: "/sbin/modinfo" exited with status 0.
2016-08-22T16:25:44.259+02:00| vthread-3| I120: to be installed: vmmon status: 0
2016-08-22T16:25:44.259+02:00| vthread-3| I120: to be installed: vmnet status: 0
2016-08-22T16:25:44.275+02:00| vthread-3| I120: Obtaining info using the running kernel.
2016-08-22T16:25:44.275+02:00|  vthread-3| I120: Setting header path for 4.4.0-34-generic to  "/lib/modules/4.4.0-34-generic/build/include".
2016-08-22T16:25:44.275+02:00|  vthread-3| I120: Validating path  "/lib/modules/4.4.0-34-generic/build/include" for kernel release  "4.4.0-34-generic".
2016-08-22T16:25:44.275+02:00| vthread-3| I120: Failed to find /lib/modules/4.4.0-34-generic/build/include/linux/version.h
2016-08-22T16:25:44.275+02:00|  vthread-3| I120:  /lib/modules/4.4.0-34-generic/build/include/linux/version.h not found,  looking for generated/uapi/linux/version.h instead.
2016-08-22T16:25:44.275+02:00| vthread-3| I120: using /usr/bin/gcc for preprocess check
2016-08-22T16:25:44.279+02:00| vthread-3| I120: Preprocessed UTS_RELEASE, got value "4.4.0-34-generic".
2016-08-22T16:25:44.279+02:00|  vthread-3| I120: The header path  "/lib/modules/4.4.0-34-generic/build/include" for the kernel  "4.4.0-34-generic" is valid.  Whoohoo!
2016-08-22T16:25:44.391+02:00|  vthread-3| I120: Kernel header path retrieved from FileEntry:  /lib/modules/4.4.0-34-generic/build/include
2016-08-22T16:25:44.391+02:00| vthread-3| I120: Update kernel header path to /lib/modules/4.4.0-34-generic/build/include
2016-08-22T16:25:44.391+02:00|  vthread-3| I120: Validating path  "/lib/modules/4.4.0-34-generic/build/include" for kernel release  "4.4.0-34-generic".
2016-08-22T16:25:44.391+02:00| vthread-3| I120: Failed to find /lib/modules/4.4.0-34-generic/build/include/linux/version.h
2016-08-22T16:25:44.391+02:00|  vthread-3| I120:  /lib/modules/4.4.0-34-generic/build/include/linux/version.h not found,  looking for generated/uapi/linux/version.h instead.
2016-08-22T16:25:44.391+02:00| vthread-3| I120: using /usr/bin/gcc for preprocess check
2016-08-22T16:25:44.397+02:00| vthread-3| I120: Preprocessed UTS_RELEASE, got value "4.4.0-34-generic".
2016-08-22T16:25:44.397+02:00|  vthread-3| I120: The header path  "/lib/modules/4.4.0-34-generic/build/include" for the kernel  "4.4.0-34-generic" is valid.  Whoohoo!
2016-08-22T16:25:44.397+02:00| vthread-3| I120: Found compiler at "/usr/bin/gcc"
2016-08-22T16:25:44.400+02:00| vthread-3| I120: Got gcc version "5.4.0".
2016-08-22T16:25:44.400+02:00| vthread-3| I120: GCC minor version 5 does not match Kernel GCC minor version 5.  But that is ok.
2016-08-22T16:25:44.400+02:00| vthread-3| I120: Using user supplied compiler "/usr/bin/gcc".
2016-08-22T16:25:44.402+02:00| vthread-3| I120: Got gcc version "5.4.0".
2016-08-22T16:25:44.402+02:00| vthread-3| I120: GCC minor version 5 does not match Kernel GCC minor version 5.  But that is ok.
2016-08-22T16:25:44.405+02:00| vthread-3| I120: Trying to find a suitable PBM set for kernel "4.4.0-34-generic".
2016-08-22T16:25:44.405+02:00| vthread-3| I120: No matching PBM set was found for kernel "4.4.0-34-generic".
2016-08-22T16:25:44.405+02:00| vthread-3| I120: GCC minor version 5 does not match Kernel GCC minor version 5.  But that is ok.
2016-08-22T16:25:44.405+02:00|  vthread-3| I120: Validating path  "/lib/modules/4.4.0-34-generic/build/include" for kernel release  "4.4.0-34-generic".
2016-08-22T16:25:44.405+02:00| vthread-3| I120: Failed to find /lib/modules/4.4.0-34-generic/build/include/linux/version.h
2016-08-22T16:25:44.405+02:00|  vthread-3| I120:  /lib/modules/4.4.0-34-generic/build/include/linux/version.h not found,  looking for generated/uapi/linux/version.h instead.
2016-08-22T16:25:44.405+02:00| vthread-3| I120: using /usr/bin/gcc for preprocess check
2016-08-22T16:25:44.411+02:00| vthread-3| I120: Preprocessed UTS_RELEASE, got value "4.4.0-34-generic".
2016-08-22T16:25:44.411+02:00|  vthread-3| I120: The header path  "/lib/modules/4.4.0-34-generic/build/include" for the kernel  "4.4.0-34-generic" is valid.  Whoohoo!
2016-08-22T16:25:44.412+02:00| vthread-3| I120: GCC minor version 5 does not match Kernel GCC minor version 5.  But that is ok.
2016-08-22T16:25:44.412+02:00|  vthread-3| I120: Validating path  "/lib/modules/4.4.0-34-generic/build/include" for kernel release  "4.4.0-34-generic".
2016-08-22T16:25:44.412+02:00| vthread-3| I120: Failed to find /lib/modules/4.4.0-34-generic/build/include/linux/version.h
2016-08-22T16:25:44.412+02:00|  vthread-3| I120:  /lib/modules/4.4.0-34-generic/build/include/linux/version.h not found,  looking for generated/uapi/linux/version.h instead.
2016-08-22T16:25:44.412+02:00| vthread-3| I120: using /usr/bin/gcc for preprocess check
2016-08-22T16:25:44.418+02:00| vthread-3| I120: Preprocessed UTS_RELEASE, got value "4.4.0-34-generic".
2016-08-22T16:25:44.418+02:00|  vthread-3| I120: The header path  "/lib/modules/4.4.0-34-generic/build/include" for the kernel  "4.4.0-34-generic" is valid.  Whoohoo!
2016-08-22T16:25:44.418+02:00| vthread-3| I120: Using temp dir "/tmp".
2016-08-22T16:25:44.419+02:00| vthread-3| I120: Obtaining info using the running kernel.
2016-08-22T16:25:44.419+02:00|  vthread-3| I120: Setting header path for 4.4.0-34-generic to  "/lib/modules/4.4.0-34-generic/build/include".
2016-08-22T16:25:44.419+02:00|  vthread-3| I120: Validating path  "/lib/modules/4.4.0-34-generic/build/include" for kernel release  "4.4.0-34-generic".
2016-08-22T16:25:44.420+02:00| vthread-3| I120: Failed to find /lib/modules/4.4.0-34-generic/build/include/linux/version.h
2016-08-22T16:25:44.420+02:00|  vthread-3| I120:  /lib/modules/4.4.0-34-generic/build/include/linux/version.h not found,  looking for generated/uapi/linux/version.h instead.
2016-08-22T16:25:44.420+02:00| vthread-3| I120: using /usr/bin/gcc for preprocess check
2016-08-22T16:25:44.426+02:00| vthread-3| I120: Preprocessed UTS_RELEASE, got value "4.4.0-34-generic".
2016-08-22T16:25:44.426+02:00|  vthread-3| I120: The header path  "/lib/modules/4.4.0-34-generic/build/include" for the kernel  "4.4.0-34-generic" is valid.  Whoohoo!
2016-08-22T16:25:44.564+02:00| vthread-3| I120: Invoking modinfo on "vmmon".
2016-08-22T16:25:44.565+02:00| vthread-3| I120: "/sbin/modinfo" exited with status 256.
2016-08-22T16:25:44.565+02:00| vthread-3| I120: Invoking modinfo on "vmnet".
2016-08-22T16:25:44.567+02:00| vthread-3| I120: "/sbin/modinfo" exited with status 256.
2016-08-22T16:25:44.701+02:00|  vthread-3| I120: Setting destination path for vmmon to  "/lib/modules/4.4.0-34-generic/misc/vmmon.ko".
2016-08-22T16:25:44.701+02:00| vthread-3| I120: Extracting the vmmon source from "/usr/lib/vmware/modules/source/vmmon.tar".
2016-08-22T16:25:44.706+02:00| vthread-3| I120: Successfully extracted the vmmon source.
2016-08-22T16:25:44.706+02:00|  vthread-3| I120: Building module with command "/usr/bin/make -j4 -C  /tmp/modconfig-Tafbm9/vmmon-only auto-build  HEADER_DIR=/lib/modules/4.4.0-34-generic/build/include CC=/usr/bin/gcc  IS_GCC_3=no"
2016-08-22T16:25:45.601+02:00| vthread-3| W110: Failed to build vmmon.  Failed to execute the build command.
2016-08-22T16:25:45.603+02:00|  vthread-3| I120: Setting destination path for vmnet to  "/lib/modules/4.4.0-34-generic/misc/vmnet.ko".
2016-08-22T16:25:45.603+02:00| vthread-3| I120: Extracting the vmnet source from "/usr/lib/vmware/modules/source/vmnet.tar".
2016-08-22T16:25:45.606+02:00| vthread-3| I120: Successfully extracted the vmnet source.
2016-08-22T16:25:45.606+02:00|  vthread-3| I120: Building module with command "/usr/bin/make -j4 -C  /tmp/modconfig-Tafbm9/vmnet-only auto-build  HEADER_DIR=/lib/modules/4.4.0-34-generic/build/include CC=/usr/bin/gcc  IS_GCC_3=no"
2016-08-22T16:25:56.845+02:00| vthread-3| W110: Failed to build vmnet.  Failed to execute the build command.
```

---

### Post by linux.girl on 2016-08-22
Admins, you can close this thread, I upgraded to workstation 12. Thanks!

---

### Post by jeremy31 on 2016-08-22
If that is the solution use the thread tools menu near the top of the page to mark as solved

---

### Post by linux.girl on 2016-08-22
Well, it is not really a "solution" as the problem was not solved, I simply overcam it by paying for a newer version fo vmware....but I will mark the thread as solved, thanks.

---

### Post by MAFoElffen on 2016-08-23
So for clarity, the problem with VMware Workstation 10 not loading Ubuntu 16.04 with VMware Tools version 10... as the toolset did not support Ubuntu 16.04. The solution was to use a version VMware tools that did support Ubuntu version 16.04, which was VMware tools version 12, which came with VMware Workstation 12.

So yes, in a way, It was solved by using the newer VMware Tools, toolset. Unfortunatley, that solution came at a cost, via upgrading to a current version of VMware Workstation (Pro). Your last comment is also true, in that there was no work-around to find a solution for production two versions older than current to support a current OS... that it did not have VM software virtualization helper files for in it's toolset. To me, that does make sense that someone would not focus their efforts on an outdated, past-tense version of their product, where it should be done for their current and future versions. 

Does that make sense to you now?

---

### Post by linux.girl on 2016-08-23
Hi, no that was not the problem. I have upgraded my HOST OS from Ubuntu 14 to Ubuntu 16 and then my vm workstation 10 stopped working because it wasn't compatible with the new kernel. The solution sometimes are patches users release, but I found none, so I upgraded my workstation to version 12 and not it is working fine. Vmware workstation is not a cheap product and workstation 10 is from 2014, so 2 years support for all current OS is not too much to ask, but well, it is what it is, all working now. Thanks!

---

### Post by TheFu on 2016-08-25
Perhaps the better long term answer is to replace VMware commercial software with one of the F/LOSS offerings?  KVM, Xen, and if you have desktops, VirtualBox is an option, provided the license for the "guest additions" isn't bad for your needs.

Of course, there are definitely reasons to stay with VMware Workstation for some edge situations. Only you can make that determination, but doing so will lead to future, similar, issues as this one.  To be fair, KVM, Xen, and virtualbox will have similar issues, but the upgrades to newer versions don't require payment.

---

### Post by linux.girl on 2016-09-06
You are absolutely right and that is what I will do next time (I already bought a new vmware license). I hope that virtual machines that are built as vmware machines can be easily converted to virtualbox for example.

Thanks!

---

### Post by TheFu on 2016-09-06
> **linux.girl said:**
> You are absolutely right and that is what I will do next time (I already bought a new vmware license). I hope that virtual machines that are built as vmware machines can be easily converted to virtualbox for example.

Thanks!

Sometimes, yes. Not always.

---

### Post by linux.girl on 2016-09-06
OK, thanks! When the time comes I will see what to do about it.

---

### Post by TheFu on 2016-09-06
> **linux.girl said:**
> OK, thanks! When the time comes I will see what to do about it.

With Linux-based VMs, you can just use the normal backup/restore methods with your daily, automatic, versioned, backup tool. It is a good test of that entire process.  Have to do it here about 2 times a year.  

Or just use rsync from the old system into a temporary boot (ISO) connected to the new system storage.  Since you are working with VMs, there isn't much to risk and trying it over and over and over until it does what you need is pretty easy (and safe).  Just be sure to minimize the storage needed, so time isn't wasted on extra stuff.

---

### Post by linux.girl on 2016-09-06
Thanks, you are right, that's why VMs are so great, you can mess around without messing it all :-)

---

