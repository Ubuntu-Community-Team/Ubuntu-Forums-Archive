---
title: "VMWARE error?"
date: 2008-02-24
forum: Server Platforms
---

### Post by supacool on 2008-02-24
Trying to install the patch, error is below. Anyone seen this beforee?

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] y

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.22-14-server/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Building for VMware Server 1.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.22-14-server/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-server'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/task.o
cc1plus: warning: command line option "-Wdeclaration-after-statement" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wno-pointer-sign" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-ffreestanding" is valid for C/ObjC but not for C++
include/asm/page.h: In function ‘pte_t native_make_pte(long long unsigned int)’:
include/asm/page.h:79: error: expected primary-expression before ‘)’ token
include/asm/page.h:79: error: expected ‘;’ before ‘{’ token
include/asm/page.h:79: error: expected primary-expression before ‘.’ token
include/asm/page.h:79: error: expected primary-expression before ‘.’ token
include/asm/page.h:79: error: expected `;' before ‘}’ token
make[2]: *** [/tmp/vmware-config1/vmmon-only/common/task.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-server'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

Thanks in advance

---

### Post by ITCons on 2008-04-27
Hello all..

I have the same error, trying to patch vmware server 1.0.4 on Ubuntu gutsy 7.10 64 bit.

when installing 1.0.4 / 1.0.5 without the any-any patch:

WARNING: could not find /tmp/vmware-config5/vmnet-only/.smac_linux.x86_64.o.cmd for /tmp/vmware-config5/vmnet-only/smac_linux.x86_64.o

Fails and exits installer.

With the any-any patch. This time, module is compiled despite of the following error.

cc1plus: warning: command line option “-Wdeclaration-after-statement” is valid for C/Obj C but not for C++ cc1plus: warning: command line option “-Wno-pointer-sign” is valid for C/ObjC but not fo r C++ cc1plus: warning: command line option “-Wstrict-prototypes” is valid for Ada/C/ObjC but not for C++ /tmp/vmware-config3/vmmon-only/common/task_compat.h: In function ‘void Task_Switch_V45(V MDriver*, Vcpuid)’: /tmp/vmware-config3/vmmon-only/common/task_compat.h:2666: warning: ‘sysenterState.Sysent erStateV45::validEIP’ may be used uninitialized in this function /tmp/vmware-config3/vmmon-only/common/task_compat.h:2666: warning: ‘sysenterState.Sysent erStateV45::cs’ may be used uninitialized in this function /tmp/vmware-config3/vmmon-only/common/task_compat.h:2666: warning: ‘sysenterState.Sysent erStateV45::rsp’ may be used uninitialized in this function /tmp/vmware-config3/vmmon-only/common/task_compat.h:2666: warning: ‘sysenterState.Sysent erStateV45::rip’ may be used uninitialized in this function

After building, only nat and host only network is available. 

Any idea, how to fix this? Is this a problem from the 64bit version of the C++ compiler?

---

