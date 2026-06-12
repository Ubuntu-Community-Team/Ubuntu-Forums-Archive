---
title: "Linux 4.15.0-99-generic with Ubuntu18.04 and VirtualBox"
date: 2020-04-30
forum: Virtualisation
---

### Post by alundgren93 on 2020-04-30
Hi all,


I'm experiencing some issues when using VirtualBox with Ubuntu 18.04 and Linux 4.15.0-99-generic kernel as Host. When trying to start my Windows guest I get prompted with the following error:

```
The VirtualBox Linux kernel driver is either not loaded or not set up correctly. Please try setting it up again by executing


'/sbin/vboxconfig'


as root.


If your system has EFI Secure Boot enabled you may also need to sign the kernel modules (vboxdrv, vboxnetflt, vboxnetadp, vboxpci) before you can load them. Please see your Linux system's documentation for more information.


where: suplibOsInit what: 3 VERR_VM_DRIVER_NOT_INSTALLED (-1908) - The support driver is not installed. On linux, open returned ENOENT.
```

I have secure boot disabled and executing '/sbin/vboxconfig' fails with the following logs:

```
Building the main VirtualBox module.
Error building the module:
make V=1 CONFIG_MODULE_SIG= CONFIG_MODULE_SIG_ALL= -C /lib/modules/4.15.0-99-generic/build M=/tmp/vbox.0 SRCROOT=/tmp/vbox.0 -j8 modules
make[1]: warning: -jN forced in submake: disabling jobserver mode.
/opt/gcc-9.2.1/libexec/gcc/x86_64-pc-linux-gnu/9.2.1/cc1: error while loading shared libraries: libisl.so.21: cannot open shared object file: No such file or directory
/opt/gcc-9.2.1/libexec/gcc/x86_64-pc-linux-gnu/9.2.1/cc1: error while loading shared libraries: libisl.so.21: cannot open shared object file: No such file or directory
mkdir -p /tmp/vbox.0/.tmp_versions ; rm -f /tmp/vbox.0/.tmp_versions/*
make -f ./scripts/Makefile.build obj=/tmp/vbox.0
  gcc -Wp,-MD,/tmp/vbox.0/linux/.SUPDrv-linux.o.d  -nostdinc -isystem /opt/gcc-9.2.1/lib/gcc/x86_64-pc-linux-gnu/9.2.1/include  -I./arch/x86/include -I./arch/x86/include/generated  -I./include -I./arch/x86/includ$
  gcc -Wp,-MD,/tmp/vbox.0/.SUPDrv.o.d  -nostdinc -isystem /opt/gcc-9.2.1/lib/gcc/x86_64-pc-linux-gnu/9.2.1/include  -I./arch/x86/include -I./arch/x86/include/generated  -I./include -I./arch/x86/include/uapi -I./a$
  gcc -Wp,-MD,/tmp/vbox.0/.SUPDrvGip.o.d  -nostdinc -isystem /opt/gcc-9.2.1/lib/gcc/x86_64-pc-linux-gnu/9.2.1/include  -I./arch/x86/include -I./arch/x86/include/generated  -I./include -I./arch/x86/include/uapi -I$
/opt/gcc-9.2.1/libexec/gcc/x86_64-pc-linux-gnu/9.2.1/cc1: error while loading shared libraries: libisl.so.21: cannot open shared object file: No such file or directory
  gcc -Wp,-MD,/tmp/vbox.0/.SUPDrvSem.o.d  -nostdinc -isystem /opt/gcc-9.2.1/lib/gcc/x86_64-pc-linux-gnu/9.2.1/include  -I./arch/x86/include -I./arch/x86/include/generated  -I./include -I./arch/x86/include/uapi -I$
/opt/gcc-9.2.1/libexec/gcc/x86_64-pc-linux-gnu/9.2.1/cc1: error while loading shared libraries: libisl.so.21: cannot open shared object file: No such file or directory
  gcc -Wp,-MD,/tmp/vbox.0/.SUPLibAll.o.d  -nostdinc -isystem /opt/gcc-9.2.1/lib/gcc/x86_64-pc-linux-gnu/9.2.1/include  -I./arch/x86/include -I./arch/x86/include/generated  -I./include -I./arch/x86/include/uapi -I$
/opt/gcc-9.2.1/libexec/gcc/x86_64-pc-linux-gnu/9.2.1/cc1: error while loading shared libraries: libisl.so.21: cannot open shared object file: No such file or directory
  gcc -Wp,-MD,/tmp/vbox.0/.SUPDrvTracer.o.d  -nostdinc -isystem /opt/gcc-9.2.1/lib/gcc/x86_64-pc-linux-gnu/9.2.1/include  -I./arch/x86/include -I./arch/x86/include/generated  -I./include -I./arch/x86/include/uapi$
/opt/gcc-9.2.1/libexec/gcc/x86_64-pc-linux-gnu/9.2.1/cc1: error while loading shared libraries: libisl.so.21: cannot open shared object file: No such file or directory
  gcc -Wp,-MD,/tmp/vbox.0/r0drv/.alloc-r0drv.o.d  -nostdinc -isystem /opt/gcc-9.2.1/lib/gcc/x86_64-pc-linux-gnu/9.2.1/include  -I./arch/x86/include -I./arch/x86/include/generated  -I./include -I./arch/x86/include$
scripts/Makefile.build:330: recipe for target '/tmp/vbox.0/linux/SUPDrv-linux.o' failed
make[2]: *** [/tmp/vbox.0/linux/SUPDrv-linux.o] Error 1
make[2]: *** Waiting for unfinished jobs....
scripts/Makefile.build:330: recipe for target '/tmp/vbox.0/SUPDrv.o' failed
make[2]: *** [/tmp/vbox.0/SUPDrv.o] Error 1
  gcc -Wp,-MD,/tmp/vbox.0/r0drv/.initterm-r0drv.o.d  -nostdinc -isystem /opt/gcc-9.2.1/lib/gcc/x86_64-pc-linux-gnu/9.2.1/include  -I./arch/x86/include -I./arch/x86/include/generated  -I./include -I./arch/x86/incl$
/opt/gcc-9.2.1/libexec/gcc/x86_64-pc-linux-gnu/9.2.1/cc1: error while loading shared libraries: libisl.so.21: cannot open shared object file: No such file or directory
/opt/gcc-9.2.1/libexec/gcc/x86_64-pc-linux-gnu/9.2.1/cc1: error while loading shared libraries: libisl.so.21: cannot open shared object file: No such file or directory
/opt/gcc-9.2.1/libexec/gcc/x86_64-pc-linux-gnu/9.2.1/cc1: error while loading shared libraries: libisl.so.21: cannot open shared object file: No such file or directory
scripts/Makefile.build:330: recipe for target '/tmp/vbox.0/SUPDrvSem.o' failed
make[2]: *** [/tmp/vbox.0/SUPDrvSem.o] Error 1
scripts/Makefile.build:330: recipe for target '/tmp/vbox.0/SUPDrvGip.o' failed
make[2]: *** [/tmp/vbox.0/SUPDrvGip.o] Error 1
/opt/gcc-9.2.1/libexec/gcc/x86_64-pc-linux-gnu/9.2.1/cc1: error while loading shared libraries: libisl.so.21: cannot open shared object file: No such file or directory
scripts/Makefile.build:330: recipe for target '/tmp/vbox.0/SUPDrvTracer.o' failed
make[2]: *** [/tmp/vbox.0/SUPDrvTracer.o] Error 1
scripts/Makefile.build:330: recipe for target '/tmp/vbox.0/SUPLibAll.o' failed
make[2]: *** [/tmp/vbox.0/SUPLibAll.o] Error 1
scripts/Makefile.build:330: recipe for target '/tmp/vbox.0/r0drv/alloc-r0drv.o' failed
make[2]: *** [/tmp/vbox.0/r0drv/alloc-r0drv.o] Error 1
scripts/Makefile.build:330: recipe for target '/tmp/vbox.0/r0drv/initterm-r0drv.o' failed
make[2]: *** [/tmp/vbox.0/r0drv/initterm-r0drv.o] Error 1
Makefile:1577: recipe for target '_module_/tmp/vbox.0' failed
make[1]: *** [_module_/tmp/vbox.0] Error 2
/tmp/vbox.0/Makefile-footer.gmk:114: recipe for target 'vboxdrv' failed
```

I have:
* Reinstalled VirtualBox,
* Tried several different versions of VirtualBox,
* Reinstalled dkms, virtualbox-dkms and headers,
* Tried installing the shared libraries,
* Updated my system.


**All without success.**


Has anyone else experienced this issue? I'm running out of ideas here. This started after I rebooted my system after having it running over several system updates.


Thank you so much for your help!

---

### Post by slickymaster on 2020-04-30
Thread moved to **Virtualisation** for a better fit

---

