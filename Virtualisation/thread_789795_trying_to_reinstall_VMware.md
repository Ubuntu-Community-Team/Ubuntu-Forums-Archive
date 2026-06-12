---
title: "trying to reinstall VMware"
date: 2008-05-10
forum: Virtualisation
---

### Post by ant2ne on 2008-05-10
```
ant2ne@2ne-buntu:~$ sudo apt-get install vmware-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmp4-info-perl libio-string-perl libaudio-wav-perl
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  vmware-server
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
Need to get 0B/79.4MB of archives.
After this operation, 131MB of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 120784 files and directories currently installed.)
Unpacking vmware-server (from .../vmware-server_1.0.4-1gutsy2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/vmware-server_1.0.4-1gutsy2_amd64.deb (--unpack):
 trying to overwrite `/usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so', which is also in package ia32-libs
Errors were encountered while processing:
 /var/cache/apt/archives/vmware-server_1.0.4-1gutsy2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ant2ne@2ne-buntu:~$ 

```What now?

---

### Post by dcstar on 2008-05-10
> **ant2ne said:**
> ```
ant2ne@2ne-buntu:~$ sudo apt-get install vmware-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmp4-info-perl libio-string-perl libaudio-wav-perl
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  vmware-server
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
Need to get 0B/79.4MB of archives.
After this operation, 131MB of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 120784 files and directories currently installed.)
Unpacking vmware-server (from .../vmware-server_1.0.4-1gutsy2_amd64.deb) ...
dpkg: error processing [B]/var/cache/apt/archives/vmware-server_1.0.4-1gutsy2_amd64.deb (--unpack):
 trying to overwrite `/usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so', which is also in package ia32-libs[/B]
Errors were encountered while processing:
 /var/cache/apt/archives/vmware-server_1.0.4-1gutsy2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ant2ne@2ne-buntu:~$ 

```What now?

Try removing the ia32-libs package.

---

### Post by ant2ne on 2008-05-11
```
ant2ne@2ne-buntu:~$ sudo apt-get remove ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libchromexvmc1 libchromexvmcpro1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  ia32-libs
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 101MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 119198 files and directories currently installed.)
Removing ia32-libs ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
ant2ne@2ne-buntu:~$ sudo apt-get install vmware-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libchromexvmc1 libchromexvmcpro1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  ia32-libs
Recommended packages:
  lib32nss-mdns
The following NEW packages will be installed:
  ia32-libs vmware-server
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/100MB of archives.
After this operation, 231MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package ia32-libs.
(Reading database ... 118257 files and directories currently installed.)
Unpacking ia32-libs (from .../ia32-libs_2.2ubuntu10_amd64.deb) ...
Unpacking vmware-server (from .../vmware-server_1.0.4-1gutsy2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/vmware-server_1.0.4-1gutsy2_amd64.deb (--unpack):
 trying to overwrite `/usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so', which is also in package ia32-libs
Errors were encountered while processing:
 /var/cache/apt/archives/vmware-server_1.0.4-1gutsy2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ant2ne@2ne-buntu:~$ 

```

Same thing

---

### Post by ant2ne on 2008-05-13
No help? Do I need to wipe and revert back to FF?

---

### Post by Nampla on 2008-05-14
when it askes "After this operation, 231MB of additional disk space will be used.
Do you want to continue [Y/n]?" try hitting n
then sudo apt-get autoremove
then sudo apt-get remove --purge vmware-server (just to be safe)
then try:   
   1. Download VMware Server from the VMware website (not from repositories).
   2. Unpack the contents of the archive to your system (perhaps /tmp)
   3. sudo aptitude install build-essential xinetd linux-headers-$(uname -r)
   4. sudo aptitude install ia32-libs
   5. Open a terminal (Applications > Accessories > Terminal), cd /tmp/vmware-server (or wherever you unpacked the archive)
   6. sudo ./vmware-install.pl

---

### Post by ant2ne on 2008-05-17
This installation is far more complicated. ```
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
your system (you need to have a C compiler installed on your system)? [yes] y

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-16-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.24-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:48:
/tmp/vmware-config0/vmmon-only/./include/vm_basic_types.h:159: error: redefinition of typedef ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:49:
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:49:
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-config0/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config0/vmmon-only/linux/driver.c:1659: error: ‘struct mm_struct’ has no member named ‘dumpable’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```
I have the feeling that this setup isn't compatible with my kernel. Probably because i'm 64bit.

Ideas?

---

### Post by HalPomeranz on 2008-05-17
I'm not wild about the VMware packages from Canonical because they're downrev from the latest version (a problem because there have been some fairly significant VMware security issues lately).  A better bet is to just download the latest VMware package directly from VMware.com and install it by hand.  It's not really that difficult if you just follow the instructions at:

[http://ubuntu-tutorials.com/2008/05/03/install-vmware-server-105-on-ubuntu-804-hardy/](http://ubuntu-tutorials.com/2008/05/03/install-vmware-server-105-on-ubuntu-804-hardy/)

I'm running VMware server 1.0.5 on my Hardy AMD-64 installation with no problems.

---

### Post by ant2ne on 2008-05-18
> **HalPomeranz said:**
> I'm not wild about the VMware packages from Canonical because they're downrev from the latest version (a problem because there have been some fairly significant VMware security issues lately).  A better bet is to just download the latest VMware package directly from VMware.com and install it by hand.  It's not really that difficult if you just follow the instructions at:

[http://ubuntu-tutorials.com/2008/05/03/install-vmware-server-105-on-ubuntu-804-hardy/](http://ubuntu-tutorials.com/2008/05/03/install-vmware-server-105-on-ubuntu-804-hardy/)

I'm running VMware server 1.0.5 on my Hardy AMD-64 installation with no problems.

Hoody Hoo!.. this worked. VMs are back. It asked me several questions during the installation that I didn't know the exact answer to. I may need to re-install with different options.

Thanks

---

### Post by fjgaude on 2008-05-18
I would suggest you answer all questions with the default ones. Just hit Enter as each question comes up.

---

