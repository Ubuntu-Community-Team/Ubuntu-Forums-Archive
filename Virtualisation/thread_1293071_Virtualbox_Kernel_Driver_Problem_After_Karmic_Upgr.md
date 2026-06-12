---
title: "Virtualbox Kernel Driver Problem After Karmic Upgrade"
date: 2009-10-16
forum: Virtualisation
---

### Post by netwarriorwy on 2009-10-16
Hi Folks!

I've just upgraded my HP Pavilion laptop from Jaunty to Karmic and now when I wanted to open my virtual machine with Win XP in it I found this error message:

> 
Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

That command did't work for me

This was the result:

> sudo /etc/init.d/vboxdrv setup
[sudo] password for netwarrior: 
 * Stopping VirtualBox kernel module                                             *  done.
 * Removing old VirtualBox kernel module                                         *  done.
 * Recompiling VirtualBox kernel module                                         
 * Look at /var/log/vbox-install.log to find out what went wrong



This is what I've found in that file:
Sorry because this is long.

> Attempting to install using DKMS
  removing old DKMS module vboxdrv version  2.2.4

-------- Uninstall Beginning --------
Module:  vboxdrv
Version: 2.2.4
Kernel:  2.6.31-14-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.31-14-generic/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod.............

DKMS: uninstall Completed.

------------------------------
Deleting module version: 2.2.4
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/2.2.4/source ->
                 /usr/src/vboxdrv-2.2.4

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
su nobody -c "make KERNELRELEASE=2.6.31-14-generic -C /lib/modules/2.6.31-14-generic/build M=/var/lib/dkms/vboxdrv/2.2.4/build"..........

Running the post_build script:
cleaning build area....

DKMS: build Completed.

vboxdrv.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.31-14-generic/updates/dkms/

depmod....

DKMS: install Completed.
Attempting to install using DKMS
  removing old DKMS module vboxnetflt version  2.2.4

------------------------------
Deleting module version: 2.2.4
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxnetflt/2.2.4/source ->
                 /usr/src/vboxnetflt-2.2.4

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Running the pre_build script:

Building module:
cleaning build area....
su nobody -c "make KERNELRELEASE=2.6.31-14-generic -C /lib/modules/2.6.31-14-generic/build M=/var/lib/dkms/vboxnetflt/2.2.4/build"....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.31-14-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/vboxnetflt/2.2.4/build/ for more information.
0
0
Failed to install using DKMS, attempting to install without
make KBUILD_VERBOSE=1 -C /lib/modules/2.6.31-14-generic/build SUBDIRS=/tmp/vbox.0 SRCROOT=/tmp/vbox.0 modules
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /tmp/vbox.0/.tmp_versions ; rm -f /tmp/vbox.0/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/vbox.0
  gcc -Wp,-MD,/tmp/vbox.0/linux/.VBoxNetFlt-linux.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.1/include  -Iinclude  -I/usr/src/linux-headers-2.6.31-14-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -fstack-protector -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -I/lib/modules/2.6.31-14-generic/build/include -I/tmp/vbox.0/ -I/tmp/vbox.0/include -I/tmp/vbox.0/r0drv/linux -D__KERNEL__ -DMODULE -DRT_OS_LINUX -DIN_RING0 -DIN_RT_R0 -DIN_SUP_R0 -DVBOX -DRT_WITH_VBOX -DVBOX_WITH_HARDENING -DRT_ARCH_X86 -DVBOX_WITH_64_BITS_GUESTS  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(VBoxNetFlt_linux)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxnetflt)"  -c -o /tmp/vbox.0/linux/.tmp_VBoxNetFlt-linux.o /tmp/vbox.0/linux/VBoxNetFlt-linux.c
In file included from /tmp/vbox.0/include/VBox/intnet.h:34,
                 from /tmp/vbox.0/linux/../VBoxNetFltInternal.h:26,
                 from /tmp/vbox.0/linux/VBoxNetFlt-linux.c:47:
/tmp/vbox.0/include/VBox/stam.h:69:7: warning: "_MSC_VER" is not defined
/tmp/vbox.0/linux/VBoxNetFlt-linux.c: In function ‘vboxNetAdpNetDevInit’:
/tmp/vbox.0/linux/VBoxNetFlt-linux.c:225: error: ‘struct net_device’ has no member named ‘open’
/tmp/vbox.0/linux/VBoxNetFlt-linux.c:226: error: ‘struct net_device’ has no member named ‘stop’
/tmp/vbox.0/linux/VBoxNetFlt-linux.c:227: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/tmp/vbox.0/linux/VBoxNetFlt-linux.c:228: error: ‘struct net_device’ has no member named ‘get_stats’
make[2]: *** [/tmp/vbox.0/linux/VBoxNetFlt-linux.o] Error 1
make[1]: *** [_module_/tmp/vbox.0] Error 2
make: *** [vboxnetflt] Error 2


By the way I went to Manage Users and Groups and I've found out that now I don't have any group at all except for root and my user :S .The other ones are gone.

I hope somebody can help me.

---

### Post by Brandel Valico on 2009-10-16
Try running the command given with sudo in front of it and see if that helps.

---

### Post by netwarriorwy on 2009-10-16
OOps I forgot to mention that i did run the command the way you're suggesting me. And thats how it tells me to look in that files output.

---

### Post by cmwslw on 2009-10-23
[http://www.virtualbox.org/ticket/4264](http://www.virtualbox.org/ticket/4264)

---

### Post by arpidez on 2009-11-09
Well this is a mess
In ubuntu 9.04, virtualbox 2.2.4 works fine
Recently i upgrade to 9.10 and my vbox was 2.2.4 and when i try to run it, crash totally.
i tried with
sudo apt-get install dkms
sudo /etc/init.d/vboxdrv setup

and nothing, i realize some problems with both comands (unsolved) 

Then i install the new version of Vbox the 3.0.1 one, and tried the same thing

sudo apt-get install dkms
sudo /etc/init.d/vboxdrv setup

and dkms was installed good, and vboxdrv compile fine BUT still not working :(

the virtualbox screen says

windows(aborted)

when i try to run it, just nothing happend

someone have a magical solution

please

---

### Post by therottenbanana on 2009-12-20
Had the same problem, solution was to uninstall  virtualbox and install the latest version (3.0).

Hope this helps.

---

