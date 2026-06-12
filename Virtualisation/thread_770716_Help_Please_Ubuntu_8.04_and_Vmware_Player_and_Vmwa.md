---
title: "Help Please Ubuntu 8.04 and Vmware Player and Vmware Workstation"
date: 2008-04-27
forum: Virtualisation
---

### Post by cchester on 2008-04-27
Hey Guys,

I need help I am trying to get either my Vmware workstation or Vmware Player working in Ubuntu 8.04 and I am having some problems.

I get the following error:

Making sure services for VMware Workstation are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the theme icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-16-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Unknown VMware Workstation 6.0.3 build 80004 detected. Building for Workstation 6.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config6/vmmon-only'
make -C /lib/modules/2.6.24-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/vmware-config6/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config6/vmmon-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config6/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config6/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-config6/vmmon-only/common/cpuid.o
In file included from include/asm/bitops.h:2,
                 from /tmp/vmware-config6/vmmon-only/./include/vcpuset.h:74,
                 from /tmp/vmware-config6/vmmon-only/./include/modulecall.h:23,
                 from /tmp/vmware-config6/vmmon-only/common/vmx86.h:19,
                 from /tmp/vmware-config6/vmmon-only/common/hostif.h:18,
                 from /tmp/vmware-config6/vmmon-only/common/cpuid.c:15:
include/asm/bitops_32.h:9:2: error: #error only <linux/bitops.h> can be included directly
make[2]: *** [/tmp/vmware-config6/vmmon-only/common/cpuid.o] Error 1
make[1]: *** [_module_/tmp/vmware-config6/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config6/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

So does anyone have any ideas on what I need to do to get this running?

Thanks

---

### Post by olskar on 2008-04-27
I do not know why you get those errors but I recommend you to try virtualbox which is a free counterpart to vmware :)

---

### Post by ninjatiger422 on 2008-04-27
I am having the same problem using VMWare Workstation 6.

I appreciate that Virtualbox is open source however I need USB 2.0 support on my windows vm. Workstation comes with this. While I have read about USB 1.1 support on virtualbox, I have not seen 2.0 support.

My question is:

1. Is it definitively possible to get usb 2.0 (must be 2.0) working on Virtualbox?

if not,

1.5, does anyone know how to get around the above error in Hardy?

Thanks!

---

### Post by Rizlaw on 2008-04-27
> **cchester said:**
> Hey Guys,

I need help I am trying to get either my Vmware workstation or Vmware Player working in Ubuntu 8.04 and I am having some problems.

I get the following error:

Making sure services for VMware Workstation are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the theme icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-16-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Unknown VMware Workstation 6.0.3 build 80004 detected. Building for Workstation 6.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config6/vmmon-only'
make -C /lib/modules/2.6.24-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/vmware-config6/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config6/vmmon-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config6/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config6/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-config6/vmmon-only/common/cpuid.o
In file included from include/asm/bitops.h:2,
                 from /tmp/vmware-config6/vmmon-only/./include/vcpuset.h:74,
                 from /tmp/vmware-config6/vmmon-only/./include/modulecall.h:23,
                 from /tmp/vmware-config6/vmmon-only/common/vmx86.h:19,
                 from /tmp/vmware-config6/vmmon-only/common/hostif.h:18,
                 from /tmp/vmware-config6/vmmon-only/common/cpuid.c:15:
include/asm/bitops_32.h:9:2: error: #error only <linux/bitops.h> can be included directly
make[2]: *** [/tmp/vmware-config6/vmmon-only/common/cpuid.o] Error 1
make[1]: *** [_module_/tmp/vmware-config6/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config6/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

So does anyone have any ideas on what I need to do to get this running?

Thanks

I had the same problem. If you are using VM Workstation 6, the following will work. Assuming you are familiar with working in terminal mode on the command line, execute the following series of commands:

    * unpack VMware-workstation-6.0.3
    * go to vmware-distrib/lib/modules/source
    * untar the file vmmon.tar (tar xvf vmmon.tar)
    * cd vmmon-only/include
    * edit the file vcpuset.h
    * go to line 74
    * change #include “asm/bitops.h” to #include “linux/bitops.h” (Because there are some changes made to the 2.6.24 kernel, it’s not possible to include bitops.h from asm and you will have to include it from the linux directory)
    * go back to vmware-distrib/lib/modules/source
    * remove the old vmmon.tar file (rm vmmon.tar)
    * repack the new vmmon.tar file (tar cvf vmmon.tar vmmon-only)
    * remove vmmon-only directory (rm -rf vmmon-only)


Now go to vmware-distrib directory and install vmware as you usualy do. It should work without a glitch.

---

### Post by danwood76 on 2008-04-27
VMware Server is free and will do everything you want.

Heres an install guide for hardy:
[http://www.bauer-power.net/2008/04/installing-vmware-server-on-ubuntu-804.html](http://www.bauer-power.net/2008/04/installing-vmware-server-on-ubuntu-804.html)

---

### Post by olskar on 2008-04-27
[QUOTE=ninjatiger422;4814255]I am having the same problem using VMWare Workstation 6.

I appreciate that Virtualbox is open source however I need USB 2.0 support on my windows vm. Workstation comes with this. While I have read about USB 1.1 support on virtualbox, I have not seen 2.0 support.

My question is:

1. Is it definitively possible to get usb 2.0 (must be 2.0) working on Virtualbox?

if not,

1.5, does anyone know how to get around the above error in Hardy?

Thanks![/QUOTE

It looks like virtualbox supports USB 2.0 according to a lot of links on google (like this: [http://www.velocityreviews.com/forums/t564607-charlie-virtualbox-with-usb-20-support-released.html](http://www.velocityreviews.com/forums/t564607-charlie-virtualbox-with-usb-20-support-released.html)).

I do not know how but virtualbox have a really good supportforum if you are interested :)

---

### Post by cchester on 2008-04-27
> **Rizlaw said:**
> I had the same problem. If you are using VM Workstation 6, the following will work. Assuming you are familiar with working in terminal mode on the command line, execute the following series of commands:

    * unpack VMware-workstation-6.0.3
    * go to vmware-distrib/lib/modules/source
    * untar the file vmmon.tar (tar xvf vmmon.tar)
    * cd vmmon-only/include
    * edit the file vcpuset.h
    * go to line 74
    * change #include “asm/bitops.h” to #include “linux/bitops.h” (Because there are some changes made to the 2.6.24 kernel, it’s not possible to include bitops.h from asm and you will have to include it from the linux directory)
    * go back to vmware-distrib/lib/modules/source
    * remove the old vmmon.tar file (rm vmmon.tar)
    * repack the new vmmon.tar file (tar cvf vmmon.tar vmmon-only)
    * remove vmmon-only directory (rm -rf vmmon-only)


Now go to vmware-distrib directory and install vmware as you usualy do. It should work without a glitch.

Thanks dude you ROCK! That worked. Don't know how you figured that out but it worked and you ROCK!

THANKS!

---

### Post by davinci0212 on 2008-04-28
> **Rizlaw said:**
> I had the same problem. If you are using VM Workstation 6, the following will work.

Thank you very, very much!!! I found a similar solution on a few other sites but they didn't make clear to edit vcpuset.h from the **vmware-distrib** directory. I was instructed to make the changes from /usr/lib/vmware directory, which of course has no effect on vmware-install.pl. 

Thank you again!!!!! :):):):):):):):)

---

### Post by trmentry on 2008-04-28
> **Rizlaw said:**
> I had the same problem. If you are using VM Workstation 6, the following will work. Assuming you are familiar with working in terminal mode on the command line, execute the following series of commands:

    * unpack VMware-workstation-6.0.3
    * go to vmware-distrib/lib/modules/source
    * untar the file vmmon.tar (tar xvf vmmon.tar)
    * cd vmmon-only/include
    * edit the file vcpuset.h
    * go to line 74
    * change #include “asm/bitops.h” to #include “linux/bitops.h” (Because there are some changes made to the 2.6.24 kernel, it’s not possible to include bitops.h from asm and you will have to include it from the linux directory)
    * go back to vmware-distrib/lib/modules/source
    * remove the old vmmon.tar file (rm vmmon.tar)
    * repack the new vmmon.tar file (tar cvf vmmon.tar vmmon-only)
    * remove vmmon-only directory (rm -rf vmmon-only)


Now go to vmware-distrib directory and install vmware as you usualy do. It should work without a glitch.


Whoohoo!  This worked for me.  Thank you very much.

---

### Post by caseywise on 2008-04-30
Thanks for sharing your knowledge, Rizlaw.  I likely wouldn't have gotten this, my shell-fu is nowhere near as strong as yours!  Thank you again, it worked perfectly!

---

### Post by munozm on 2008-04-30
> **Rizlaw said:**
> I had the same problem. If you are using VM Workstation 6, the following will work. 

Just wanted to add that this worked for me as well.  I had a previous 5.5 copy on my machine and upgraded to VMware Workstation 6.0.3 build-80004 (when upgraded to Ubuntu 8.04).

I found patches on the web but none worked for me.  These instructions worked great.  Thanks.

---

### Post by Etiksan on 2008-05-02
> **Rizlaw said:**
> I had the same problem. If you are using VM Workstation 6, the following will work. Assuming you are familiar with working in terminal mode on the command line, execute the following series of commands:

    * unpack VMware-workstation-6.0.3
    * go to vmware-distrib/lib/modules/source
    * untar the file vmmon.tar (tar xvf vmmon.tar)
    * cd vmmon-only/include
    * edit the file vcpuset.h
    * go to line 74
    * change #include “asm/bitops.h” to #include “linux/bitops.h” (Because there are some changes made to the 2.6.24 kernel, it’s not possible to include bitops.h from asm and you will have to include it from the linux directory)
    * go back to vmware-distrib/lib/modules/source
    * remove the old vmmon.tar file (rm vmmon.tar)
    * repack the new vmmon.tar file (tar cvf vmmon.tar vmmon-only)
    * remove vmmon-only directory (rm -rf vmmon-only)


Now go to vmware-distrib directory and install vmware as you usualy do. It should work without a glitch.

thanks for your help !

---

### Post by pan69 on 2008-05-02
Hi. I'm having issues compiling 5.5.6 (bought a license for 5 about a year ago and haven't upgraded to 6 and probably not going to 'cos all vmware gives me is greef). Anyways, I paid money for this stuff and all the vmware website wants to do is shove a new version down my throat. If 'll be so kind to shell out another couple of hundred.

Starting with a full installation (after doing to tip given for 6)
```

$ sudo ./vmware-install.pl 

```

```

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.24-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:48:
/tmp/vmware-config1/vmmon-only/./include/vm_basic_types.h:160: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.c:80:
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
/tmp/vmware-config1/vmmon-only/linux/driver.c:145: warning: initialisation from incompatible pointer type
/tmp/vmware-config1/vmmon-only/linux/driver.c:149: warning: initialisation from incompatible pointer type
/tmp/vmware-config1/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config1/vmmon-only/linux/driver.c:1661: error: ‘struct mm_struct’ has no member named ‘dumpable’
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

Alas. With previous Ubuntu (kernel) upgrades I had to recompile and it always worked without to much hassle. This time it seems all to be f'ed.

Any help would be very much appreciated 'cos the vmware website doesn't seem to be capable of doing that.

Thanks,
Luke

---

### Post by pan69 on 2008-05-03
In the end I found my answer here: [http://blog.creonfx.com/linux/how-to-install-vmware-player-workstation-on-2624-kernel](http://blog.creonfx.com/linux/how-to-install-vmware-player-workstation-on-2624-kernel)

One of the comments:
> 
#  gregster Says:
March 6th, 2008 at 9:11 am

I’m running Hardy alpha 5 (2.6.24-11 generic)
The tip works, but only if g++ is installed.
When trying to run VMWare (Server 1.04) I then had problems like this:
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0&#8242; not found (required by /usr/lib/libstdc++.so.6)

So I ran these commands:
cd /usr/lib/vmware/lib/libpng12.so.0
sudo mv libpng12.so.0 libpng12.so.0.old
sudo ln -sf /usr/lib/libpng12.so.0 libpng12.so.0
cd /usr/lib/vmware/lib/libgcc_s.so.1
sudo mv libgcc_s.so.1 libgcc_s.so.1.old
sudo ln -sf /lib/libgcc_s.so.1
(hope that’s clear…)

Now it seems to be OK.


Thanks gregster!!!

> **pan69 said:**
> Hi. I'm having issues compiling 5.5.6 (bought a license for 5 about a year ago and haven't upgraded to 6 and probably not going to 'cos all vmware gives me is greef). Anyways, I paid money for this stuff and all the vmware website wants to do is shove a new version down my throat. If 'll be so kind to shell out another couple of hundred.

Starting with a full installation (after doing to tip given for 6)
```

$ sudo ./vmware-install.pl 

```

```

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.24-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:48:
/tmp/vmware-config1/vmmon-only/./include/vm_basic_types.h:160: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.c:80:
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
/tmp/vmware-config1/vmmon-only/linux/driver.c:145: warning: initialisation from incompatible pointer type
/tmp/vmware-config1/vmmon-only/linux/driver.c:149: warning: initialisation from incompatible pointer type
/tmp/vmware-config1/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config1/vmmon-only/linux/driver.c:1661: error: ‘struct mm_struct’ has no member named ‘dumpable’
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

Alas. With previous Ubuntu (kernel) upgrades I had to recompile and it always worked without to much hassle. This time it seems all to be f'ed.

Any help would be very much appreciated 'cos the vmware website doesn't seem to be capable of doing that.

Thanks,
Luke

---

### Post by anupkshah on 2008-05-04
Thanks for those instructions. Just confirming they worked for VMWare Player too.

---

### Post by RikardSvenningsen on 2008-05-06
Amazing how you do it, it works for me to.
PS!
Don't try it on Workstation 6.0.2, that don't work.
:guitar:

---

### Post by scrime on 2008-05-17
FWIW I think a slightly easier way of doing this might be to use a file I found on Google, vmware-any-any-update-116.tgz.  VMWare has had this vmon bug for the last several versions, so instead of manually editing that file this file seems to do that for you.  I helped me with Workstation and server.

---

### Post by Christian Groove on 2008-05-17
> **olskar said:**
> [QUOTE=ninjatiger422;4814255]I am having the same problem using VMWare Workstation 6.

> I appreciate that Virtualbox is open source however I need USB

Salut Olskar,

i assume that you do not own a nVidia-Card, cause 
VirtualBox that has been shipped with Ubuntu8.04
will completly mess up your configuration.
I testet this for two times with the same
result. Iff you have the accelerated nvidia-driver
loaded and load the the virtualbox-modules-generic
then there will be a conflict that cause the
nvidia-kernel module to stop working.

I could reproduce this on my Dell M90 Laptop,
that caused me to reinstall Kubuntu for 2 times.


I do not know how but virtualbox have a really good supportforum if you are interested :)

---

### Post by pangloss on 2008-05-22
In order to get wireless bridging to work, I also had to apply the following patch: [http://www.hauke-m.de/fileadmin/vmware/vmware-wireless.patch]("http://www.hauke-m.de/fileadmin/vmware/vmware-wireless.patch")

So, the full set of instructions, including Rizlaw's instructions:
```
tar xvzf VMware-workstation-6.0.3-80004.i386.tar.gz
cd vmware-distrib/lib/modules/source/
tar xvf vmmon.tar
sed -i'' -e's/#include "asm\/bitops.h"/#include "linux\/bitops.h"/' vmmon-only/include/vcpuset.h
rm vmmon.tar
tar cvf vmmon.tar vmmon-only
rm -rf vmmon-only

tar xvf vmnet.tar
sed -i'' -e's/#ifdef CONFIG_NET_RADIO/#if defined CONFIG_NET_RADIO || defined CONFIG_WLAN_80211/' vmnet-only/bridge.c
sed -i'' -e's/#if !defined(CONFIG_NET_RADIO)/#if !defined CONFIG_NET_RADIO \&\& !defined CONFIG_WLAN_80211/' vmnet-only/bridge.c
rm vmnet.tar
tar cvf vmnet.tar vmnet-only
rm -rf vmnet-only
cd ../../../
```

Moreover, as I'm using an Atheros card, I also had to apply the patch attached to [http://madwifi.org/ticket/407]("http://madwifi.org/ticket/407") (note: you should have installed build-essential):

```
wget http://downloads.sourceforge.net/madwifi/madwifi-0.9.4.tar.gz
tar xvzf madwifi-0.9.4.tar.gz
cd madwifi-0.9.4/
sed -i'' -e's/#define USE_HEADERLEN_RESV\t1/#undef USE_HEADERLEN_RESV/' net80211/if_athproto.h
make clean
make
sudo make install
```

(remove the old module when prompted by make install)

---

### Post by sunbird on 2008-05-29
Trying to get VMplayerx64 running on my 8.04x64 install. I've tried each method listed here and still get this error every time:

```

$ /usr/bin/vmplayer
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

```

I've tried the any-any patch and the other steps mentioned here but nothing seems to work. Each of the modules "loads perfectly" during the install, with warnings, but bridged networking service fails to start. The vmware-any-any gives an error:

```

vmware-any-any-update116$ sudo ./runme.pl 
Updating /usr/bin/vmware ... failed
Cannot open /usr/bin/vmware: No such file or directory
Updating /usr/bin/vmnet-bridge ... No patch needed/available
Updating /usr/lib/vmware/bin/vmware-vmx ... No patch needed/available
Updating /usr/lib/vmware/bin-debug/vmware-vmx ... No patch needed/available
VMware modules in "/usr/lib/vmware/modules/source" has been updated.

```

And here's vmconfig.pl:

```

Making sure services for VMware Player are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Blocking file system:                                               done
   Bridged networking on /dev/vmnet0                                   done
   Host network detection                                              done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   Bridged networking on /dev/vmnet2                                   done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the theme icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Player is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-17-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Unknown VMware Workstation 6.0.3 build 80004 detected. Building for Workstation 6.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.24-17-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-17-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/task.o
cc1plus: warning: command line option "-Werror-implicit-function-declaration" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wdeclaration-after-statement" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wno-pointer-sign" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
In file included from /tmp/vmware-config0/vmmon-only/common/task.c:1194:
/tmp/vmware-config0/vmmon-only/common/task_compat.h: In function &#8216;void Task_Switch_V45(VMDriver*, Vcpuid)&#8217;:
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2666: warning: &#8216;sysenterState.SysenterStateV45::validEIP&#8217; may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2666: warning: &#8216;sysenterState.SysenterStateV45::cs&#8217; may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2666: warning: &#8216;sysenterState.SysenterStateV45::rsp&#8217; may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2666: warning: &#8216;sysenterState.SysenterStateV45::rip&#8217; may be used uninitialized in this function
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciContext.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciDatagram.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciDriver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciDs.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciGroup.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciHashtable.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciProcess.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciResource.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciSharedMem.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config0/vmmon-only/vmcore/compat.o
  CC [M]  /tmp/vmware-config0/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config0/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-17-generic'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
The module loads perfectly in the running kernel.

/dev is dynamic:
Trying to find a suitable vmblock module for your running kernel.

None of the pre-built vmblock modules for VMware Player is suitable for your 
running kernel.  Do you want this program to try to build the vmblock module 
for your system (you need to have a C compiler installed on your system)? 
[yes] 

Extracting the sources of the vmblock module.

Building the vmblock module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmblock-only'
make -C /lib/modules/2.6.24-17-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-17-generic'
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/block.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/control.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/dbllnklst.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/dentry.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/file.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/filesystem.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/inode.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/module.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/stubs.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/super.o
  LD [M]  /tmp/vmware-config0/vmblock-only/vmblock.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config0/vmblock-only/vmblock.mod.o
  LD [M]  /tmp/vmware-config0/vmblock-only/vmblock.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-17-generic'
cp -f vmblock.ko ./../vmblock.o
make: Leaving directory `/tmp/vmware-config0/vmblock-only'
The module loads perfectly in the running kernel.

/dev is dynamic:
You have already setup networking.

Would you like to skip networking setup and keep your old settings as they are?
(yes/no) [no] 

Do you want networking for your virtual machines? (yes/no/help) [yes] 

Would you prefer to modify your existing networking configuration using the 
wizard or the editor? (wizard/editor/help) [wizard] 

The following bridged networks have been defined:

. vmnet0 is bridged to ath0
. vmnet2 is bridged to eth0

All your ethernet interfaces are already bridged.

Do you want to be able to use NAT networking in your virtual machines? (yes/no)
[yes] 

The following NAT networks have been defined:

. vmnet8 is a NAT network on private subnet 192.168.3.0.

Do you wish to configure another NAT network? (yes/no) [no] 

Do you want to be able to use host-only networking in your virtual machines? 
[yes] 

The following host-only networks have been defined:

. vmnet1 is a host-only network on private subnet 193.168.4.0.

Do you wish to configure another host-only network? (yes/no) [no] 

Trying to find a suitable vmnet module for your running kernel.

None of the pre-built vmnet modules for VMware Player is suitable for your 
running kernel.  Do you want this program to try to build the vmnet module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Extracting the sources of the vmnet module.

Building the vmnet module.

Unknown VMware Workstation 6.0.3 build 80004 detected. Building for Workstation 6.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmnet-only'
make -C /lib/modules/2.6.24-17-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-17-generic'
  CC [M]  /tmp/vmware-config0/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config0/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config0/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/bridge.o
  CC [M]  /tmp/vmware-config0/vmnet-only/filter.o
  CC [M]  /tmp/vmware-config0/vmnet-only/procfs.o
  CC [M]  /tmp/vmware-config0/vmnet-only/smac_compat.o
  CC [M]  /tmp/vmware-config0/vmnet-only/smac_linux.x86_64.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config0/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-17-generic'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config0/vmnet-only'
The module loads perfectly in the running kernel.

Starting VMware services:
   Virtual machine monitor                                             done
   Blocking file system:                                               done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host network detection                                              done
   Host-only networking on /dev/vmnet1 (background)                    done
   DHCP server on /dev/vmnet1                                          done
   Bridged networking on /dev/vmnet2                                   done
   Host-only networking on /dev/vmnet8 (background)                    done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done

The configuration of VMware Player 2.0.3 build-80004 for Linux for this running
kernel completed successfully.

You can now run VMware Player by invoking the following command: 
"/usr/bin/vmplayer".

```

I'm a noob so sorry if the answer is obvious.

---

### Post by sunbird on 2008-05-31
**Bump**. Anyone?

---

### Post by danwood76 on 2008-05-31
did the vmnet module compile properly during install of vmware?

---

### Post by sunbird on 2008-05-31
*I'm going to move my question over to [this post in the virtualization forum]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=5086063"). So please post any replies there.*

Danwood: See my earlier post. The module seems to have compiled fine, but the module fails to start:

```

Unknown VMware Workstation 6.0.3 build 80004 detected. Building for Workstation 6.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmnet-only'
make -C /lib/modules/2.6.24-17-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-17-generic'
  CC [M]  /tmp/vmware-config0/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config0/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config0/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/bridge.o
  CC [M]  /tmp/vmware-config0/vmnet-only/filter.o
  CC [M]  /tmp/vmware-config0/vmnet-only/procfs.o
  CC [M]  /tmp/vmware-config0/vmnet-only/smac_compat.o
  CC [M]  /tmp/vmware-config0/vmnet-only/smac_linux.x86_64.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config0/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-17-generic'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config0/vmnet-only'
The module loads perfectly in the running kernel.

Starting VMware services:
   Virtual machine monitor                                             done
   Blocking file system:                                               done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed

```

---

### Post by brunomk8 on 2008-06-11
> 
In order to get wireless bridging to work, I also had to apply the following patch: [http://www.hauke-m.de/fileadmin/vmwa...wireless.patch](http://www.hauke-m.de/fileadmin/vmwa...wireless.patch)

So, the full set of instructions, including Rizlaw's instructions:
Code:

tar xvzf VMware-workstation-6.0.3-80004.i386.tar.gz
cd vmware-distrib/lib/modules/source/
tar xvf vmmon.tar
sed -i'' -e's/#include "asm\/bitops.h"/#include "linux\/bitops.h"/' vmmon-only/include/vcpuset.h
rm vmmon.tar
tar cvf vmmon.tar vmmon-only
rm -rf vmmon-only

tar xvf vmnet.tar
sed -i'' -e's/#ifdef CONFIG_NET_RADIO/#if defined CONFIG_NET_RADIO || defined CONFIG_WLAN_80211/' vmnet-only/bridge.c
sed -i'' -e's/#if !defined(CONFIG_NET_RADIO)/#if !defined CONFIG_NET_RADIO \&\& !defined CONFIG_WLAN_80211/' vmnet-only/bridge.c
rm vmnet.tar
tar cvf vmnet.tar vmnet-only
rm -rf vmnet-only
cd ../../../

Moreover, as I'm using an Atheros card, I also had to apply the patch attached to [http://madwifi.org/ticket/407](http://madwifi.org/ticket/407) (note: you should have installed build-essential):

Code:

wget [http://downloads.sourceforge.net/madwifi/madwifi-0.9.4.tar.gz](http://downloads.sourceforge.net/madwifi/madwifi-0.9.4.tar.gz)
tar xvzf madwifi-0.9.4.tar.gz
cd madwifi-0.9.4/
sed -i'' -e's/#define USE_HEADERLEN_RESV\t1/#undef USE_HEADERLEN_RESV/' net80211/if_athproto.h
make clean
make
sudo make install

(remove the old module when prompted by make install)



PANGLOSS, this works with bcm43xx driver installed with ndiswrapper? In my Ubuntu 8.04 kernel 2.6.24-16-generic doesn't works...

:(

---

### Post by Brain_of_J on 2008-06-13
> **danwood76 said:**
> VMware Server is free and will do everything you want.

Heres an install guide for hardy:
[http://www.bauer-power.net/2008/04/installing-vmware-server-on-ubuntu-804.html](http://www.bauer-power.net/2008/04/installing-vmware-server-on-ubuntu-804.html)

I'm trying to follow his instructions listed on the click-through of the above page
[http://www.bauer-power.net/2007/07/installing-free-vmware-server-on-ubuntu.html](http://www.bauer-power.net/2007/07/installing-free-vmware-server-on-ubuntu.html)

But am having trouble with the instructions.
the line:
sudo aptitude install linux-headers-`uname -r` build-essential

returns a 'Couldn't find any package whose name or description matched "build-essential" '
'Couldn't find any package whose name or description matched "uname -r" '

I'm a complete newbie to any form of linux so please be patient with me.  (i also tried substituting in my user name for uname but that returned the same error)

Ideas?

---

### Post by danwood76 on 2008-06-13
the uname-r displays your current kernel version.
This is basically downloading the stuff required ot build the virtual networking modules.

Check that you have all the repositories enabled in System -> Administration -> Software Sources.
Then do the following to install the packages required:
```

sudo apt-get update
sudo apt-get install linux-headers-`uname -r` build-essential

```
Just copy and paste those lines into the terminal.

---

### Post by Brain_of_J on 2008-06-16
> 
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-18-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Building for VMware Server 1.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.24-18-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-18-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/cpuid.o
In file included from include/asm/bitops.h:2,
                 from /tmp/vmware-config1/vmmon-only/./include/vcpuset.h:74,
                 from /tmp/vmware-config1/vmmon-only/./include/modulecall.h:23,
                 from /tmp/vmware-config1/vmmon-only/common/vmx86.h:19,
                 from /tmp/vmware-config1/vmmon-only/common/hostif.h:18,
                 from /tmp/vmware-config1/vmmon-only/common/cpuid.c:15:
include/asm/bitops_32.h:9:2: error: #error only <linux/bitops.h> can be included directly
make[2]: *** [/tmp/vmware-config1/vmmon-only/common/cpuid.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-18-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

The commands you gave me worked but when I got to the portion of the instructions to install the patch, it errored out after stating the the line about the prebuilt vmmon modules.

Ideas?

edit:

This is beyond weird.
I downloaded the any-any patch again (this time version 116) and placed it in my home directory (following the directions mentioned before). I deleted version 115 of the any-any patch)
I re-ran the vmware installation (following the instructions from before) and it installed correctly but without my having to expressly install the newer version of the any-any patch.
However, the output from the install stated that i'd have to input a the serial code for vmware to run. I was following the instructions on downloading and installing the FREE version of vmware...double weird.

---

### Post by Brain_of_J on 2008-06-17
delete please (sorry for the double post)

---

### Post by danwood76 on 2008-06-18
When you install vmware server you get given a serial number on the download page.
Its completely free still.

On the link I gave it does say to use v116 of the any any patch.

---

### Post by Brain_of_J on 2008-06-18
I'll look for the serial number then.
Thanks for the help.

---

### Post by topoignaz on 2008-09-12
It also worked for VMware Player 2.0.3 build-80004 on Ubuntu Hardy. Many thanks, Rizlaw.



> **Rizlaw said:**
> I had the same problem. If you are using VM Workstation 6, the following will work. Assuming you are familiar with working in terminal mode on the command line, execute the following series of commands:

    * unpack VMware-workstation-6.0.3
    * go to vmware-distrib/lib/modules/source
    * untar the file vmmon.tar (tar xvf vmmon.tar)
    * cd vmmon-only/include
    * edit the file vcpuset.h
    * go to line 74
    * change #include “asm/bitops.h” to #include “linux/bitops.h” (Because there are some changes made to the 2.6.24 kernel, it’s not possible to include bitops.h from asm and you will have to include it from the linux directory)
    * go back to vmware-distrib/lib/modules/source
    * remove the old vmmon.tar file (rm vmmon.tar)
    * repack the new vmmon.tar file (tar cvf vmmon.tar vmmon-only)
    * remove vmmon-only directory (rm -rf vmmon-only)


Now go to vmware-distrib directory and install vmware as you usualy do. It should work without a glitch.

---

### Post by kiloraw on 2008-10-30
Hey everyone I just switched to Ubuntu...vista crash .....but i still need some type of windows...going to use xp since my college depends on it. I had a Vmware license on windows which I going to use now on Ubuntu. So read through this thread and saw the acheivement of the install of Vmware. But it said in the "answer to, how to install vmware" that if you know the terminal,...well I dont know it know that well, so if someone could show me step by step that would be awesome. Thank you.

---

### Post by rbmorse on 2008-10-30
Go to [www.vmware.com]("http://www.vmware.com") and download Workstation 6.5 for linux to your desktop (choose the 32-bit or 64-bit package as appropriate for your Linux installation). When the download is complete, right click on the package (somethingsomething.bundle) and then click properties and then permissions.  Put a check mark in the box labeled "allow executing file as program" and close the file browser window. 

From the Ubuntu menu panel select applications > accessories > terminal.  That should open a user terminal window.  With the mouse, grab the right side of the window and drag it to the right (make the terminal bigger).  At the terminal prompt enter:

cd Desktop<enter> where <enter> is the <enter> key. Note the capital "D" in desktop

Then enter:

sudo ./VMwar<tab>  where <tab> is the <tab> key. That should auto complete the file name of the bundle package and place the cursor at the end of the line.  Press the <enter> key. Enter your user password when prompted. 

Accept the license agreement. At the next screen it will ask you for a path to the eclipse debugger. Leave the dialog box empty and click on forward. That should start the installer.  You should have to do nothing else until the installer finishes. If it starts asking lots of questions, just press the <enter> key to accept the default. 

Once the installer finishes, go to the Ubuntu menu panel and click on Applications > System Tools > VMware workstation.  That should start the main VMware application program.  Click on the "about" menu and enter the license information in the appropriate location.  After that, you can create a new XP VM or assign an existing VM as desired.  

Don't forget to install/reinstall VMWare tools into the virtual machine.

---

### Post by kiloraw on 2008-10-30
rbmorse, because of you, I will now stick with open source software and Ubuntu. i honsetly mean this. I would never have gotten such a quick response from windows or any other forum for that matter. Thank you very much.
                                          kilo

---

### Post by RikardSvenningsen on 2008-11-01
Ubuntu did change my world.
Sorry I don't know where to put this acknowledged to the open source community, so here it comes. (Some Administrator might want to move it that's ok.)
I only use Ubuntu on Desktop, Before that I used Windows 2k. and Vmware Workstation, I use it for lab test of programs or isolation off special program witch i later export to Company users running Vmplayer on Windows. My shift to Ubuntu went on becouse of my Windows machine broke once in a monthly basic witch I spend to much power on. After turning to Ubuntu and VmWare Workstation for Linux I haven't done any reinstall that's to years now. 
Private I only uses Ubuntu and OpenOffice I have been using OpenOffice since version 1.0 now I planing to use it in the company instead of MS Office.

I Could tell more storrys about Open Source and Linux in real life but that's probably not here to go...

Thanks anyway to all off you help full guys.

---

### Post by Megatrom on 2008-11-28
> **Rizlaw said:**
> I had the same problem. If you are using VM Workstation 6, the following will work.**[SIZE="5"] Assuming you are familiar with working in terminal mode on the command line[/SIZE]**, execute the following series of commands:

    * unpack VMware-workstation-6.0.3
    * go to vmware-distrib/lib/modules/source
    * untar the file vmmon.tar (tar xvf vmmon.tar)
    * cd vmmon-only/include
    * edit the file vcpuset.h
    * go to line 74
    * change #include “asm/bitops.h” to #include “linux/bitops.h” (Because there are some changes made to the 2.6.24 kernel, it’s not possible to include bitops.h from asm and you will have to include it from the linux directory)
    * go back to vmware-distrib/lib/modules/source
    * remove the old vmmon.tar file (rm vmmon.tar)
    * repack the new vmmon.tar file (tar cvf vmmon.tar vmmon-only)
    * remove vmmon-only directory (rm -rf vmmon-only)


Now go to vmware-distrib directory and install vmware as you usualy do. It should work without a glitch.

I am not, can someone walk me through this please???

---

### Post by dpj23 on 2008-11-30
I just fixed the error you have posted.  To do so I downloaded and installed workstation  6.0.1-55017.i386 this version installed without the problems you outlined... 

I hope this information helps...  email if you need more specific instructions...

---

