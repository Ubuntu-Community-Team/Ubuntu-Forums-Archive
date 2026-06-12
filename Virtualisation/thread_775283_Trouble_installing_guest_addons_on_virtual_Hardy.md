---
title: "Trouble installing guest addons on virtual Hardy"
date: 2008-04-30
forum: Virtualisation
---

### Post by Lord Xeb on 2008-04-30
I really don't understand the install log.

```
Installing VirtualBox 1.5.0 Guest Additions, built Fri Aug 31 14:57:14 CEST 2007

Testing the setup of the guest system

Building a test kernel module...

make KBUILD_VERBOSE=1 -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/tmp/selfgz5495/module/test SRCROOT=/tmp/selfgz5495/module/test modules
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /tmp/selfgz5495/module/test/.tmp_versions ; rm -f /tmp/selfgz5495/module/test/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/selfgz5495/module/test
  gcc -m32 -Wp,-MD,/tmp/selfgz5495/module/test/.test.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -I/lib/modules/2.6.24-16-generic/build/include  -I/tmp/selfgz5495/module/test/ -I/tmp/selfgz5495/module/test/include -I/tmp/selfgz5495/module/test/r0drv/linux -D__KERNEL__ -DMODULE -D__LINUX__ -DIN_RING0 -D_X86_ -DIN_RT_R0 -DIN_SUP_R0 -DVBGL_VBOXGUEST -DVBGL_HGCM -DVBOX_HGCM   -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(test)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxadd_test)" -c -o /tmp/selfgz5495/module/test/.tmp_test.o /tmp/selfgz5495/module/test/test.c
  ld -m elf_i386 -m elf_i386   -r -o /tmp/selfgz5495/module/test/vboxadd_test.o /tmp/selfgz5495/module/test/test.o
  Building modules, stage 2.
make -f /usr/src/linux-headers-2.6.24-16-generic/scripts/Makefile.modpost
  scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.24-16-generic/Module.symvers -I /tmp/selfgz5495/module/test/Module.symvers -o /tmp/selfgz5495/module/test/Module.symvers -w -s
  gcc -m32 -Wp,-MD,/tmp/selfgz5495/module/test/.vboxadd_test.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign    -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(vboxadd_test.mod)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxadd_test)" -DMODULE -c -o /tmp/selfgz5495/module/test/vboxadd_test.mod.o /tmp/selfgz5495/module/test/vboxadd_test.mod.c
  ld -m elf_i386 -r -m elf_i386  --build-id -o /tmp/selfgz5495/module/test/vboxadd_test.ko /tmp/selfgz5495/module/test/vboxadd_test.o /tmp/selfgz5495/module/test/vboxadd_test.mod.o
Inserting the test module module/test/vboxadd_test.ko into the kernel.

Building the VirtualBox Guest Additions kernel module.

make KBUILD_VERBOSE=1 -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/tmp/vbox.0 SRCROOT=/tmp/vbox.0 modules
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /tmp/vbox.0/.tmp_versions ; rm -f /tmp/vbox.0/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/vbox.0
  gcc -m32 -Wp,-MD,/tmp/vbox.0/.cmc.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -I/lib/modules/2.6.24-16-generic/build/include  -I/tmp/vbox.0/ -I/tmp/vbox.0/include -I/tmp/vbox.0/r0drv/linux -D__KERNEL__ -DMODULE -DRT_OS_LINUX -DIN_RING0 -D_X86_ -DIN_RT_R0 -DIN_SUP_R0 -DVBGL_VBOXGUEST -DVBOX_HGCM -DLOG_TO_BACKDOOR   -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(cmc)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxadd)" -c -o /tmp/vbox.0/.tmp_cmc.o /tmp/vbox.0/cmc.c
In file included from /tmp/vbox.0/include/iprt/types.h:72,
                 from /tmp/vbox.0/r0drv/linux/the-linux-kernel.h:25,
                 from /tmp/vbox.0/cmc.c:17:
include/linux/types.h:40: error: redefinition of typedef ‘uintptr_t’
/tmp/vbox.0/include/iprt/stdint.h:118: error: previous declaration of ‘uintptr_t’ was here
In file included from include/linux/thread_info.h:33,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:49,
                 from /tmp/vbox.0/r0drv/linux/the-linux-kernel.h:53,
                 from /tmp/vbox.0/cmc.c:17:
include/linux/bitops.h:6:1: warning: "BIT" redefined
In file included from /tmp/vbox.0/include/iprt/types.h:20,
                 from /tmp/vbox.0/r0drv/linux/the-linux-kernel.h:25,
                 from /tmp/vbox.0/cmc.c:17:
/tmp/vbox.0/include/iprt/cdefs.h:1019:1: warning: this is the location of the previous definition
make[2]: *** [/tmp/vbox.0/cmc.o] Error 1
make[1]: *** [_module_/tmp/vbox.0] Error 2
make: *** [vboxadd] Error 2
```

what can you make of this. I know it says that kernal validation is wrong, but what does it mean? How do I fix it?


:confused:

---

### Post by _angel__ on 2008-04-30
The version you tried to installed was 1.5.0, Maybe you can try the latest verion 1.5.6. I don't think the older versions support the new linux kernels.(if you're using hardy).

---

