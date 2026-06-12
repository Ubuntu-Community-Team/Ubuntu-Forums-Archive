---
title: "upgrade from 13.04 to 13.10 broke nvidia driver"
date: 2013-10-29
forum: Ubuntu Studio
---

### Post by psy-man on 2013-10-29
Hi all, not a complaint just a heads up.
I just upgraded ubuntu studio from 13.04 to 13.10.
The upgrade didn't run smoothly. I had to  'sudo dpkg --configure -a' to get it to finnish.
After reboot the nvidia kernel module didn't load. I run a dual head system ...( I use the nvidia driver to stretch my desktop across two monitors) 
I guess I shall have to wait for nvidia to catch up.
Here's the gory details

Release Ubuntu 13.10 (saucy)
Gnome 3.8.4 (Ubuntu 2013-09-04)
Kernel 3.11.0-11-lowlatency (#4-Ubuntu SMP PREEMPT Wed Oct 2 22:48:21 UTC 2013)
GCC version 4.8 (x86_64-linux-gnu)
Xorg Version 1.14.3 (15 October 2013  09:23:37AM)

NVIDIA driver NVIDIA-Linux-x86_64-331.17

logs to follow

nvidia-installer.log
```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Tue Oct 29 09:23:56 2013
installer version: 331.17

PATH: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

nvidia-installer command line:
    ./nvidia-installer

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 331.17.
-> There appears to already be a driver installed on your system (version: 331.17).  As part of installing this driver (version: 331.17), the existing driver will be uninstalled.  Are you sure you want to continue? ('no' will abort installation) (Answer: Yes)
-> Running distribution scripts
   executing: '/usr/lib/nvidia/pre-install'...
-> done.
-> The distribution-provided pre-install script failed!  Continue installation anyway? (Answer: Yes)
-> Would you like to register the kernel module sources with DKMS? This will allow DKMS to automatically build a new module, if you install a different kernel later. (Answer: Yes)
-> Installing both new and classic TLS OpenGL libraries.
-> Installing both new and classic TLS 32bit OpenGL libraries.
-> Install NVIDIA's 32-bit compatibility libraries? (Answer: No)
-> Parsing log file:
-> done.
-> Validating previous installation:
-> done.
-> Uninstalling NVIDIA Accelerated Graphics Driver for Linux-x86_64 (1.0-33117 (331.17)):
-> DKMS module detected; removing...
-> done.
-> Uninstallation of existing driver: NVIDIA Accelerated Graphics Driver for Linux-x86_64 (331.17) is complete.
-> Skipping installation of the libvdpau wrapper library.
-> Searching for conflicting X files:
-> done.
-> Searching for conflicting OpenGL files:
-> done.
-> Installing 'NVIDIA Accelerated Graphics Driver for Linux-x86_64' (331.17):
   executing: '/sbin/ldconfig'...
   executing: '/sbin/depmod -aq'...
   ignored deprecated option -q
-> done.
-> Driver file installation is complete.
-> Installing DKMS kernel module:
ERROR: Failed to run `/usr/sbin/dkms build -m nvidia -v 331.17 -k 3.11.0-11-lowlatency`: 
Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.11.0-11-lowlatency module KERNEL_UNAME=3.11.0-11-lowlatency; make -C uvm module KERNEL_UNAME=3.11.0-11-lowlatency KBUILD_EXTMOD=/var/lib/dkms/nvidia/331.17/build/uvm.......................(bad exit status: 2)
ERROR (dkms apport): binary package for nvidia: 331.17 not found
Error! Bad return status for module build on kernel: 3.11.0-11-lowlatency (x86_64)
Consult /var/lib/dkms/nvidia/331.17/build/make.log for more information.
-> error.
ERROR: Failed to install the kernel module through DKMS. No kernel module was installed; please try installing again without DKMS, or check the DKMS logs for more information.
ERROR: Installation has failed.  Please see the file '/var/log/nvidia-installer.log' for details.  You may find suggestions on fixing installation problems in the README available on the Linux driver download page at www.nvidia.com.
```
make.log (DKMS)
```
DKMS make.log for nvidia-331.17 for kernel 3.11.0-11-lowlatency (x86_64)
Tue Oct 29 09:25:15 GMT 2013
NVIDIA: calling KBUILD...
make[1]: Entering directory `/usr/src/linux-headers-3.11.0-11-lowlatency'
test -e include/generated/autoconf.h -a -e include/config/auto.conf || (        \
    echo >&2;                            \
    echo >&2 "  ERROR: Kernel configuration is invalid.";        \
    echo >&2 "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
    echo >&2 "         Run 'make oldconfig && make prepare' on kernel src to fix it.";    \
    echo >&2 ;                            \
    /bin/false)
mkdir -p /var/lib/dkms/nvidia/331.17/build/.tmp_versions ; rm -f /var/lib/dkms/nvidia/331.17/build/.tmp_versions/*
make -f scripts/Makefile.build obj=/var/lib/dkms/nvidia/331.17/build
  cc -Wp,-MD,/var/lib/dkms/nvidia/331.17/build/.nv.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-11-lowlatency/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DNV_MODULE_INSTANCE=0 -DNV_BUILD_MODULE_INSTANCES=0 -UDEBUG -U_DEBUG -DNDEBUG -I/var/lib/dkms/nvidia/331.17/build -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"331.17\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -DNV_UVM_ENABLE -D__linux__ -DNV_DEV_NAME=\"nvidia\"  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /var/lib/dkms/nvidia/331.17/build/.tmp_nv.o /var/lib/dkms/nvidia/331.17/build/nv.c
In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/bitops.h:514:0,
                 from include/linux/bitops.h:22,
                 from include/linux/kernel.h:10,
                 from include/linux/sched.h:15,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv.c:13:
include/linux/bitops.h: In function ‘hweight_long’:
include/asm-generic/bitops/const_hweight.h:27:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
 #define hweight64(w) (__builtin_constant_p(w) ? __const_hweight64(w) : __arch_hweight64(w))
                                                                      ^
include/linux/bitops.h:66:41: note: in expansion of macro ‘hweight64’
  return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                                         ^
In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/cpumask.h:4:0,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:5,
                 from include/uapi/linux/timex.h:56,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:17,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv.c:13:
include/linux/cpumask.h: In function ‘cpumask_parse’:
include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
  int len = nl ? nl - buf : strlen(buf);
                          ^
In file included from include/uapi/linux/stddef.h:1:0,
                 from include/linux/stddef.h:4,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi/linux/posix_types.h:4,
                 from include/uapi/linux/types.h:13,
                 from include/linux/types.h:5,
                 from include/uapi/linux/capability.h:16,
                 from include/linux/capability.h:15,
                 from include/linux/sched.h:13,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv.c:13:
/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h: In function ‘copy_from_user’:
/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h:62:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
  if (likely(sz == -1 || sz >= n))
                            ^
include/linux/compiler.h:152:40: note: in definition of macro ‘likely’
 # define likely(x) __builtin_expect(!!(x), 1)
                                        ^
  if [ "-pg" = "-pg" ]; then if [ /var/lib/dkms/nvidia/331.17/build/nv.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-11-lowlatency/scripts/recordmcount  "/var/lib/dkms/nvidia/331.17/build/nv.o"; fi; fi;
  cc -Wp,-MD,/var/lib/dkms/nvidia/331.17/build/.nv-acpi.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-11-lowlatency/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DNV_MODULE_INSTANCE=0 -DNV_BUILD_MODULE_INSTANCES=0 -UDEBUG -U_DEBUG -DNDEBUG -I/var/lib/dkms/nvidia/331.17/build -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"331.17\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -DNV_UVM_ENABLE -D__linux__ -DNV_DEV_NAME=\"nvidia\"  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_acpi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /var/lib/dkms/nvidia/331.17/build/.tmp_nv-acpi.o /var/lib/dkms/nvidia/331.17/build/nv-acpi.c
In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/bitops.h:514:0,
                 from include/linux/bitops.h:22,
                 from include/linux/kernel.h:10,
                 from include/linux/sched.h:15,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-acpi.c:15:
include/linux/bitops.h: In function ‘hweight_long’:
include/asm-generic/bitops/const_hweight.h:27:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
 #define hweight64(w) (__builtin_constant_p(w) ? __const_hweight64(w) : __arch_hweight64(w))
                                                                      ^
include/linux/bitops.h:66:41: note: in expansion of macro ‘hweight64’
  return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                                         ^
In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/cpumask.h:4:0,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:5,
                 from include/uapi/linux/timex.h:56,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:17,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-acpi.c:15:
include/linux/cpumask.h: In function ‘cpumask_parse’:
include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
  int len = nl ? nl - buf : strlen(buf);
                          ^
In file included from include/uapi/linux/stddef.h:1:0,
                 from include/linux/stddef.h:4,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi/linux/posix_types.h:4,
                 from include/uapi/linux/types.h:13,
                 from include/linux/types.h:5,
                 from include/uapi/linux/capability.h:16,
                 from include/linux/capability.h:15,
                 from include/linux/sched.h:13,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-acpi.c:15:
/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h: In function ‘copy_from_user’:
/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h:62:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
  if (likely(sz == -1 || sz >= n))
                            ^
include/linux/compiler.h:152:40: note: in definition of macro ‘likely’
 # define likely(x) __builtin_expect(!!(x), 1)
                                        ^
/var/lib/dkms/nvidia/331.17/build/nv-acpi.c: At top level:
/var/lib/dkms/nvidia/331.17/build/nv-acpi.c:70:9: warning: initialization from incompatible pointer type [enabled by default]
         .remove = nv_acpi_remove,
         ^
/var/lib/dkms/nvidia/331.17/build/nv-acpi.c:70:9: warning: (near initialization for ‘nv_acpi_driver_template.ops.remove’) [enabled by default]
  if [ "-pg" = "-pg" ]; then if [ /var/lib/dkms/nvidia/331.17/build/nv-acpi.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-11-lowlatency/scripts/recordmcount  "/var/lib/dkms/nvidia/331.17/build/nv-acpi.o"; fi; fi;
  cc -Wp,-MD,/var/lib/dkms/nvidia/331.17/build/.nv-chrdev.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-11-lowlatency/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DNV_MODULE_INSTANCE=0 -DNV_BUILD_MODULE_INSTANCES=0 -UDEBUG -U_DEBUG -DNDEBUG -I/var/lib/dkms/nvidia/331.17/build -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"331.17\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -DNV_UVM_ENABLE -D__linux__ -DNV_DEV_NAME=\"nvidia\"  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_chrdev)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /var/lib/dkms/nvidia/331.17/build/.tmp_nv-chrdev.o /var/lib/dkms/nvidia/331.17/build/nv-chrdev.c
In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/bitops.h:514:0,
                 from include/linux/bitops.h:22,
                 from include/linux/kernel.h:10,
                 from include/linux/sched.h:15,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-chrdev.c:15:
include/linux/bitops.h: In function ‘hweight_long’:
include/asm-generic/bitops/const_hweight.h:27:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
 #define hweight64(w) (__builtin_constant_p(w) ? __const_hweight64(w) : __arch_hweight64(w))
                                                                      ^
include/linux/bitops.h:66:41: note: in expansion of macro ‘hweight64’
  return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                                         ^
In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/cpumask.h:4:0,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:5,
                 from include/uapi/linux/timex.h:56,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:17,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-chrdev.c:15:
include/linux/cpumask.h: In function ‘cpumask_parse’:
include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
  int len = nl ? nl - buf : strlen(buf);
                          ^
In file included from include/uapi/linux/stddef.h:1:0,
                 from include/linux/stddef.h:4,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi/linux/posix_types.h:4,
                 from include/uapi/linux/types.h:13,
                 from include/linux/types.h:5,
                 from include/uapi/linux/capability.h:16,
                 from include/linux/capability.h:15,
                 from include/linux/sched.h:13,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-chrdev.c:15:
/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h: In function ‘copy_from_user’:
/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h:62:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
  if (likely(sz == -1 || sz >= n))
                            ^
include/linux/compiler.h:152:40: note: in definition of macro ‘likely’
 # define likely(x) __builtin_expect(!!(x), 1)
                                        ^
  if [ "-pg" = "-pg" ]; then if [ /var/lib/dkms/nvidia/331.17/build/nv-chrdev.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-11-lowlatency/scripts/recordmcount  "/var/lib/dkms/nvidia/331.17/build/nv-chrdev.o"; fi; fi;
  cc -Wp,-MD,/var/lib/dkms/nvidia/331.17/build/.nv-cray.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-11-lowlatency/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DNV_MODULE_INSTANCE=0 -DNV_BUILD_MODULE_INSTANCES=0 -UDEBUG -U_DEBUG -DNDEBUG -I/var/lib/dkms/nvidia/331.17/build -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"331.17\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -DNV_UVM_ENABLE -D__linux__ -DNV_DEV_NAME=\"nvidia\"  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_cray)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /var/lib/dkms/nvidia/331.17/build/.tmp_nv-cray.o /var/lib/dkms/nvidia/331.17/build/nv-cray.c
In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/bitops.h:514:0,
                 from include/linux/bitops.h:22,
                 from include/linux/kernel.h:10,
                 from include/linux/sched.h:15,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-cray.c:15:
include/linux/bitops.h: In function ‘hweight_long’:
include/asm-generic/bitops/const_hweight.h:27:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
 #define hweight64(w) (__builtin_constant_p(w) ? __const_hweight64(w) : __arch_hweight64(w))
                                                                      ^
include/linux/bitops.h:66:41: note: in expansion of macro ‘hweight64’
  return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                                         ^
In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/cpumask.h:4:0,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:5,
                 from include/uapi/linux/timex.h:56,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:17,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-cray.c:15:
include/linux/cpumask.h: In function ‘cpumask_parse’:
include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
  int len = nl ? nl - buf : strlen(buf);
                          ^
In file included from include/uapi/linux/stddef.h:1:0,
                 from include/linux/stddef.h:4,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi/linux/posix_types.h:4,
                 from include/uapi/linux/types.h:13,
                 from include/linux/types.h:5,
                 from include/uapi/linux/capability.h:16,
                 from include/linux/capability.h:15,
                 from include/linux/sched.h:13,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-cray.c:15:
/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h: In function ‘copy_from_user’:
/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h:62:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
  if (likely(sz == -1 || sz >= n))
                            ^
include/linux/compiler.h:152:40: note: in definition of macro ‘likely’
 # define likely(x) __builtin_expect(!!(x), 1)
                                        ^
  if [ "-pg" = "-pg" ]; then if [ /var/lib/dkms/nvidia/331.17/build/nv-cray.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-11-lowlatency/scripts/recordmcount  "/var/lib/dkms/nvidia/331.17/build/nv-cray.o"; fi; fi;
  cc -Wp,-MD,/var/lib/dkms/nvidia/331.17/build/.nv-drm.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-11-lowlatency/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DNV_MODULE_INSTANCE=0 -DNV_BUILD_MODULE_INSTANCES=0 -UDEBUG -U_DEBUG -DNDEBUG -I/var/lib/dkms/nvidia/331.17/build -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"331.17\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -DNV_UVM_ENABLE -D__linux__ -DNV_DEV_NAME=\"nvidia\"  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_drm)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /var/lib/dkms/nvidia/331.17/build/.tmp_nv-drm.o /var/lib/dkms/nvidia/331.17/build/nv-drm.c
In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/bitops.h:514:0,
                 from include/linux/bitops.h:22,
                 from include/linux/kernel.h:10,
                 from include/linux/sched.h:15,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-drm.c:15:
include/linux/bitops.h: In function ‘hweight_long’:
include/asm-generic/bitops/const_hweight.h:27:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
 #define hweight64(w) (__builtin_constant_p(w) ? __const_hweight64(w) : __arch_hweight64(w))
                                                                      ^
include/linux/bitops.h:66:41: note: in expansion of macro ‘hweight64’
  return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                                         ^
In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/cpumask.h:4:0,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:5,
                 from include/uapi/linux/timex.h:56,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:17,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-drm.c:15:
include/linux/cpumask.h: In function ‘cpumask_parse’:
include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
  int len = nl ? nl - buf : strlen(buf);
                          ^
In file included from include/uapi/linux/stddef.h:1:0,
                 from include/linux/stddef.h:4,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi/linux/posix_types.h:4,
                 from include/uapi/linux/types.h:13,
                 from include/linux/types.h:5,
                 from include/uapi/linux/capability.h:16,
                 from include/linux/capability.h:15,
                 from include/linux/sched.h:13,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-drm.c:15:
/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h: In function ‘copy_from_user’:
/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h:62:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
  if (likely(sz == -1 || sz >= n))
                            ^
include/linux/compiler.h:152:40: note: in definition of macro ‘likely’
 # define likely(x) __builtin_expect(!!(x), 1)
                                        ^
In file included from include/drm/drm_crtc.h:32:0,
                 from include/drm/drmP.h:688,
                 from /var/lib/dkms/nvidia/331.17/build/nv-drm.c:19:
include/linux/fb.h: In function ‘__fb_pad_aligned_buffer’:
include/linux/fb.h:650:17: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   for (j = 0; j < s_pitch; j++)
                 ^
  if [ "-pg" = "-pg" ]; then if [ /var/lib/dkms/nvidia/331.17/build/nv-drm.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-11-lowlatency/scripts/recordmcount  "/var/lib/dkms/nvidia/331.17/build/nv-drm.o"; fi; fi;
  cc -Wp,-MD,/var/lib/dkms/nvidia/331.17/build/.nv-gvi.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-11-lowlatency/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DNV_MODULE_INSTANCE=0 -DNV_BUILD_MODULE_INSTANCES=0 -UDEBUG -U_DEBUG -DNDEBUG -I/var/lib/dkms/nvidia/331.17/build -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"331.17\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -DNV_UVM_ENABLE -D__linux__ -DNV_DEV_NAME=\"nvidia\"  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_gvi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /var/lib/dkms/nvidia/331.17/build/.tmp_nv-gvi.o /var/lib/dkms/nvidia/331.17/build/nv-gvi.c
In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/bitops.h:514:0,
                 from include/linux/bitops.h:22,
                 from include/linux/kernel.h:10,
                 from include/linux/sched.h:15,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-gvi.c:15:
include/linux/bitops.h: In function ‘hweight_long’:
include/asm-generic/bitops/const_hweight.h:27:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
 #define hweight64(w) (__builtin_constant_p(w) ? __const_hweight64(w) : __arch_hweight64(w))
                                                                      ^
include/linux/bitops.h:66:41: note: in expansion of macro ‘hweight64’
  return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                                         ^
In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/cpumask.h:4:0,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:5,
                 from include/uapi/linux/timex.h:56,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:17,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-gvi.c:15:
include/linux/cpumask.h: In function ‘cpumask_parse’:
include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
  int len = nl ? nl - buf : strlen(buf);
                          ^
In file included from include/uapi/linux/stddef.h:1:0,
                 from include/linux/stddef.h:4,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi/linux/posix_types.h:4,
                 from include/uapi/linux/types.h:13,
                 from include/linux/types.h:5,
                 from include/uapi/linux/capability.h:16,
                 from include/linux/capability.h:15,
                 from include/linux/sched.h:13,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-gvi.c:15:
/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h: In function ‘copy_from_user’:
/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h:62:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
  if (likely(sz == -1 || sz >= n))
                            ^
include/linux/compiler.h:152:40: note: in definition of macro ‘likely’
 # define likely(x) __builtin_expect(!!(x), 1)
                                        ^
  if [ "-pg" = "-pg" ]; then if [ /var/lib/dkms/nvidia/331.17/build/nv-gvi.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-11-lowlatency/scripts/recordmcount  "/var/lib/dkms/nvidia/331.17/build/nv-gvi.o"; fi; fi;
  cc -Wp,-MD,/var/lib/dkms/nvidia/331.17/build/.nv-i2c.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-11-lowlatency/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DNV_MODULE_INSTANCE=0 -DNV_BUILD_MODULE_INSTANCES=0 -UDEBUG -U_DEBUG -DNDEBUG -I/var/lib/dkms/nvidia/331.17/build -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"331.17\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -DNV_UVM_ENABLE -D__linux__ -DNV_DEV_NAME=\"nvidia\"  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_i2c)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /var/lib/dkms/nvidia/331.17/build/.tmp_nv-i2c.o /var/lib/dkms/nvidia/331.17/build/nv-i2c.c
In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/bitops.h:514:0,
                 from include/linux/bitops.h:22,
                 from include/linux/kernel.h:10,
                 from include/linux/sched.h:15,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-i2c.c:15:
include/linux/bitops.h: In function ‘hweight_long’:
include/asm-generic/bitops/const_hweight.h:27:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
 #define hweight64(w) (__builtin_constant_p(w) ? __const_hweight64(w) : __arch_hweight64(w))
                                                                      ^
include/linux/bitops.h:66:41: note: in expansion of macro ‘hweight64’
  return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                                         ^
In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/cpumask.h:4:0,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:5,
                 from include/uapi/linux/timex.h:56,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:17,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-i2c.c:15:
include/linux/cpumask.h: In function ‘cpumask_parse’:
include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
  int len = nl ? nl - buf : strlen(buf);
                          ^
In file included from include/uapi/linux/stddef.h:1:0,
                 from include/linux/stddef.h:4,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi/linux/posix_types.h:4,
                 from include/uapi/linux/types.h:13,
                 from include/linux/types.h:5,
                 from include/uapi/linux/capability.h:16,
                 from include/linux/capability.h:15,
                 from include/linux/sched.h:13,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-i2c.c:15:
/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h: In function ‘copy_from_user’:
/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h:62:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
  if (likely(sz == -1 || sz >= n))
                            ^
include/linux/compiler.h:152:40: note: in definition of macro ‘likely’
 # define likely(x) __builtin_expect(!!(x), 1)
                                        ^
  if [ "-pg" = "-pg" ]; then if [ /var/lib/dkms/nvidia/331.17/build/nv-i2c.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-11-lowlatency/scripts/recordmcount  "/var/lib/dkms/nvidia/331.17/build/nv-i2c.o"; fi; fi;
  cc -Wp,-MD,/var/lib/dkms/nvidia/331.17/build/.nv-mempool.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-11-lowlatency/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DNV_MODULE_INSTANCE=0 -DNV_BUILD_MODULE_INSTANCES=0 -UDEBUG -U_DEBUG -DNDEBUG -I/var/lib/dkms/nvidia/331.17/build -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"331.17\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -DNV_UVM_ENABLE -D__linux__ -DNV_DEV_NAME=\"nvidia\"  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_mempool)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /var/lib/dkms/nvidia/331.17/build/.tmp_nv-mempool.o /var/lib/dkms/nvidia/331.17/build/nv-mempool.c
In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/bitops.h:514:0,
                 from include/linux/bitops.h:22,
                 from include/linux/kernel.h:10,
                 from include/linux/sched.h:15,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-mempool.c:15:
include/linux/bitops.h: In function ‘hweight_long’:
include/asm-generic/bitops/const_hweight.h:27:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
 #define hweight64(w) (__builtin_constant_p(w) ? __const_hweight64(w) : __arch_hweight64(w))
                                                                      ^
include/linux/bitops.h:66:41: note: in expansion of macro ‘hweight64’
  return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                                         ^
In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/cpumask.h:4:0,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:5,
                 from include/uapi/linux/timex.h:56,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:17,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-mempool.c:15:
include/linux/cpumask.h: In function ‘cpumask_parse’:
include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
  int len = nl ? nl - buf : strlen(buf);
                          ^
In file included from include/uapi/linux/stddef.h:1:0,
                 from include/linux/stddef.h:4,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi/linux/posix_types.h:4,
                 from include/uapi/linux/types.h:13,
                 from include/linux/types.h:5,
                 from include/uapi/linux/capability.h:16,
                 from include/linux/capability.h:15,
                 from include/linux/sched.h:13,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-mempool.c:15:
/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h: In function ‘copy_from_user’:
/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h:62:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
  if (likely(sz == -1 || sz >= n))
                            ^
include/linux/compiler.h:152:40: note: in definition of macro ‘likely’
 # define likely(x) __builtin_expect(!!(x), 1)
                                        ^
  if [ "-pg" = "-pg" ]; then if [ /var/lib/dkms/nvidia/331.17/build/nv-mempool.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-11-lowlatency/scripts/recordmcount  "/var/lib/dkms/nvidia/331.17/build/nv-mempool.o"; fi; fi;
  cc -Wp,-MD,/var/lib/dkms/nvidia/331.17/build/.nv-mlock.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-11-lowlatency/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DNV_MODULE_INSTANCE=0 -DNV_BUILD_MODULE_INSTANCES=0 -UDEBUG -U_DEBUG -DNDEBUG -I/var/lib/dkms/nvidia/331.17/build -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"331.17\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -DNV_UVM_ENABLE -D__linux__ -DNV_DEV_NAME=\"nvidia\"  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_mlock)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /var/lib/dkms/nvidia/331.17/build/.tmp_nv-mlock.o /var/lib/dkms/nvidia/331.17/build/nv-mlock.c
In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/bitops.h:514:0,
                 from include/linux/bitops.h:22,
                 from include/linux/kernel.h:10,
                 from include/linux/sched.h:15,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-mlock.c:15:
include/linux/bitops.h: In function ‘hweight_long’:
include/asm-generic/bitops/const_hweight.h:27:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
 #define hweight64(w) (__builtin_constant_p(w) ? __const_hweight64(w) : __arch_hweight64(w))
                                                                      ^
include/linux/bitops.h:66:41: note: in expansion of macro ‘hweight64’
  return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                                         ^
In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/cpumask.h:4:0,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:5,
                 from include/uapi/linux/timex.h:56,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:17,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-mlock.c:15:
include/linux/cpumask.h: In function ‘cpumask_parse’:
include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
  int len = nl ? nl - buf : strlen(buf);
                          ^
In file included from include/uapi/linux/stddef.h:1:0,
                 from include/linux/stddef.h:4,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi/linux/posix_types.h:4,
                 from include/uapi/linux/types.h:13,
                 from include/linux/types.h:5,
                 from include/uapi/linux/capability.h:16,
                 from include/linux/capability.h:15,
                 from include/linux/sched.h:13,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-mlock.c:15:
/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h: In function ‘copy_from_user’:
/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h:62:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
  if (likely(sz == -1 || sz >= n))
                            ^
include/linux/compiler.h:152:40: note: in definition of macro ‘likely’
 # define likely(x) __builtin_expect(!!(x), 1)
                                        ^
  if [ "-pg" = "-pg" ]; then if [ /var/lib/dkms/nvidia/331.17/build/nv-mlock.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-11-lowlatency/scripts/recordmcount  "/var/lib/dkms/nvidia/331.17/build/nv-mlock.o"; fi; fi;
  cc -Wp,-MD,/var/lib/dkms/nvidia/331.17/build/.nv-mmap.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-11-lowlatency/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DNV_MODULE_INSTANCE=0 -DNV_BUILD_MODULE_INSTANCES=0 -UDEBUG -U_DEBUG -DNDEBUG -I/var/lib/dkms/nvidia/331.17/build -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"331.17\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -DNV_UVM_ENABLE -D__linux__ -DNV_DEV_NAME=\"nvidia\"  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_mmap)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /var/lib/dkms/nvidia/331.17/build/.tmp_nv-mmap.o /var/lib/dkms/nvidia/331.17/build/nv-mmap.c
In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/bitops.h:514:0,
                 from include/linux/bitops.h:22,
                 from include/linux/kernel.h:10,
                 from include/linux/sched.h:15,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-mmap.c:15:
include/linux/bitops.h: In function ‘hweight_long’:
include/asm-generic/bitops/const_hweight.h:27:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
 #define hweight64(w) (__builtin_constant_p(w) ? __const_hweight64(w) : __arch_hweight64(w))
                                                                      ^
include/linux/bitops.h:66:41: note: in expansion of macro ‘hweight64’
  return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                                         ^
In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/cpumask.h:4:0,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:5,
                 from include/uapi/linux/timex.h:56,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:17,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-mmap.c:15:
include/linux/cpumask.h: In function ‘cpumask_parse’:
include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
  int len = nl ? nl - buf : strlen(buf);
                          ^
In file included from include/uapi/linux/stddef.h:1:0,
                 from include/linux/stddef.h:4,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi/linux/posix_types.h:4,
                 from include/uapi/linux/types.h:13,
                 from include/linux/types.h:5,
                 from include/uapi/linux/capability.h:16,
                 from include/linux/capability.h:15,
                 from include/linux/sched.h:13,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-mmap.c:15:
/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h: In function ‘copy_from_user’:
/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h:62:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
  if (likely(sz == -1 || sz >= n))
                            ^
include/linux/compiler.h:152:40: note: in definition of macro ‘likely’
 # define likely(x) __builtin_expect(!!(x), 1)
                                        ^
  if [ "-pg" = "-pg" ]; then if [ /var/lib/dkms/nvidia/331.17/build/nv-mmap.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-11-lowlatency/scripts/recordmcount  "/var/lib/dkms/nvidia/331.17/build/nv-mmap.o"; fi; fi;
  cc -Wp,-MD,/var/lib/dkms/nvidia/331.17/build/.nv-p2p.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-11-lowlatency/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DNV_MODULE_INSTANCE=0 -DNV_BUILD_MODULE_INSTANCES=0 -UDEBUG -U_DEBUG -DNDEBUG -I/var/lib/dkms/nvidia/331.17/build -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"331.17\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -DNV_UVM_ENABLE -D__linux__ -DNV_DEV_NAME=\"nvidia\"  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_p2p)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /var/lib/dkms/nvidia/331.17/build/.tmp_nv-p2p.o /var/lib/dkms/nvidia/331.17/build/nv-p2p.c
In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/bitops.h:514:0,
                 from include/linux/bitops.h:22,
                 from include/linux/kernel.h:10,
                 from include/linux/sched.h:15,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-p2p.c:15:
include/linux/bitops.h: In function ‘hweight_long’:
include/asm-generic/bitops/const_hweight.h:27:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
 #define hweight64(w) (__builtin_constant_p(w) ? __const_hweight64(w) : __arch_hweight64(w))
                                                                      ^
include/linux/bitops.h:66:41: note: in expansion of macro ‘hweight64’
  return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                                         ^
In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/cpumask.h:4:0,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:5,
                 from include/uapi/linux/timex.h:56,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:17,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-p2p.c:15:
include/linux/cpumask.h: In function ‘cpumask_parse’:
include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
  int len = nl ? nl - buf : strlen(buf);
                          ^
In file included from include/uapi/linux/stddef.h:1:0,
                 from include/linux/stddef.h:4,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi/linux/posix_types.h:4,
                 from include/uapi/linux/types.h:13,
                 from include/linux/types.h:5,
                 from include/uapi/linux/capability.h:16,
                 from include/linux/capability.h:15,
                 from include/linux/sched.h:13,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-p2p.c:15:
/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h: In function ‘copy_from_user’:
/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h:62:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
  if (likely(sz == -1 || sz >= n))
                            ^
include/linux/compiler.h:152:40: note: in definition of macro ‘likely’
 # define likely(x) __builtin_expect(!!(x), 1)
                                        ^
  if [ "-pg" = "-pg" ]; then if [ /var/lib/dkms/nvidia/331.17/build/nv-p2p.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-11-lowlatency/scripts/recordmcount  "/var/lib/dkms/nvidia/331.17/build/nv-p2p.o"; fi; fi;
  cc -Wp,-MD,/var/lib/dkms/nvidia/331.17/build/.nv-pat.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-11-lowlatency/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DNV_MODULE_INSTANCE=0 -DNV_BUILD_MODULE_INSTANCES=0 -UDEBUG -U_DEBUG -DNDEBUG -I/var/lib/dkms/nvidia/331.17/build -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"331.17\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -DNV_UVM_ENABLE -D__linux__ -DNV_DEV_NAME=\"nvidia\"  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_pat)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /var/lib/dkms/nvidia/331.17/build/.tmp_nv-pat.o /var/lib/dkms/nvidia/331.17/build/nv-pat.c
In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/bitops.h:514:0,
                 from include/linux/bitops.h:22,
                 from include/linux/kernel.h:10,
                 from include/linux/sched.h:15,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-pat.c:15:
include/linux/bitops.h: In function ‘hweight_long’:
include/asm-generic/bitops/const_hweight.h:27:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
 #define hweight64(w) (__builtin_constant_p(w) ? __const_hweight64(w) : __arch_hweight64(w))
                                                                      ^
include/linux/bitops.h:66:41: note: in expansion of macro ‘hweight64’
  return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                                         ^
In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/cpumask.h:4:0,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:5,
                 from include/uapi/linux/timex.h:56,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:17,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-pat.c:15:
include/linux/cpumask.h: In function ‘cpumask_parse’:
include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
  int len = nl ? nl - buf : strlen(buf);
                          ^
In file included from include/uapi/linux/stddef.h:1:0,
                 from include/linux/stddef.h:4,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi/linux/posix_types.h:4,
                 from include/uapi/linux/types.h:13,
                 from include/linux/types.h:5,
                 from include/uapi/linux/capability.h:16,
                 from include/linux/capability.h:15,
                 from include/linux/sched.h:13,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-pat.c:15:
/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h: In function ‘copy_from_user’:
/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h:62:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
  if (likely(sz == -1 || sz >= n))
                            ^
include/linux/compiler.h:152:40: note: in definition of macro ‘likely’
 # define likely(x) __builtin_expect(!!(x), 1)
                                        ^
  if [ "-pg" = "-pg" ]; then if [ /var/lib/dkms/nvidia/331.17/build/nv-pat.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-11-lowlatency/scripts/recordmcount  "/var/lib/dkms/nvidia/331.17/build/nv-pat.o"; fi; fi;
  cc -Wp,-MD,/var/lib/dkms/nvidia/331.17/build/.nv-procfs.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-11-lowlatency/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DNV_MODULE_INSTANCE=0 -DNV_BUILD_MODULE_INSTANCES=0 -UDEBUG -U_DEBUG -DNDEBUG -I/var/lib/dkms/nvidia/331.17/build -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"331.17\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -DNV_UVM_ENABLE -D__linux__ -DNV_DEV_NAME=\"nvidia\"  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_procfs)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /var/lib/dkms/nvidia/331.17/build/.tmp_nv-procfs.o /var/lib/dkms/nvidia/331.17/build/nv-procfs.c
In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/bitops.h:514:0,
                 from include/linux/bitops.h:22,
                 from include/linux/kernel.h:10,
                 from include/linux/sched.h:15,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-procfs.c:15:
include/linux/bitops.h: In function ‘hweight_long’:
include/asm-generic/bitops/const_hweight.h:27:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
 #define hweight64(w) (__builtin_constant_p(w) ? __const_hweight64(w) : __arch_hweight64(w))
                                                                      ^
include/linux/bitops.h:66:41: note: in expansion of macro ‘hweight64’
  return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                                         ^
In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/cpumask.h:4:0,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:5,
                 from include/uapi/linux/timex.h:56,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:17,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-procfs.c:15:
include/linux/cpumask.h: In function ‘cpumask_parse’:
include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
  int len = nl ? nl - buf : strlen(buf);
                          ^
In file included from include/uapi/linux/stddef.h:1:0,
                 from include/linux/stddef.h:4,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi/linux/posix_types.h:4,
                 from include/uapi/linux/types.h:13,
                 from include/linux/types.h:5,
                 from include/uapi/linux/capability.h:16,
                 from include/linux/capability.h:15,
                 from include/linux/sched.h:13,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-procfs.c:15:
/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h: In function ‘copy_from_user’:
/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h:62:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
  if (likely(sz == -1 || sz >= n))
                            ^
include/linux/compiler.h:152:40: note: in definition of macro ‘likely’
 # define likely(x) __builtin_expect(!!(x), 1)
                                        ^
  if [ "-pg" = "-pg" ]; then if [ /var/lib/dkms/nvidia/331.17/build/nv-procfs.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-11-lowlatency/scripts/recordmcount  "/var/lib/dkms/nvidia/331.17/build/nv-procfs.o"; fi; fi;
  cc -Wp,-MD,/var/lib/dkms/nvidia/331.17/build/.nv-usermap.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-11-lowlatency/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DNV_MODULE_INSTANCE=0 -DNV_BUILD_MODULE_INSTANCES=0 -UDEBUG -U_DEBUG -DNDEBUG -I/var/lib/dkms/nvidia/331.17/build -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"331.17\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -DNV_UVM_ENABLE -D__linux__ -DNV_DEV_NAME=\"nvidia\"  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_usermap)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /var/lib/dkms/nvidia/331.17/build/.tmp_nv-usermap.o /var/lib/dkms/nvidia/331.17/build/nv-usermap.c
In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/bitops.h:514:0,
                 from include/linux/bitops.h:22,
                 from include/linux/kernel.h:10,
                 from include/linux/sched.h:15,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-usermap.c:15:
include/linux/bitops.h: In function ‘hweight_long’:
include/asm-generic/bitops/const_hweight.h:27:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
 #define hweight64(w) (__builtin_constant_p(w) ? __const_hweight64(w) : __arch_hweight64(w))
                                                                      ^
include/linux/bitops.h:66:41: note: in expansion of macro ‘hweight64’
  return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                                         ^
In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/cpumask.h:4:0,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:5,
                 from include/uapi/linux/timex.h:56,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:17,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-usermap.c:15:
include/linux/cpumask.h: In function ‘cpumask_parse’:
include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
  int len = nl ? nl - buf : strlen(buf);
                          ^
In file included from include/uapi/linux/stddef.h:1:0,
                 from include/linux/stddef.h:4,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi/linux/posix_types.h:4,
                 from include/uapi/linux/types.h:13,
                 from include/linux/types.h:5,
                 from include/uapi/linux/capability.h:16,
                 from include/linux/capability.h:15,
                 from include/linux/sched.h:13,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-usermap.c:15:
/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h: In function ‘copy_from_user’:
/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h:62:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
  if (likely(sz == -1 || sz >= n))
                            ^
include/linux/compiler.h:152:40: note: in definition of macro ‘likely’
 # define likely(x) __builtin_expect(!!(x), 1)
                                        ^
  if [ "-pg" = "-pg" ]; then if [ /var/lib/dkms/nvidia/331.17/build/nv-usermap.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-11-lowlatency/scripts/recordmcount  "/var/lib/dkms/nvidia/331.17/build/nv-usermap.o"; fi; fi;
  cc -Wp,-MD,/var/lib/dkms/nvidia/331.17/build/.nv-vm.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-11-lowlatency/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DNV_MODULE_INSTANCE=0 -DNV_BUILD_MODULE_INSTANCES=0 -UDEBUG -U_DEBUG -DNDEBUG -I/var/lib/dkms/nvidia/331.17/build -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"331.17\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -DNV_UVM_ENABLE -D__linux__ -DNV_DEV_NAME=\"nvidia\"  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_vm)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /var/lib/dkms/nvidia/331.17/build/.tmp_nv-vm.o /var/lib/dkms/nvidia/331.17/build/nv-vm.c
In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/bitops.h:514:0,
                 from include/linux/bitops.h:22,
                 from include/linux/kernel.h:10,
                 from include/linux/sched.h:15,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-vm.c:14:
include/linux/bitops.h: In function ‘hweight_long’:
include/asm-generic/bitops/const_hweight.h:27:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
 #define hweight64(w) (__builtin_constant_p(w) ? __const_hweight64(w) : __arch_hweight64(w))
                                                                      ^
include/linux/bitops.h:66:41: note: in expansion of macro ‘hweight64’
  return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                                         ^
In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/cpumask.h:4:0,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:5,
                 from include/uapi/linux/timex.h:56,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:17,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-vm.c:14:
include/linux/cpumask.h: In function ‘cpumask_parse’:
include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
  int len = nl ? nl - buf : strlen(buf);
                          ^
In file included from include/uapi/linux/stddef.h:1:0,
                 from include/linux/stddef.h:4,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi/linux/posix_types.h:4,
                 from include/uapi/linux/types.h:13,
                 from include/linux/types.h:5,
                 from include/uapi/linux/capability.h:16,
                 from include/linux/capability.h:15,
                 from include/linux/sched.h:13,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-vm.c:14:
/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h: In function ‘copy_from_user’:
/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h:62:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
  if (likely(sz == -1 || sz >= n))
                            ^
include/linux/compiler.h:152:40: note: in definition of macro ‘likely’
 # define likely(x) __builtin_expect(!!(x), 1)
                                        ^
  if [ "-pg" = "-pg" ]; then if [ /var/lib/dkms/nvidia/331.17/build/nv-vm.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-11-lowlatency/scripts/recordmcount  "/var/lib/dkms/nvidia/331.17/build/nv-vm.o"; fi; fi;
  cc -Wp,-MD,/var/lib/dkms/nvidia/331.17/build/.nv-vtophys.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-11-lowlatency/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DNV_MODULE_INSTANCE=0 -DNV_BUILD_MODULE_INSTANCES=0 -UDEBUG -U_DEBUG -DNDEBUG -I/var/lib/dkms/nvidia/331.17/build -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"331.17\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -DNV_UVM_ENABLE -D__linux__ -DNV_DEV_NAME=\"nvidia\"  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_vtophys)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /var/lib/dkms/nvidia/331.17/build/.tmp_nv-vtophys.o /var/lib/dkms/nvidia/331.17/build/nv-vtophys.c
In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/bitops.h:514:0,
                 from include/linux/bitops.h:22,
                 from include/linux/kernel.h:10,
                 from include/linux/sched.h:15,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-vtophys.c:15:
include/linux/bitops.h: In function ‘hweight_long’:
include/asm-generic/bitops/const_hweight.h:27:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
 #define hweight64(w) (__builtin_constant_p(w) ? __const_hweight64(w) : __arch_hweight64(w))
                                                                      ^
include/linux/bitops.h:66:41: note: in expansion of macro ‘hweight64’
  return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                                         ^
In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/cpumask.h:4:0,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:5,
                 from include/uapi/linux/timex.h:56,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:17,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-vtophys.c:15:
include/linux/cpumask.h: In function ‘cpumask_parse’:
include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
  int len = nl ? nl - buf : strlen(buf);
                          ^
In file included from include/uapi/linux/stddef.h:1:0,
                 from include/linux/stddef.h:4,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi/linux/posix_types.h:4,
                 from include/uapi/linux/types.h:13,
                 from include/linux/types.h:5,
                 from include/uapi/linux/capability.h:16,
                 from include/linux/capability.h:15,
                 from include/linux/sched.h:13,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/nv-vtophys.c:15:
/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h: In function ‘copy_from_user’:
/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h:62:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
  if (likely(sz == -1 || sz >= n))
                            ^
include/linux/compiler.h:152:40: note: in definition of macro ‘likely’
 # define likely(x) __builtin_expect(!!(x), 1)
                                        ^
  if [ "-pg" = "-pg" ]; then if [ /var/lib/dkms/nvidia/331.17/build/nv-vtophys.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-11-lowlatency/scripts/recordmcount  "/var/lib/dkms/nvidia/331.17/build/nv-vtophys.o"; fi; fi;
  cc -Wp,-MD,/var/lib/dkms/nvidia/331.17/build/.os-interface.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-11-lowlatency/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DNV_MODULE_INSTANCE=0 -DNV_BUILD_MODULE_INSTANCES=0 -UDEBUG -U_DEBUG -DNDEBUG -I/var/lib/dkms/nvidia/331.17/build -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"331.17\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -DNV_UVM_ENABLE -D__linux__ -DNV_DEV_NAME=\"nvidia\"  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_interface)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /var/lib/dkms/nvidia/331.17/build/.tmp_os-interface.o /var/lib/dkms/nvidia/331.17/build/os-interface.c
In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/bitops.h:514:0,
                 from include/linux/bitops.h:22,
                 from include/linux/kernel.h:10,
                 from include/linux/sched.h:15,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/os-interface.c:15:
include/linux/bitops.h: In function ‘hweight_long’:
include/asm-generic/bitops/const_hweight.h:27:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
 #define hweight64(w) (__builtin_constant_p(w) ? __const_hweight64(w) : __arch_hweight64(w))
                                                                      ^
include/linux/bitops.h:66:41: note: in expansion of macro ‘hweight64’
  return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                                         ^
In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/cpumask.h:4:0,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:5,
                 from include/uapi/linux/timex.h:56,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:17,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/os-interface.c:15:
include/linux/cpumask.h: In function ‘cpumask_parse’:
include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
  int len = nl ? nl - buf : strlen(buf);
                          ^
In file included from include/uapi/linux/stddef.h:1:0,
                 from include/linux/stddef.h:4,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi/linux/posix_types.h:4,
                 from include/uapi/linux/types.h:13,
                 from include/linux/types.h:5,
                 from include/uapi/linux/capability.h:16,
                 from include/linux/capability.h:15,
                 from include/linux/sched.h:13,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/os-interface.c:15:
/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h: In function ‘copy_from_user’:
/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h:62:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
  if (likely(sz == -1 || sz >= n))
                            ^
include/linux/compiler.h:152:40: note: in definition of macro ‘likely’
 # define likely(x) __builtin_expect(!!(x), 1)
                                        ^
In file included from /var/lib/dkms/nvidia/331.17/build/os-interface.c:15:0:
/var/lib/dkms/nvidia/331.17/build/os-interface.c: In function ‘os_get_system_memory_size’:
/var/lib/dkms/nvidia/331.17/build/nv-linux.h:959:41: error: ‘num_physpages’ undeclared (first use in this function)
 #define NV_NUM_PHYSPAGES                num_physpages
                                         ^
/var/lib/dkms/nvidia/331.17/build/os-interface.c:244:21: note: in expansion of macro ‘NV_NUM_PHYSPAGES’
     return (((NvU64)NV_NUM_PHYSPAGES * PAGE_SIZE) / RM_PAGE_SIZE);
                     ^
/var/lib/dkms/nvidia/331.17/build/nv-linux.h:959:41: note: each undeclared identifier is reported only once for each function it appears in
 #define NV_NUM_PHYSPAGES                num_physpages
                                         ^
/var/lib/dkms/nvidia/331.17/build/os-interface.c:244:21: note: in expansion of macro ‘NV_NUM_PHYSPAGES’
     return (((NvU64)NV_NUM_PHYSPAGES * PAGE_SIZE) / RM_PAGE_SIZE);
                     ^
/var/lib/dkms/nvidia/331.17/build/os-interface.c:245:1: warning: control reaches end of non-void function [-Wreturn-type]
 }
 ^
make[2]: *** [/var/lib/dkms/nvidia/331.17/build/os-interface.o] Error 1
make[1]: *** [_module_/var/lib/dkms/nvidia/331.17/build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-11-lowlatency'
NVIDIA: left KBUILD.
 nvidia.ko failed to build!
make: *** [nvidia.ko] Error 1
make: Entering directory `/var/lib/dkms/nvidia/331.17/build/uvm'
cd /var/lib/dkms/nvidia/331.17/build; make module SYSSRC=/lib/modules/3.11.0-11-lowlatency/build SYSOUT=/lib/modules/3.11.0-11-lowlatency/build KBUILD_EXTMOD=/var/lib/dkms/nvidia/331.17/build
make[1]: Entering directory `/var/lib/dkms/nvidia/331.17/build'
NVIDIA: calling KBUILD...
make[2]: Entering directory `/usr/src/linux-headers-3.11.0-11-lowlatency'
test -e include/generated/autoconf.h -a -e include/config/auto.conf || (        \
    echo >&2;                            \
    echo >&2 "  ERROR: Kernel configuration is invalid.";        \
    echo >&2 "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
    echo >&2 "         Run 'make oldconfig && make prepare' on kernel src to fix it.";    \
    echo >&2 ;                            \
    /bin/false)
mkdir -p /var/lib/dkms/nvidia/331.17/build/.tmp_versions ; rm -f /var/lib/dkms/nvidia/331.17/build/.tmp_versions/*
make -f scripts/Makefile.build obj=/var/lib/dkms/nvidia/331.17/build
  cc -Wp,-MD,/var/lib/dkms/nvidia/331.17/build/.os-interface.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-11-lowlatency/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DNV_MODULE_INSTANCE=0 -DNV_BUILD_MODULE_INSTANCES=0 -UDEBUG -U_DEBUG -DNDEBUG -I/var/lib/dkms/nvidia/331.17/build -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"331.17\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -DNV_UVM_ENABLE -D__linux__ -DNV_DEV_NAME=\"nvidia\"  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_interface)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /var/lib/dkms/nvidia/331.17/build/.tmp_os-interface.o /var/lib/dkms/nvidia/331.17/build/os-interface.c
In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/bitops.h:514:0,
                 from include/linux/bitops.h:22,
                 from include/linux/kernel.h:10,
                 from include/linux/sched.h:15,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/os-interface.c:15:
include/linux/bitops.h: In function ‘hweight_long’:
include/asm-generic/bitops/const_hweight.h:27:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
 #define hweight64(w) (__builtin_constant_p(w) ? __const_hweight64(w) : __arch_hweight64(w))
                                                                      ^
include/linux/bitops.h:66:41: note: in expansion of macro ‘hweight64’
  return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                                         ^
In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/cpumask.h:4:0,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:5,
                 from include/uapi/linux/timex.h:56,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:17,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/os-interface.c:15:
include/linux/cpumask.h: In function ‘cpumask_parse’:
include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
  int len = nl ? nl - buf : strlen(buf);
                          ^
In file included from include/uapi/linux/stddef.h:1:0,
                 from include/linux/stddef.h:4,
                 from /usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi/linux/posix_types.h:4,
                 from include/uapi/linux/types.h:13,
                 from include/linux/types.h:5,
                 from include/uapi/linux/capability.h:16,
                 from include/linux/capability.h:15,
                 from include/linux/sched.h:13,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/331.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/331.17/build/os-interface.c:15:
/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h: In function ‘copy_from_user’:
/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h:62:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
  if (likely(sz == -1 || sz >= n))
                            ^
include/linux/compiler.h:152:40: note: in definition of macro ‘likely’
 # define likely(x) __builtin_expect(!!(x), 1)
                                        ^
In file included from /var/lib/dkms/nvidia/331.17/build/os-interface.c:15:0:
/var/lib/dkms/nvidia/331.17/build/os-interface.c: In function ‘os_get_system_memory_size’:
/var/lib/dkms/nvidia/331.17/build/nv-linux.h:959:41: error: ‘num_physpages’ undeclared (first use in this function)
 #define NV_NUM_PHYSPAGES                num_physpages
                                         ^
/var/lib/dkms/nvidia/331.17/build/os-interface.c:244:21: note: in expansion of macro ‘NV_NUM_PHYSPAGES’
     return (((NvU64)NV_NUM_PHYSPAGES * PAGE_SIZE) / RM_PAGE_SIZE);
                     ^
/var/lib/dkms/nvidia/331.17/build/nv-linux.h:959:41: note: each undeclared identifier is reported only once for each function it appears in
 #define NV_NUM_PHYSPAGES                num_physpages
                                         ^
/var/lib/dkms/nvidia/331.17/build/os-interface.c:244:21: note: in expansion of macro ‘NV_NUM_PHYSPAGES’
     return (((NvU64)NV_NUM_PHYSPAGES * PAGE_SIZE) / RM_PAGE_SIZE);
                     ^
/var/lib/dkms/nvidia/331.17/build/os-interface.c:245:1: warning: control reaches end of non-void function [-Wreturn-type]
 }
 ^
make[3]: *** [/var/lib/dkms/nvidia/331.17/build/os-interface.o] Error 1
make[2]: *** [_module_/var/lib/dkms/nvidia/331.17/build] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.11.0-11-lowlatency'
NVIDIA: left KBUILD.
 nvidia.ko failed to build!
make[1]: *** [nvidia.ko] Error 1
make[1]: Leaving directory `/var/lib/dkms/nvidia/331.17/build'
make: *** [/var/lib/dkms/nvidia/331.17/build/Module.symvers] Error 2
make: Leaving directory `/var/lib/dkms/nvidia/331.17/build/uvm'
```

nvidia build log no dkms
```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Tue Oct 29 16:07:50 2013
installer version: 331.17

PATH: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

nvidia-installer command line:
    ./nvidia-installer

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 331.17.
-> There appears to already be a driver installed on your system (version: 331.17).  As part of installing this driver (version: 331.17), the existing driver will be uninstalled.  Are you sure you want to continue? ('no' will abort installation) (Answer: Yes)
-> Running distribution scripts
   executing: '/usr/lib/nvidia/pre-install'...
-> done.
-> The distribution-provided pre-install script failed!  Continue installation anyway? (Answer: Yes)
-> Would you like to register the kernel module sources with DKMS? This will allow DKMS to automatically build a new module, if you install a different kernel later. (Answer: No)
-> Performing CC sanity check with CC="cc".
-> Kernel source path: '/lib/modules/3.11.0-11-lowlatency/build'
-> Kernel output path: '/lib/modules/3.11.0-11-lowlatency/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Performing PREEMPT_RT check.
-> Cleaning kernel module build directory.
   executing: 'cd ./kernel; make clean'...
-> Building NVIDIA kernel module:
   executing: 'cd ./kernel; make module SYSSRC=/lib/modules/3.11.0-11-lowlatency/build SYSOUT=/lib/modules/3.11.0-11-lowlatency/build NV_BUILD_MODULE_INSTANCES='...
   NVIDIA: calling KBUILD...
   make[1]: Entering directory `/usr/src/linux-headers-3.11.0-11-lowlatency'
   test -e include/generated/autoconf.h -a -e include/config/auto.conf || (        \
       echo >&2;                            \
       echo >&2 "  ERROR: Kernel configuration is invalid.";        \
       echo >&2 "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
       echo >&2 "         Run 'make oldconfig && make prepare' on kernel src to fix it.";    \
       echo >&2 ;                            \
       /bin/false)
   mkdir -p /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/.tmp_versions ; rm -f /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/.tmp_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel
     cc -Wp,-MD,/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/.nv.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/uapi -Iarch/x86/include/ge
   nerated/uapi -I/usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-11-lowlatency/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE
   _ASM_GOTO -DNV_MODULE_INSTANCE=0 -DNV_BUILD_MODULE_INSTANCES=0 -UDEBUG -U_DEBUG -DNDEBUG -I/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"331.17\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -DNV_UVM_ENABLE -D__linux__ -DNV_DEV_NAME=\"nvidia\"  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/.tmp_nv.o /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv.c
   In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/bitops.h:514:0,
                    from include/linux/bitops.h:22,
                    from include/linux/kernel.h:10,
                    from include/linux/sched.h:15,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv.c:13:
   include/linux/bitops.h: In function ‘hweight_long’:
   include/asm-generic/bitops/const_hweight.h:27:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
    #define hweight64(w) (__builtin_constant_p(w) ? __const_hweight64(w) : __arch_hweight64(w))
                                                                         ^
   include/linux/bitops.h:66:41: note: in expansion of macro ‘hweight64’
     return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                                            ^
   In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/cpumask.h:4:0,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/msr.h:10,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/processor.h:20,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/thread_info.h:22,
                    from include/linux/thread_info.h:54,
                    from include/linux/preempt.h:9,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:5,
                    from include/uapi/linux/timex.h:56,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:17,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv.c:13:
   include/linux/cpumask.h: In function ‘cpumask_parse’:
   include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
     int len = nl ? nl - buf : strlen(buf);
                             ^
   In file included from include/uapi/linux/stddef.h:1:0,
                    from include/linux/stddef.h:4,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi/linux/posix_types.h:4,
                    from include/uapi/linux/types.h:13,
                    from include/linux/types.h:5,
                    from include/uapi/linux/capability.h:16,
                    from include/linux/capability.h:15,
                    from include/linux/sched.h:13,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv.c:13:
   /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h: In function ‘copy_from_user’:
   /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h:62:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if (likely(sz == -1 || sz >= n))
                               ^
   include/linux/compiler.h:152:40: note: in definition of macro ‘likely’
    # define likely(x) __builtin_expect(!!(x), 1)
                                           ^
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-11-lowlatency/scripts/recordmcount  "/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/.nv-acpi.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-11-lowlatency/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulat
   e-outgoing-args -fstack-protector -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DNV_MODULE_INSTANCE=0 -DNV_BUILD_MODULE_INSTANCES=0 -UDEBUG -U_DEBUG -DNDEBUG -I/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"331.17\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -DNV_UVM_ENABLE -D__linux__ -DNV_DEV_NAME=\"nvidia\"  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_acpi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/self
   gz2758/NVIDIA-Linux-x86_64-331.17/kernel/.tmp_nv-acpi.o /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-acpi.c
   In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/bitops.h:514:0,
                    from include/linux/bitops.h:22,
                    from include/linux/kernel.h:10,
                    from include/linux/sched.h:15,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-acpi.c:15:
   include/linux/bitops.h: In function ‘hweight_long’:
   include/asm-generic/bitops/const_hweight.h:27:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
    #define hweight64(w) (__builtin_constant_p(w) ? __const_hweight64(w) : __arch_hweight64(w))
                                                                         ^
   include/linux/bitops.h:66:41: note: in expansion of macro ‘hweight64’
     return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                                            ^
   In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/cpumask.h:4:0,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/msr.h:10,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/processor.h:20,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/thread_info.h:22,
                    from include/linux/thread_info.h:54,
                    from include/linux/preempt.h:9,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:5,
                    from include/uapi/linux/timex.h:56,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:17,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-acpi.c:15:
   include/linux/cpumask.h: In function ‘cpumask_parse’:
   include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
     int len = nl ? nl - buf : strlen(buf);
                             ^
   In file included from include/uapi/linux/stddef.h:1:0,
                    from include/linux/stddef.h:4,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi/linux/posix_types.h:4,
                    from include/uapi/linux/types.h:13,
                    from include/linux/types.h:5,
                    from include/uapi/linux/capability.h:16,
                    from include/linux/capability.h:15,
                    from include/linux/sched.h:13,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-acpi.c:15:
   /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h: In function ‘copy_from_user’:
   /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h:62:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if (likely(sz == -1 || sz >= n))
                               ^
   include/linux/compiler.h:152:40: note: in definition of macro ‘likely’
    # define likely(x) __builtin_expect(!!(x), 1)
                                           ^
   /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-acpi.c: At top level:
   /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-acpi.c:70:9: warning: initialization from incompatible pointer type [enabled by default]
            .remove = nv_acpi_remove,
            ^
   /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-acpi.c:70:9: warning: (near initialization for ‘nv_acpi_driver_template.ops.remove’) [enabled by default]
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-acpi.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-11-lowlatency/scripts/recordmcount  "/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-acpi.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/.nv-chrdev.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-11-lowlatency/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protec
   tor -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DNV_MODULE_INSTANCE=0 -DNV_BUILD_MODULE_INSTANCES=0 -UDEBUG -U_DEBUG -DNDEBUG -I/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"331.17\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -DNV_UVM_ENABLE -D__linux__ -DNV_DEV_NAME=\"nvidia\"  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_chrdev)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz2758/NVIDIA-Linux-x86_64-3
   31.17/kernel/.tmp_nv-chrdev.o /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-chrdev.c
   In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/bitops.h:514:0,
                    from include/linux/bitops.h:22,
                    from include/linux/kernel.h:10,
                    from include/linux/sched.h:15,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-chrdev.c:15:
   include/linux/bitops.h: In function ‘hweight_long’:
   include/asm-generic/bitops/const_hweight.h:27:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
    #define hweight64(w) (__builtin_constant_p(w) ? __const_hweight64(w) : __arch_hweight64(w))
                                                                         ^
   include/linux/bitops.h:66:41: note: in expansion of macro ‘hweight64’
     return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                                            ^
   In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/cpumask.h:4:0,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/msr.h:10,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/processor.h:20,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/thread_info.h:22,
                    from include/linux/thread_info.h:54,
                    from include/linux/preempt.h:9,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:5,
                    from include/uapi/linux/timex.h:56,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:17,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-chrdev.c:15:
   include/linux/cpumask.h: In function ‘cpumask_parse’:
   include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
     int len = nl ? nl - buf : strlen(buf);
                             ^
   In file included from include/uapi/linux/stddef.h:1:0,
                    from include/linux/stddef.h:4,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi/linux/posix_types.h:4,
                    from include/uapi/linux/types.h:13,
                    from include/linux/types.h:5,
                    from include/uapi/linux/capability.h:16,
                    from include/linux/capability.h:15,
                    from include/linux/sched.h:13,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-chrdev.c:15:
   /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h: In function ‘copy_from_user’:
   /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h:62:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if (likely(sz == -1 || sz >= n))
                               ^
   include/linux/compiler.h:152:40: note: in definition of macro ‘likely’
    # define likely(x) __builtin_expect(!!(x), 1)
                                           ^
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-chrdev.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-11-lowlatency/scripts/recordmcount  "/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-chrdev.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/.nv-cray.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-11-
   lowlatency/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-11-lowlatency/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wno-pointe
   r-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DNV_MODULE_INSTANCE=0 -DNV_BUILD_MODULE_INSTANCES=0 -UDEBUG -U_DEBUG -DNDEBUG -I/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"331.17\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -DNV_UVM_ENABLE -D__linux__ -DNV_DEV_NAME=\"nvidia\"  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_cray)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/.tmp_nv-cray.o /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-cray.c
   In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/bitops.h:514:0,
                    from include/linux/bitops.h:22,
                    from include/linux/kernel.h:10,
                    from include/linux/sched.h:15,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-cray.c:15:
   include/linux/bitops.h: In function ‘hweight_long’:
   include/asm-generic/bitops/const_hweight.h:27:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
    #define hweight64(w) (__builtin_constant_p(w) ? __const_hweight64(w) : __arch_hweight64(w))
                                                                         ^
   include/linux/bitops.h:66:41: note: in expansion of macro ‘hweight64’
     return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                                            ^
   In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/cpumask.h:4:0,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/msr.h:10,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/processor.h:20,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/thread_info.h:22,
                    from include/linux/thread_info.h:54,
                    from include/linux/preempt.h:9,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:5,
                    from include/uapi/linux/timex.h:56,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:17,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-cray.c:15:
   include/linux/cpumask.h: In function ‘cpumask_parse’:
   include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
     int len = nl ? nl - buf : strlen(buf);
                             ^
   In file included from include/uapi/linux/stddef.h:1:0,
                    from include/linux/stddef.h:4,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi/linux/posix_types.h:4,
                    from include/uapi/linux/types.h:13,
                    from include/linux/types.h:5,
                    from include/uapi/linux/capability.h:16,
                    from include/linux/capability.h:15,
                    from include/linux/sched.h:13,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-cray.c:15:
   /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h: In function ‘copy_from_user’:
   /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h:62:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if (likely(sz == -1 || sz >= n))
                               ^
   include/linux/compiler.h:152:40: note: in definition of macro ‘likely’
    # define likely(x) __builtin_expect(!!(x), 1)
                                           ^
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-cray.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-11-lowlatency/scripts/recordmcount  "/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-cray.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/.nv-drm.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-11-lowlatency/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mno-sse -mpreferr
   ed-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DNV_MODULE_INSTANCE=0 -DNV_BUILD_MODULE_INSTANCES=0 -UDEBUG -U_DEBUG -DNDEBUG -I/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"331.17\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -DNV_UVM_ENABLE -D__linux__ -DNV_DEV_NAME=\"nvidia\"  -DMODULE  -D"KBUILD_STR(s)=#s" -
   D"KBUILD_BASENAME=KBUILD_STR(nv_drm)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/.tmp_nv-drm.o /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-drm.c
   In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/bitops.h:514:0,
                    from include/linux/bitops.h:22,
                    from include/linux/kernel.h:10,
                    from include/linux/sched.h:15,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-drm.c:15:
   include/linux/bitops.h: In function ‘hweight_long’:
   include/asm-generic/bitops/const_hweight.h:27:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
    #define hweight64(w) (__builtin_constant_p(w) ? __const_hweight64(w) : __arch_hweight64(w))
                                                                         ^
   include/linux/bitops.h:66:41: note: in expansion of macro ‘hweight64’
     return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                                            ^
   In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/cpumask.h:4:0,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/msr.h:10,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/processor.h:20,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/thread_info.h:22,
                    from include/linux/thread_info.h:54,
                    from include/linux/preempt.h:9,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:5,
                    from include/uapi/linux/timex.h:56,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:17,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-drm.c:15:
   include/linux/cpumask.h: In function ‘cpumask_parse’:
   include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
     int len = nl ? nl - buf : strlen(buf);
                             ^
   In file included from include/uapi/linux/stddef.h:1:0,
                    from include/linux/stddef.h:4,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi/linux/posix_types.h:4,
                    from include/uapi/linux/types.h:13,
                    from include/linux/types.h:5,
                    from include/uapi/linux/capability.h:16,
                    from include/linux/capability.h:15,
                    from include/linux/sched.h:13,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-drm.c:15:
   /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h: In function ‘copy_from_user’:
   /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h:62:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if (likely(sz == -1 || sz >= n))
                               ^
   include/linux/compiler.h:152:40: note: in definition of macro ‘likely’
    # define likely(x) __builtin_expect(!!(x), 1)
                                           ^
   In file included from include/drm/drm_crtc.h:32:0,
                    from include/drm/drmP.h:688,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-drm.c:19:
   include/linux/fb.h: In function ‘__fb_pad_aligned_buffer’:
   include/linux/fb.h:650:17: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
      for (j = 0; j < s_pitch; j++)
                    ^
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-drm.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-11-lowlatency/scripts/recordmcount  "/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-drm.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/.nv-gvi.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-11-lowlatency/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=
   kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DNV_MODULE_INSTANCE=0 -DNV_BUILD_MODULE_INSTANCES=0 -UDEBUG -U_DEBUG -DNDEBUG -I/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"331.17\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -DNV_UVM_ENABLE -D__linux__ -DNV_DEV_NAME=\"nvidia\"  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_gvi)"  -D"KBUILD_MODNAME=K
   BUILD_STR(nvidia)" -c -o /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/.tmp_nv-gvi.o /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-gvi.c
   In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/bitops.h:514:0,
                    from include/linux/bitops.h:22,
                    from include/linux/kernel.h:10,
                    from include/linux/sched.h:15,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-gvi.c:15:
   include/linux/bitops.h: In function ‘hweight_long’:
   include/asm-generic/bitops/const_hweight.h:27:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
    #define hweight64(w) (__builtin_constant_p(w) ? __const_hweight64(w) : __arch_hweight64(w))
                                                                         ^
   include/linux/bitops.h:66:41: note: in expansion of macro ‘hweight64’
     return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                                            ^
   In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/cpumask.h:4:0,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/msr.h:10,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/processor.h:20,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/thread_info.h:22,
                    from include/linux/thread_info.h:54,
                    from include/linux/preempt.h:9,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:5,
                    from include/uapi/linux/timex.h:56,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:17,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-gvi.c:15:
   include/linux/cpumask.h: In function ‘cpumask_parse’:
   include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
     int len = nl ? nl - buf : strlen(buf);
                             ^
   In file included from include/uapi/linux/stddef.h:1:0,
                    from include/linux/stddef.h:4,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi/linux/posix_types.h:4,
                    from include/uapi/linux/types.h:13,
                    from include/linux/types.h:5,
                    from include/uapi/linux/capability.h:16,
                    from include/linux/capability.h:15,
                    from include/linux/sched.h:13,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-gvi.c:15:
   /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h: In function ‘copy_from_user’:
   /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h:62:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if (likely(sz == -1 || sz >= n))
                               ^
   include/linux/compiler.h:152:40: note: in definition of macro ‘likely’
    # define likely(x) __builtin_expect(!!(x), 1)
                                           ^
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-gvi.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-11-lowlatency/scripts/recordmcount  "/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-gvi.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/.nv-i2c.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-11-lowlatency/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -mfentry -DCC_USING_FENTRY -
   Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DNV_MODULE_INSTANCE=0 -DNV_BUILD_MODULE_INSTANCES=0 -UDEBUG -U_DEBUG -DNDEBUG -I/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"331.17\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -DNV_UVM_ENABLE -D__linux__ -DNV_DEV_NAME=\"nvidia\"  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_i2c)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/.tmp_nv-i2c.o /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-i2c.c
   In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/bitops.h:514:0,
                    from include/linux/bitops.h:22,
                    from include/linux/kernel.h:10,
                    from include/linux/sched.h:15,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-i2c.c:15:
   include/linux/bitops.h: In function ‘hweight_long’:
   include/asm-generic/bitops/const_hweight.h:27:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
    #define hweight64(w) (__builtin_constant_p(w) ? __const_hweight64(w) : __arch_hweight64(w))
                                                                         ^
   include/linux/bitops.h:66:41: note: in expansion of macro ‘hweight64’
     return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                                            ^
   In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/cpumask.h:4:0,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/msr.h:10,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/processor.h:20,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/thread_info.h:22,
                    from include/linux/thread_info.h:54,
                    from include/linux/preempt.h:9,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:5,
                    from include/uapi/linux/timex.h:56,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:17,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-i2c.c:15:
   include/linux/cpumask.h: In function ‘cpumask_parse’:
   include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
     int len = nl ? nl - buf : strlen(buf);
                             ^
   In file included from include/uapi/linux/stddef.h:1:0,
                    from include/linux/stddef.h:4,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi/linux/posix_types.h:4,
                    from include/uapi/linux/types.h:13,
                    from include/linux/types.h:5,
                    from include/uapi/linux/capability.h:16,
                    from include/linux/capability.h:15,
                    from include/linux/sched.h:13,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-i2c.c:15:
   /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h: In function ‘copy_from_user’:
   /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h:62:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if (likely(sz == -1 || sz >= n))
                               ^
   include/linux/compiler.h:152:40: note: in definition of macro ‘likely’
    # define likely(x) __builtin_expect(!!(x), 1)
                                           ^
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-i2c.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-11-lowlatency/scripts/recordmcount  "/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-i2c.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/.nv-mempool.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-11-lowlatency/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointe
   r-checks -O2 -m64 -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DNV_MODULE_INSTANCE=0 -DNV_BUILD_MODULE_INSTANCES=0 -UDEBUG -U_DEBUG -DNDEBUG -I/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"331.17\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -DNV_UVM_ENABLE -D__linux__ -DNV_DEV_NAME=\"nvidia
   \"  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_mempool)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/.tmp_nv-mempool.o /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-mempool.c
   In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/bitops.h:514:0,
                    from include/linux/bitops.h:22,
                    from include/linux/kernel.h:10,
                    from include/linux/sched.h:15,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-mempool.c:15:
   include/linux/bitops.h: In function ‘hweight_long’:
   include/asm-generic/bitops/const_hweight.h:27:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
    #define hweight64(w) (__builtin_constant_p(w) ? __const_hweight64(w) : __arch_hweight64(w))
                                                                         ^
   include/linux/bitops.h:66:41: note: in expansion of macro ‘hweight64’
     return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                                            ^
   In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/cpumask.h:4:0,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/msr.h:10,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/processor.h:20,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/thread_info.h:22,
                    from include/linux/thread_info.h:54,
                    from include/linux/preempt.h:9,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:5,
                    from include/uapi/linux/timex.h:56,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:17,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-mempool.c:15:
   include/linux/cpumask.h: In function ‘cpumask_parse’:
   include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
     int len = nl ? nl - buf : strlen(buf);
                             ^
   In file included from include/uapi/linux/stddef.h:1:0,
                    from include/linux/stddef.h:4,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi/linux/posix_types.h:4,
                    from include/uapi/linux/types.h:13,
                    from include/linux/types.h:5,
                    from include/uapi/linux/capability.h:16,
                    from include/linux/capability.h:15,
                    from include/linux/sched.h:13,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-mempool.c:15:
   /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h: In function ‘copy_from_user’:
   /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h:62:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if (likely(sz == -1 || sz >= n))
                               ^
   include/linux/compiler.h:152:40: note: in definition of macro ‘likely’
    # define likely(x) __builtin_expect(!!(x), 1)
                                           ^
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-mempool.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-11-lowlatency/scripts/recordmcount  "/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-mempool.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/.nv-mlock.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-11-lowlatency/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-la
   rger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DNV_MODULE_INSTANCE=0 -DNV_BUILD_MODULE_INSTANCES=0 -UDEBUG -U_DEBUG -DNDEBUG -I/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"331.17\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -DNV_UVM_ENABLE -D__linux__ -DNV_DEV_NAME=\"nvidia\"  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_mlock)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/.tmp_nv-mlock.o /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-mlock.c
   In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/bitops.h:514:0,
                    from include/linux/bitops.h:22,
                    from include/linux/kernel.h:10,
                    from include/linux/sched.h:15,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-mlock.c:15:
   include/linux/bitops.h: In function ‘hweight_long’:
   include/asm-generic/bitops/const_hweight.h:27:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
    #define hweight64(w) (__builtin_constant_p(w) ? __const_hweight64(w) : __arch_hweight64(w))
                                                                         ^
   include/linux/bitops.h:66:41: note: in expansion of macro ‘hweight64’
     return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                                            ^
   In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/cpumask.h:4:0,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/msr.h:10,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/processor.h:20,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/thread_info.h:22,
                    from include/linux/thread_info.h:54,
                    from include/linux/preempt.h:9,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:5,
                    from include/uapi/linux/timex.h:56,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:17,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-mlock.c:15:
   include/linux/cpumask.h: In function ‘cpumask_parse’:
   include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
     int len = nl ? nl - buf : strlen(buf);
                             ^
   In file included from include/uapi/linux/stddef.h:1:0,
                    from include/linux/stddef.h:4,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi/linux/posix_types.h:4,
                    from include/uapi/linux/types.h:13,
                    from include/linux/types.h:5,
                    from include/uapi/linux/capability.h:16,
                    from include/linux/capability.h:15,
                    from include/linux/sched.h:13,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-mlock.c:15:
   /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h: In function ‘copy_from_user’:
   /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h:62:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if (likely(sz == -1 || sz >= n))
                               ^
   include/linux/compiler.h:152:40: note: in definition of macro ‘likely’
    # define likely(x) __builtin_expect(!!(x), 1)
                                           ^
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-mlock.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-11-lowlatency/scripts/recordmcount  "/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-mlock.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/.nv-mmap.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-11-lowlatency/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-
   prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DNV_MODULE_INSTANCE=0 -DNV_BUILD_MODULE_INSTANCES=0 -UDEBUG -U_DEBUG -DNDEBUG -I/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VE
   RSION_STRING=\"331.17\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -DNV_UVM_ENABLE -D__linux__ -DNV_DEV_NAME=\"nvidia\"  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_mmap)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/.tmp_nv-mmap.o /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-mmap.c
   In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/bitops.h:514:0,
                    from include/linux/bitops.h:22,
                    from include/linux/kernel.h:10,
                    from include/linux/sched.h:15,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-mmap.c:15:
   include/linux/bitops.h: In function ‘hweight_long’:
   include/asm-generic/bitops/const_hweight.h:27:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
    #define hweight64(w) (__builtin_constant_p(w) ? __const_hweight64(w) : __arch_hweight64(w))
                                                                         ^
   include/linux/bitops.h:66:41: note: in expansion of macro ‘hweight64’
     return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                                            ^
   In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/cpumask.h:4:0,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/msr.h:10,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/processor.h:20,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/thread_info.h:22,
                    from include/linux/thread_info.h:54,
                    from include/linux/preempt.h:9,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:5,
                    from include/uapi/linux/timex.h:56,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:17,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-mmap.c:15:
   include/linux/cpumask.h: In function ‘cpumask_parse’:
   include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
     int len = nl ? nl - buf : strlen(buf);
                             ^
   In file included from include/uapi/linux/stddef.h:1:0,
                    from include/linux/stddef.h:4,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi/linux/posix_types.h:4,
                    from include/uapi/linux/types.h:13,
                    from include/linux/types.h:5,
                    from include/uapi/linux/capability.h:16,
                    from include/linux/capability.h:15,
                    from include/linux/sched.h:13,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-mmap.c:15:
   /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h: In function ‘copy_from_user’:
   /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h:62:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if (likely(sz == -1 || sz >= n))
                               ^
   include/linux/compiler.h:152:40: note: in definition of macro ‘likely’
    # define likely(x) __builtin_expect(!!(x), 1)
                                           ^
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-mmap.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-11-lowlatency/scripts/recordmcount  "/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-mmap.o"; f
   i; fi;
     cc -Wp,-MD,/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/.nv-p2p.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-11-lowlatency/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1
    -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DNV_MODULE_INSTANCE=0 -DNV_BUILD_MODULE_INSTANCES=0 -UDEBUG -U_DEBUG -DNDEBUG -I/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"331.17\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -DNV_UVM_ENABLE -D__linux__ -DNV_DEV_NAME=\"nvidia\"  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_p2p)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/.tmp_nv-p2p.o /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-p2p.c
   In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/bitops.h:514:0,
                    from include/linux/bitops.h:22,
                    from include/linux/kernel.h:10,
                    from include/linux/sched.h:15,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-p2p.c:15:
   include/linux/bitops.h: In function ‘hweight_long’:
   include/asm-generic/bitops/const_hweight.h:27:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
    #define hweight64(w) (__builtin_constant_p(w) ? __const_hweight64(w) : __arch_hweight64(w))
                                                                         ^
   include/linux/bitops.h:66:41: note: in expansion of macro ‘hweight64’
     return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                                            ^
   In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/cpumask.h:4:0,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/msr.h:10,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/processor.h:20,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/thread_info.h:22,
                    from include/linux/thread_info.h:54,
                    from include/linux/preempt.h:9,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:5,
                    from include/uapi/linux/timex.h:56,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:17,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-p2p.c:15:
   include/linux/cpumask.h: In function ‘cpumask_parse’:
   include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
     int len = nl ? nl - buf : strlen(buf);
                             ^
   In file included from include/uapi/linux/stddef.h:1:0,
                    from include/linux/stddef.h:4,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi/linux/posix_types.h:4,
                    from include/uapi/linux/types.h:13,
                    from include/linux/types.h:5,
                    from include/uapi/linux/capability.h:16,
                    from include/linux/capability.h:15,
                    from include/linux/sched.h:13,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-p2p.c:15:
   /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h: In function ‘copy_from_user’:
   /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h:62:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if (likely(sz == -1 || sz >= n))
                               ^
   include/linux/compiler.h:152:40: note: in definition of macro ‘likely’
    # define likely(x) __builtin_expect(!!(x), 1)
                                           ^
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-p2p.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-11-lowlatency/scripts/recordmcount  "/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-p2p.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/.nv-pat.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3
   .11.0-11-lowlatency/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DNV_MODULE_INSTANCE=0 -DNV_BUILD_MODULE_INSTANCES=0 -UDEBUG -U_DEBUG -DNDEBUG -I/tmp/selfgz2758/NVIDIA-Linux-x86_64-331
   .17/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"331.17\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -DNV_UVM_ENABLE -D__linux__ -DNV_DEV_NAME=\"nvidia\"  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_pat)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/.tmp_nv-pat.o /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-pat.c
   In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/bitops.h:514:0,
                    from include/linux/bitops.h:22,
                    from include/linux/kernel.h:10,
                    from include/linux/sched.h:15,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-pat.c:15:
   include/linux/bitops.h: In function ‘hweight_long’:
   include/asm-generic/bitops/const_hweight.h:27:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
    #define hweight64(w) (__builtin_constant_p(w) ? __const_hweight64(w) : __arch_hweight64(w))
                                                                         ^
   include/linux/bitops.h:66:41: note: in expansion of macro ‘hweight64’
     return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                                            ^
   In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/cpumask.h:4:0,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/msr.h:10,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/processor.h:20,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/thread_info.h:22,
                    from include/linux/thread_info.h:54,
                    from include/linux/preempt.h:9,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:5,
                    from include/uapi/linux/timex.h:56,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:17,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-pat.c:15:
   include/linux/cpumask.h: In function ‘cpumask_parse’:
   include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
     int len = nl ? nl - buf : strlen(buf);
                             ^
   In file included from include/uapi/linux/stddef.h:1:0,
                    from include/linux/stddef.h:4,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi/linux/posix_types.h:4,
                    from include/uapi/linux/types.h:13,
                    from include/linux/types.h:5,
                    from include/uapi/linux/capability.h:16,
                    from include/linux/capability.h:15,
                    from include/linux/sched.h:13,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-pat.c:15:
   /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h: In function ‘copy_from_user’:
   /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h:62:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if (likely(sz == -1 || sz >= n))
                               ^
   include/linux/compiler.h:152:40: note: in definition of macro ‘likely’
    # define likely(x) __builtin_expect(!!(x), 1)
                                           ^
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-pat.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-11-lowlatency/scripts/recordmcount  "/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-pat.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/.nv-procfs.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-11-lowlatency/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_
   FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DNV_MODULE_INSTANCE=0 -DNV_BUILD_MODULE_INSTANCES=0 -UDEBUG -U_DEBUG -DNDEBUG -I/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"331.17\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -DNV_UVM_ENABLE -D__linux__ -DNV_DEV_NAME=\"nvidia\"  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_procfs)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/.tmp_nv-procfs.o /tmp/selfgz2758/NVIDIA-Linux-x86_64-
   331.17/kernel/nv-procfs.c
   In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/bitops.h:514:0,
                    from include/linux/bitops.h:22,
                    from include/linux/kernel.h:10,
                    from include/linux/sched.h:15,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-procfs.c:15:
   include/linux/bitops.h: In function ‘hweight_long’:
   include/asm-generic/bitops/const_hweight.h:27:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
    #define hweight64(w) (__builtin_constant_p(w) ? __const_hweight64(w) : __arch_hweight64(w))
                                                                         ^
   include/linux/bitops.h:66:41: note: in expansion of macro ‘hweight64’
     return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                                            ^
   In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/cpumask.h:4:0,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/msr.h:10,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/processor.h:20,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/thread_info.h:22,
                    from include/linux/thread_info.h:54,
                    from include/linux/preempt.h:9,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:5,
                    from include/uapi/linux/timex.h:56,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:17,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-procfs.c:15:
   include/linux/cpumask.h: In function ‘cpumask_parse’:
   include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
     int len = nl ? nl - buf : strlen(buf);
                             ^
   In file included from include/uapi/linux/stddef.h:1:0,
                    from include/linux/stddef.h:4,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi/linux/posix_types.h:4,
                    from include/uapi/linux/types.h:13,
                    from include/linux/types.h:5,
                    from include/uapi/linux/capability.h:16,
                    from include/linux/capability.h:15,
                    from include/linux/sched.h:13,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-procfs.c:15:
   /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h: In function ‘copy_from_user’:
   /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h:62:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if (likely(sz == -1 || sz >= n))
                               ^
   include/linux/compiler.h:152:40: note: in definition of macro ‘likely’
    # define likely(x) __builtin_expect(!!(x), 1)
                                           ^
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-procfs.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-11-lowlatency/scripts/recordmcount  "/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-procfs.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/.nv-usermap.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/uapi -Iarch/x86/include/generated/u
   api -I/usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-11-lowlatency/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO
    -DNV_MODULE_INSTANCE=0 -DNV_BUILD_MODULE_INSTANCES=0 -UDEBUG -U_DEBUG -DNDEBUG -I/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"331.17\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -DNV_UVM_ENABLE -D__linux__ -DNV_DEV_NAME=\"nvidia\"  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_usermap)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/.tmp_nv-usermap.o /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-usermap.c
   In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/bitops.h:514:0,
                    from include/linux/bitops.h:22,
                    from include/linux/kernel.h:10,
                    from include/linux/sched.h:15,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-usermap.c:15:
   include/linux/bitops.h: In function ‘hweight_long’:
   include/asm-generic/bitops/const_hweight.h:27:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
    #define hweight64(w) (__builtin_constant_p(w) ? __const_hweight64(w) : __arch_hweight64(w))
                                                                         ^
   include/linux/bitops.h:66:41: note: in expansion of macro ‘hweight64’
     return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                                            ^
   In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/cpumask.h:4:0,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/msr.h:10,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/processor.h:20,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/thread_info.h:22,
                    from include/linux/thread_info.h:54,
                    from include/linux/preempt.h:9,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:5,
                    from include/uapi/linux/timex.h:56,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:17,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-usermap.c:15:
   include/linux/cpumask.h: In function ‘cpumask_parse’:
   include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
     int len = nl ? nl - buf : strlen(buf);
                             ^
   In file included from include/uapi/linux/stddef.h:1:0,
                    from include/linux/stddef.h:4,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi/linux/posix_types.h:4,
                    from include/uapi/linux/types.h:13,
                    from include/linux/types.h:5,
                    from include/uapi/linux/capability.h:16,
                    from include/linux/capability.h:15,
                    from include/linux/sched.h:13,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-usermap.c:15:
   /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h: In function ‘copy_from_user’:
   /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h:62:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if (likely(sz == -1 || sz >= n))
                               ^
   include/linux/compiler.h:152:40: note: in definition of macro ‘likely’
    # define likely(x) __builtin_expect(!!(x), 1)
                                           ^
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-usermap.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-11-lowlatency/scripts/recordmcount  "/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-usermap.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/.nv-vm.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-11-lowlatency/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-
   red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DNV_MODULE_INSTANCE=0 -DNV_BUILD_MODULE_INSTANCES=0 -UDEBUG -U_DEBUG -DNDEBUG -I/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"331.17\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -DNV_UVM_ENABLE -D__linux__ -DNV_DEV_NAME=\"nvidia\"  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_vm)"  -D
   "KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/.tmp_nv-vm.o /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-vm.c
   In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/bitops.h:514:0,
                    from include/linux/bitops.h:22,
                    from include/linux/kernel.h:10,
                    from include/linux/sched.h:15,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-vm.c:14:
   include/linux/bitops.h: In function ‘hweight_long’:
   include/asm-generic/bitops/const_hweight.h:27:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
    #define hweight64(w) (__builtin_constant_p(w) ? __const_hweight64(w) : __arch_hweight64(w))
                                                                         ^
   include/linux/bitops.h:66:41: note: in expansion of macro ‘hweight64’
     return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                                            ^
   In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/cpumask.h:4:0,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/msr.h:10,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/processor.h:20,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/thread_info.h:22,
                    from include/linux/thread_info.h:54,
                    from include/linux/preempt.h:9,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:5,
                    from include/uapi/linux/timex.h:56,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:17,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-vm.c:14:
   include/linux/cpumask.h: In function ‘cpumask_parse’:
   include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
     int len = nl ? nl - buf : strlen(buf);
                             ^
   In file included from include/uapi/linux/stddef.h:1:0,
                    from include/linux/stddef.h:4,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi/linux/posix_types.h:4,
                    from include/uapi/linux/types.h:13,
                    from include/linux/types.h:5,
                    from include/uapi/linux/capability.h:16,
                    from include/linux/capability.h:15,
                    from include/linux/sched.h:13,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-vm.c:14:
   /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h: In function ‘copy_from_user’:
   /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h:62:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if (likely(sz == -1 || sz >= n))
                               ^
   include/linux/compiler.h:152:40: note: in definition of macro ‘likely’
    # define likely(x) __builtin_expect(!!(x), 1)
                                           ^
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-vm.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-11-lowlatency/scripts/recordmcount  "/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-vm.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/.nv-vtophys.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-11-lowlatency/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -mfentry -DCC_
   USING_FENTRY -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DNV_MODULE_INSTANCE=0 -DNV_BUILD_MODULE_INSTANCES=0 -UDEBUG -U_DEBUG -DNDEBUG -I/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"331.17\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -DNV_UVM_ENABLE -D__linux__ -DNV_DEV_NAME=\"nvidia\"  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_vtophys)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/.tmp_nv-vtophys.o /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-vtophys.c
   In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/bitops.h:514:0,
                    from include/linux/bitops.h:22,
                    from include/linux/kernel.h:10,
                    from include/linux/sched.h:15,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-vtophys.c:15:
   include/linux/bitops.h: In function ‘hweight_long’:
   include/asm-generic/bitops/const_hweight.h:27:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
    #define hweight64(w) (__builtin_constant_p(w) ? __const_hweight64(w) : __arch_hweight64(w))
                                                                         ^
   include/linux/bitops.h:66:41: note: in expansion of macro ‘hweight64’
     return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                                            ^
   In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/cpumask.h:4:0,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/msr.h:10,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/processor.h:20,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/thread_info.h:22,
                    from include/linux/thread_info.h:54,
                    from include/linux/preempt.h:9,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:5,
                    from include/uapi/linux/timex.h:56,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:17,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-vtophys.c:15:
   include/linux/cpumask.h: In function ‘cpumask_parse’:
   include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
     int len = nl ? nl - buf : strlen(buf);
                             ^
   In file included from include/uapi/linux/stddef.h:1:0,
                    from include/linux/stddef.h:4,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi/linux/posix_types.h:4,
                    from include/uapi/linux/types.h:13,
                    from include/linux/types.h:5,
                    from include/uapi/linux/capability.h:16,
                    from include/linux/capability.h:15,
                    from include/linux/sched.h:13,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-vtophys.c:15:
   /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h: In function ‘copy_from_user’:
   /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h:62:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if (likely(sz == -1 || sz >= n))
                               ^
   include/linux/compiler.h:152:40: note: in definition of macro ‘likely’
    # define likely(x) __builtin_expect(!!(x), 1)
                                           ^
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-vtophys.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-11-lowlatency/scripts/recordmcount  "/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-vtophys.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/.os-interface.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-11-lowlatency/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declarat
   ion -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DNV_MODULE_INSTANCE=0 -DNV_BUILD_MODULE_INSTANCES=0 -UDEBUG -U_DEBUG -DNDEBUG -I/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"331.17\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -D
   NV_UVM_ENABLE -D__linux__ -DNV_DEV_NAME=\"nvidia\"  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_interface)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/.tmp_os-interface.o /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/os-interface.c
   In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/bitops.h:514:0,
                    from include/linux/bitops.h:22,
                    from include/linux/kernel.h:10,
                    from include/linux/sched.h:15,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/os-interface.c:15:
   include/linux/bitops.h: In function ‘hweight_long’:
   include/asm-generic/bitops/const_hweight.h:27:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
    #define hweight64(w) (__builtin_constant_p(w) ? __const_hweight64(w) : __arch_hweight64(w))
                                                                         ^
   include/linux/bitops.h:66:41: note: in expansion of macro ‘hweight64’
     return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                                            ^
   In file included from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/cpumask.h:4:0,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/msr.h:10,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/processor.h:20,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/thread_info.h:22,
                    from include/linux/thread_info.h:54,
                    from include/linux/preempt.h:9,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:5,
                    from include/uapi/linux/timex.h:56,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:17,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/os-interface.c:15:
   include/linux/cpumask.h: In function ‘cpumask_parse’:
   include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
     int len = nl ? nl - buf : strlen(buf);
                             ^
   In file included from include/uapi/linux/stddef.h:1:0,
                    from include/linux/stddef.h:4,
                    from /usr/src/linux-headers-3.11.0-11-lowlatency/include/uapi/linux/posix_types.h:4,
                    from include/uapi/linux/types.h:13,
                    from include/linux/types.h:5,
                    from include/uapi/linux/capability.h:16,
                    from include/linux/capability.h:15,
                    from include/linux/sched.h:13,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:44,
                    from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/os-interface.c:15:
   /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h: In function ‘copy_from_user’:
   /usr/src/linux-headers-3.11.0-11-lowlatency/arch/x86/include/asm/uaccess_64.h:62:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if (likely(sz == -1 || sz >= n))
                               ^
   include/linux/compiler.h:152:40: note: in definition of macro ‘likely’
    # define likely(x) __builtin_expect(!!(x), 1)
                                           ^
   In file included from /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/os-interface.c:15:0:
   /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/os-interface.c: In function ‘os_get_system_memory_size’:
   /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:959:41: error: ‘num_physpages’ undeclared (first use in this function)
    #define NV_NUM_PHYSPAGES                num_physpages
                                            ^
   /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/os-interface.c:244:21: note: in expansion of macro ‘NV_NUM_PHYSPAGES’
        return (((NvU64)NV_NUM_PHYSPAGES * PAGE_SIZE) / RM_PAGE_SIZE);
                        ^
   /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/nv-linux.h:959:41: note: each undeclared identifier is reported only once for each function it appears in
    #define NV_NUM_PHYSPAGES                num_physpages
                                            ^
   /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/os-interface.c:244:21: note: in expansion of macro ‘NV_NUM_PHYSPAGES’
        return (((NvU64)NV_NUM_PHYSPAGES * PAGE_SIZE) / RM_PAGE_SIZE);
                        ^
   /tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/os-interface.c:245:1: warning: control reaches end of non-void function [-Wreturn-type]
    }
    ^
   make[2]: *** [/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel/os-interface.o] Error 1
   make[1]: *** [_module_/tmp/selfgz2758/NVIDIA-Linux-x86_64-331.17/kernel] Error 2
   make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-11-lowlatency'
   NVIDIA: left KBUILD.
    nvidia.ko failed to build!
   make: *** [nvidia.ko] Error 1
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
-> done.
ERROR: Installation has failed.  Please see the file '/var/log/nvidia-installer.log' for details.  You may find suggestions on fixing installation problems in the README available on the Linux driver download page at www.nvidia.com.
```

---

### Post by psy-man on 2013-10-30
Alls well. fixed it with synaptic. 
replaced nvidia-current 304.88
with packages for 319.60
and rebooted. No need to run the installer from nvidia.

---

