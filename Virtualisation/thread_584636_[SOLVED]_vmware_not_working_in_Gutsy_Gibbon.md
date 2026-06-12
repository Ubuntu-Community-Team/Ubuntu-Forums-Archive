---
title: "[SOLVED] vmware not working in Gutsy Gibbon"
date: 2007-10-21
forum: Virtualisation
---

### Post by uroskriznar on 2007-10-21
Does anyone know, why vmware is not working in Gutsy Gibon any more? I upgraded from from Feisty - vmware worked perfectly before.

---

### Post by MegaSvensk on 2007-10-21
Run "sudo /usr/bin/vmware-config.pl" (no quotes) in a terminal window. Allow it to reconfigure the network when it asks.

---

### Post by ziggykg on 2007-10-21
VMware (vmware server to be exact) not working for me either on Gutsy.  On runnning the 'config', I get to the point where it's trying " to build the vmmon module for your system" as it reckons "None of the pre-built vmmon modules for VMware Server is suitable for your running kernel."

It fails trying to build the vmmon module thus:

```

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.22-14-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.c:80:
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

```

Anyone out there who's succeeded in running VMware on Gutsy?

---

### Post by ziggykg on 2007-10-21
Hey,

I've got VMware Server running in Gutsy Gibbon.  To get it working here are some prerequisites:
GCC
G++

If it's still not working, download [http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-any-any-update114.tar.gz]("http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-any-any-update114.tar.gz"), and run 'runme.pl'

---

### Post by Rumo on 2007-10-21
You need the vmware kernel modules for your kernel. They were in the feisty commercial repository but aren't build yet for gutsy. However, I'm pretty optimistic that they will appear in the gutsy canonical partner repository pretty soon (activate this repository in your /etc/apt/sources.list and wait for a couple of weeks).

You can of course build the modules yourself. I have done this several times in the past and am now to lazy to do it again (so I'm running gutsy with an 2.6.20 kernel while I wait for the modules from the repo). To do this you'll definitely need the 'build-essential" meta-package and the kernel-header files for your kernel. Just search the forums for a step-by-step tutorials.

---

### Post by uroskriznar on 2007-10-21
For ziggykg: I tried running runme.pl but nothing happens???

uros6@uros6-desktop:~$ cd desktop
bash: cd: desktop: No such file or directory
uros6@uros6-desktop:~$ cd Desktop
uros6@uros6-desktop:~/Desktop$ ls
povabljeni.xls  ubuntu.txt~       vmware-any-any-update114
sinhronizacija  uTorrent.desktop  vmware-any-any-update114.tar.gz
uros6@uros6-desktop:~/Desktop$ cd vmware-any-any-update114
uros6@uros6-desktop:~/Desktop/vmware-any-any-update114$ ls
runme.pl  services.sh  update  update.c  vmblock.tar  vmmon.tar  vmnet.tar
uros6@uros6-desktop:~/Desktop/vmware-any-any-update114$ sudo runme.pl
sudo: runme.pl: command not found
uros6@uros6-desktop:~/Desktop/vmware-any-any-update114$

---

### Post by MegaSvensk on 2007-10-21
Hmm... it rebuilt just fine for me using the config.pl. Although I am using the workstation version, not the server.

---

### Post by uroskriznar on 2007-10-21
**I now ran runme.pl and this is what happened:**

uros6@uros6-desktop:~$ cd Desktop
uros6@uros6-desktop:~/Desktop$ cd vmware-any-any-update114
uros6@uros6-desktop:~/Desktop/vmware-any-any-update114$ sudo runme.pl
sudo: runme.pl: command not found
uros6@uros6-desktop:~/Desktop/vmware-any-any-update114$ ls
runme.pl  services.sh  update  update.c  vmblock.tar  vmmon.tar  vmnet.tar
uros6@uros6-desktop:~/Desktop/vmware-any-any-update114$ sudo ./runme.pl
Updating /usr/bin/vmware ... No patch needed/available
Updating /usr/bin/vmnet-bridge ... No patch needed/available
Updating /usr/lib/vmware/bin/vmware-vmx ... No patch needed/available
Updating /usr/lib/vmware/bin-debug/vmware-vmx ... No patch needed/available
VMware modules in "/usr/lib/vmware/modules/source" has been updated.

Before running VMware for the first time after update, you need to configure it 
for your running kernel by invoking the following command: 
"/usr/bin/vmware-config.pl". Do you want this script to invoke the command for 
you now? [yes] yes

Making sure services for VMware Workstation are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Blocking file system:                                               done
   Bridged networking on /dev/vmnet0                                   done
   Host network detection                                              done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
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

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] yes

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Your kernel was built with "gcc" version "4.1.2", while you are trying to use 
"/usr/bin/gcc" version "4.1.3". This configuration is not recommended and 
VMware Workstation may crash if you'll continue. Please try to use exactly same
compiler as one used for building your kernel. Do you want to go with compiler 
"/usr/bin/gcc" version "4.1.3" anyway? [no] 

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

**If I say yes instead of no this is what happens:**

Your kernel was built with "gcc" version "4.1.2", while you are trying to use 
"/usr/bin/gcc" version "4.1.3". This configuration is not recommended and 
VMware Workstation may crash if you'll continue. Please try to use exactly same
compiler as one used for building your kernel. Do you want to go with compiler 
"/usr/bin/gcc" version "4.1.3" anyway? [no] yes

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] uros6@uros6-desktop:~/Desktop/vmware-any-any-update114$ 

**How should I go from here on?**

---

### Post by uroskriznar on 2007-10-21
Oh, and I tried running vmware workstation in Gutsy with 2.6.20 Kernel like someone suggested, but it doesn't work either,

---

### Post by uroskriznar on 2007-10-21
I solved the problem. Thanks to everyone.

Read: [http://igordevlog.blogspot.com/2007/07/vmware-in-ubuntu-gutsy-kernel-2622.html](http://igordevlog.blogspot.com/2007/07/vmware-in-ubuntu-gutsy-kernel-2622.html)

---

### Post by bodhi.zazen on 2007-10-21
> **uroskriznar said:**
> I solved the problem. Thanks to everyone.

Read: [http://igordevlog.blogspot.com/2007/07/vmware-in-ubuntu-gutsy-kernel-2622.html](http://igordevlog.blogspot.com/2007/07/vmware-in-ubuntu-gutsy-kernel-2622.html)

Nice link, thank you for sharing. I added it to the sticky at the top of thes forum.

---

### Post by marklid on 2007-10-23
> **ziggykg said:**
> Hey,

I've got VMware Server running in Gutsy Gibbon.  To get it working here are some prerequisites:
GCC
G++

If it's still not working, download [http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-any-any-update114.tar.gz]("http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-any-any-update114.tar.gz"), and run 'runme.pl'

Worked a treat ! Cheers :)

---

### Post by Low J. on 2007-10-23
My vmware player disappeared altogether when I did the gutsy gibbon upgrade so I went out just now to the vmware site and downloaded vmware player 2.0.2 and installed it with the defaults and it worked right away without having to apply the patch.

---

### Post by ALittleSlow on 2007-11-14
FWIW:

I upgraded from Fiesty Fox to Gutsy Gibbon and ran vmware-config.pl. The kernel module rebuild failed with these messages:
```

Building the vmmon module.

Building for VMware Workstation 5.5.2 or 5.5.3.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.22-14-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/task.o
cc1plus: warning: command line option "-Wdeclaration-after-statement" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wno-pointer-sign" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-ffreestanding" is valid for C/ObjC but not for C++
include/asm/page.h: In function &#8216;pte_t native_make_pte(long unsigned int)&#8217;:
include/asm/page.h:112: error: expected primary-expression before &#8216;)&#8217; token
include/asm/page.h:112: error: expected &#8216;;&#8217; before &#8216;{&#8217; token
include/asm/page.h:112: error: expected primary-expression before &#8216;.&#8217; token
include/asm/page.h:112: error: expected `;' before &#8216;}&#8217; token
make[2]: *** [/tmp/vmware-config1/vmmon-only/common/task.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

Unable to build the vmmon module.
```

I installed the build-essential package but with the same results. I applied the vmware-any-any patch (version114) mentioned on this thread and the vmmon module built successfully, but with warnings.
Looks like I had used the version 109 patch under Fiesty Fox.

I'm  testing my VM's now. They seem to be taking unusually long to load...
--ALittleSlow

---

### Post by gooboo on 2007-12-19
I see the same behavior. VMware runs under Gutsy Gibbon, but VMs can take up to 5 minutes to start up. In the process, it takes up 100% CPU of my host and essentially locks me out of doing anything else.

Any solution for this one, anyone?

Thanks,
GB

---

### Post by bodhi.zazen on 2007-12-19
I do not have this problem and suggest you start a new thread rather then adding to an unrelated thread marked as "Solved"

---

