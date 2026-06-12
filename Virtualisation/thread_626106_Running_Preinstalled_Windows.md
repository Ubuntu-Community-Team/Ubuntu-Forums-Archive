---
title: "Running Preinstalled Windows"
date: 2007-11-28
forum: Virtualisation
---

### Post by Holmes89 on 2007-11-28
I have Ubuntu running on one hard drive and windows running on another. I'm kind of new to the whole virtualization thing so first off I was wondering what software is best to do this and my other question is can I run my window's partition in a virtual environment with any software without having to reinstall it?

---

### Post by mouseboyx on 2007-11-28
vmware server can mount existing harddrives and boot like you would normaly.

---

### Post by coelho on 2007-11-28
I've played around with VirtualBox and am using QEMU for WinXP

VirtualBox is very easy to use and has a friendly GUI. This might be a good place to start just to see how it works. But I noticed that the CPU meter hangs around 90% all the time even when not doing anything.

QEMU is open source (command line) but there are some GUIs for it: I've settled on Qemu Launcher. And QEMU doesn't do the busy CPU thing all the time.

Some people love VMWare but I haven't tried it.

I tried getting VirtualBox to run off an existing windows partition (it claims to be able to do it via the command line) but I couldn't get it working...

---

### Post by Holmes89 on 2007-11-28
I installed it and try to install the patch and this keeps happening and now the program won't start. Here's what happens:
> Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.22-14-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Building for VMware Server 1.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmmon-only'
make -C /lib/modules/2.6.22-14-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/task.o
cc1plus: warning: command line option "-Wdeclaration-after-statement" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wno-pointer-sign" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-ffreestanding" is valid for C/ObjC but not for C++
include/asm/page.h: In function ‘pte_t native_make_pte(long unsigned int)’:
include/asm/page.h:112: error: expected primary-expression before ‘)’ token
include/asm/page.h:112: error: expected ‘;’ before ‘{’ token
include/asm/page.h:112: error: expected primary-expression before ‘.’ token
include/asm/page.h:112: error: expected `;' before ‘}’ token
make[2]: *** [/tmp/vmware-config2/vmmon-only/common/task.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


What do I do?

---

### Post by Victory on 2007-11-28
You could try following the instructions on this website: [http://www.squidoo.com/use-existing-windows-installation-and-apps-in-ubuntu/](http://www.squidoo.com/use-existing-windows-installation-and-apps-in-ubuntu/)

---

### Post by Holmes89 on 2007-12-05
Ok I have it working now I was just wondering what I need to do to get it finally working. I can start up my old Windows partition but when it finally loads it asks for a licensing key and is unable to connect to the internet to verify it and validate my copy of Windows. What do I need to do next?

---

### Post by n1ght28 on 2007-12-05
hey i followed the above tutorial but when i power up the virtual machine i just get a black screen with an _ cursor, i think this could be to do with my ram, i only have 384mb, any suggestions on what way to divide my ram, i'm running ubuntu and win xp on the virtual machine, its  a cut down version tho which can run at 80 mb ram when nothing is running, also can you edit a preexisting VM or do you just have to create a new one. thanks.

---

### Post by n1ght28 on 2007-12-05
also at the bottom of the window it is saying i don't have VMware tools installed, is it necessary to install this,

---

### Post by Victory on 2007-12-06
The tutorial I linked is for pre-existing windows installations, not for newly created virtual installations.

Holmes: Try out this link for an activation work around. [http://mazimi.wordpress.com/2007/07/11/getting-around-windows-activation-when-virtualizing/](http://mazimi.wordpress.com/2007/07/11/getting-around-windows-activation-when-virtualizing/)

---

### Post by johndoe32102002 on 2008-02-24
> **Holmes89 said:**
> I have Ubuntu running on one hard drive and windows running on another. I'm kind of new to the whole virtualization thing so first off I was wondering what software is best to do this and my other question is can I run my window's partition in a virtual environment with any software without having to reinstall it?

I think people on this thread are veering away from Holmes89's question, which happens to be the same one I have.  I have installed Qemu and want to run a pre-installed Windows XP using Qemu (rather than VMware because it is opensource).

I viewed Qemu Launcher, downloadable here: [http://www.gnomefiles.org/app.php/Qemu_launcher](http://www.gnomefiles.org/app.php/Qemu_launcher), but it failed to solve this problem.  Can someone post the exact command-line code or screenshots of the GUI using Qemu Launcher?

---

