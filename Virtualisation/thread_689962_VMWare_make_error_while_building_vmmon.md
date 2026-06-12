---
title: "VMWare make error while building vmmon"
date: 2008-02-06
forum: Virtualisation
---

### Post by ChasingVertigo on 2008-02-06
On 7.10 I'm trying to get VMWare Workstation working from the tar.gz, it seems to install alright, but while running 

```
sudo vmware-config.pl
```

this error occurs

> andrew@andrew:~/Desktop/untitled folder$ sudo vmware-config.pl

...

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux-headers-2.6.22-14-generic/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Building for VMware Workstation 5.5.2 or 5.5.3.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config5/vmmon-only'
make -C /usr/src/linux-headers-2.6.22-14-generic/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /tmp/vmware-config5/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config5/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config5/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config5/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config5/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config5/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config5/vmmon-only/common/task.o
cc1plus: warning: command line option "-Wdeclaration-after-statement" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wno-pointer-sign" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-ffreestanding" is valid for C/ObjC but not for C++
include/asm/page.h: In function &#8216;pte_t native_make_pte(long unsigned int)&#8217;:
include/asm/page.h:112: error: expected primary-expression before &#8216;)&#8217; token
include/asm/page.h:112: error: expected &#8216;;&#8217; before &#8216;{&#8217; token
include/asm/page.h:112: error: expected primary-expression before &#8216;.&#8217; token
include/asm/page.h:112: error: expected `;' before &#8216;}&#8217; token
make[2]: *** [/tmp/vmware-config5/vmmon-only/common/task.o] Error 1
make[1]: *** [_module_/tmp/vmware-config5/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config5/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


I have build-essential installed, and I've checked its the latest. I'd appreciate some suggestions on how I could fix this.

---

### Post by fjgaude on 2008-02-07
You might see if you have the gcc compiler installed. Build-essential may not be all that is required.

---

### Post by shekhark on 2009-03-08
I'm encountering the same problem with the gcc compiler installed. Would appreciate some help.

---

### Post by veloce on 2009-03-08
> **ChasingVertigo said:**
> On 7.10 I'm trying to get VMWare Workstation working from the tar.gz, it seems to install alright, but while running 

```
sudo vmware-config.pl
```

this error occurs



I have build-essential installed, and I've checked its the latest. I'd appreciate some suggestions on how I could fix this.

I think you need to find the appropriate patch to vmware-config.pl for your specific version of Ubuntu and Workstation. This happens often.  Search the forum for links to the right patch.

---

