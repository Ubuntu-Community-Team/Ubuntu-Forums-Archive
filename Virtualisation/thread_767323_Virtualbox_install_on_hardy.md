---
title: "Virtualbox install on hardy"
date: 2008-04-25
forum: Virtualisation
---

### Post by uraliss on 2008-04-25
Hi Folks,
Whats the easiest\best way of getting virtualbox installed on my new hardy heron build?

Thanks in advance

---

### Post by eddyr on 2008-04-26
I'd like to know this as well.

---

### Post by howefield on 2008-04-26
virtualbox ose is in the repository, install from synaptic package manager, but if you need USB support you would want the PUEL version, I believe the gutsy version works in hardy as I read eleswhere in these forums.

---

### Post by gmcalp on 2008-04-26
I can confirm that VB does in fact run under Hardy using the Gutsy VB release... if you already had VB installed and then upgraded from Gutsy to Hardy, you will have to issue the following command from a terminal:

```
sudo /etc/init.d/vboxdrv setup
```

that will recompile the VirtualBox module into the kernel.

Hope that helps.

---

### Post by jetpeach on 2008-04-26
on my hardy, i'm still using the virtualbox.org repository, but to get it to work i left it on gutsy (they apparently don't have a hardy one yet)

add to /etc/apt/sources.list

deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) gutsy non-free

then
sudo apt-get update
sudo apt-get install virtualbox

and it should be installed. follow the final instructions (adding vbox user stuff) and you should be good to go (worked for me at least!)

---

### Post by irifan on 2008-04-26
First install sun java 6.

Then I went to 
[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.5.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.5.6-G-F@CDS-CDS_SMI)

and downloaded the debian 4.0 file. right-click on the .deb file and select Open with GDebi Package installer

The non free version supports USB. You need to enable USB support in hardy first tough. The open source version is already included in the universe repo.

---

### Post by pormogo on 2008-04-27
So the binary package for the non free edition for debian etch will run on Ubuntu hardy? 

The only issue with mine is that the kernel module does not seem to want to load. I was under the impression that it was not possible to compile the kernel module for the non free version.

Answered my own question here. Look like all you have to do to get the kernel module to comply to the new kernel is run it's setup from init

/etc/init.d/vboxdrv setup

now it's working for me :)

---

### Post by kurumin on 2008-04-27
I update my gutsy to hardy heron and i had this problem:
i have 2 hds and the virtualbox virtualdisk was in the hd windows calling
/media/disk-1 now when i start ubuntu this hd is mounted as
/media/disk-3/4/5/6 etc... a new name at new start them the virtualbox
don t find the disk and donot work. if anybody have a solution
please e-mail to [email]spifercor_ect@yahoo.com.br[/email] tanks.

---

### Post by MasterNetra on 2008-04-28
I am sorry for being a noob but how do you install and run it on a fresh install of Hardy? I am still quite a noob when it comes to linux, don't know much about compiling or any of that more advance stuff as of yet so i kinda need the detailed steps for it... Also will Virtualbox run 3Ds Max 8? Does anyone know?

---

### Post by Saneless on 2008-04-28
I just installed the Debian 4.0 version and haven't had any issues and I didn't have to do anything special (aside from the usual vbox users and usbusers changes)

---

### Post by Fran89 on 2008-04-29
Mine says ```
No suitable module for running kernel found.
```
it will not let me run.. it not even with sudo /etc/init.d/vboxdrv setup

any ideas?

---

### Post by seamuso on 2008-04-29
I'm using the closed source version (need usb support) .. I installed the gutsy .deb with no issues in hh x86_64

---

### Post by _angel__ on 2008-04-30
[http://www.virtualbox.org/download/1.5.6/](http://www.virtualbox.org/download/1.5.6/)

Here's the closed source version (with usb support) for Hardy
[http://www.virtualbox.org/download/1.5.6/virtualbox_1.5.6-28266_Ubuntu_hardy_i386.deb](http://www.virtualbox.org/download/1.5.6/virtualbox_1.5.6-28266_Ubuntu_hardy_i386.deb)

---

### Post by vexorian on 2008-04-30
so
```

vx@ubuntuvx:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for vx: 
 * Stopping VirtualBox kernel module vboxdrv                             [ OK ] 
 * Recompiling VirtualBox kernel module vboxdrv                                 
 * Look at /var/log/vbox-install.log to find out what went wrong
vx@ubuntuvx:~$ cat /var/log/vbox-install.log
make KBUILD_VERBOSE=1 -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/tmp/vbox.0 SRCROOT=/tmp/vbox.0 modules
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.24-16-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /tmp/vbox.0/.tmp_versions ; rm -f /tmp/vbox.0/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/vbox.0
  gcc -m32 -Wp,-MD,/tmp/vbox.0/linux/.SUPDrv-linux.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -I/lib/modules/2.6.24-16-generic/build/include  -I/tmp/vbox.0/ -I/tmp/vbox.0/include -I/tmp/vbox.0/r0drv/linux -D__KERNEL__ -DMODULE -DRT_OS_LINUX -DIN_RING0 -DIN_RT_R0 -DIN_SUP_R0 -DCONFIG_VBOXDRV_AS_MISC -DRT_ARCH_X86 -DUSE_NEW_OS_INTERFACE_FOR_MM   -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(SUPDrv_linux)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxdrv)" -c -o /tmp/vbox.0/linux/.tmp_SUPDrv-linux.o /tmp/vbox.0/linux/SUPDrv-linux.c
In file included from /tmp/vbox.0/include/iprt/types.h:72,
                 from /tmp/vbox.0/include/VBox/types.h:21,
                 from /tmp/vbox.0/SUPDRV.h:26,
                 from /tmp/vbox.0/linux/SUPDrv-linux.c:22:
include/linux/types.h:40: error: redefinición de la definición de tipo &#8216;uintptr_t&#8217;
/tmp/vbox.0/include/iprt/stdint.h:118: error: la declaración previa de &#8216;uintptr_t&#8217; estaba aquí
En el fichero incluído de include/linux/thread_info.h:33,
                 de include/linux/preempt.h:9,
                 de include/linux/spinlock.h:49,
                 de /tmp/vbox.0/SUPDRV.h:84,
                 de /tmp/vbox.0/linux/SUPDrv-linux.c:22:
include/linux/bitops.h:6:1: aviso: se redefinió "BIT"
En el fichero incluído de /tmp/vbox.0/include/VBox/cdefs.h:20,
                 de /tmp/vbox.0/SUPDRV.h:25,
                 de /tmp/vbox.0/linux/SUPDrv-linux.c:22:
/tmp/vbox.0/include/iprt/cdefs.h:1019:1: aviso: esta es la ubicación de la definición previa
make[2]: *** [/tmp/vbox.0/linux/SUPDrv-linux.o] Error 1
make[1]: *** [_module_/tmp/vbox.0] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vboxdrv] Error 2

```

:(

I'll check the hardy .deb out. It is odd that they got a deb yet no hardy repo...

--
Edit: So, I have installed the deb and virtual box works, new icons yay! I have noticed though that windows' taskbar is invisible in seamless mode, I really didn't use it, I setup a custom bar instead though.

Edit: reinstalled guest additions in XP, now the taskbar appears, there's a small problem though and it is that the gnome panel overlaps it... I got both horizontal panels so things got tricky .

---

### Post by drhiii on 2008-04-30
Hello,

After hitting the same upgrade to 8.04 then VirtualBox failure, followed the flow here and dnld'd the recommended .DEB file, installed, everything seemed happy, then Starting the VDI file that is left over from teh prior build, failed.  Received the following popup from VirtualBox:


PIIX3 cannot attach drive to the Secondary Master.
VBox status code: -102 (VERR_FILE_NOT_FOUND).

Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}



I went thru the Settings and tried to see what may have bonked, but slightly n00bish and couldn't figure out what I was being told according to the settings.

Ideas anyone?


UPDATE:  Would this have anything to do with Guest Additions?  I see where there is a call to Guest Additions in the Settings, but it is pointing to /opt/VirtualBox-1.4.0/additions  which does not exist anymore, having removed it.  When I installed the .DEB file, did it install VB and it's Guest Additions components too?  Again, new to this so am feeling my way around.

---

### Post by drhiii on 2008-05-01
A more general question for this thread would be... once one installs virtualbox_1.5.6-28266_Ubuntu_hardy_i386.deb, what else needs to be done besides installing it?  Like, Guest Additions?  I have an already built VDI file that was already running, and when I upgraded, it broke which is why I'm here after I uninstalled a prior version of VB.  Should I have not uninstall VB?   After following the thread recommendations, I thought things were going to smooth out until I received the error message in the post above.  

Is it looking for I think, a Guest Addition .ISO file???  Would that be right?  If yes, where did it get installed?  Or, did it?  I've searched the drive and cannot find any reference to it.

Basic question is... is there something else that needs to be done after installing the .DEB file, or, can someone shed some light on the error message above?

tx in advance.  I surely do appreciate how terrific Ubuntu and its community is.

---

### Post by tonyhuman on 2008-05-01
Try this link. It's a gr8 tutorial and it worked for me with no problems.

[http://ubuntuforums.org/showthread.php?t=770745](http://ubuntuforums.org/showthread.php?t=770745)

---

