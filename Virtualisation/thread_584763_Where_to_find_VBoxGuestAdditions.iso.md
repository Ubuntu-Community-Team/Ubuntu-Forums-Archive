---
title: "Where to find VBoxGuestAdditions.iso"
date: 2007-10-21
forum: Virtualisation
---

### Post by nianhbg on 2007-10-21
Hi I installed Viritualbox in Unbuntu 7.10 and it went well. Now I have installed Windows XP and i would like to install VBoxGuestAdditions but  I dont find the iso file. Any suggestions?

---

### Post by insane_alien on 2007-10-21
boot up the virtual machine, when that is done. go to the devices dropdown menu and click 'install Vbox guest additions'

---

### Post by bodhi.zazen on 2007-10-21
See if this helps : [http://doc.gwos.org/doku.php/doc:office:virtualbox#additions_.iso](http://doc.gwos.org/doku.php/doc:office:virtualbox#additions_.iso)

---

### Post by Tux Aubrey on 2007-10-21
I had this (embarrassing) problem too.  I think it has to with the VBox version in the repos.  I don't think it comes with LinuxAdditions.  I uninstalled it and got the deb from the VirtualBox site and all was cool.

It "suddenly" appeared in /usr/share/virtualbox/

I mounted the iso in the guest, copied the LinuxAdditions run file to /home and ran it with sudo sh./

All is now well in my virtual world - I can even get a windowless VM! yay.

---

### Post by MarsmanA on 2007-11-09
Hi!

I also have some similar problem. I mounted the ISO file and run the .RUN file, but I always get a message that I do not have the administrator privileges (thou I have) to install it. Somebody knows why?
Please help. Thank you.

---

### Post by bodhi.zazen on 2007-11-09
Use sudo :

sudo sh xxx.Run

---

### Post by ericesque on 2007-11-09
To elaborate on what insane_alien said, if you have installed the version from VirtualBox's website (HIGHLY recommended), start the XP guest and click devices>Install GuestAdditions

Now here's the part that's not as intuitive.  When  you click it, for some people, nothing appears to have happened.  But it actually just mounted the iso for you.  Just go to My Computer in the XP guest and 'Explore' the Rom to find an executable for guestAdditions.

---

### Post by schase02 on 2008-04-09
awesome - late thread, but that very last post did the trick

---

### Post by w00t1138 on 2008-06-18
Thanks, ericesque!

That did the trick for me as well :)

---

### Post by RavUn on 2008-11-02
Hey, I'm running kubuntu under virtualbox and am trying to adjust the resolution since 800x600 is ridiculously small.  I've mounted the vboxadditions.iso and run the .run file and get the following: 
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


I assume the kernel I have is not yet supported, or am I missing any libraries or anything?  I don't know what to make of that log.

---

### Post by surelock22 on 2008-11-04
sweeeeet. i have it all installed, ready to go.

now i have to convince myself that all this time i spent installing VB and it's guest additions was worth it.

oh yeah, i **HAVE** to have windows for the 20-20 design and 98 Rock stream.

:guitar:

---

### Post by madverb on 2009-01-15
[http://download.virtualbox.org/virtualbox/2.0.4/VBoxGuestAdditions_2.0.4.iso](http://download.virtualbox.org/virtualbox/2.0.4/VBoxGuestAdditions_2.0.4.iso)

---

### Post by davewantsmoore on 2009-01-22
> **madverb said:**
> [http://download.virtualbox.org/virtualbox/2.0.4/VBoxGuestAdditions_2.0.4.iso](http://download.virtualbox.org/virtualbox/2.0.4/VBoxGuestAdditions_2.0.4.iso)

OH MAN... thankyou.

Could find a link for this on their site no matterr how I tried.

---

### Post by HotShotDJ on 2009-01-23
Why are people wanting to download the Guest Additions separately.  All you have to do is start your guest OS.  After it is booted up and ready to use, make sure you are in windowed mode (as opposed to full screen), open "Devices" from the menu bar, and select "Install Guest Additions..."  Normally, it will start up automatically, but if it doesn't, just open the Windows "start" menu, go to "My Computer" (or "Computer" in Vista) and double click on the CD labeled "VirtualBox Guest Additions." I've never had to download the ISO either in the OSE or PUEL versions.

---

### Post by MrDelish on 2009-01-24
> **HotShotDJ said:**
> Why are people wanting to download the Guest Additions separately.  All you have to do is start your guest OS.  After it is booted up and ready to use, make sure you are in windowed mode (as opposed to full screen), open "Devices" from the menu bar, and select "Install Guest Additions..."  Normally, it will start up automatically, but if it doesn't, just open the Windows "start" menu, go to "My Computer" (or "Computer" in Vista) and double click on the CD labeled "VirtualBox Guest Additions." I've never had to download the ISO either in the OSE or PUEL versions.

Some tutorials I've seen online don't mention the same steps, so I thought I might have to download it myself until I came across your post. That made it MUCH clearer. :KS

---

### Post by Stu09 on 2009-01-24
> **madverb said:**
> [http://download.virtualbox.org/virtualbox/2.0.4/VBoxGuestAdditions_2.0.4.iso](http://download.virtualbox.org/virtualbox/2.0.4/VBoxGuestAdditions_2.0.4.iso)

I had to rename this iso to VBoxGuesAdditions.iso so that VirtualBox would find it.
Worked a treat.

---

### Post by Vadi on 2009-01-28
> **madverb said:**
> [http://download.virtualbox.org/virtualbox/2.0.4/VBoxGuestAdditions_2.0.4.iso](http://download.virtualbox.org/virtualbox/2.0.4/VBoxGuestAdditions_2.0.4.iso)

Thanks a bunch

---

### Post by HotShotDJ on 2009-01-28
> **Stu09 said:**
> I had to rename this iso to VBoxGuesAdditions.iso so that VirtualBox would find it.
Worked a treat.

> **Vadi said:**
> Thanks a bunch

But.... WHY?  Why are you folks finding it necessary to download the Guest Additions ISO separately?  I'd like to find out why the following isn't working for you.  You should NOT have to download the ISO manually.  It is should already be on your computer in /usr/share/virtualbox and is installable using this VERY simple method.
> **HotShotDJ said:**
> All you have to do is start your guest OS.  After it is booted up and ready to use, make sure you are in windowed mode (as opposed to full screen), open "Devices" from the menu bar, and select "Install Guest Additions..."  Normally, it will start up automatically, but if it doesn't, just open the Windows "start" menu, go to "My Computer" (or "Computer" in Vista) and double click on the CD labeled "VirtualBox Guest Additions." I've never had to download the ISO either in the OSE or PUEL versions.

---

### Post by Vadi on 2009-01-28
Because uploading the .iso to another location and then downloading inside vm isn't painless.

Just downloading from an already uploaded location is easier. Plus, "Install Guest Additions" wasn't mounting the cd in KDE 4.

---

### Post by Malaz on 2009-01-28
The version of VirtualBox OSE included in Ubuntu doesn't include the iso, and won't download it.  That is why it must be downloaded separately.

---

### Post by HotShotDJ on 2009-01-28
> **Malaz said:**
> The version of VirtualBox OSE included in Ubuntu doesn't include the iso, and won't download it.  That is why it must be downloaded separately.Got it.  Also found the bug: [https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/210352](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/210352)

Definitely something that needs fixing.

---

### Post by stoian on 2009-10-02
Using Ubuntu Hardy Heron...

I followed the instructions from VirtualBox.org, so I added the repos from Virtualbox as described here:
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Please note that the latest release as of today is 3.0.6.

Then I installed from Synaptic. Make sure you select all these:
1. virtualbox-3.0
2. virtualbox-ose-guest-modules-24.0.10 (meta-package, see description: virtualbox-ose-guest module for linux-image-generic)
3. virtualbox-ose-guest-utils

Make sure you add the meta-package(s) for your specific kernel (I have "generic").

After installation a shortcut is placed under menu in Applications > System Tools > Sun VirtualBox.

On my machine the menu item was there but didn't show up, so I had to either log out and log back in, or reset the gnome panels with this command in the terminal: killall gnome-panel.

The guest additions iso is located here:
/usr/share/virtualbox/VBoxGuestAdditions.iso

After this all went nicely, I just followed the instructions in the user manual, which can be downloaded from here:
[http://download.virtualbox.org/virtualbox/3.0.6/UserManual.pdf](http://download.virtualbox.org/virtualbox/3.0.6/UserManual.pdf)

Hope this helps... good luck!
:KS

---

### Post by rewyllys on 2010-02-14
> **HotShotDJ said:**
> Why are people wanting to download the Guest Additions separately.  All you have to do is start your guest OS.  After it is booted up and ready to use, make sure you are in windowed mode (as opposed to full screen), open "Devices" from the menu bar, and select "Install Guest Additions..."  Normally, it will start up automatically, but if it doesn't, just open the Windows "start" menu, go to "My Computer" (or "Computer" in Vista) and double click on the CD labeled "VirtualBox Guest Additions." I've never had to download the ISO either in the OSE or PUEL versions.

Thank you, thank you, thank you, for these instructions! :popcorn:

 I'd been going crazy for at least 2 hours with my mouse locked inside the VirtualBox (running in Ubuntu 9.10) containing Windows XP, before I found your post.  I had to download the ".iso" file but was able to do that smoothly within Windows XP.  Simply installing the Guest Additions has freed my mouse to move freely between the VirtualBox and Unbuntu.

BTW, the VBoxGuestAdditions are now version 3.0.8.

PS: What a shame that income-tax software isn't available for Linux! :sad: (If it were, I wouldn't have had to spend several hours today installing VirtualBox, then XP inside it, and then seemingly endless updates.)

---

### Post by bodhi.zazen on 2010-02-14
> **rewyllys said:**
> PS: What a shame that income-tax software isn't available for Linux! :sad: (If it were, I wouldn't have had to spend several hours today installing VirtualBox, then XP inside it, and then seemingly endless updates.)

There are several options available for LInux, GNUCash and KMyMoney are the two I would start with.

---

### Post by rewyllys on 2010-02-15
> **bodhi.zazen said:**
> There are several options available for LInux, GNUCash and KMyMoney are the two I would start with.

GNUCash and KMyMoney are good programs for recording one's income and expenditures, but what I had in mind was programs like TurboTax and H&R Block At Home. These prepare a person's or family's Federal and State income-tax forms, a task which for most of us in the USA is an annoyingly laborious annual necessity.  To my regret, I couldn't get Wine to handle either TurboTax or At Home--and April 15 is looming closer and closer.:frown:

---

### Post by rewyllys on 2010-02-15
> **rewyllys said:**
> BTW, the VBoxGuestAdditions are now version 3.0.8.

And, on my system, the ".iso" file is stored as

/home/ron/.VirtualBox/VBoxGuestAdditions_3.0.8.iso

---

