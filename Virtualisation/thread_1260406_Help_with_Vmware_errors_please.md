---
title: "Help with Vmware errors please?"
date: 2009-09-07
forum: Virtualisation
---

### Post by Julian David Pitt on 2009-09-07
Could someone please tell me what these error messages mean when I run Vmware-config.pl please

```
/usr/src/linux-headers-2.6.28-14-generic/arch/x86/include/asm/apicdef.h:132:1: warning: this is the location of the previous definition
/tmp/vmware-config0/vmmon-only/linux/hostif.c: In function ‘HostIF_SetFastClockRate’:
/tmp/vmware-config0/vmmon-only/linux/hostif.c:3441: warning: passing argument 2 of ‘send_sig’ discards qualifiers from pointer target type
  CC [M]  /tmp/vmware-config0/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/task.o
gcc: error trying to exec 'cc1plus': execvp: No such file or directory
make[2]: *** [/tmp/vmware-config0/vmmon-only/common/task.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-14-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.
```
Many thanks in advance.

---

### Post by dk06 on 2009-09-08
Have you installed gcc and the other dependencies for vmware?

> gcc: error trying to exec 'cc1plus': execvp: No such file or directory
means you need to install gcc

[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

---

### Post by Julian David Pitt on 2009-09-08
> means you need to install gcc

Indeed I do have gcc already installed, but I have reinstalled anyway. This is waht I now get when I run vmware-config.pl
```

Building the vmmon module.

Building for VMware Server 1.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.28-14-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-14-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/./include/x86.h:21,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:53:
/tmp/vmware-config1/vmmon-only/./include/x86apic.h:80:1: warning: "APIC_BASE_MSR" redefined
In file included from /usr/src/linux-headers-2.6.28-14-generic/arch/x86/include/asm/fixmap_32.h:29,
                 from /usr/src/linux-headers-2.6.28-14-generic/arch/x86/include/asm/fixmap.h:5,
                 from /usr/src/linux-headers-2.6.28-14-generic/arch/x86/include/asm/apic.h:8,
                 from /usr/src/linux-headers-2.6.28-14-generic/arch/x86/include/asm/smp.h:13,
                 from include/linux/smp.h:30,
                 from include/linux/topology.h:33,
                 from include/linux/mmzone.h:763,
                 from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:16:
/usr/src/linux-headers-2.6.28-14-generic/arch/x86/include/asm/apicdef.h:132:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config1/vmmon-only/./include/x86.h:21,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:53:
/tmp/vmware-config1/vmmon-only/./include/x86apic.h:80:1: warning: "APIC_BASE_MSR" redefined
In file included from /usr/src/linux-headers-2.6.28-14-generic/arch/x86/include/asm/fixmap_32.h:29,
                 from /usr/src/linux-headers-2.6.28-14-generic/arch/x86/include/asm/fixmap.h:5,
                 from /usr/src/linux-headers-2.6.28-14-generic/arch/x86/include/asm/apic.h:8,
                 from /usr/src/linux-headers-2.6.28-14-generic/arch/x86/include/asm/smp.h:13,
                 from include/linux/smp.h:30,
                 from include/linux/topology.h:33,
                 from include/linux/mmzone.h:763,
                 from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:16:
/usr/src/linux-headers-2.6.28-14-generic/arch/x86/include/asm/apicdef.h:132:1: warning: this is the location of the previous definition
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/hostif.o
In file included from /tmp/vmware-config1/vmmon-only/./include/x86.h:21,
                 from /tmp/vmware-config1/vmmon-only/linux/hostif.c:51:
/tmp/vmware-config1/vmmon-only/./include/x86apic.h:80:1: warning: "APIC_BASE_MSR" redefined
In file included from /usr/src/linux-headers-2.6.28-14-generic/arch/x86/include/asm/fixmap_32.h:29,
                 from /usr/src/linux-headers-2.6.28-14-generic/arch/x86/include/asm/fixmap.h:5,
                 from /usr/src/linux-headers-2.6.28-14-generic/arch/x86/include/asm/apic.h:8,
                 from /usr/src/linux-headers-2.6.28-14-generic/arch/x86/include/asm/smp.h:13,
                 from include/linux/smp.h:30,
                 from include/linux/topology.h:33,
                 from include/linux/mmzone.h:763,
                 from include/linux/gfp.h:4,
                 from include/linux/mm.h:8,
                 from /tmp/vmware-config1/vmmon-only/./include/compat_page.h:5,
                 from /tmp/vmware-config1/vmmon-only/linux/hostif.c:18:
/usr/src/linux-headers-2.6.28-14-generic/arch/x86/include/asm/apicdef.h:132:1: warning: this is the location of the previous definition
/tmp/vmware-config1/vmmon-only/linux/hostif.c: In function ‘HostIF_SetFastClockRate’:
/tmp/vmware-config1/vmmon-only/linux/hostif.c:3441: warning: passing argument 2 of ‘send_sig’ discards qualifiers from pointer target type
  CC [M]  /tmp/vmware-config1/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/task.o
[B]gcc: error trying to exec 'cc1plus': execvp: No such file or directory
make[2]: *** [/tmp/vmware-config1/vmmon-only/common/task.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-14-generic'
make: *** [vmmon.ko] Error 2[/B]
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.
```

Your thoughts would be appreciated.

---

### Post by dk06 on 2009-09-08
I had similar errors when I tried installing VMware Workstation on Fedora v11 when it first came out, I ended up going back to v10 to make it work. (the kernel headers were an issue)

Are you running the newest version of Ubuntu? If so, you may want to try a more stable release like 8.04

If you want to wrangle with it, the problem is that it is having trouble building the module(as you probably already noticed).
____________________________________________
Ubuntu thread similar issue w/older version.
[http://ubuntuforums.org/showthread.php?t=606020](http://ubuntuforums.org/showthread.php?t=606020)
____________________________________________

If you wanna make it work with v9.04 or v8.04 here are the step-by-step instructions:
[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

> [SIZE=3][B]
v9.04[/B][/SIZE]
**Installation and Quick Start**

  
**Ubuntu 9.04 (VMWare Server 2.0.1 Build 156745)**

 There is no package yet available. You can download it at [http://www.vmware.com/go/getserver](http://www.vmware.com/go/getserver) 

[LIST=1]
[*]Get a serial number (displayed at the download page link received by email as part of the registration process)
[*]Download the tar.gz file to your home directory
[*]Install required packages
[/LIST]

sudo apt-get install build-essential linux-headers-`uname -r`
[LIST=1]
[*]Download the required patch at [http://ubuntuforums.org/attachment.php?attachmentid=94477&d=1227872015](http://ubuntuforums.org/attachment.php?attachmentid=94477&d=1227872015) and save in your home directory
[*]Unpack, apply patch and run vmware-install.pl
[/LIST]

cd ~
tar zxvf VMware-server-2.0.0-122956.i386.tar.gz

cd vmware-server-distrib
sudo patch ./bin/vmware-config.pl ~/vmware-config.pl.patch.txt
sudo ./vmware-install.pl
[LIST=1]
[*]Follow the settings displayed at your screen and don't change default values if not necessary. **Be sure to add your normal username as VMware Server administrator**
[*]Enter the serial number when prompted
[*]Vmware2 has a web interface. Browse with Firefox to [http://localhost:8222]("http://localhost:8222/").
[*]Log in with your normal username and password
[/LIST]
Note: You can also access the web interface via SSL at [https://localhost:8333]("https://localhost:8333/"). You will probably need to add this site to your SSL Exception sites on your browser. 
> 
[SIZE=4]v8.04[/SIZE]
**Ubuntu 8.04 (VMWare Server 2.0.0 Build 116503)**

 There is no package yet available. You can download it at [http://www.vmware.com/go/getserver](http://www.vmware.com/go/getserver) 

[LIST=1]
[*]Get a serial number (displayed at the download page link received by email as part of the registration process)
[*]Download the tar.gz file
[*]Install the build package
[/LIST]

sudo apt-get install build-essential linux-headers-`uname -r`
[LIST=1]
[*]Unzip and run vmware-install.pl
[*]Follow the settings displayed at your screen and don't change default values if not necessary. **Be sure to add your normal username as VMware Server administrator**
[*]Enter the serial number when prompted
[*]Vmware2 has a web interface. Browse with Firefox to [http://localhost:8222]("http://localhost:8222/").
[*]Log in with your normal username and password
[/LIST]
Note: You can also access the web interface via SSL at [https://localhost:8333]("https://localhost:8333/"). You will probably need to add this site to your SSL Exception sites on your browser. 
If you're using 64bit, there are additional instructions here:
[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

Not sure if you care but VMware works really well on openSUSE and on CentOS 
(and is extremely easy to install)

I've found Sun's Virtualbox to work better w/Ubuntu (just my observation)

---

### Post by dcstar on 2009-09-10
> **Julian David Pitt said:**
> Indeed I do have gcc already installed, but I have reinstalled anyway. This is waht I now get when I run vmware-config.pl
```

Building the vmmon module.

Building for **VMware Server 1.0.0**.
Using 2.6.x kernel build system.
.........
Execution aborted.
```

Your thoughts would be appreciated.

And **exactly** what version of VMware Server are you trying to install?

---

### Post by VMSandman on 2009-09-10
I've heard there are some kernel header issues when installing from a few people.... if you can stomach an earlier version is will "probably" work.

---

### Post by fjgaude on 2009-09-10
From memory the way to fix for kernel issues is to use a program called vmware-update-2.6.27. Run it after you get the compile errors. It has worked from me from about 7.10, 8.04 and all its updates through 8.10 with its 15 or so updates. Here's how to get the patch:

```
wget http://www.insecure.ws/warehouse/vmware-update-2.6.27-5.5.7-2.tar.gz
tar -xvzf vmware-update-2.6.27-5.5.7-2.tar.gz
cd vmware-update-2.6.27-5.5.7-2
./runme.pl
```

After you have successfully done this, try this:
```

/etc/init.d/vmware status
```
At least one instance of VMware Server is still running.

Bridged networking on /dev/vmnet0 is running
Host-only networking on /dev/vmnet1 is running
Host-only networking on /dev/vmnet8 is running
NAT networking on /dev/vmnet8 is running
Module vmmon loaded
Module vmnet loaded

The patch doesn't work yet on 9.10 Alpha 5... we'll have to wait and see if something else comes out.

---

