---
title: "Can't install guest additions on Lubuntu"
date: 2010-05-15
forum: Virtualisation
---

### Post by arashiko28 on 2010-05-15
I have Ubuntu 10.04 64-bit as my main OS, and I am running Lubuntu 10.04 through VB, when trying to install guest additions I get this error message.

> $ sudo sh ./VBoxLinuxAdditions-x86.run
Verifying archive integrity... All good.
Uncompressing VirtualBox 3.1.6 Guest Additions for Linux.........
VirtualBox Guest Additions installer
Removing installed version of VirtualBox Guest Additions...
tar: Record size = 8 blocks
Building the VirtualBox Guest Additions kernel modules ...fail!
(Your system does not seem to be set up to build kernel modules.
Look at /var/log/vboxadd-install.log to find out what went wrong)
Installing the Window System drivers
Installing experimental X.Org Server 1.7 modules ...done.
Setting up the Window System to use the Guest Additions ...done.
You may need to restart the hal service and the Window System (or just restart
the guest system) to enable the Guest Additions.

Installing graphics libraries and desktop services components ...done.

And at /var/log/vboxadd-install.log:

> make KBUILD_VERBOSE=1 -C /lib/modules/2.6.32-21-generic/build SUBDIRS=/tmp/vbox.0 SRCROOT=/tmp/vbox.0 modules
/usr/src/linux-headers-2.6.32-21-generic/scripts/gcc-version.sh: line 25: gcc: command not found
/usr/src/linux-headers-2.6.32-21-generic/scripts/gcc-version.sh: line 26: gcc: command not found
/usr/src/linux-headers-2.6.32-21-generic/arch/x86/Makefile:81: stack protector enabled but no compiler support
make[1]: gcc: Command not found
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /tmp/vbox.0/.tmp_versions ; rm -f /tmp/vbox.0/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/vbox.0
  gcc -Wp,-MD,/tmp/vbox.0/.test.o.d  -nostdinc -isystem   -Iinclude  -I/usr/src/linux-headers-2.6.32-21-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -msoft-float -mregparm=3 -freg-struct-return -march=i586 -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -I/lib/modules/2.6.32-21-generic/build/include -I/tmp/vbox.0/ -I/tmp/vbox.0/include -I/tmp/vbox.0/r0drv/linux -D__KERNEL__ -DMODULE -DRT_OS_LINUX -DIN_RING0 -D_X86_ -DIN_RT_R0 -DIN_SUP_R0 -DVBGL_VBOXGUEST -DVBGL_HGCM -DVBOX_WITH_HGCM  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(test)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxadd_test)"  -c -o /tmp/vbox.0/.tmp_test.o /tmp/vbox.0/test.c
/bin/sh: gcc: not found
make[2]: *** [/tmp/vbox.0/test.o] Error 127
make[1]: *** [_module_/tmp/vbox.0] Error 2
make: *** [vboxadd_test] Error 2


Please help!

---

### Post by raziv on 2010-05-15
Looking at the log it says:```
/bin/sh: gcc: not found
```
This is the GNU C compiler missing.
Try installing the build-essential package - use your favorite method. I prefer aptitude: ```
sudo aptitude install build-essential
``` and then try again.

---

### Post by lmarmisa on 2010-05-16
Try to install these two packages: **build-essential** and **linux-headers-generic**.

> 
**[FONT=Times New Roman][SIZE=2]sudo apt-get  install build-essential  linux-headers-generic[/SIZE][/FONT]** 
I think that you will be able to compile the kernel modules after  this update.

Best regards,

Luis

---

### Post by Plumtreed on 2010-05-16
Google 'The Catling Mindswipe: Instaling Guest Additions in Lubuntu' for an effective and detailed 'Howto'.

---

### Post by arashiko28 on 2010-05-16
> **lmarmisa said:**
> Try to install these two packages: **build-essential** and **linux-headers-generic**.

I think that you will be able to compile the kernel modules after  this update.

Best regards,

Luis

I tried that, but I got an error message about no package available :(

---

### Post by arashiko28 on 2010-05-16
> **Plumtreed said:**
> Google 'The Catling Mindswipe: Instaling Guest Additions in Lubuntu' for an effective and detailed 'Howto'.

I've repeated these steps so many times, I already know them by heart, thanks for helping, but it doesn't say anything I haven't tried.

---

### Post by Plumtreed on 2010-05-17
Have you upgraded to the latest VBox version  virtualbox-3.1_3.1.8-61349~ubuntu~lucid_i386.deb

---

### Post by raziv on 2010-05-21
> **arashiko28 said:**
> I tried that, but I got an error message about no package available :(
Could you post the whole output when you try to install? Just copy & paste from the terminal.

---

### Post by arashiko28 on 2010-05-22
I solved it by uninstalling all, including Virtual Box and installing again. Thanks to all for your help.

---

