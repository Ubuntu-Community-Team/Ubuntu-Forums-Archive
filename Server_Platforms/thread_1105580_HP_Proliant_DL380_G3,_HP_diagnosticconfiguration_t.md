---
title: "HP Proliant DL380 G3, HP diagnostic/configuration tools"
date: 2009-03-24
forum: Server Platforms
---

### Post by gtfourdreams on 2009-03-24
Well.. I was surfing around trying to figure out an easy way to configure and diagnose the SCSI Smart Array 5i Plus that came with my server. It turns out HP does include some software for Debian which might be useful for us. For the sake of making these files public so that more people (who are much better at this than myself) can use and try these files out, here is a list of what I have found. Please if you find any use of these files, post up some information for others.

Installation Information for Debian Etch 4.0 (i386)
[https://h20392.www2.hp.com/portal/swdepot/displayProductInfo.do?productNumber=T8570AAE]("https://h20392.www2.hp.com/portal/swdepot/displayProductInfo.do?productNumber=T8570AAE")

Installation Information for Debian Etch 4.0 (AMD64/EM64T)
[http://h20392.www2.hp.com/portal/swdepot/displayProductInfo.do?productNumber=T8569AAE]("http://h20392.www2.hp.com/portal/swdepot/displayProductInfo.do?productNumber=T8569AAE")


On the bottom of that page, you can 'receive for free' the following files:

 
Additional product information
Product #: 	T8570AAE
Version: 	Debian 4.0 (Etch)
Software specification: 	hpasm-7.8.0-100.etch26.i386.deb
hp-OpenIPMI-7.8.0-108.etch26.i386.deb
hprsm-7.8.0-103.etch26.i386.deb
cmanic_7.9.0-5b.etch_i386.deb
hpsmh-2.1.7-167.debian.i386.deb
cpqacuxe-7.80-4.linux.deb
hpacucli-7.80-3.linux.deb
hpadu-7.80-4.linux.deb 

Additional product information
Product #: 	T8569AAE
Version: 	Debian 4.0 (Etch)
Software specification: 	hpasm-7.8.0-91.etch26.amd64.deb
hp-OpenIPMI-7.8.0-108.etch26.amd64.deb
hprsm-7.8.0-104.etch26.amd64.deb
cmanic_7.9.0-5b.etch_amd64.deb
hpsmh-2.1.7-167.debian.amd64.deb
cpqacuxe-7.80-4.linux.deb
hpacucli-7.80-3.linux.deb
hpadu-7.80-4.linux.deb 

Fill out the information and download the files.

You may also need this:
[http://packages.ubuntu.com/gutsy/i386/libstdc++2.10-glibc2.2/download]("http://packages.ubuntu.com/gutsy/i386/libstdc++2.10-glibc2.2/download")

Good luck. I am going to try to install these on my server, per HP's instructions and see what happens. 

Reference: [http://www.zabbix.com/forum/showthread.php?p=35469](http://www.zabbix.com/forum/showthread.php?p=35469)
[http://ubuntuforums.org/showthread.php?t=521911&highlight=hp-OpenIPMI](http://ubuntuforums.org/showthread.php?t=521911&highlight=hp-OpenIPMI)

---

### Post by gtfourdreams on 2009-03-24
Error? Anybody with any advice?

```

$ sudo dpkg --install hp-OpenIPMI-7.8.0-108.etch26.i386.deb
Selecting previously deselected package hp-openipmi.
(Reading database ... 37205 files and directories currently installed.)
Unpacking hp-openipmi (from hp-OpenIPMI-7.8.0-108.etch26.i386.deb) ...
Setting up hp-openipmi (7.8.0-108.etch26) ...
This kernel requires a rebuild.  Seeking source files
Basic source files appear to be installed.  Investigating further.
Unknown Linux Distribution - will attempt to build
The hp-OpenIPMI(4) and hpasm(4) man pages have additional
information to resolve this issue. The HP Advanced System
Management software is currently disabled on this system.
if [ -d OpenIPMI ]; then \
                rm -rf drivers ;\
                rm -rf include ;\
                if [ -d drivers.ORIG ]; then \
                        mv drivers.ORIG drivers ;\
                fi  ;\
                if [ -d include.ORIG ]; then \
                        mv include.ORIG include ;\
                fi ;\
        fi
for kversion in 2.6.24-23-server; do \
                LINUX_BUILD_DIR="/lib/modules/$kversion/build/"  ;\
                echo "Cleaning  KERNEL VERSION $kversion  LINUX_BUILD_DIR:  $LINUX_BUILD_DIR"  ;\
                if [ `pwd` != "/" ] ; then \
                        rm -rf `pwd`/bin/$kversion ;\
                fi  ;\
                if [ -d $LINUX_BUILD_DIR ]; then \
                        if [ -f $LINUX_BUILD_DIR/include/linux/ipmi.h.ORIG ]; then \
                                rm $LINUX_BUILD_DIR/include/linux/ipmi.h ;\
                                mv $LINUX_BUILD_DIR/include/linux/ipmi.h.ORIG $LINUX_BUILD_DIR/include/linux/ipmi.h ;\
                        fi ;\
                        if [ -f $LINUX_BUILD_DIR/include/linux/ipmi_msgdefs.h.ORIG ]; then \
                                rm $LINUX_BUILD_DIR/include/linux/ipmi_msgdefs.h ;\
                                mv $LINUX_BUILD_DIR/include/linux/ipmi_msgdefs.h.ORIG $LINUX_BUILD_DIR/include/linux/ipmi_msgdefs.h ;\
                        fi ;\
                        if [ -f $LINUX_BUILD_DIR/include/linux/ipmi_smi.h.ORIG ];  then \
                                rm $LINUX_BUILD_DIR/include/linux/ipmi_smi.h ;\
                                mv $LINUX_BUILD_DIR/include/linux/ipmi_smi.h.ORIG $LINUX_BUILD_DIR/include/linux/ipmi_smi.h ;\
                        fi ;\
                fi   ;\
        done
Cleaning  KERNEL VERSION 2.6.24-23-server  LINUX_BUILD_DIR:  /lib/modules/2.6.24-23-server/build/
if [ -d OpenIPMI ]; then \
                if [ -d drivers ]; then \
                        mv drivers drivers.ORIG ;\
                        mv /opt/hp/hp-OpenIPMI/OpenIPMI/drivers . ;\
                fi  ;\
                if [ -d include ]; then \
                        mv include include.ORIG ;\
                        mv /opt/hp/hp-OpenIPMI/OpenIPMI/include . ;\
                fi  ;\
        fi
for kversion in 2.6.24-23-server; do \
                LINUX_BUILD_DIR="/lib/modules/$kversion/build/" ;\
                echo "Initializing KERNEL VERSION $kversion  LINUX_BUILD_DIR:  $LINUX_BUILD_DIR"  ;\
                if [ -d $LINUX_BUILD_DIR ]; then \
                        if [ ! -f $LINUX_BUILD_DIR/include/linux/ipmi.h.ORIG ]; then \
                                mv $LINUX_BUILD_DIR/include/linux/ipmi.h $LINUX_BUILD_DIR/include/linux/ipmi.h.ORIG; \
                        fi ;\
                        if [ ! -f $LINUX_BUILD_DIR/include/linux/ipmi_msgdefs.h.ORIG ]; then \
                                mv $LINUX_BUILD_DIR/include/linux/ipmi_msgdefs.h $LINUX_BUILD_DIR/include/linux/ipmi_msgdefs.h.ORIG; \
                        fi ;\
                        if [ ! -f $LINUX_BUILD_DIR/include/linux/ipmi_smi.h.ORIG ];  then \
                                mv $LINUX_BUILD_DIR/include/linux/ipmi_smi.h $LINUX_BUILD_DIR/include/linux/ipmi_smi.h.ORIG; \
                        fi ;\
                        cp include/linux/ipmi.h $LINUX_BUILD_DIR/include/linux/ipmi.h ;\
                        cp include/linux/ipmi_msgdefs.h $LINUX_BUILD_DIR/include/linux/ipmi_msgdefs.h ;\
                        cp include/linux/ipmi_smi.h $LINUX_BUILD_DIR/include/linux/ipmi_smi.h ;\
                fi ;\
        done
Initializing KERNEL VERSION 2.6.24-23-server  LINUX_BUILD_DIR:  /lib/modules/2.6.24-23-server/build/
for kversion in 2.6.24-23-server; do \
                LINUX_BUILD_DIR="/lib/modules/$kversion/build/" ;\
                echo "Building  KERNEL VERSION $kversion  LINUX_BUILD_DIR:  $LINUX_BUILD_DIR"  ;\
                if [ -d $LINUX_BUILD_DIR ]; then \
                        mkdir -p `pwd`/bin/$kversion  ;\
                        rm -f drivers/char/ipmi/*.o  ;\
                        rm -f drivers/char/ipmi/*.ko  ;\
                        rm -f drivers/char/ipmi/*.mod.c  ;\
                        rm -f drivers/char/ipmi/.ipmi*.cmd  ;\
                        rm -rf drivers/char/ipmi/.tmp_versions  ;\
                        make -C $LINUX_BUILD_DIR V=1 M=`pwd`/drivers/char/ipmi modules   ;\
                        if [ -f drivers/char/ipmi/ipmi_devintf.ko ]; then \
                                mv -vf drivers/char/ipmi/ipmi_*.ko `pwd`/bin/$kversion/.  ;\
                        else \
                                echo "BUILD ERROR: Build for  KERNEL VERSION: $kversion  LINUX_BUILD_DIR:  $LINUX_BUILD_DIR FAILED"  ;\
                                exit 1  ;\
                        fi  ;\
                else \
                        echo  " "  ;\
                        echo "WARNING:  THIS IS NO BUILD DIRECTORY FOR VERSION:  $kversion"  ;\
                        echo "          The LINUX_BUILD_DIR resolves to:  $LINUX_BUILD_DIR"  ;\
                        echo  " "  ;\
                fi ;\
        done
Building  KERNEL VERSION 2.6.24-23-server  LINUX_BUILD_DIR:  /lib/modules/2.6.24-23-server/build/
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-23-server'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (            \
        echo;                                                           \
        echo "  ERROR: Kernel configuration is invalid.";               \
        echo "         include/linux/autoconf.h or include/config/auto.conf are missing."; \
        echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";     \
        echo;                                                           \
        /bin/false)
mkdir -p /opt/hp/hp-OpenIPMI/drivers/char/ipmi/.tmp_versions ; rm -f /opt/hp/hp-OpenIPMI/drivers/char/ipmi/.tmp_versions/*
make -f scripts/Makefile.build obj=/opt/hp/hp-OpenIPMI/drivers/char/ipmi
  gcc -m32 -Wp,-MD,/opt/hp/hp-OpenIPMI/drivers/char/ipmi/.ipmi_msghandler.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.4/include -D__KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i686 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign    -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(ipmi_msghandler)"  -D"KBUILD_MODNAME=KBUILD_STR(ipmi_msghandler)" -c -o /opt/hp/hp-OpenIPMI/drivers/char/ipmi/.tmp_ipmi_msghandler.o /opt/hp/hp-OpenIPMI/drivers/char/ipmi/ipmi_msghandler.c
  gcc -m32 -Wp,-MD,/opt/hp/hp-OpenIPMI/drivers/char/ipmi/.ipmi_devintf.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.4/include -D__KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i686 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign    -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(ipmi_devintf)"  -D"KBUILD_MODNAME=KBUILD_STR(ipmi_devintf)" -c -o /opt/hp/hp-OpenIPMI/drivers/char/ipmi/.tmp_ipmi_devintf.o /opt/hp/hp-OpenIPMI/drivers/char/ipmi/ipmi_devintf.c
  gcc -m32 -Wp,-MD,/opt/hp/hp-OpenIPMI/drivers/char/ipmi/.ipmi_si_intf.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.4/include -D__KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i686 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign    -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(ipmi_si_intf)"  -D"KBUILD_MODNAME=KBUILD_STR(ipmi_si)" -c -o /opt/hp/hp-OpenIPMI/drivers/char/ipmi/.tmp_ipmi_si_intf.o /opt/hp/hp-OpenIPMI/drivers/char/ipmi/ipmi_si_intf.c
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-23-server'
BUILD ERROR: Build for  KERNEL VERSION: 2.6.24-23-server  LINUX_BUILD_DIR:  /lib/modules/2.6.24-23-server/build/ FAILED

WARNING:  Build did not complete successfully!

Please read the Licence Agreement for this software at

         /opt/hp/hp-OpenIPMI/COPYING
                       and
         /opt/hp/hp-OpenIPMI/hp-OpenIPMI.license

By not removing this package, you are accepting the terms
of the included licenses.

The man page, hp-OpenIPMI(4), describes how enable and use
the hp-OpenIPMI device drivers.



```

---

### Post by Franzen on 2009-03-31
I ran into the same problem with a DL380 G4 and found that the "Lenny" (5.0) distributables provided on ISO work great with Ubuntu 8.10

i've installed the amd64T version of the HP tools and the only package I needed for the tools wat "libc6-i386".

hope this helps

good luck

---

### Post by quequotion on 2009-07-10
> **Franzen said:**
> I ran into the same problem with a DL380 G4 and found that the "Lenny" (5.0) distributables provided on ISO work great with Ubuntu 8.10

i've installed the amd64T version of the HP tools and the only package I needed for the tools wat "libc6-i386".

hope this helps

good luck

There are Lenny distributions?
What/Where is "ISO"? Do you mean the Lenny disk image?
Did you really install the amd64 version? Why did you need the 32bit version of libc6?
Which packages exactly were available? All of those on the HP site?

It sounds like you solved a big problem I'm also having..

---

### Post by gtfourdreams on 2009-12-12
if anybody still needs to figure this out, i had to figure it again when i upgraded to 9.10

along with the links above, you will need
[http://packages.ubuntu.com/dapper/i386/libstdc++2.10-glibc2.2/download](http://packages.ubuntu.com/dapper/i386/libstdc++2.10-glibc2.2/download)

```

sudo dpkg --install libstdc++2.10-glibc2.2_2.95.4-24_i386.deb
sudo apt-get install snmpd
sudo dpkg --install hpasm-7.8.0-100.etch26.i386.deb
sudo hpasm activate

```

that will install and activate it. use hpasmcli to access.

on a side note, with previous versions of Ubuntu you may have more errors partially due to bash/dash/sh. see: [http://debian.catsanddogs.com/component/option,com_smf/Itemid,41/topic,106.0/](http://debian.catsanddogs.com/component/option,com_smf/Itemid,41/topic,106.0/)

BUT it looks like that issue has been resolved in 9.10

also, hpacucli for the controller management installed without any issues.

---

### Post by webdirector on 2010-02-09
Hi I need help :-) 

I am new to the hp proliant DL380 G3 ( i got it cheap and want to use it as a server at home)

I have 4 HD in Raid 1 all are 72GB HD.

But I only see 72GB available as disk space. Is it correct when I assume I need to install [COLOR=windowtext][FONT=Arial][SIZE=2]hpacucli[/SIZE][/FONT][/COLOR]  to add the HD or partitions ? 

I was able to install [COLOR=windowtext][FONT=Arial][SIZE=2]hpacucli[/SIZE][/FONT][/COLOR] software and it looks like it is running OK. But I have not figured oiut how to add the HD ?

if I go into /dev/cciss/ I see [COLOR=windowtext][FONT=Arial][/FONT][/COLOR] " c0d0 c0d0p1 c0p0p2 c0p0p5 c0p1"

so what do I need to do to be able to use the c0p1. I tried with fdisk but I am unable to add it. I believe I have to use [COLOR=windowtext][FONT=Arial][SIZE=2]hpacucli[/SIZE][/FONT][/COLOR] to add the HD with but I have no idea how ? I read the "help" and the "add help" but I still do not understand 

please help

Thanks** **[COLOR=windowtext][FONT=Arial][/FONT][/COLOR]

---

### Post by webdirector on 2010-02-09
I do not know if this can help:

if I do cat /proc/driver/cciss/cciss0  iget this :

 cat /proc/driver/cciss/cciss0
cciss0: HP Smart Array 5i Controller
Board ID: 0x40800e11
Firmware Version: 2.66
IRQ: 30
Logical drives: 2
Current Q depth: 0
Current # commands on controller: 0
Max Q depth since init: 8
Max # commands on controller since init: 21
Max SG entries since init: 31
Sequential access devices: 0

cciss/c0d0:       72.83GB       RAID 1(1+0)
cciss/c0d1:       72.83GB       RAID 1(1+0)

---

### Post by webdirector on 2010-02-09
some more info:

 hpacucli ctrl slot=0 physicaldrive all show

Smart Array 5i in Slot 0

   array A

      physicaldrive 2:0   (port 2:id 0 , Parallel SCSI, 72.8 GB, OK)
      physicaldrive 2:1   (port 2:id 1 , Parallel SCSI, 72.8 GB, OK)

   array B

      physicaldrive 2:2   (port 2:id 2 , Parallel SCSI, 72.8 GB, OK)
      physicaldrive 2:3   (port 2:id 3 , Parallel SCSI, 72.8 GB, OK)

---

### Post by webdirector on 2010-02-09
when I do in hpacucli " ctrl all show config" iget :
 ctrl all show config

Smart Array 5i in Slot 0      ()

   array A (Parallel SCSI, Unused Space: 0 MB)

      logicaldrive 1 (67.8 GB, RAID 1+0, OK)

      physicaldrive 2:0   (port 2:id 0 , Parallel SCSI, 72.8 GB, OK)
      physicaldrive 2:1   (port 2:id 1 , Parallel SCSI, 72.8 GB, OK)

   array B (Parallel SCSI, Unused Space: 0 MB)

      logicaldrive 2 (67.8 GB, RAID 1+0, Failed)

      physicaldrive 2:2   (port 2:id 2 , Parallel SCSI, 72.8 GB, OK)
      physicaldrive 2:3   (port 2:id 3 , Parallel SCSI, 72.8 GB, OK)

array B as logical drive failed ??

---

### Post by webdirector on 2010-02-11
Can someone help ?

Thanks

---

