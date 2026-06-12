---
title: "Have a problem with Virtualbox after upgrade to 8.10 RC"
date: 2008-10-27
forum: Virtualisation
---

### Post by diablo75 on 2008-10-27
I just finished upgrading from Ubuntu 8.04 to 8.10 RC.  After opening Virtualbox and attempting to start my XP machine, I get the following error:

> The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).

It says that I need to be a member of the vboxusers group.  Thing is, I already am and have confirmed this.

Before posting here, I attempted to recompile the kernel headers using "sudo /etc/init.d/vboxdrv setup" and this is what I got:

```
zeke@ubuntu:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                             *  done.
 * Removing old VirtualBox kernel module                                         *  done.
 * Recompiling VirtualBox kernel module                                         
 * Look at /var/log/vbox-install.log to find out what went wrong

```

So I looked at the log file (and can't make sense out of it):

> Attempting to install using DKMS
info: No menu item ` removing old DKMS module vboxdrv version ' in node `(dir)Top'.

Error! Invalid number of parameters passed.
Usage: remove -m <module> -v <module-version> --all
   or: remove -m <module> -v <module-version> -k <kernel-version>

------------------------------
Deleting module version: 1.6.2
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/1.6.2/source ->
                 /usr/src/vboxdrv-1.6.2

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.27-7-generic -C /lib/modules/2.6.27-7-generic/build M=/var/lib/dkms/vboxdrv/1.6.2/build....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.27-7-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/vboxdrv/1.6.2/build/ for more information.
0
0
Failed to install using DKMS, attempting to install without
make KBUILD_VERBOSE=1 -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/tmp/vbox.1 SRCROOT=/tmp/vbox.1 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /tmp/vbox.1/.tmp_versions ; rm -f /tmp/vbox.1/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/vbox.1
  gcc -Wp,-MD,/tmp/vbox.1/linux/.SUPDrv-linux.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.27-7-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -I/lib/modules/2.6.27-7-generic/build/include -I/tmp/vbox.1/ -I/tmp/vbox.1/include -I/tmp/vbox.1/r0drv/linux -D__KERNEL__ -DMODULE -DRT_OS_LINUX -DIN_RING0 -DIN_RT_R0 -DIN_SUP_R0 -DVBOX -DRT_WITH_VBOX -DCONFIG_VBOXDRV_AS_MISC -DRT_ARCH_X86 -DUSE_NEW_OS_INTERFACE_FOR_MM -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(SUPDrv_linux)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxdrv)" -c -o /tmp/vbox.1/linux/.tmp_SUPDrv-linux.o /tmp/vbox.1/linux/SUPDrv-linux.c
In file included from /tmp/vbox.1/linux/SUPDrv-linux.c:35:
/tmp/vbox.1/SUPDRV.h:99:30: error: asm/semaphore.h: No such file or directory
/tmp/vbox.1/linux/SUPDrv-linux.c: In function ‘supdrvOSGipResume’:
/tmp/vbox.1/linux/SUPDrv-linux.c:1331: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vbox.1/linux/SUPDrv-linux.o] Error 1
make[1]: *** [_module_/tmp/vbox.1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [vboxdrv] Error 2

What should I do now?

---

### Post by Paresh on 2008-10-28
I have exactly this problem with Virtual Box

the ```
sudo /etc/init.d/vboxdrv setup
``` that used to work with 8.04 kernel upgrades does not work now.

A speedy solution would be greatly appreciated

---

### Post by Paresh on 2008-10-28
I followed instructions here
```
http://www.virtualbox.org/wiki/Linux_Downloads
```

After adding the 'hardy non-free' to sources, downloading the key and registering, run update-manager to download and configure the latest version.

When you start up VirtualBox for the first time, any existing VMs have to be converted to a new format, so make sure you backup.

I haven't fully tested yet, but it's working fine and the upgrade was painless.

---

### Post by diablo75 on 2008-10-29
That did the trick!  Thanks a bunch!  (Although I should mention that all I had to do was add the repository to my sources list, add the key, and then run Update Manager.  I did not have to use the deb package on the download site to upgrade my current installation of Virtualbox).

---

### Post by 080729jk on 2008-10-30
&#32593;&#32476;&#30417;&#21548;&#65306;[**&#24405;&#38899;&#30418;**](http://www.rp-cti.com/Chinese/289.html)&#36890;&#36807;&#32593;&#32476;&#21487;&#20197;&#23454;&#26102;&#30417;&#21548;&#20219;&#24847;&#36890;&#36947;&#30340;&#29366;&#24577;&#21644;&#36890;&#36947;&#30340;&#36890;&#35805;&#12290;&#30041;&#35328;&#26597;&#35810;&#65306;[**&#24405;&#38899;&#20202;**](http://www.rp-cti.com/Chinese/411.html)&#22312;&#25351;&#23450;&#25391;&#38083;&#27425;&#25968;&#26080;&#20154;&#25509;&#21548;&#30005;&#35805;&#26102;&#65292;&#21551;&#21160;&#33258;&#21160;&#30041;&#35328;&#21151;&#33021;&#12290;&#65288;&#21487;&#36873;&#65289;&#23433;&#20840;&#21487;&#38752;&#65306;[**&#30005;&#35805;&#24405;&#38899;&#20202;**](http://www.rp-cti.com/Chinese/411.html)&#20998;&#32423;&#23494;&#30721;&#26435;&#38480;&#31649;&#29702;&#65292;&#36890;&#35805;&#35760;&#24405;&#20445;&#23494;&#24615;&#24378;&#12290;&#24037;&#19994;&#32423;&#39640;&#21487;&#38752;&#24615;&#22120;&#20214;&#12290;[**&#24405;&#38899;&#31649;&#29702;**](http://www.rp-cti.com/Chinese/404.html)&#31995;&#32479;&#20027;&#35201;&#21151;&#33021;&#65306;[**&#35821;&#38899;&#23548;&#33322;&#30418;**](http://www.rp-cti.com/Chinese/201.html)&#25903;&#25345;16&#36335;&#30005;&#35805;&#21516;&#26102;&#24405;&#38899;&#65307;[

---

