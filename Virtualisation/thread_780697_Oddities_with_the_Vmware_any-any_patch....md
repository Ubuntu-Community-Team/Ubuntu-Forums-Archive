---
title: "Oddities with the Vmware any-any patch..."
date: 2008-05-03
forum: Virtualisation
---

### Post by diablo75 on 2008-05-03
I am trying to install VMware Server, using a tutorial I found here:

[http://ubuntu-tutorials.com/2008/05/03/install-vmware-server-105-on-ubuntu-804-hardy/](http://ubuntu-tutorials.com/2008/05/03/install-vmware-server-105-on-ubuntu-804-hardy/)

It looks very similar to the sticky here, if not identical.

The oddities arise when I execute the ./runme.pl patch.  I've isolated what I'm refering to:

> Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

/usr/share/applications/vmware-server.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
/usr/share/applications/vmware-console-uri-handler.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-16-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Building for VMware Server 1.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.24-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/task.o
[COLOR="Red"]cc1plus: warning: command line option "-Werror-implicit-function-declaration" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wdeclaration-after-statement" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wno-pointer-sign" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-ffreestanding" is valid for C/ObjC but not for C++
In file included from /tmp/vmware-config1/vmmon-only/common/task.c:1194:
/tmp/vmware-config1/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMCrossPage*, VMDriver*) [with VMCrossPage = VMCrossPageV321]’:
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2491: warning: ‘sysenterState.SysenterStateV45::rsp’ is used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rsp’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2492: warning: ‘sysenterState.SysenterStateV45::rip’ is used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rip’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::validEIP’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::cs’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMCrossPage*, VMDriver*) [with VMCrossPage = VMCrossPageV3]’:
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2491: warning: ‘sysenterState.SysenterStateV45::rsp’ is used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rsp’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2492: warning: ‘sysenterState.SysenterStateV45::rip’ is used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rip’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::validEIP’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::cs’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMCrossPage*, VMDriver*) [with VMCrossPage = VMCrossPageGSX1]’:
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2491: warning: ‘sysenterState.SysenterStateV45::rsp’ is used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rsp’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2492: warning: ‘sysenterState.SysenterStateV45::rip’ is used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rip’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::validEIP’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::cs’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMCrossPage*, VMDriver*) [with VMCrossPage = VMCrossPageV2]’:
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2491: warning: ‘sysenterState.SysenterStateV45::rsp’ is used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rsp’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2492: warning: ‘sysenterState.SysenterStateV45::rip’ is used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rip’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::validEIP’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::cs’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM_V4(VMDriver*, Vcpuid) [with VMCrossPage = VMCrossPageV4]’:
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::validEIP’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::cs’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::rsp’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rsp’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::rip’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rip’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMDriver*, Vcpuid)’:
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2491: warning: ‘sysenterState.SysenterStateV45::rsp’ is used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rsp’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2492: warning: ‘sysenterState.SysenterStateV45::rip’ is used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rip’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::validEIP’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::cs’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::validEIP’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::cs’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::rsp’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rsp’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::rip’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rip’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::validEIP’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::cs’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::rsp’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rsp’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::rip’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rip’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h: In function ‘void Task_Switch_V45(VMDriver*, Vcpuid)’:
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2666: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2666: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2666: warning: ‘sysenterState.SysenterStateV45::rsp’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2666: warning: ‘sysenterState.SysenterStateV45::rip’ may be used uninitialized in this function[/COLOR]
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmciContext.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmciDatagram.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmciDriver.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmciDs.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmciGroup.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmciHashtable.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmciProcess.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmciResource.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmciSharedMem.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config1/vmmon-only/vmcore/compat.o
  CC [M]  /tmp/vmware-config1/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config1/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config1/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config1/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
The module loads perfectly in the running kernel.

After the install is finished, and after creating the symbolic links, I tried to run Vmware from the Applications>Other menu, but the only thing that happens is a task bar item appearing for about 10 seconds that says "Starting VMware" and then it goes away.  No Vmware to be found.

I uninstalled VMware Server with "sudo vmware-uninstall.pl", and then reinstalled via the guide, but I get the same problem in the end.  Anybody know what's wrong?

---

### Post by Lord_Phoenix on 2008-05-03
I think this is what you're looking for.
To be sure, just open a terminal and run [COLOR="Red"]vmware[/COLOR]. If it works check out this link, it should solve it.

[http://ubuntuforums.org/showthread.php?t=728536&highlight=vmware+permission+denied]("http://ubuntuforums.org/showthread.php?t=728536&highlight=vmware+permission+denied")

Your compile looks like mine though, pretty much an exact duplicate. I do hope it works for you, because I am getting some lib issues and am not going anywhere fast.

HAL04LoadHALLibraries: Could not dlopen libhal.so.0.
HAL05LoadHALLibraries: Could not dlopen libdbus-1.so.1 or libdbus-1.so.2.
HostDeviceInfoFindHostIDECDROMs: /proc/ide could not be explored. Unable to enumerate host IDE cdroms.

This is what my logs show, I still have no clue how to solve it, am now going to try VirtualBox, maybe that one actually works.

---

### Post by diablo75 on 2008-05-04
Well, I guess I'm going to try and reinstall it again.

Since I've attempted to install this a couple times, I'm assuming there's new files and folders on my drives that were created.  Should I do anything (like find and delete) files containing vmware related stuff and remove them before attempting this again.  I just want to make sure I've got my ducks in a row.  I really need this to work.

---

### Post by fjgaude on 2008-05-04
You do have to remove some items before you can re-install vmware. I've found the best way is to rename the vmware folder to something like vmwarebak and then after the re-install you can delete it. Go to /etc/vmware to do the rename.

```
sudo mv /etc/vmware /etc/vmwarebak
```

Re-install will create a new vmware folder and you should be good to go.

Let us know how you are doing. Notice the new Sticky:

[http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934) #1 post

---

### Post by diablo75 on 2008-05-04
> **fjgaude said:**
> You do have to remove some items before you can re-install vmware. I've found the best way is to rename the vmware folder to something like vmwarebak and then after the re-install you can delete it. Go to /etc/vmware to do the rename.

```
sudo mv /etc/vmware /etc/vmwarebak
```

Re-intall will create a new vmware folder and you should be good to go.

Let us know how you are doing. Notice the new Sticky:

[http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934) #1 post

I'll follow the sticky to the letter and come back with an update a little later.  Thanks for the help!

---

### Post by diablo75 on 2008-05-04
Success!  It was probably human error the first time around, but thanks for the mv command to change the name of my vmware folder.  It appears to be running with no issues now.  Thank you very much!

---

### Post by fjgaude on 2008-05-04
> **diablo75 said:**
> Success!  It was probably human error the first time around, but thanks for the mv command to change the name of my vmware folder.  It appears to be running with no issues now.  Thank you very much!

You know, we all learn something new each day, eh?

---

