---
title: "Repairing vbox after Hardy upgrade"
date: 2008-05-25
forum: Virtualisation
---

### Post by lingenfr on 2008-05-25
The upgrade to hardy hosed all of my virtualbox installs. Rerunning the setup fixed all but one of them. One pc with kubuntu 8.04 and virtualbox installed (w/ usb working) will not start. I get the error message telling me to run setup. I run setup and get an error and it tells me to read the log. I read the log and it says the following:
---------------------------------------------------------------------------
make KBUILD_VERBOSE=1 -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/tmp/vbox.3 SRCROOT=/tmp/vbox.3 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (            \
        echo;                                                           \
        echo "  ERROR: Kernel configuration is invalid.";               \
        echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";      \
        echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";  \
        echo;                                                           \
        /bin/false)
mkdir -p /tmp/vbox.3/.tmp_versions ; rm -f /tmp/vbox.3/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/vbox.3
  gcc -m32 -Wp,-MD,/tmp/vbox.3/linux/.SUPDrv-linux.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wa
ll -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mprefe
rred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -Iinclude/asm-x86/mach-default -fomit-
frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -I/lib/modules/2.6.24-16-generic/build/include  -I/tmp/vbox.3/ -I/tmp/vbox.3/include -I/tm
p/vbox.3/r0drv/linux -D__KERNEL__ -DMODULE -DRT_OS_LINUX -DIN_RING0 -DIN_RT_R0 -DIN_SUP_R0 -DCONFIG_VBOXDRV_AS_MISC -DRT_ARCH_X86 -DVBOX_WITHOUT_IDT_PATCHING -DUSE_NEW_OS_INTERFAC
E_FOR_MM   -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(SUPDrv_linux)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxdrv)" -c -o /tmp/vbox.3/linux/.tmp_SUPDrv-linux.o /tmp/vbox
.3/linux/SUPDrv-linux.c
In file included from /tmp/vbox.3/include/iprt/types.h:72,
                 from /tmp/vbox.3/include/VBox/types.h:21,
                 from /tmp/vbox.3/SUPDRV.h:26,
                 from /tmp/vbox.3/linux/SUPDrv-linux.c:22:
include/linux/types.h:40: error: redefinition of typedef ‘uintptr_t’
/tmp/vbox.3/include/iprt/stdint.h:118: error: previous declaration of ‘uintptr_t’ was here
In file included from include/linux/thread_info.h:33,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:49,
                 from /tmp/vbox.3/SUPDRV.h:87,
                 from /tmp/vbox.3/linux/SUPDrv-linux.c:22:
include/linux/bitops.h:6:1: warning: "BIT" redefined
In file included from /tmp/vbox.3/include/VBox/cdefs.h:20,
                 from /tmp/vbox.3/SUPDRV.h:25,
                 from /tmp/vbox.3/linux/SUPDrv-linux.c:22:
/tmp/vbox.3/include/iprt/cdefs.h:1042:1: warning: this is the location of the previous definition
make[2]: *** [/tmp/vbox.3/linux/SUPDrv-linux.o] Error 1
make[1]: *** [_module_/tmp/vbox.3] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vboxdrv] Error 2
---------------------------------------------------------------------------

Can I fix this? Thanks.

---

