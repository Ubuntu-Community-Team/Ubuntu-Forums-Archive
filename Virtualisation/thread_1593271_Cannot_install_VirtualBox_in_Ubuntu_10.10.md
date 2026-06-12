---
title: "Cannot install VirtualBox in Ubuntu 10.10"
date: 2010-10-11
forum: Virtualisation
---

### Post by irfad on 2010-10-11
I have downloaded and tried to install VirtualBox .deb file. it opens in  Ubuntu software center and afte proceed installation it shows me an  error "An unhandlable error occured, 
There seems to be a programming  error in aptdaemon, the software that allows you to install/remove  software and to perform other package management related tasks. Please  report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry." 

Please help me. :(

---

### Post by irfad on 2010-10-11
bump

---

### Post by empty_spaces on 2010-10-12
Where did you download the virtualbox deb?
Are you trying to install the OSE version or PUEL version?
Rather than download deb files, I would suggest installing it through the repos.

See this link for the PUEL version
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by zuerston on 2010-10-12
Yes use apt-get to install that.
Its also in Synaptic but I haven't used that for VB

---

### Post by irfad on 2010-10-13
> **empty_spaces said:**
> Where did you download the virtualbox deb?
Are you trying to install the OSE version or PUEL version?
Rather than download deb files, I would suggest installing it through the repos.

See this link for the PUEL version
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Ya i donwloaded the latest version. no the OSE. but cannot install it. tried dpkg in command line also.

---

### Post by ysNoi on 2010-10-15
Hi irfad...

Have you tried installing VBox on Synaptic?

How about using OSE?

---

### Post by denfio on 2010-10-18
i've upgraded to ubuntu 10.10 maverick and now virtual box will not work.

Attempting to install using DKMS
  removing old DKMS module vboxdrv version  3.1.2

------------------------------
Deleting module version: 3.1.2
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/3.1.2/source ->
                 /usr/src/vboxdrv-3.1.2

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.35-22-generic -C /lib/modules/2.6.35-22-generic/build M=/var/lib/dkms/vboxdrv/3.1.2/build....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.35-22-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/vboxdrv/3.1.2/build/ for more information.
0
0
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module>
    report.write(open(apport.fileutils.make_report_path(report), 'w'))
IOError: [Errno 2] No such file or directory: '/var/crash/virtualbox-3.1.0.crash'
Failed to install using DKMS, attempting to install without
make KBUILD_VERBOSE=1 -C /lib/modules/2.6.35-22-generic/build SUBDIRS=/tmp/vbox.0 SRCROOT=/tmp/vbox.0 modules
test -e include/generated/autoconf.h -a -e include/config/auto.conf || (        \
    echo;                                \
    echo "  ERROR: Kernel configuration is invalid.";        \
    echo "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
    echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";    \
    echo;                                \
    /bin/false)
mkdir -p /tmp/vbox.0/.tmp_versions ; rm -f /tmp/vbox.0/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/vbox.0
  gcc -Wp,-MD,/tmp/vbox.0/linux/.SUPDrv-linux.o.d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.4.5/include  -I/usr/src/linux-headers-2.6.35-22-generic/arch/x86/include -Iinclude  -include include/generated/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -I/lib/modules/2.6.35-22-generic/build/include -I/tmp/vbox.0/ -I/tmp/vbox.0/include -I/tmp/vbox.0/r0drv/linux -D__KERNEL__ -DMODULE -DRT_OS_LINUX -DIN_RING0 -DIN_RT_R0 -DIN_SUP_R0 -DVBOX -DRT_WITH_VBOX -DVBOX_WITH_HARDENING -DCONFIG_VBOXDRV_AS_MISC -DRT_ARCH_X86 -DVBOX_WITH_64_BITS_GUESTS  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(SUPDrv_linux)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxdrv)"  -c -o /tmp/vbox.0/linux/.tmp_SUPDrv-linux.o /tmp/vbox.0/linux/SUPDrv-linux.c
In file included from /tmp/vbox.0/include/VBox/types.h:34,
                 from /tmp/vbox.0/linux/../SUPDrvInternal.h:39,
                 from /tmp/vbox.0/linux/SUPDrv-linux.c:37:
/tmp/vbox.0/include/iprt/types.h:100: fatal error: linux/autoconf.h: No such file or directory
compilation terminated.
make[2]: *** [/tmp/vbox.0/linux/SUPDrv-linux.o] Error 1
make[1]: *** [_module_/tmp/vbox.0] Error 2
make: *** [vboxdrv] Error 2

---

### Post by ysNoi on 2010-10-21
How about considering an upgrade or reinstalling of VirtualBox?

---

### Post by MunksterMan2 on 2010-10-22
> **ysNoi said:**
> How about considering an upgrade or reinstalling of VirtualBox?

Thanks.  I had this same problem after updating to maverick.  Upgrading VirtualBox from 3.0 to 3.2.10 solved it.

---

### Post by Darth Penguin on 2010-10-22
It's available in the Ubuntu Software Center and installs an updated version automatically.

---

### Post by ysNoi on 2010-10-22
> **MunksterMan2 said:**
> Thanks.  I had this same problem after updating to maverick. Upgrading VirtualBox from 3.0 to 3.2.10 solved it.

I'm glad you did it..!

You're most welcome... :guitar:

---

