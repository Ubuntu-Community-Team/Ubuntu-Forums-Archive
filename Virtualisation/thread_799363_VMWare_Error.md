---
title: "VMWare Error"
date: 2008-05-18
forum: Virtualisation
---

### Post by Skeet on 2008-05-18
I have just installed VMWare Workstation 6.0.3-80004. I got the rpm file and used alien to convert it to .deb for installation.

I installed it fine, no hitches. But when I try to run it, it comes up with the following error in Terminal

```
/usr/bin/vmware: 166: cannot open /etc/vmware/locations: No such file
exec: 180: /lib/wrapper-gtk24.sh: not found
```

I get this when I type 'sudo vmware'

Why am I getting this error and what does it mean? I'm relatively new to Ubuntu.

OS is Ubuntu 8.04 Hardy Heron.

---

### Post by Skeet on 2008-05-19
I have tried uninstalling it and reinstalling using the tar.gz version of it, and running the vmware-install.pl file, it all installed fine (again) but now during configuration, it comes up with this.

```
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-16-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmmon-only'
make -C /lib/modules/2.6.24-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/cpuid.o
In file included from include/asm/bitops.h:2,
                 from /tmp/vmware-config2/vmmon-only/./include/vcpuset.h:74,
                 from /tmp/vmware-config2/vmmon-only/./include/modulecall.h:23,
                 from /tmp/vmware-config2/vmmon-only/common/vmx86.h:18,
                 from /tmp/vmware-config2/vmmon-only/common/hostif.h:18,
                 from /tmp/vmware-config2/vmmon-only/common/cpuid.c:14:
include/asm/bitops_32.h:9:2: error: #error only <linux/bitops.h> can be included directly
make[2]: *** [/tmp/vmware-config2/vmmon-only/common/cpuid.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

Is there a way of building the vmmon module in another fashion? Or can I fix this error, i've had more luck with this installation method, its just the configuration thats the problem now. Is there a incompatibility between VMWare Workstation 6 and Ubuntu 8.04?

---

### Post by Skeet on 2008-05-19
Apon further reading at VMWares website, it turns out that it is a compatibility issue with the Ubuntu 8.04 kernel and vmware workstation. I have tried running the vmware any any update to no prevail.

Does anyone know another way of getting around the compatibility issue?

:confused:

PS: apologies for duplicate posts but I just wanted to post my progress. Any help will be beneficial as i'm completely stuck now.

---

### Post by Skeet on 2008-05-19
Apon **further** research, I came across an updated vmware any any update (116) available [here]("http://vmkernelnewbies.googlegroups.com/web/vmware-any-any-update-116.tgz"), and it configured perfectly. I was too quick to jump the gun and post.

This is good for future reference if others stumble across the same problem as me.

:lolflag:

---

### Post by echo6 on 2008-05-25
> **Skeet said:**
> compatibility issue with the Ubuntu 8.04 kernel and vmware workstation.

It effects not just Ubuntu but any kernel from 2.6.24 onwards.

The fix is posted somewhere on the Wiki,  but I can't find it atm.

Basically you have to manually extract the file vmware-distrib/lib/modules/source/vmmon.tar
Then edit the file vmware-distrib/lib/modules/source/vmmon-only/include/vcpuset.h
At line 74 change the asm/bitops.h to linux/bitops.h.  Remove the old vmmon.tar and create a new one from the extracted directory containing the edited file.

After that you should find it compiles correctly.

---

