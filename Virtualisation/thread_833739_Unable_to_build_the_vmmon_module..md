---
title: "Unable to build the vmmon module."
date: 2008-06-18
forum: Virtualisation
---

### Post by tlages on 2008-06-18
I couldn't post this in the installation section but can anyone figure out my error? 
```
Configuring fallback GTK+ 2.4 libraries.

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
kernel? [/lib/modules/2.6.24-19-generic/build/include] /usr/lib/vmware/modules/source/

The path "/usr/lib/vmware/modules/source" is an existing directory, but it does
not contain a "linux" subdirectory as expected.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-19-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config8/vmmon-only'
make -C /lib/modules/2.6.24-19-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /tmp/vmware-config8/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config8/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config8/vmmon-only/linux/driver.c:48:
/tmp/vmware-config8/vmmon-only/./include/vm_basic_types.h:159: error: redefinition of typedef ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config8/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config8/vmmon-only/linux/driver.c:49:
/tmp/vmware-config8/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config8/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config8/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config8/vmmon-only/linux/driver.c:49:
/tmp/vmware-config8/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-config8/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config8/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config8/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config8/vmmon-only/linux/driver.c:1659: error: ‘struct mm_struct’ has no member named ‘dumpable’
make[2]: *** [/tmp/vmware-config8/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config8/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config8/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

tony@tony-desktop:~/Desktop/vmware-server-distrib$ vmware-config.pl
Please re-run this program as the super user.

Execution aborted.

tony@tony-desktop:~/Desktop/vmware-server-distrib$ sudo vmware-config.pl
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Configuring fallback GTK+ 2.4 libraries.

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
kernel? [/lib/modules/2.6.24-19-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config9/vmmon-only'
make -C /lib/modules/2.6.24-19-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /tmp/vmware-config9/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config9/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config9/vmmon-only/linux/driver.c:48:
/tmp/vmware-config9/vmmon-only/./include/vm_basic_types.h:159: error: redefinition of typedef ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config9/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config9/vmmon-only/linux/driver.c:49:
/tmp/vmware-config9/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config9/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config9/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config9/vmmon-only/linux/driver.c:49:
/tmp/vmware-config9/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-config9/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config9/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config9/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config9/vmmon-only/linux/driver.c:1659: error: ‘struct mm_struct’ has no member named ‘dumpable’
make[2]: *** [/tmp/vmware-config9/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config9/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config9/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

---

### Post by hariprs on 2008-06-18
1. Install VMware*, Do all the default choices, but not the compile modules option.

2. Download this patch script: 

[http://download.rsbac.org/tmp/?C=S;O=A](http://download.rsbac.org/tmp/?C=S;O=A)
vmware-any-any-update117.tar.gz

3. Extract all those tar files.

4. 
$cd vmware-any-any-update-117
$sudo ./runme.pl

6. Run the configuration script: sudo vmware-config.pl that should compile all the modules then select your preferred options.

And that's it, run vmware wherever ;)

Other problems:

If you are running the VM from a NTFS partition you need to hack the vm config file(*.vmx) and add this line:

mainmem.UseNamedFile = "FALSE"

---

### Post by tlages on 2008-06-18
That worked! thank you. But now when I try to start it, it won't start. It shows in my taskbar as loading, but never loads.

---

### Post by bodhi.zazen on 2008-06-18
See the thread on the top of these forums.

FYI any-any update is no longer needed (with VMWare server 1.0.6)

I found the ant-any-update-117 was not working on 1.0.5 and fell back to any-any-116.

Your mileage may vary.

The vmware section reviews pot-install configuration and troubbleshooting as well.

HTH.

---

### Post by gtdaqua on 2008-06-19
> **bodhi.zazen said:**
> See the thread on the top of these forums.

FYI any-any update is no longer needed (with VMWare server 1.0.6)



False. It is still required in 64 bit editions. See [here]("http://ubuntuforums.org/showthread.php?t=826624") for a guide no 64-bit installs.

---

### Post by bodhi.zazen on 2008-06-19
> **gtdaqua said:**
> False. It is still required in 64 bit editions. See [here]("http://ubuntuforums.org/showthread.php?t=826624") for a guide no 64-bit installs.

I installed VMWare server 1.0.6 on 2 64 bit machines without any problem and no need for the any-any-update.

---

### Post by bodhi.zazen on 2008-06-19
> **gtdaqua said:**
> False. It is still required in 64 bit editions. See [here]("http://ubuntuforums.org/showthread.php?t=826624") for a guide no 64-bit installs.

I installed VMWare server 1.0.6 on 2 64 bit machines without any problem and no need for the any-any-update.

Thank you for the link though I will look at it.

---

### Post by hariprs on 2008-06-20
> **bodhi.zazen said:**
> See the thread on the top of these forums.

FYI any-any update is no longer needed (with VMWare server 1.0.6)

I found the ant-any-update-117 was not working on 1.0.5 and fell back to any-any-116.

Your mileage may vary.

The vmware section reviews pot-install configuration and troubbleshooting as well.

HTH.

Hi, It doesnot depend on arch, it depends on the kernel version.

---

