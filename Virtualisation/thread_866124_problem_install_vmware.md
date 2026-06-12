---
title: "problem install vmware"
date: 2008-07-21
forum: Virtualisation
---

### Post by james_bandido on 2008-07-21
```

Building the vmmon module.

Building for VMware Server 1.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.24-19-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/cpuid.o
In file included from include/asm/bitops.h:2,
                 from /tmp/vmware-config1/vmmon-only/./include/vcpuset.h:74,
                 from /tmp/vmware-config1/vmmon-only/./include/modulecall.h:23,
                 from /tmp/vmware-config1/vmmon-only/common/vmx86.h:19,
                 from /tmp/vmware-config1/vmmon-only/common/hostif.h:18,
                 from /tmp/vmware-config1/vmmon-only/common/cpuid.c:15:
include/asm/bitops_32.h:9:2: error: #error only <linux/bitops.h> can be included directly
make[2]: *** [/tmp/vmware-config1/vmmon-only/common/cpuid.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

can somebody guide me on how to get over this error ?

thank you very much.

---

### Post by Partyboi2 on 2008-07-23
Maybe post #3 of [[COLOR=Blue]this[/COLOR]]("http://www.howtoforge.com/forums/showthread.php?t=23666") thread will work

---

### Post by james_bandido on 2008-07-23
@Partyboi2, thank you very much ...

just one last q ... 

how do i add the vmware server console gui ?

---

### Post by james_bandido on 2008-07-26
okay i got them vmware server 1.0.5 installed properly ... 
i now got the vmware server mui however when i install it, it tells me that vmware server is not installed ... 

```

Do you accept? (yes/no) yes

Thank you.

Installing the content of the package.

VMware Server must be installed on this machine for the VMware Management 
Interface to work

Execution aborted.

root@bandido-laptop-linux:/home/james/vmware-mui-distrib# 

```

can somebody guide me ? thanks in advance ...

---

### Post by overdrank on 2008-07-26
Moved to  Virtualization
:)

---

### Post by james_bandido on 2008-07-26
me bad ... 
i did a little research and found that some libs are missing ... [IMG]http://justlinux.com/forum/images/smilies/biggrin.gif[/IMG]
now thats a software bug for me since it installed properly ...

```
root@bandido-laptop-linux:/# vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
root@bandido-laptop-linux:/#

```

anyway, can somebody please tell me how do i get these libs ?

thanks in advance ...

and have a nice weekend !!!

cheers !!!

---

### Post by Partyboi2 on 2008-07-26
If you are running 64bit you could try what is mentioned on the [[COLOR=Blue]VMware page[/COLOR]]("https://help.ubuntu.com/community/VMware/Server#Installing%20from%20Source")

Someone else also suggests moving the offending library out of the way
[http://radio.javaranch.com/davo/2008/06/18/1213791596327.html](http://radio.javaranch.com/davo/2008/06/18/1213791596327.html)

---

