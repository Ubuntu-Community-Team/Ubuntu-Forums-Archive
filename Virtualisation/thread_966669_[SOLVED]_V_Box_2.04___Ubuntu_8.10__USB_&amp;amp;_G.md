---
title: "[SOLVED] V Box 2.04  / Ubuntu 8.10  USB &amp;amp; Guest Additions."
date: 2008-11-01
forum: Virtualisation
---

### Post by Dyffo on 2008-11-01
Have just upgraded to Ubuntu 8.10 and installed V.Box 2.04, my question is How to activate the USB port and install Guest Additions. I have tried the methods used for Hardy, but they no longer seem to work for the new package.
Any ideas ???

---

### Post by matza55 on 2008-11-01
Same here! But I got the Guest Additions to work. (in XP Pro) The OS must support Guest Additions. But still usb don't work. I have asked the question on the forum in Sweden,and if/then I get the answer I let Y now!

---

### Post by uidb4056 on 2008-11-01
Which version have you installed, the OSE one from standard repositories or the free non open source from [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) , the OSE version has no support of USB, if you have installed it I would suggest to uninstall and get it installed from the link (Hardy version and sources is working for me on 8.10).

In addtion you must have to add in your /etc/fstab the following line:

none /proc/bus/usb usbfs devgid=XXX,devmode=664 0 0

Being XXX the Group ID of vboxusers (see under System-Administration-Users and Groups).

---

### Post by matza55 on 2008-11-01
Now I'm back: in terminal: "sudo gedit /etc/fstab" insert: "# Access till VirtualBox USB-enheter
/dev/bus/usb /proc/bus/usb usbfs defaults,devmode=666   0 0" before # /dev/xxxx.
after that: "sudo mount -a" - maybe you must restart the computer. I did and it working well! 
link to swedish forum: [http://ubuntu-se.org/phpBB3/viewtopic.php?f=208&t=33179&p=259938#p259938](http://ubuntu-se.org/phpBB3/viewtopic.php?f=208&t=33179&p=259938#p259938) if you will see for your self. But you said that you have more problems?  

Have a nice holiday from Sweden!

---

### Post by matza55 on 2008-11-01
I forgot that you must have the nonfree-version. Sorry...

---

### Post by Dyffo on 2008-11-01
> **uidb4056 said:**
> Which version have you installed, the OSE one from standard repositories or the free non open source from [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) , the OSE version has no support of USB, if you have installed it I would suggest to uninstall and get it installed from the link (Hardy version and sources is working for me on 8.10).

In addtion you must have to add in your /etc/fstab the following line:

none /proc/bus/usb usbfs devgid=XXX,devmode=664 0 0

Being XXX the Group ID of vboxusers (see under System-Administration-Users and Groups).
YES got V.Box from the free open source .  Being a novice newbie can you tell me how I add  " none /proc/bus/usb usbfs devgid=XXX,devmode=664 0 0 " to my " /etc/fstab ", do I use sudo commands from the terminal ??.  V.Box has installed perfectly I just get the message "FAILED TO ACCESS USB SUB SYSTSTEM ". 
For interest I am installing XP Home - I have not tried to locate Guest Additions yet, but it would help if I could have advice on where to look.

---

### Post by uidb4056 on 2008-11-01
Open the terminal (Applications-Accessories-Terminal menu), then type 'sudo gedit /etc/fstab' (without the quotes), you will be asked for your password (type in even is not showed what you type and press enter).
Go to the end of the file, add a new line (enter) and type what I said before press enter again, save and close.
Before this you need to write down the Group ID to replace XXX.

---

### Post by Dyffo on 2008-11-01
> **uidb4056 said:**
> Open the terminal (Applications-Accessories-Terminal menu), then type 'sudo gedit /etc/fstab' (without the quotes), you will be asked for your password (type in even is not showed what you type and press enter).
Go to the end of the file, add a new line (enter) and type what I said before press enter again, save and close.
Before this you need to write down the Group ID to replace XXX.
Thank you - ALL done and works  - tomorrow I will continue installing XP and see how we get on with Guest Additions.

---

### Post by Anden100 on 2008-11-02
> **Dyffo said:**
> Thank you - ALL done and works  - tomorrow I will continue installing XP and see how we get on with Guest Additions.

In the window, where your Guest OS is running, go to "Devices>Install Guest Additions" (in the menu bar at the top), A program will automatically run in your Guest

Just did it at Ubuntu 8.10, and mouse-interfacing works, together with resolution change when you go to full screen mode, and back again :)

now... im going to set up the USB...

---

### Post by Dyffo on 2008-11-02
> **Anden100 said:**
> In the window, where your Guest OS is running, go to "Devices>Install Guest Additions" (in the menu bar at the top), A program will automatically run in your Guest

Just did it at Ubuntu 8.10, and mouse-interfacing works, together with resolution change when you go to full screen mode, and back again :)

now... im going to set up the USB...
Have got it all working now !! I did have a problem with Guest Additions. When I tried to install from the drop downh menu nothing happened !!!!! then by accident whilst I was in Windows, I opened "my computer", and low and behold sitting in the CD drive space was a file for Guest additions -I opened this and ran it - it all loaded perfectly, so now everything is O.K.. Just have a problem with my network file  printer & sharing.More on this later !!

---

### Post by RavUn on 2008-11-02
Do Guest Additions work in Kubuntu?  I have the OSE version and tried installing guest additions and I get an error with the following in the log file:
```

Installing VirtualBox 1.5.6 Guest Additions, built Tue Feb 19 17:21:02 CET 2008

Testing the setup of the guest system

Building a test kernel module...

make KBUILD_VERBOSE=1 -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/tmp/selfgz13036/module/test SRCROOT=/tmp/selfgz13036/module/test modules
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /tmp/selfgz13036/module/test/.tmp_versions ; rm -f /tmp/selfgz13036/module/test/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/selfgz13036/module/test
  gcc -Wp,-MD,/tmp/selfgz13036/module/test/.test.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.27-7-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -I/lib/modules/2.6.27-7-generic/build/include -I/tmp/selfgz13036/module/test/ -I/tmp/selfgz13036/module/test/include -I/tmp/selfgz13036/module/test/r0drv/linux -D__KERNEL__ -DMODULE -D__LINUX__ -DIN_RING0 -D_X86_ -DIN_RT_R0 -DIN_SUP_R0 -DVBGL_VBOXGUEST -DVBGL_HGCM -DVBOX_HGCM -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(test)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxadd_test)" -c -o /tmp/selfgz13036/module/test/.tmp_test.o /tmp/selfgz13036/module/test/test.c
  ld -m elf_i386   -r -o /tmp/selfgz13036/module/test/vboxadd_test.o /tmp/selfgz13036/module/test/test.o 
(cat /dev/null;   echo kernel//tmp/selfgz13036/module/test/vboxadd_test.ko;) > /tmp/selfgz13036/module/test/modules.order
  Building modules, stage 2.
make -f /usr/src/linux-headers-2.6.27-7-generic/scripts/Makefile.modpost
  scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.27-7-generic/Module.symvers -I /tmp/selfgz13036/module/test/Module.symvers  -o /tmp/selfgz13036/module/test/Module.symvers -S -K /usr/src/linux-headers-2.6.27-7-generic/Module.markers -M /tmp/selfgz13036/module/test/Module.markers -w  -s
  gcc -Wp,-MD,/tmp/selfgz13036/module/test/.vboxadd_test.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.27-7-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -I/lib/modules/2.6.27-7-generic/build/include -I/tmp/selfgz13036/module/test/ -I/tmp/selfgz13036/module/test/include -I/tmp/selfgz13036/module/test/r0drv/linux -D__KERNEL__ -DMODULE -D__LINUX__ -DIN_RING0 -D_X86_ -DIN_RT_R0 -DIN_SUP_R0 -DVBGL_VBOXGUEST -DVBGL_HGCM -DVBOX_HGCM  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(vboxadd_test.mod)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxadd_test)" -DMODULE -c -o /tmp/selfgz13036/module/test/vboxadd_test.mod.o /tmp/selfgz13036/module/test/vboxadd_test.mod.c
  ld -r -m elf_i386  --build-id -o /tmp/selfgz13036/module/test/vboxadd_test.ko /tmp/selfgz13036/module/test/vboxadd_test.o /tmp/selfgz13036/module/test/vboxadd_test.mod.o
Inserting the test module module/test/vboxadd_test.ko into the kernel.

Building the VirtualBox Guest Additions kernel module.

make KBUILD_VERBOSE=1 -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/tmp/vbox.5 SRCROOT=/tmp/vbox.5 modules
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /tmp/vbox.5/.tmp_versions ; rm -f /tmp/vbox.5/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/vbox.5
grep: /tmp/vbox.5/include/linux/version.h: No such file or directory
  gcc -Wp,-MD,/tmp/vbox.5/.cmc.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.27-7-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -I/lib/modules/2.6.27-7-generic/build/include -I/tmp/vbox.5/ -I/tmp/vbox.5/include -I/tmp/vbox.5/r0drv/linux -D__KERNEL__ -DMODULE -DRT_OS_LINUX -DIN_RING0 -D_X86_ -DIN_RT_R0 -DIN_SUP_R0 -DVBGL_VBOXGUEST -DVBOX_HGCM -DLOG_TO_BACKDOOR -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(cmc)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxadd)" -c -o /tmp/vbox.5/.tmp_cmc.o /tmp/vbox.5/cmc.c
In file included from /tmp/vbox.5/cmc.c:17:
/tmp/vbox.5/r0drv/linux/the-linux-kernel.h:55:27: error: asm/semaphore.h: No such file or directory
make[2]: *** [/tmp/vbox.5/cmc.o] Error 1
make[1]: *** [_module_/tmp/vbox.5] Error 2
make: *** [vboxadd] Error 2

```

---

