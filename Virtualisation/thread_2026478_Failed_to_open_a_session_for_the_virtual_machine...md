---
title: "Failed to open a session for the virtual machine..."
date: 2012-07-15
forum: Virtualisation
---

### Post by Jonners59 on 2012-07-15
AMD Dual Core 64 processor   RAM 3.8Gb  Platform x86 64   Ubuntu 12.04 precise
Oracl Virtualbox 4.1.18 r78361

DKMS is and always has been installed though I keep getting messages to install it.

Running Windows7 Home

Everything is fully up to date.

After updates and upgrades of Ubuntu, Virtual box always has error messages, as per below.  Normally I seem - not sure how - to clear them.  This time it refuses to work.  The messages are as per below and I have tried everything suggested.

[HTML]Failed to open a session for the virtual machine 3cx Server_1.

The virtual machine '3cx Server_1' has terminated unexpectedly during startup with exit code 1.

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: Machine
Interface: IMachine {5eaa9319-62fc-4b0a-843c-0cb1940f8a91}
[/HTML][HTML]  p, li { white-space: pre-wrap; }  Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.
[/HTML]After doing these I have then tried to completl;y remove VB and re install:
```
sudo apt-get purge virtualbox virtualbox-dkms virtualbox-ose-qt virtualbox-qt
``````
sudo apt-get install virtualbox virtualbox-dkms virtualbox-ose virtualbox
``````
sudo apt-get install virtualbox-4.0
```That failed so I removed it again and then downloaded the *.deb file from the website and installed that using the SW Centre.

That too does not work, so I have removed again...
And retried.
```
server@server:~$ sudo apt-get install virtualbox-dkms
[sudo] password for server: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libgsoap1 virtualbox virtualbox-qt
Suggested packages:
  virtualbox-guest-additions-iso vde2
The following packages will be REMOVED
  virtualbox-4.1
The following NEW packages will be installed
  libgsoap1 virtualbox virtualbox-dkms virtualbox-qt
0 upgraded, 4 newly installed, 1 to remove and 0 not upgraded.
Need to get 23.3 MB of archives.
After this operation, 57.9 MB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ precise/universe libgsoap1 amd64 2.8.4-2 [507 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ precise-updates/universe virtualbox amd64 4.1.12-dfsg-2ubuntu0.1 [15.6 MB]
Get:3 http://archive.ubuntu.com/ubuntu/ precise-updates/universe virtualbox-dkms all 4.1.12-dfsg-2ubuntu0.1 [675 kB]
Get:4 http://archive.ubuntu.com/ubuntu/ precise-updates/universe virtualbox-qt amd64 4.1.12-dfsg-2ubuntu0.1 [6,491 kB]
Fetched 23.3 MB in 39s (592 kB/s)                                              
(Reading database ... 
dpkg: warning: files list file for package `freeglut3:i386' missing, assuming package has no files currently installed.
(Reading database ... 301933 files and directories currently installed.)
Removing virtualbox-4.1 ...
 * Stopping VirtualBox kernel modules                                    [ OK ] 
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for ureadahead ...
Selecting previously unselected package libgsoap1.
(Reading database ... 
dpkg: warning: files list file for package `freeglut3:i386' missing, assuming package has no files currently installed.
(Reading database ... 301195 files and directories currently installed.)
Unpacking libgsoap1 (from .../libgsoap1_2.8.4-2_amd64.deb) ...
Selecting previously unselected package virtualbox.
Unpacking virtualbox (from .../virtualbox_4.1.12-dfsg-2ubuntu0.1_amd64.deb) ...
Selecting previously unselected package virtualbox-dkms.
Unpacking virtualbox-dkms (from .../virtualbox-dkms_4.1.12-dfsg-2ubuntu0.1_all.deb) ...
Selecting previously unselected package virtualbox-qt.
Unpacking virtualbox-qt (from .../virtualbox-qt_4.1.12-dfsg-2ubuntu0.1_amd64.deb) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Processing triggers for menu ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Setting up libgsoap1 (2.8.4-2) ...
Setting up virtualbox (4.1.12-dfsg-2ubuntu0.1) ...
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Starting VirtualBox kernel modules                                            * modprobe vboxdrv failed. Please use 'dmesg' to find out why
                                                                         [fail]
invoke-rc.d: initscript virtualbox, action "restart" failed.
Processing triggers for python-central ...
Setting up virtualbox-dkms (4.1.12-dfsg-2ubuntu0.1) ...
Loading new virtualbox-4.1.12 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-26-generic
Building initial module for 3.2.0-26-generic
Done.

vboxdrv:
Running module version sanity check.
Error! Module version 4.1.12_Ubuntu for vboxdrv.ko
is not newer than what is already found in kernel 3.2.0-26-generic (4.1.18).
You may override by specifying --force.

vboxnetadp.ko:
Running module version sanity check.
Error! Module version 4.1.12_Ubuntu for vboxnetadp.ko
is not newer than what is already found in kernel 3.2.0-26-generic (4.1.18).
You may override by specifying --force.

vboxnetflt.ko:
Running module version sanity check.
Error! Module version 4.1.12_Ubuntu for vboxnetflt.ko
is not newer than what is already found in kernel 3.2.0-26-generic (4.1.18).
You may override by specifying --force.

vboxpci.ko:
Running module version sanity check.
Error! Module version 4.1.12_Ubuntu for vboxpci.ko
is not newer than what is already found in kernel 3.2.0-26-generic (4.1.18).
You may override by specifying --force.

depmod........(bad exit status: 135)

-------- Uninstall Beginning --------
Module:  virtualbox
Version: 4.1.12
Kernel:  3.2.0-26-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod........(bad exit status: 135)

DKMS: uninstall completed.
Error! Problems with depmod detected.  Automatically uninstalling this module.
DKMS: Install Failed (depmod problems).  Module rolled back to built state.
dpkg: error processing virtualbox-dkms (--configure):
 subprocess installed post-installation script returned error exit status 6
Setting up virtualbox-qt (4.1.12-dfsg-2ubuntu0.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
Errors were encountered while processing:
 virtualbox-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)

```When I run the purge it says virtual box is not installed, yet it is!

tried reinstalling, but I can not get all the dependencies to install... see  error messages attached.


How do I get this up and running?

What is wrong?

---

### Post by CharlesA on 2012-07-15
I hate the version in the repos.

What happens when you run this:

```
dpkg -l | grep virtualbox
```

That should give you a list of virtualbox stuff that is installed.

---

### Post by Jonners59 on 2012-07-16
> **CharlesA said:**
> I hate the version in the repos.

What happens when you run this:

```
dpkg -l | grep virtualbox
```That should give you a list of virtualbox stuff that is installed.

Quite a bit there:
[HTML]ii  virtualbox                                    4.1.12-dfsg-2ubuntu0.1                            x86 virtualization solution - base binaries
rc  virtualbox-4.1                                4.1.18-78361~Ubuntu~precise                       Oracle VM VirtualBox
iF  virtualbox-dkms                               4.1.12-dfsg-2ubuntu0.1                            x86 virtualization solution - kernel module sources for dkms
iF  virtualbox-guest-dkms                         4.1.12-dfsg-2ubuntu0.1                            x86 virtualization solution - guest addition module source for dkms
ii  virtualbox-guest-utils                        4.1.12-dfsg-2ubuntu0.1                            x86 virtualization solution - non-X11 guest utilities
ii  virtualbox-guest-x11                          4.1.12-dfsg-2ubuntu0.1                            x86 virtualization solution - X11 guest utilities
ii  virtualbox-ose                                4.1.12-dfsg-2ubuntu0.1                            transitional package for virtualbox
iU  virtualbox-ose-dkms                           4.1.12-dfsg-2ubuntu0.1                            transitional package for virtualbox-dkms
iU  virtualbox-ose-guest-dkms                     4.1.12-dfsg-2ubuntu0.1                            transitional package for virtualbox-guest-dkms
ii  virtualbox-qt                                 4.1.12-dfsg-2ubuntu0.1                            x86 virtualization solution - Qt based user interface
[/HTML]

Error messages I get when installing any components are as taken from the end of the install script...
```
DKMS: uninstall completed.
Error! Problems with depmod detected.  Automatically uninstalling this module.
DKMS: Install Failed (depmod problems).  Module rolled back to built state.
dpkg: error processing v4l2loopback-dkms (--configure):
 subprocess installed post-installation script returned error exit status 6
No apport report written because MaxReports has already been reached
                                                                    Setting up virtualbox-ose (4.1.12-dfsg-2ubuntu0.1) ...
Errors were encountered while processing:
 virtualbox-dkms
 virtualbox-guest-dkms
 virtualbox-ose-dkms
 virtualbox-ose-guest-dkms
 backfire-dkms
 open-vm-dkms
 v4l2loopback-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

So not sure things are installed fully or correctly.

---

### Post by CharlesA on 2012-07-16
```
ii  virtualbox                                    4.1.12-dfsg-2ubuntu0.1                            x86 virtualization solution - base binaries
rc  virtualbox-4.1                                4.1.18-78361~Ubuntu~precise                       Oracle VM VirtualBox
iF  virtualbox-dkms                               4.1.12-dfsg-2ubuntu0.1                            x86 virtualization solution - kernel module sources for dkms
iF  virtualbox-guest-dkms                         4.1.12-dfsg-2ubuntu0.1                            x86 virtualization solution - guest addition module source for dkms
ii  virtualbox-guest-utils                        4.1.12-dfsg-2ubuntu0.1                            x86 virtualization solution - non-X11 guest utilities
ii  virtualbox-guest-x11                          4.1.12-dfsg-2ubuntu0.1                            x86 virtualization solution - X11 guest utilities
ii  virtualbox-ose                                4.1.12-dfsg-2ubuntu0.1                            transitional package for virtualbox
iU  virtualbox-ose-dkms                           4.1.12-dfsg-2ubuntu0.1                            transitional package for virtualbox-dkms
iU  virtualbox-ose-guest-dkms                     4.1.12-dfsg-2ubuntu0.1                            transitional package for virtualbox-guest-dkms
ii  virtualbox-qt                                 4.1.12-dfsg-2ubuntu0.1
```

I couldn't really find much info on dpkg output, but it looks like iU and iF are very bad. [See this mailing list entry]("https://lists.ubuntu.com/archives/kubuntu-users/2006-July/006993.html").

It looks like something with DKMS has caused it to get all messed up. I saw the sanity check in the OP and that isn't good at all.

Anyhow, run this:
```
ls -l /var/lib/dkms/vboxhost/
```

---

### Post by Jonners59 on 2012-07-16
> **CharlesA said:**
> ```
ii  virtualbox                                    4.1.12-dfsg-2ubuntu0.1                            x86 virtualization solution - base binaries
rc  virtualbox-4.1                                4.1.18-78361~Ubuntu~precise                       Oracle VM VirtualBox
iF  virtualbox-dkms                               4.1.12-dfsg-2ubuntu0.1                            x86 virtualization solution - kernel module sources for dkms
iF  virtualbox-guest-dkms                         4.1.12-dfsg-2ubuntu0.1                            x86 virtualization solution - guest addition module source for dkms
ii  virtualbox-guest-utils                        4.1.12-dfsg-2ubuntu0.1                            x86 virtualization solution - non-X11 guest utilities
ii  virtualbox-guest-x11                          4.1.12-dfsg-2ubuntu0.1                            x86 virtualization solution - X11 guest utilities
ii  virtualbox-ose                                4.1.12-dfsg-2ubuntu0.1                            transitional package for virtualbox
iU  virtualbox-ose-dkms                           4.1.12-dfsg-2ubuntu0.1                            transitional package for virtualbox-dkms
iU  virtualbox-ose-guest-dkms                     4.1.12-dfsg-2ubuntu0.1                            transitional package for virtualbox-guest-dkms
ii  virtualbox-qt                                 4.1.12-dfsg-2ubuntu0.1
```I couldn't really find much info on dpkg output, but it looks like iU and iF are very bad. [See this mailing list entry]("https://lists.ubuntu.com/archives/kubuntu-users/2006-July/006993.html").

It looks like something with DKMS has caused it to get all messed up. I saw the sanity check in the OP and that isn't good at all.

Anyhow, run this:
```
ls -l /var/lib/dkms/vboxhost/
```

Cheers
Here you are:
[HTML] ls -l /var/lib/dkms/vboxhost/
total 12
drwxr-xr-x 5 root root 4096 Mar 19  2011 4.0.4
drwxr-xr-x 4 root root 4096 Apr 28  2011 4.0.6
drwxr-xr-x 4 root root 4096 Oct 13  2011 4.1.4
[/HTML]

---

### Post by CharlesA on 2012-07-16
Well that seems to be part of the problem. Mine returns this:

```
charles@Thor:~$ ls -l /var/lib/dkms/vboxhost/
total 4
drwxr-xr-x 4 root root 4096 Jun 29 06:30 4.1.18
lrwxrwxrwx 1 root root   30 Jun 29 06:31 kernel-3.2.0-26-generic-x86_64 -> 4.1.18/3.2.0-26-generic/x86_64

```

Run this please:

```
dkms status
```

It should return something like this:

```
vboxhost, 4.1.18, 3.2.0-26-generic, x86_64: installed

```

---

### Post by Jonners59 on 2012-07-16
```
 dkms status
backfire, 0.73-1, 3.2.0-26-generic, x86_64: built
blcr, 0.8.2: added
dahdi, 2.5.0.1+dfsg-1ubuntu2, 3.2.0-24-generic, x86_64: installed (WARNING! Diff between built and installed module!)Error! Could not locate dkms.conf file.
File:  does not exist.

dahdi, 2.5.0.1+dfsg-1ubuntu2, 3.2.0-25-generic, x86_64: installed (WARNING! Diff between built and installed module!)
dahdi, 2.5.0.1+dfsg-1ubuntu2, 3.2.0-26-generic, x86_64: installed (WARNING! Diff between built and installed module!)
openafs, 1.6.1, 3.2.0-24-generic, x86_64: installed
openafs, 1.6.1, 3.2.0-25-generic, x86_64: installed
openafs, 1.6.1, 3.2.0-26-generic, x86_64: installed
open-vm-tools, 2011.12.20, 3.2.0-26-generic, x86_64: built
openvswitch, 1.4.0, 3.2.0-26-generic, x86_64: built
oss4, 4.2-build2005: added
v4l2loopback, 0.4.1, 3.2.0-26-generic, x86_64: built

```

---

### Post by CharlesA on 2012-07-16
Well, I guess that is a good thing - the vboxhost modules aren't installed.

Run this:

```
sudo mv /var/lib/dkms/vboxhost ~/vboxhost.old
```

Then try removing virtualbox.

---

### Post by Jonners59 on 2012-07-16
OK, done
Now running 
```
sudo apt-get purge virtualbox virtualbox-dkms virtualbox-ose-qt virtualbox-qt
```

Out put, cut n paste from terminal - still errors:

```
$ sudo apt-get purge virtualbox virtualbox-dkms virtualbox-ose-qt virtualbox-qt
[sudo] password for server: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package virtualbox-ose-qt is not installed, so not removed
The following packages will be REMOVED
  virtualbox* virtualbox-dkms* virtualbox-ose* virtualbox-ose-dkms*
  virtualbox-qt*
0 upgraded, 0 newly installed, 5 to remove and 8 not upgraded.
7 not fully installed or removed.
After this operation, 68.8 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 
dpkg: warning: files list file for package `freeglut3:i386' missing, assuming package has no files currently installed.
(Reading database ... 305899 files and directories currently installed.)
Removing virtualbox-ose-dkms ...
Removing virtualbox-dkms ...

-------- Uninstall Beginning --------
Module:  virtualbox
Version: 4.1.12
Kernel:  3.2.0-26-generic (x86_64)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod..............(bad exit status: 135)

DKMS: uninstall completed.

------------------------------
Deleting module version: 4.1.12
completely from the DKMS tree.
------------------------------
Done.
Removing virtualbox-qt ...
Purging configuration files for virtualbox-qt ...
Removing virtualbox-ose ...
Removing virtualbox ...
 * Stopping VirtualBox kernel modules                                    [ OK ] 
Purging configuration files for virtualbox ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for menu ...
Processing triggers for ureadahead ...
Setting up virtualbox-guest-dkms (4.1.12-dfsg-2ubuntu0.1) ...
Removing old virtualbox-guest-4.1.12 DKMS files...

-------- Uninstall Beginning --------
Module:  virtualbox-guest
Version: 4.1.12
Kernel:  3.2.0-26-generic (x86_64)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod.........(bad exit status: 135)

DKMS: uninstall completed.

------------------------------
Deleting module version: 4.1.12
completely from the DKMS tree.
------------------------------
Done.
Loading new virtualbox-guest-4.1.12 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-26-generic
Building initial module for 3.2.0-26-generic
Done.

vboxguest:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

vboxsf.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

vboxvideo.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

depmod........(bad exit status: 135)

-------- Uninstall Beginning --------
Module:  virtualbox-guest
Version: 4.1.12
Kernel:  3.2.0-26-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxguest.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxsf.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxvideo.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod........(bad exit status: 135)

DKMS: uninstall completed.
Error! Problems with depmod detected.  Automatically uninstalling this module.
DKMS: Install Failed (depmod problems).  Module rolled back to built state.
dpkg: error processing virtualbox-guest-dkms (--configure):
 subprocess installed post-installation script returned error exit status 6
dpkg: dependency problems prevent configuration of virtualbox-ose-guest-dkms:
 virtualbox-ose-guest-dkms depends on virtualbox-guest-dkms; however:
  Package virtualbox-guest-dkms is not configured yet.
dpkg: error processing virtualbox-ose-guest-dkms (--configure):
 dependency problems - leaving unconfigured
Setting up backfire-dkms (0.83-1) ...
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            Removing old backfire-0.73-1 DKMS files...

-------- Uninstall Beginning --------
Module:  backfire
Version: 0.73-1
Kernel:  3.2.0-26-generic (x86_64)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod.........(bad exit status: 135)

DKMS: uninstall completed.

------------------------------
Deleting module version: 0.73-1
completely from the DKMS tree.
------------------------------
Done.
Loading new backfire-0.73-1 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-26-generic
Building initial module for 3.2.0-26-generic
Done.

backfire:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

depmod........(bad exit status: 135)

-------- Uninstall Beginning --------
Module:  backfire
Version: 0.73-1
Kernel:  3.2.0-26-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

backfire.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod.........(bad exit status: 135)

DKMS: uninstall completed.
Error! Problems with depmod detected.  Automatically uninstalling this module.
DKMS: Install Failed (depmod problems).  Module rolled back to built state.
dpkg: error processing backfire-dkms (--configure):
 subprocess installed post-installation script returned error exit status 6
Setting up open-vm-dkms (2011.12.20-562307-0ubuntu1) ...
Removing old open-vm-tools-2011.12.20 DKMS files...

-------- Uninstall Beginning --------
Module:  open-vm-tools
Version: 2011.12.20
Kernel:  3.2.0-26-generic (x86_64)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod.........(bad exit status: 135)

DKMS: uninstall completed.

------------------------------
Deleting module version: 2011.12.20
completely from the DKMS tree.
------------------------------
Done.
Loading new open-vm-tools-2011.12.20 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-26-generic
Building for architecture x86_64
Building initial module for 3.2.0-26-generic
Done.

vmblock:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

vmci.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

vmhgfs.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

vmsync.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

vmxnet.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

vsock.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

depmod........(bad exit status: 135)

-------- Uninstall Beginning --------
Module:  open-vm-tools
Version: 2011.12.20
Kernel:  3.2.0-26-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vmblock.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vmci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vmhgfs.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vmsync.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vmxnet.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vsock.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod.........(bad exit status: 135)

DKMS: uninstall completed.
Error! Problems with depmod detected.  Automatically uninstalling this module.
DKMS: Install Failed (depmod problems).  Module rolled back to built state.
dpkg: error processing open-vm-dkms (--configure):
 subprocess installed post-installation script returned error exit status 6
No apport report written because MaxReports has already been reached
                                                                    Setting up v4l2loopback-dkms (0.4.1-1) ...
Removing old v4l2loopback-0.4.1 DKMS files...

-------- Uninstall Beginning --------
Module:  v4l2loopback
Version: 0.4.1
Kernel:  3.2.0-26-generic (x86_64)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod........(bad exit status: 135)

DKMS: uninstall completed.

------------------------------
Deleting module version: 0.4.1
completely from the DKMS tree.
------------------------------
Done.
Loading new v4l2loopback-0.4.1 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-26-generic
Building initial module for 3.2.0-26-generic
Done.

v4l2loopback:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

depmod........(bad exit status: 135)

-------- Uninstall Beginning --------
Module:  v4l2loopback
Version: 0.4.1
Kernel:  3.2.0-26-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

v4l2loopback.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod.........(bad exit status: 135)

DKMS: uninstall completed.
Error! Problems with depmod detected.  Automatically uninstalling this module.
DKMS: Install Failed (depmod problems).  Module rolled back to built state.
dpkg: error processing v4l2loopback-dkms (--configure):
 subprocess installed post-installation script returned error exit status 6
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 virtualbox-guest-dkms
 virtualbox-ose-guest-dkms
 backfire-dkms
 open-vm-dkms
 v4l2loopback-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by CharlesA on 2012-07-16
Try this:
[http://www.masaokitamura.com/2010/10/apt-not-fully-installed-or-removed/](http://www.masaokitamura.com/2010/10/apt-not-fully-installed-or-removed/)

---

### Post by Jonners59 on 2012-07-16
Done that, still gets errors in the terminal

EG:
```
Error! Problems with depmod detected
```

```
Status: This module version was INACTIVE for this kernel.
depmod........(bad exit status: 135)
```

```
ldconfig deferred processing now taking place
Errors were encountered while processing:
 virtualbox-guest-dkms
 virtualbox-ose-guest-dkms
 backfire-dkms
 open-vm-dkms
 v4l2loopback-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Full terminal out put=
```
$ sudo apt-get remove --purge slapd
[sudo] password for server: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package slapd is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
5 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up virtualbox-guest-dkms (4.1.12-dfsg-2ubuntu0.1) ...
Removing old virtualbox-guest-4.1.12 DKMS files...

-------- Uninstall Beginning --------
Module:  virtualbox-guest
Version: 4.1.12
Kernel:  3.2.0-26-generic (x86_64)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod..............(bad exit status: 135)

DKMS: uninstall completed.

------------------------------
Deleting module version: 4.1.12
completely from the DKMS tree.
------------------------------
Done.
Loading new virtualbox-guest-4.1.12 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-26-generic
Building initial module for 3.2.0-26-generic
Done.

vboxguest:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

vboxsf.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

vboxvideo.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

depmod.........(bad exit status: 135)

-------- Uninstall Beginning --------
Module:  virtualbox-guest
Version: 4.1.12
Kernel:  3.2.0-26-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxguest.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxsf.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxvideo.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod.........(bad exit status: 135)

DKMS: uninstall completed.
Error! Problems with depmod detected.  Automatically uninstalling this module.
DKMS: Install Failed (depmod problems).  Module rolled back to built state.
dpkg: error processing virtualbox-guest-dkms (--configure):
 subprocess installed post-installation script returned error exit status 6
dpkg: dependency problems prevent configuration of virtualbox-ose-guest-dkms:
 virtualbox-ose-guest-dkms depends on virtualbox-guest-dkms; however:
  Package virtualbox-guest-dkms is not configured yet.
dpkg: error processing virtualbox-ose-guest-dkms (--configure):
 dependency problems - leaving unconfigured
Setting up backfire-dkms (0.83-1) ...
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            Removing old backfire-0.73-1 DKMS files...

-------- Uninstall Beginning --------
Module:  backfire
Version: 0.73-1
Kernel:  3.2.0-26-generic (x86_64)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod........(bad exit status: 135)

DKMS: uninstall completed.

------------------------------
Deleting module version: 0.73-1
completely from the DKMS tree.
------------------------------
Done.
Loading new backfire-0.73-1 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-26-generic
Building initial module for 3.2.0-26-generic
Done.

backfire:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

depmod.........(bad exit status: 135)

-------- Uninstall Beginning --------
Module:  backfire
Version: 0.73-1
Kernel:  3.2.0-26-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

backfire.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod........(bad exit status: 135)

DKMS: uninstall completed.
Error! Problems with depmod detected.  Automatically uninstalling this module.
DKMS: Install Failed (depmod problems).  Module rolled back to built state.
dpkg: error processing backfire-dkms (--configure):
 subprocess installed post-installation script returned error exit status 6
Setting up open-vm-dkms (2011.12.20-562307-0ubuntu1) ...
Removing old open-vm-tools-2011.12.20 DKMS files...

-------- Uninstall Beginning --------
Module:  open-vm-tools
Version: 2011.12.20
Kernel:  3.2.0-26-generic (x86_64)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod........(bad exit status: 135)

DKMS: uninstall completed.

------------------------------
Deleting module version: 2011.12.20
completely from the DKMS tree.
------------------------------
Done.
Loading new open-vm-tools-2011.12.20 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-26-generic
Building for architecture x86_64
Building initial module for 3.2.0-26-generic
Done.

vmblock:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

vmci.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

vmhgfs.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

vmsync.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

vmxnet.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

vsock.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

depmod.........(bad exit status: 135)

-------- Uninstall Beginning --------
Module:  open-vm-tools
Version: 2011.12.20
Kernel:  3.2.0-26-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vmblock.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vmci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vmhgfs.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vmsync.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vmxnet.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vsock.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod.........(bad exit status: 135)

DKMS: uninstall completed.
Error! Problems with depmod detected.  Automatically uninstalling this module.
DKMS: Install Failed (depmod problems).  Module rolled back to built state.
dpkg: error processing open-vm-dkms (--configure):
 subprocess installed post-installation script returned error exit status 6
Setting up v4l2loopback-dkms (0.4.1-1) ...
No apport report written because MaxReports has already been reached
                                                                    Removing old v4l2loopback-0.4.1 DKMS files...

-------- Uninstall Beginning --------
Module:  v4l2loopback
Version: 0.4.1
Kernel:  3.2.0-26-generic (x86_64)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod.........(bad exit status: 135)

DKMS: uninstall completed.

------------------------------
Deleting module version: 0.4.1
completely from the DKMS tree.
------------------------------
Done.
Loading new v4l2loopback-0.4.1 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-26-generic
Building initial module for 3.2.0-26-generic
Done.

v4l2loopback:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

depmod.........(bad exit status: 135)

-------- Uninstall Beginning --------
Module:  v4l2loopback
Version: 0.4.1
Kernel:  3.2.0-26-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

v4l2loopback.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod........(bad exit status: 135)

DKMS: uninstall completed.
Error! Problems with depmod detected.  Automatically uninstalling this module.
DKMS: Install Failed (depmod problems).  Module rolled back to built state.
dpkg: error processing v4l2loopback-dkms (--configure):
 subprocess installed post-installation script returned error exit status 6
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 virtualbox-guest-dkms
 virtualbox-ose-guest-dkms
 backfire-dkms
 open-vm-dkms
 v4l2loopback-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)
server@server:~$ apt-get install -y slapd
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
server@server:~$ sudo apt-get install -y slapd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ldap-utils
The following NEW packages will be installed
  slapd
0 upgraded, 1 newly installed, 0 to remove and 8 not upgraded.
5 not fully installed or removed.
Need to get 1,722 kB of archives.
After this operation, 4,193 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ precise/main slapd amd64 2.4.28-1.1ubuntu4 [1,722 kB]
Fetched 1,722 kB in 2s (613 kB/s)  
Preconfiguring packages ...
Selecting previously unselected package slapd.
(Reading database ... 
dpkg: warning: files list file for package `freeglut3:i386' missing, assuming package has no files currently installed.
(Reading database ... 305358 files and directories currently installed.)
Unpacking slapd (from .../slapd_2.4.28-1.1ubuntu4_amd64.deb) ...
Processing triggers for ufw ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up virtualbox-guest-dkms (4.1.12-dfsg-2ubuntu0.1) ...
Removing old virtualbox-guest-4.1.12 DKMS files...

-------- Uninstall Beginning --------
Module:  virtualbox-guest
Version: 4.1.12
Kernel:  3.2.0-26-generic (x86_64)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod........(bad exit status: 135)

DKMS: uninstall completed.

------------------------------
Deleting module version: 4.1.12
completely from the DKMS tree.
------------------------------
Done.
Loading new virtualbox-guest-4.1.12 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-26-generic
Building initial module for 3.2.0-26-generic
Done.

vboxguest:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

vboxsf.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

vboxvideo.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

depmod........(bad exit status: 135)

-------- Uninstall Beginning --------
Module:  virtualbox-guest
Version: 4.1.12
Kernel:  3.2.0-26-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxguest.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxsf.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxvideo.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod........(bad exit status: 135)

DKMS: uninstall completed.
Error! Problems with depmod detected.  Automatically uninstalling this module.
DKMS: Install Failed (depmod problems).  Module rolled back to built state.
dpkg: error processing virtualbox-guest-dkms (--configure):
 subprocess installed post-installation script returned error exit status 6
dpkg: dependency problems prevent configuration of virtualbox-ose-guest-dkms:
 virtualbox-ose-guest-dkms depends on virtualbox-guest-dkms; however:
  Package virtualbox-guest-dkms is not configured yet.
dpkg: error processing virtualbox-ose-guest-dkms (--configure):
 dependency problems - leaving unconfigured
Setting up backfire-dkms (0.83-1) ...
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            Removing old backfire-0.73-1 DKMS files...

-------- Uninstall Beginning --------
Module:  backfire
Version: 0.73-1
Kernel:  3.2.0-26-generic (x86_64)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod.........(bad exit status: 135)

DKMS: uninstall completed.

------------------------------
Deleting module version: 0.73-1
completely from the DKMS tree.
------------------------------
Done.
Loading new backfire-0.73-1 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-26-generic
Building initial module for 3.2.0-26-generic
Done.

backfire:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

depmod........(bad exit status: 135)

-------- Uninstall Beginning --------
Module:  backfire
Version: 0.73-1
Kernel:  3.2.0-26-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

backfire.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod.........(bad exit status: 135)

DKMS: uninstall completed.
Error! Problems with depmod detected.  Automatically uninstalling this module.
DKMS: Install Failed (depmod problems).  Module rolled back to built state.
dpkg: error processing backfire-dkms (--configure):
 subprocess installed post-installation script returned error exit status 6
Setting up open-vm-dkms (2011.12.20-562307-0ubuntu1) ...
Removing old open-vm-tools-2011.12.20 DKMS files...

-------- Uninstall Beginning --------
Module:  open-vm-tools
Version: 2011.12.20
Kernel:  3.2.0-26-generic (x86_64)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod.........(bad exit status: 135)

DKMS: uninstall completed.

------------------------------
Deleting module version: 2011.12.20
completely from the DKMS tree.
------------------------------
Done.
Loading new open-vm-tools-2011.12.20 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-26-generic
Building for architecture x86_64
Building initial module for 3.2.0-26-generic
Done.

vmblock:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

vmci.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

vmhgfs.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

vmsync.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

vmxnet.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

vsock.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

depmod.........(bad exit status: 135)

-------- Uninstall Beginning --------
Module:  open-vm-tools
Version: 2011.12.20
Kernel:  3.2.0-26-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vmblock.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vmci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vmhgfs.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vmsync.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vmxnet.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vsock.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod.........(bad exit status: 135)

DKMS: uninstall completed.
Error! Problems with depmod detected.  Automatically uninstalling this module.
DKMS: Install Failed (depmod problems).  Module rolled back to built state.
dpkg: error processing open-vm-dkms (--configure):
 subprocess installed post-installation script returned error exit status 6
Setting up v4l2loopback-dkms (0.4.1-1) ...
No apport report written because MaxReports has already been reached
                                                                    Removing old v4l2loopback-0.4.1 DKMS files...

-------- Uninstall Beginning --------
Module:  v4l2loopback
Version: 0.4.1
Kernel:  3.2.0-26-generic (x86_64)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod........(bad exit status: 135)

DKMS: uninstall completed.

------------------------------
Deleting module version: 0.4.1
completely from the DKMS tree.
------------------------------
Done.
Loading new v4l2loopback-0.4.1 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-26-generic
Building initial module for 3.2.0-26-generic
Done.

v4l2loopback:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

depmod........(bad exit status: 135)

-------- Uninstall Beginning --------
Module:  v4l2loopback
Version: 0.4.1
Kernel:  3.2.0-26-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

v4l2loopback.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod.........(bad exit status: 135)

DKMS: uninstall completed.
Error! Problems with depmod detected.  Automatically uninstalling this module.
DKMS: Install Failed (depmod problems).  Module rolled back to built state.
dpkg: error processing v4l2loopback-dkms (--configure):
 subprocess installed post-installation script returned error exit status 6
No apport report written because MaxReports has already been reached
                                                                    Setting up slapd (2.4.28-1.1ubuntu4) ...
  Creating new user openldap... done.
  Creating initial configuration... done.
  Creating LDAP directory... done.
 * Starting OpenLDAP slapd                                               [ OK ] 
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 virtualbox-guest-dkms
 virtualbox-ose-guest-dkms
 backfire-dkms
 open-vm-dkms
 v4l2loopback-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by CharlesA on 2012-07-16
EDIT: Read this and try it out:
[http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/](http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/)

```
sudo apt-get --remove --force-remove-reinstreq virtualbox
sudo dpkg --remove --force-all virtualbox
```

Thanks to bodhi. :)

---

### Post by matt_symes on 2012-07-16
Hi

> **CharlesA said:**
> ```
ii  virtualbox                                    4.1.12-dfsg-2ubuntu0.1                            x86 virtualization solution - base binaries
rc  virtualbox-4.1                                4.1.18-78361~Ubuntu~precise                       Oracle VM VirtualBox
iF  virtualbox-dkms                               4.1.12-dfsg-2ubuntu0.1                            x86 virtualization solution - kernel module sources for dkms
iF  virtualbox-guest-dkms                         4.1.12-dfsg-2ubuntu0.1                            x86 virtualization solution - guest addition module source for dkms
ii  virtualbox-guest-utils                        4.1.12-dfsg-2ubuntu0.1                            x86 virtualization solution - non-X11 guest utilities
ii  virtualbox-guest-x11                          4.1.12-dfsg-2ubuntu0.1                            x86 virtualization solution - X11 guest utilities
ii  virtualbox-ose                                4.1.12-dfsg-2ubuntu0.1                            transitional package for virtualbox
iU  virtualbox-ose-dkms                           4.1.12-dfsg-2ubuntu0.1                            transitional package for virtualbox-dkms
iU  virtualbox-ose-guest-dkms                     4.1.12-dfsg-2ubuntu0.1                            transitional package for virtualbox-guest-dkms
ii  virtualbox-qt                                 4.1.12-dfsg-2ubuntu0.1
```I couldn't really find much info on dpkg output, but it looks like iU and iF are very bad. [See this mailing list entry]("https://lists.ubuntu.com/archives/kubuntu-users/2006-July/006993.html").


dpkg-query deals with this.

From 

```
man dpkg-query
```

> 
 Desired action:
                u = Unknown
                i = Install
                h = Hold
                r = Remove
                p = Purge

              Package status:
                n = Not-installed
                c = Config-files
                H = Half-installed
                U = Unpacked
                F = Half-configured
                W = Triggers-awaiting
                t = Triggers-pending
                i = Installed

              Error flags:
                <empty> = (none)
                R = Reinst-required

Kind regards

---

### Post by Bachstelze on 2012-07-16
It's really a DKMS problem, not an Apt or DPKG problem. Run this and tell us what gives:

```
sudo dkms status
```

---

### Post by Jonners59 on 2012-07-16
I tried the cmd Charles and it did not work
So I tried also the cmd from the link...  See below.

```
$ sudo apt-get --remove --force-remove-reinstreq virtualbox
[sudo] password for server: 
E: Command line option --force-remove-reinstreq is not understood
server@server:~$ cd /var/lib/dpkg/info
server@server:/var/lib/dpkg/info$ sudo rm virtualbox
rm: cannot remove `virtualbox': No such file or directory
server@server:/var/lib/dpkg/info$ sudo dpkg --remove --force-all virtualbox
dpkg: warning: there's no installed package matching virtualbox
```


```
$ sudo dpkg --remove --force-all virtualbox
[sudo] password for server: 
dpkg: warning: there's no installed package matching virtualbox
 
```

---

### Post by Jonners59 on 2012-07-16
> **Bachstelze said:**
> It's really a DKMS problem, not an Apt or DPKG problem. Run this and tell us what gives:

```
sudo dkms status
```

Bachstelze, thanks, this is what I got:


```
$ sudo dkms status
[sudo] password for server: 
backfire, 0.73-1, 3.2.0-26-generic, x86_64: built
blcr, 0.8.2: added
dahdi, 2.5.0.1+dfsg-1ubuntu2, 3.2.0-24-generic, x86_64: installed (WARNING! Diff between built and installed module!)
dahdi, 2.5.0.1+dfsg-1ubuntu2, 3.2.0-25-generic, x86_64: installed (WARNING! Diff between built and installed module!)
dahdi, 2.5.0.1+dfsg-1ubuntu2, 3.2.0-26-generic, x86_64: installed (WARNING! Diff between built and installed module!)
openafs, 1.6.1, 3.2.0-24-generic, x86_64: installed
openafs, 1.6.1, 3.2.0-25-generic, x86_64: installed
openafs, 1.6.1, 3.2.0-26-generic, x86_64: installed
open-vm-tools, 2011.12.20, 3.2.0-26-generic, x86_64: built
openvswitch, 1.4.0, 3.2.0-26-generic, x86_64: built
oss4, 4.2-build2005: added
v4l2loopback, 0.4.1, 3.2.0-26-generic, x86_64: built
virtualbox-guest, 4.1.12, 3.2.0-26-generic, x86_64: built
```

---

### Post by CharlesA on 2012-07-16
> **Bachstelze said:**
> It's really a DKMS problem, not an Apt or DPKG problem. Run this and tell us what gives:

```
sudo dkms status
```

> **Jonners59 said:**
> ```
 dkms status
backfire, 0.73-1, 3.2.0-26-generic, x86_64: built
blcr, 0.8.2: added
dahdi, 2.5.0.1+dfsg-1ubuntu2, 3.2.0-24-generic, x86_64: installed (WARNING! Diff between built and installed module!)Error! Could not locate dkms.conf file.
File:  does not exist.

dahdi, 2.5.0.1+dfsg-1ubuntu2, 3.2.0-25-generic, x86_64: installed (WARNING! Diff between built and installed module!)
dahdi, 2.5.0.1+dfsg-1ubuntu2, 3.2.0-26-generic, x86_64: installed (WARNING! Diff between built and installed module!)
openafs, 1.6.1, 3.2.0-24-generic, x86_64: installed
openafs, 1.6.1, 3.2.0-25-generic, x86_64: installed
openafs, 1.6.1, 3.2.0-26-generic, x86_64: installed
open-vm-tools, 2011.12.20, 3.2.0-26-generic, x86_64: built
openvswitch, 1.4.0, 3.2.0-26-generic, x86_64: built
oss4, 4.2-build2005: added
v4l2loopback, 0.4.1, 3.2.0-26-generic, x86_64: built

```

Status as of earlier. I figured it was a DKMS problem, but not sure what the cause of it is.

You could try this, but I don't know if it will work or not:
```
sudo dpkg --remove --force-remove-reinstreq virtualbox
```

---

### Post by Jonners59 on 2012-07-16
Tried, did nothing...

```

$ sudo dpkg --remove --force-remove-reinstreq virtualbox
dpkg: warning: there's no installed package matching virtualbox
```What if I clean the index...  I mean if it thinks certain packages are installed and they are not, then a clean and start again may work..?  I.e.[COLOR=#333333][SIZE=2]

[/SIZE][/COLOR]```
sudo rm /var/lib/apt/lists/*
sudo apt-get clean
sudo apt-get autoclean

sudo apt-get update
sudo apt-get install -f

sudo dpkg-reconfigure -phigh -a
```Results, prior to the last cmd being applied:

```
DKMS: uninstall completed.
Error! Problems with depmod detected.  Automatically uninstalling this module.
DKMS: Install Failed (depmod problems).  Module rolled back to built state.
dpkg: error processing v4l2loopback-dkms (--configure):
 subprocess installed post-installation script returned error exit status 6
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 virtualbox-guest-dkms
 virtualbox-ose-guest-dkms
 backfire-dkms
 open-vm-dkms
 v4l2loopback-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Last cmd:

```
$ sudo dpkg-reconfigure -phigh -a
Package `freeglut3' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: freeglut3 is not installed.
```

---

### Post by Bachstelze on 2012-07-16
Like I said, the problem is not really in the packages, it's in DKMS. When DKMS tries to build the kernel module, it fails and so the installation is aborted. Your dkms output shows no problem. What does this give?

```
ls -l /usr/src
```

---

### Post by Jonners59 on 2012-07-16
> **Bachstelze said:**
> Like I said, the problem is not really in the packages, it's in DKMS. When DKMS tries to build the kernel module, it fails and so the installation is aborted. Your dkms output shows no problem. What does this give?

```
ls -l /usr/src
```

Sorry was doing stuff and it took an age...  Here you are:

```
# ls -l /usr/src
total 80
drwxr-xr-x  2 root root  4096 Jul 15 16:40 backfire-0.73-1
drwxr-xr-x 17 root root  4096 Jun 24 15:56 blcr-0.8.2
drwxr-xr-x  5 root root  4096 Jun  3 13:33 dahdi-2.5.0.1+dfsg-1ubuntu2
drwxr-xr-x 24 root root  4096 Jun  3 13:27 linux-headers-3.2.0-24
drwxr-xr-x  7 root root  4096 Jun  3 13:27 linux-headers-3.2.0-24-generic
drwxr-xr-x 24 root root  4096 Jun 24 15:56 linux-headers-3.2.0-25
drwxr-xr-x  7 root root  4096 Jun 24 15:56 linux-headers-3.2.0-25-generic
drwxr-xr-x 24 root root  4096 Jul 14 18:49 linux-headers-3.2.0-26
drwxr-xr-x  7 root root  4096 Jul 14 18:49 linux-headers-3.2.0-26-generic
drwxr-xr-x  5 root root  4096 Jun  3 13:42 openafs-1.6.1
drwxr-xr-x  8 root root  4096 Jul 15 16:40 open-vm-tools-2011.12.20
drwxr-xr-x 17 root root  4096 Jul 15 16:40 openvswitch-1.4.0
drwxr-xr-x  5 root root  4096 Jun  3 13:38 oss4-4.2-build2005
drwxr-xr-x  2 root root  4096 Jul 15 16:40 v4l2loopback-0.4.1
-rw-r--r--  1 root root 16744 Dec 16  2011 v4l2loopback.tar.bz2
drwxr-xr-x  7 root root  4096 Jul 15 19:32 virtualbox-guest-4.1.12
```

---

### Post by Bachstelze on 2012-07-16
No problem here either... Apparently it's depmod that fails, so try

```
sudo depmod -a
```

---

### Post by Jonners59 on 2012-07-16
OK, done...  After a few seconds just went into the next line.....  SHould I have expected an out put???

```
# sudo depmod -a
root@server:/home/server# 
```

---

### Post by Bachstelze on 2012-07-16
I would say yes because no output means everything worked fine, but you seem to have a problem with it, so I expected some output. Just to be sure:

```
sudo depmod -a
echo $?
```

---

### Post by Jonners59 on 2012-07-16
```
$ echo $?
135
```

---

### Post by Bachstelze on 2012-07-16
Okay, so you do have a problem (if no problem, the output should be 0). I suspect that it's related to the dahdi module that you saw in your dkms status output. Can you afford to uninstall it for now? Then you can try reinstalling VBox and see if it works.

---

### Post by Jonners59 on 2012-07-16
OK, but how, please talk me through...

---

### Post by Bachstelze on 2012-07-16
Try

```
sudo dkms remove dahdi/2.5.0.1+dfsg-1ubuntu2 --all
```

---

### Post by Jonners59 on 2012-07-16
> **Bachstelze said:**
> Try

```
sudo dkms remove dahdi/2.5.0.1+dfsg-1ubuntu2 --all
```
Done, and seems to have worked.... what next, please?

```
$ sudo depmod -a
server@server:~$ echo $?
135
server@server:~$ sudo dkms remove dahdi/2.5.0.1+dfsg-1ubuntu2 --all

-------- Uninstall Beginning --------
Module:  dahdi
Version: 2.5.0.1+dfsg-1ubuntu2
Kernel:  3.2.0-24-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

dahdi_dummy.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi_dynamic_eth.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi_dynamic.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi_dynamic_loc.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi_echocan_jpah.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi_echocan_kb1.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi_echocan_mg2.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi_echocan_sec2.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi_echocan_sec.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi_transcode.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


pciradio.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


tor2.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


wcb4xxp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


wcfxo.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


wct1xxp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


wct4xxp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


wctc4xxp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


wctdm.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


wctdm24xxp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


wcte11xp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


wcte12xp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


xpd_fxo.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


xpd_fxs.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


xpd_pri.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


xpp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


xpp_usb.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


xpd_bri.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi_voicebus.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


opvxa1200.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


wcopenpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi_echocan_oslec.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


echo.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


zaphfc.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi_vpmadt032_loader.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


ap400.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


opvxd115.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod.........

DKMS: uninstall completed.

-------- Uninstall Beginning --------
Module:  dahdi
Version: 2.5.0.1+dfsg-1ubuntu2
Kernel:  3.2.0-25-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

dahdi_dummy.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi_dynamic_eth.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi_dynamic.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi_dynamic_loc.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi_echocan_jpah.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi_echocan_kb1.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi_echocan_mg2.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi_echocan_sec2.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi_echocan_sec.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi_transcode.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


pciradio.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


tor2.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


wcb4xxp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


wcfxo.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


wct1xxp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


wct4xxp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


wctc4xxp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


wctdm.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


wctdm24xxp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


wcte11xp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


wcte12xp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


xpd_fxo.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


xpd_fxs.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


xpd_pri.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


xpp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


xpp_usb.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


xpd_bri.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi_voicebus.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


opvxa1200.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


wcopenpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi_echocan_oslec.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


echo.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


zaphfc.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi_vpmadt032_loader.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


ap400.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


opvxd115.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod.........

DKMS: uninstall completed.

-------- Uninstall Beginning --------
Module:  dahdi
Version: 2.5.0.1+dfsg-1ubuntu2
Kernel:  3.2.0-26-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

dahdi_dummy.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi_dynamic_eth.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi_dynamic.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi_dynamic_loc.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi_echocan_jpah.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi_echocan_kb1.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi_echocan_mg2.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi_echocan_sec2.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi_echocan_sec.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi_transcode.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


pciradio.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


tor2.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


wcb4xxp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


wcfxo.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


wct1xxp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


wct4xxp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


wctc4xxp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


wctdm.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


wctdm24xxp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


wcte11xp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


wcte12xp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


xpd_fxo.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


xpd_fxs.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


xpd_pri.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


xpp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


xpp_usb.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


xpd_bri.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi_voicebus.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


opvxa1200.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


wcopenpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi_echocan_oslec.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


echo.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


zaphfc.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


dahdi_vpmadt032_loader.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


ap400.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


opvxd115.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod..............(bad exit status: 135)

DKMS: uninstall completed.

------------------------------
Deleting module version: 2.5.0.1+dfsg-1ubuntu2
completely from the DKMS tree.
------------------------------
Done.
```

---

### Post by Bachstelze on 2012-07-16
You should expect the module to be uninstalled. After that, try reinstalling VirtualBox again.

```
sudo apt-get install virtualbox
```

---

### Post by Jonners59 on 2012-07-16
OK, it is running, but I have noticed some error messages still:
```





-------- Uninstall Beginning --------
Module:  virtualbox-guest
Version: 4.1.12
Kernel:  3.2.0-26-generic (x86_64)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod.............(bad exit status: 135)

DKMS: uninstall completed.
```
```

DKMS: uninstall completed.
Error! Problems with depmod detected.  Automatically uninstalling this module.
DKMS: Install Failed (depmod problems).  Module rolled back to built state.
dpkg: error processing v4l2loopback-dkms (--configure):
 subprocess installed post-installation script returned error exit status 6
No apport report written because MaxReports has already been reached
                                                                    Setting up virtualbox (4.1.12-dfsg-2ubuntu0.1) ...
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Starting VirtualBox kernel modules                                            * modprobe vboxdrv failed. Please use 'dmesg' to find out why
                                                                         [fail]
invoke-rc.d: initscript virtualbox, action "restart" failed.
Processing triggers for python-central ...
Setting up virtualbox-dkms (4.1.12-dfsg-2ubuntu0.1) ...
Loading new virtualbox-4.1.12 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-26-generic
Building initial module for 3.2.0-26-generic
```

---

### Post by Bachstelze on 2012-07-16
Yes I saw them too. If installation fails again, we will have to look depper into depmod...

---

### Post by Jonners59 on 2012-07-16
Failed sorry....

I need to hit the sack soon...

what next?

---

### Post by Bachstelze on 2012-07-16
We need to find out what's wrong with depmod... I am not very familiar with it, but try

```
sudo depmod -aw
```

---

### Post by Jonners59 on 2012-07-16
ok done, no out put... is that correct?

---

### Post by Bachstelze on 2012-07-16
Not really because it doesn't tell us what's wrong. :p In your last paste, it seems to be v4l2loopback that seems to be causing trouble. You can try removing that one because it is not even installed, only built.

```
sudo dkms remove v4l2loopback/0.4.1 --all
```

---

### Post by Jonners59 on 2012-07-16
OK done and I think a success, what next?

---

### Post by Bachstelze on 2012-07-16
Does it still say "exit code 135"?

---

### Post by Jonners59 on 2012-07-16
Sorry, it did not work...  It still says 135 when I type
```
sudo depmod -a echo $?
```I then also noticed in the un-install it had not worked either......  I am shattered, are you about tomorrow eve..?

---

### Post by Bachstelze on 2012-07-16
Probably, but now I'm not sure where to go from here...

---

### Post by Jonners59 on 2012-07-16
> **Bachstelze said:**
> Probably, but now I'm not sure where to go from here...
Should I open a new thread and if so with what as the subject...?

---

### Post by CharlesA on 2012-07-18
> **Jonners59 said:**
> Should I open a new thread and if so with what as the subject...?
Not sure. If the machine is messed up to this point, I would say back up your stuff and do a clean install of 12.04, but that is an extreme solution.

---

### Post by Jonners59 on 2012-07-19
With no follow up messages I created another thread, but as that got no replies either I decided to try a new build....  And then it all went from bad to worse.

I could not load from CD, it would stick at scanning the Disks, so I deleted the disk and tried again, but to no avail, so then I replaced the disk with a new one, and have been having fun installing on that too.
I am at the stage where it is, I am supposing installed but it will not boot past GRUB.  It freezes with some text.

I am looking for any info on GRUB errors at boot.

Also the fan has failed in the power supply so bought a new one today.  It NEVER just rains!  bad joke this year here in London - wettest on record.

---

### Post by CharlesA on 2012-07-19
Sheesh. Did you very the MD5SUM before burning the ISO?

Have you tried to put the drive in another machine and see what happens?

---

### Post by Jonners59 on 2012-07-19
The machine is, hardware wise running.....  I have just changed the power supply so now I am needing to look at the boot...  I have seen this prob before, a couple of years ago, but can't recall how to fix.  I had help then.  Something about setting nomodeset and one other thingie in to the Grub boot conf.....  Well, that's what i hope it is!!!!!

---

### Post by CharlesA on 2012-07-19
> **Jonners59 said:**
> The machine is, hardware wise running.....  I have just changed the power supply so now I am needing to look at the boot...  I have seen this prob before, a couple of years ago, but can't recall how to fix.  I had help then.  Something about setting nomodeset and one other thingie in to the Grub boot conf.....  Well, that's what i hope it is!!!!!
That's what I think it is too. Something with the video drivers/resolution.

---

### Post by Jonners59 on 2012-07-19
> **CharlesA said:**
> That's what I think it is too. Something with the video drivers/resolution.
Except I can't find what I need and am looking at old threads I created and making things worse.  I am opening a new thread for this.....

---

### Post by CharlesA on 2012-07-19
> **Jonners59 said:**
> Except I can't find what I need and am looking at old threads I created and making things worse.  I am opening a new thread for this.....
Hi,

I didn't see a new thread so I'm posting this here:
[http://askubuntu.com/questions/110315/ubuntu-11-10-and-12-04-blackscreen-on-boot](http://askubuntu.com/questions/110315/ubuntu-11-10-and-12-04-blackscreen-on-boot)

---

### Post by Jonners59 on 2012-07-19
Sorry, I got called away by the PC whilst in the process of writing it .....

I tried boot-repair, but I think I may have more than one Grub installed some where.  As I now get a "Grub" terminal
It starts with "GRUB>"

Yet the repair and other purge and re-install commands say it is installed correctly and working??????

Also, FYI when I use the CD I need to do F6 and set the acpi=off and nomodeset.  I think, before I screwed this up more, finding where to add these cmds is all I had to do.

---

### Post by CharlesA on 2012-07-19
Try this:

[http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/](http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/)

I haven't heard of much success with boot repair.

---

### Post by Jonners59 on 2012-07-21
Resolved by rebuilding.......

---

