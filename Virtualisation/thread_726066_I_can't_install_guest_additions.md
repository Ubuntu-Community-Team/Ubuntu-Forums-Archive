---
title: "I can't install guest additions"
date: 2008-03-16
forum: Virtualisation
---

### Post by patrickaupperle on 2008-03-16
when I tell it to  install guest additions it gives me this:
Screenshot

So I go to /var/log/vboxadd-install.log
I have to post that from the virtual machine

---

### Post by patrickaupperle on 2008-03-16
Here is a copy of that log:
```

Installing VirtualBox 1.5.0 Guest Additions, built Fri Aug 31 14:57:14 CEST 2007

Testing the setup of the guest system

Building a test kernel module...

make KBUILD_VERBOSE=1 -C /lib/modules/2.6.24-12-generic/build SUBDIRS=/tmp/selfgz58833593/module/test SRCROOT=/tmp/selfgz58833593/module/test modules
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /tmp/selfgz58833593/module/test/.tmp_versions ; rm -f /tmp/selfgz58833593/module/test/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/selfgz58833593/module/test
  gcc -m32 -Wp,-MD,/tmp/selfgz58833593/module/test/.test.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -I/lib/modules/2.6.24-12-generic/build/include  -I/tmp/selfgz58833593/module/test/ -I/tmp/selfgz58833593/module/test/include -I/tmp/selfgz58833593/module/test/r0drv/linux -D__KERNEL__ -DMODULE -D__LINUX__ -DIN_RING0 -D_X86_ -DIN_RT_R0 -DIN_SUP_R0 -DVBGL_VBOXGUEST -DVBGL_HGCM -DVBOX_HGCM   -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(test)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxadd_test)" -c -o /tmp/selfgz58833593/module/test/.tmp_test.o /tmp/selfgz58833593/module/test/test.c
  ld -m elf_i386 -m elf_i386   -r -o /tmp/selfgz58833593/module/test/vboxadd_test.o /tmp/selfgz58833593/module/test/test.o
  Building modules, stage 2.
make -f /usr/src/linux-headers-2.6.24-12-generic/scripts/Makefile.modpost
  scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.24-12-generic/Module.symvers -I /tmp/selfgz58833593/module/test/Module.symvers -o /tmp/selfgz58833593/module/test/Module.symvers -w -s
  gcc -m32 -Wp,-MD,/tmp/selfgz58833593/module/test/.vboxadd_test.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign    -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(vboxadd_test.mod)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxadd_test)" -DMODULE -c -o /tmp/selfgz58833593/module/test/vboxadd_test.mod.o /tmp/selfgz58833593/module/test/vboxadd_test.mod.c
  ld -m elf_i386 -r -m elf_i386  --build-id -o /tmp/selfgz58833593/module/test/vboxadd_test.ko /tmp/selfgz58833593/module/test/vboxadd_test.o /tmp/selfgz58833593/module/test/vboxadd_test.mod.o
Inserting the test module module/test/vboxadd_test.ko into the kernel.

Building the VirtualBox Guest Additions kernel module.

make KBUILD_VERBOSE=1 -C /lib/modules/2.6.24-12-generic/build SUBDIRS=/tmp/vbox.1 SRCROOT=/tmp/vbox.1 modules
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /tmp/vbox.1/.tmp_versions ; rm -f /tmp/vbox.1/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/vbox.1
  gcc -m32 -Wp,-MD,/tmp/vbox.1/.cmc.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -I/lib/modules/2.6.24-12-generic/build/include  -I/tmp/vbox.1/ -I/tmp/vbox.1/include -I/tmp/vbox.1/r0drv/linux -D__KERNEL__ -DMODULE -DRT_OS_LINUX -DIN_RING0 -D_X86_ -DIN_RT_R0 -DIN_SUP_R0 -DVBGL_VBOXGUEST -DVBOX_HGCM -DLOG_TO_BACKDOOR   -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(cmc)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxadd)" -c -o /tmp/vbox.1/.tmp_cmc.o /tmp/vbox.1/cmc.c
In file included from /tmp/vbox.1/include/iprt/types.h:72,
                 from /tmp/vbox.1/r0drv/linux/the-linux-kernel.h:25,
                 from /tmp/vbox.1/cmc.c:17:
include/linux/types.h:40: error: redefinition of typedef &#8216;uintptr_t&#8217;
/tmp/vbox.1/include/iprt/stdint.h:118: error: previous declaration of &#8216;uintptr_t&#8217; was here
In file included from include/linux/thread_info.h:33,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:49,
                 from /tmp/vbox.1/r0drv/linux/the-linux-kernel.h:53,
                 from /tmp/vbox.1/cmc.c:17:
include/linux/bitops.h:6:1: warning: "BIT" redefined
In file included from /tmp/vbox.1/include/iprt/types.h:20,
                 from /tmp/vbox.1/r0drv/linux/the-linux-kernel.h:25,
                 from /tmp/vbox.1/cmc.c:17:
/tmp/vbox.1/include/iprt/cdefs.h:1019:1: warning: this is the location of the previous definition
make[2]: *** [/tmp/vbox.1/cmc.o] Error 1
make[1]: *** [_module_/tmp/vbox.1] Error 2
make: *** [vboxadd] Error 2

```

Also included is the log file. I did a save as and changed it to txt so it would be accepted

---

### Post by patrickaupperle on 2008-03-16
Oh, I forgot to mention that the guest OS is Kubuntu 8.04 Hardy KDE 4 with all updates.

---

### Post by patrickaupperle on 2008-03-16
How would anyone even start to troubleshoot? If someone could just start me off, I might be able to come up with a few ideas myself.

---

### Post by patrickaupperle on 2008-03-17
bump

---

### Post by ripperzane on 2008-03-30
Did you try
sudo apt-get install linux-headers-generic
if you are using server, virtual, xen or etc at the time of boot for your running kernel, substitute "generic" for the appropriate kernel.
Hope this helps.
> **patrickaupperle said:**
> bump

---

### Post by patrickaupperle on 2008-03-31
I tried it, but unfortunately it still gave the same error message. Any other ideas?

---

### Post by patrickaupperle on 2008-03-31
I tried installing build-essential. The install of build-essential went well, but did not help.

---

### Post by patrickaupperle on 2008-04-04
Bump

---

### Post by greybirds on 2008-04-07
I had the same problem, using VirtualBox 1.5.0 from the repository and I could not get to the root of the problem.

I solved it by uninstalling VirtualBox and the VB module, installing the version from [http://www.virtualbox.org/download/1.5.6/](http://www.virtualbox.org/download/1.5.6/) and it worked perfectly. 

I assume it is/was an obscure bug. 

Hope this works for you, too. It's an annoying problem.

---

### Post by patrickaupperle on 2008-04-09
> **greybirds said:**
> I had the same problem, using VirtualBox 1.5.0 from the repository and I could not get to the root of the problem.

I solved it by uninstalling VirtualBox and the VB module, installing the version from [http://www.virtualbox.org/download/1.5.6/](http://www.virtualbox.org/download/1.5.6/) and it worked perfectly. 

I assume it is/was an obscure bug. 

Hope this works for you, too. It's an annoying problem.

This won't screw anything up will it?

---

### Post by animefan82 on 2008-05-31
> **patrickaupperle said:**
> This won't screw anything up will it?

**The world as you know it will most probably end**, *which in short means you'll learn something new.*

---

### Post by bradmkjr on 2008-05-31
It may be overkill, but pretty sure it will do any compiling you will need:

apt-get install linux-headers-`uname -r` build-essential

apt-get install gcc binutils-doc cpp-doc make manpages-dev autoconf automake1.9 libtool flex bison gdb libc6-dev-amd64 lib64gcc1

copied from: [http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server)

Good Luck,
Bradford Knowlton
[http://x86Virtualization.com/](http://x86Virtualization.com/)

---

