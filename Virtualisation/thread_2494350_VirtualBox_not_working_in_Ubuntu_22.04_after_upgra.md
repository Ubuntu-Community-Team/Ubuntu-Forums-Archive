---
title: "VirtualBox not working in Ubuntu 22.04 after upgrading to Kernel 6.5.0-14"
date: 2024-01-13
forum: Virtualisation
---

### Post by propaneacc on 2024-01-13
VirtualBox not working in Ubuntu 22.04 after upgrading to Kernel 6.5.0-14
My situation is similar to this thread [https://ubuntuforums.org/showthread.php?t=2055886](https://ubuntuforums.org/showthread.php?t=2055886)
I have upgraded to Kernel 6.5.0-14 from the 6.1 series kernel and now Virtualbox stops working and requests that I load or recompile the Virtualbox kernel driver.
I ran
```
 apt-get remove virtualbox virtualbox-dkms virtualbox-source
```
then
```
 apt-get install virtualbox virtualbox-dkms virtualbox-source
```
It seems maybe there is no Virtualbox dkms package for the 6.5 series kernel as it looks like apt is pulling the 6.1 package for dkms. Anyway to solve this?

>     USER@HOSTNAME:~/Downloads$ sudo apt-get install virtualbox-source virtualbox virtualbox-dkms
    Reading package lists... Done
    Building dependency tree... Done
    Reading state information... Done
    The following packages were automatically installed and are no longer required:
    libroar2 libwmf0.2-7
    Use 'sudo apt autoremove' to remove them.
    The following additional packages will be installed:
    virtualbox-qt
    Suggested packages:
    vde2 virtualbox-guest-additions-iso
    The following NEW packages will be installed:
    virtualbox virtualbox-dkms virtualbox-qt virtualbox-source
    0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
    Need to get 0 B/46.9 MB of archives.
    After this operation, 178 MB of additional disk space will be used.
    Do you want to continue? [Y/n]
    Selecting previously unselected package virtualbox-dkms.
    (Reading database ... 260275 files and directories currently installed.)
    Preparing to unpack .../virtualbox-dkms_6.1.38-dfsg-3~ubuntu1.22.04.1_amd64.deb ...
    Unpacking virtualbox-dkms (6.1.38-dfsg-3~ubuntu1.22.04.1) ...
    Selecting previously unselected package virtualbox-source.
    Preparing to unpack .../virtualbox-source_6.1.38-dfsg-3~ubuntu1.22.04.1_amd64.deb ...
    Unpacking virtualbox-source (6.1.38-dfsg-3~ubuntu1.22.04.1) ...
    Selecting previously unselected package virtualbox.
    Preparing to unpack .../virtualbox_6.1.38-dfsg-3~ubuntu1.22.04.1_amd64.deb ...
    Unpacking virtualbox (6.1.38-dfsg-3~ubuntu1.22.04.1) ...
    Selecting previously unselected package virtualbox-qt.
    Preparing to unpack .../virtualbox-qt_6.1.38-dfsg-3~ubuntu1.22.04.1_amd64.deb ...
    Unpacking virtualbox-qt (6.1.38-dfsg-3~ubuntu1.22.04.1) ...
    Setting up virtualbox-source (6.1.38-dfsg-3~ubuntu1.22.04.1) ...
    Setting up virtualbox (6.1.38-dfsg-3~ubuntu1.22.04.1) ...
    Job for virtualbox.service failed because the control process exited with error code.
    See "systemctl status virtualbox.service" and "journalctl -xeu virtualbox.service" for details.
    invoke-rc.d: initscript virtualbox, action "restart" failed.
    × virtualbox.service - LSB: VirtualBox Linux kernel module
    Loaded: loaded (/etc/init.d/virtualbox; generated)
    Active: failed (Result: exit-code) since Sat 2024-01-13 14:08:00 EST; 3ms ago
    Docs: man:systemd-sysv-generator(8)
    Process: 476217 ExecStart=/etc/init.d/virtualbox start (code=exited, status=1/FAILURE)
    CPU: 23ms

    Jan 13 14:08:00 HOSTNAME systemd[1]: Starting LSB: VirtualBox Linux kernel module...
    Jan 13 14:08:00 HOSTNAME virtualbox[476217]: * Loading VirtualBox kernel modules...
    Jan 13 14:08:00 HOSTNAME virtualbox[476217]: * No suitable module for running kernel found
    Jan 13 14:08:00 HOSTNAME virtualbox[476217]: ...fail!
    Jan 13 14:08:00 HOSTNAME systemd[1]: virtualbox.service: Control process exited, code=exited, status=1/FAILURE
    Jan 13 14:08:00 HOSTNAME systemd[1]: virtualbox.service: Failed with result 'exit-code'.
    Jan 13 14:08:00 HOSTNAME systemd[1]: Failed to start LSB: VirtualBox Linux kernel module.
    Setting up virtualbox-dkms (6.1.38-dfsg-3~ubuntu1.22.04.1) ...
    Loading new virtualbox-6.1.38 DKMS files...
    Building for 6.5.0-14-generic
    Building initial module for 6.5.0-14-generic
    ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/virtualbox-dkms.0.crash'
    Error! Bad return status for module build on kernel: 6.5.0-14-generic (x86_64)
    Consult /var/lib/dkms/virtualbox/6.1.38/build/make.log for more information.
    dpkg: error processing package virtualbox-dkms (--configure):
    installed virtualbox-dkms package post-installation script subprocess returned error exit status 10
    Setting up virtualbox-qt (6.1.38-dfsg-3~ubuntu1.22.04.1) ...
    Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
    Processing triggers for desktop-file-utils (0.26-1ubuntu3) ...
    Processing triggers for hicolor-icon-theme (0.17-2) ...
    Processing triggers for man-db (2.10.2-1) ...
    Processing triggers for shared-mime-info (2.1-2) ...
    Errors were encountered while processing:
    virtualbox-dkms
    E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by propaneacc on 2024-01-13
Here is the contents of the build log at  /var/lib/dkms/virtualbox/6.1.38/build/make.log 
> 
DKMS make.log for virtualbox-6.1.38 for kernel 6.5.0-14-generic (x86_64)
Sat Jan 13 02:08:00 PM EST 2024
make: Entering directory '/usr/src/linux-headers-6.5.0-14-generic'
warning: the compiler differs from the one used to build the kernel
  The kernel was built by: x86_64-linux-gnu-gcc-12 (Ubuntu 12.3.0-1ubuntu1~22.04) 12.3.0
  You are using:           gcc-12 (Ubuntu 12.3.0-1ubuntu1~22.04) 12.3.0
  CC [M]  /var/lib/dkms/virtualbox/6.1.38/build/vboxdrv/linux/SUPDrv-linux.o
  CC [M]  /var/lib/dkms/virtualbox/6.1.38/build/vboxdrv/SUPDrv.o
  CC [M]  /var/lib/dkms/virtualbox/6.1.38/build/vboxdrv/SUPDrvGip.o
  CC [M]  /var/lib/dkms/virtualbox/6.1.38/build/vboxdrv/SUPDrvSem.o
  CC [M]  /var/lib/dkms/virtualbox/6.1.38/build/vboxdrv/SUPDrvTracer.o
  CC [M]  /var/lib/dkms/virtualbox/6.1.38/build/vboxdrv/SUPLibAll.o
  CC [M]  /var/lib/dkms/virtualbox/6.1.38/build/vboxdrv/r0drv/alloc-r0drv.o
  CC [M]  /var/lib/dkms/virtualbox/6.1.38/build/vboxdrv/r0drv/initterm-r0drv.o
  CC [M]  /var/lib/dkms/virtualbox/6.1.38/build/vboxdrv/r0drv/memobj-r0drv.o
  CC [M]  /var/lib/dkms/virtualbox/6.1.38/build/vboxdrv/r0drv/mpnotification-r0drv.o
  CC [M]  /var/lib/dkms/virtualbox/6.1.38/build/vboxdrv/r0drv/powernotification-r0drv.o
  CC [M]  /var/lib/dkms/virtualbox/6.1.38/build/vboxdrv/r0drv/linux/assert-r0drv-linux.o
  CC [M]  /var/lib/dkms/virtualbox/6.1.38/build/vboxdrv/r0drv/linux/alloc-r0drv-linux.o
  CC [M]  /var/lib/dkms/virtualbox/6.1.38/build/vboxdrv/r0drv/linux/initterm-r0drv-linux.o
  CC [M]  /var/lib/dkms/virtualbox/6.1.38/build/vboxdrv/r0drv/linux/memobj-r0drv-linux.o
/var/lib/dkms/virtualbox/6.1.38/build/vboxdrv/SUPDrvTracer.o: warning: objtool: SUPR0TracerFireProbe+0x7: indirect jump found in RETPOLINE build
/var/lib/dkms/virtualbox/6.1.38/build/vboxdrv/SUPDrvTracer.o: warning: objtool: supdrvTracerProbeFireStub+0x0: 'naked' return found in RETHUNK build
  CC [M]  /var/lib/dkms/virtualbox/6.1.38/build/vboxdrv/r0drv/linux/memuserkernel-r0drv-linux.o
  CC [M]  /var/lib/dkms/virtualbox/6.1.38/build/vboxdrv/r0drv/linux/mp-r0drv-linux.o
  CC [M]  /var/lib/dkms/virtualbox/6.1.38/build/vboxdrv/r0drv/linux/mpnotification-r0drv-linux.o
  CC [M]  /var/lib/dkms/virtualbox/6.1.38/build/vboxdrv/r0drv/linux/process-r0drv-linux.o
  CC [M]  /var/lib/dkms/virtualbox/6.1.38/build/vboxdrv/r0drv/linux/rtStrFormatKernelAddress-r0drv-linux.o
  CC [M]  /var/lib/dkms/virtualbox/6.1.38/build/vboxdrv/r0drv/linux/semevent-r0drv-linux.o
  CC [M]  /var/lib/dkms/virtualbox/6.1.38/build/vboxdrv/r0drv/linux/semeventmulti-r0drv-linux.o
/var/lib/dkms/virtualbox/6.1.38/build/vboxdrv/r0drv/linux/memobj-r0drv-linux.c: In function &#8216;rtR0MemObjNativeLockUser&#8217;:
/var/lib/dkms/virtualbox/6.1.38/build/vboxdrv/r0drv/linux/memobj-r0drv-linux.c:1228:18: error: too many arguments to function &#8216;get_user_pages&#8217;
 1228 |             rc = get_user_pages(R3Ptr,                  /* Where from. */
      |                  ^~~~~~~~~~~~~~
In file included from /var/lib/dkms/virtualbox/6.1.38/build/vboxdrv/r0drv/linux/the-linux-kernel.h:102,
                 from /var/lib/dkms/virtualbox/6.1.38/build/vboxdrv/r0drv/linux/memobj-r0drv-linux.c:31:
./include/linux/mm.h:2430:6: note: declared here
 2430 | long get_user_pages(unsigned long start, unsigned long nr_pages,
      |      ^~~~~~~~~~~~~~
/var/lib/dkms/virtualbox/6.1.38/build/vboxdrv/r0drv/linux/memobj-r0drv-linux.c:1261:33: error: passing argument 6 of &#8216;get_user_pages_remote&#8217; from incompatible pointer type [-Werror=incompatible-pointer-types]
 1261 |                                 papVMAs                 /* vmas */
      |                                 ^~~~~~~
      |                                 |
      |                                 struct vm_area_struct **
./include/linux/mm.h:2400:33: note: expected &#8216;int *&#8217; but argument is of type &#8216;struct vm_area_struct **&#8217;
 2400 |                            int *locked);
      |                            ~~~~~^~~~~~
/var/lib/dkms/virtualbox/6.1.38/build/vboxdrv/r0drv/linux/memobj-r0drv-linux.c:1245:18: error: too many arguments to function &#8216;get_user_pages_remote&#8217;
 1245 |             rc = get_user_pages_remote(
      |                  ^~~~~~~~~~~~~~~~~~~~~
./include/linux/mm.h:2397:6: note: declared here
 2397 | long get_user_pages_remote(struct mm_struct *mm,
      |      ^~~~~~~~~~~~~~~~~~~~~
/var/lib/dkms/virtualbox/6.1.38/build/vboxdrv/r0drv/linux/memobj-r0drv-linux.c:1304:39: error: assignment of read-only member &#8216;vm_flags&#8217;
 1304 |                 papVMAs[rc]->vm_flags |= VM_DONTCOPY | VM_LOCKED;
      |                                       ^~
/var/lib/dkms/virtualbox/6.1.38/build/vboxdrv/r0drv/linux/memobj-r0drv-linux.c: In function &#8216;rtR0MemObjNativeMapUser&#8217;:
/var/lib/dkms/virtualbox/6.1.38/build/vboxdrv/r0drv/linux/memobj-r0drv-linux.c:1774:35: error: assignment of read-only member &#8216;vm_flags&#8217;
 1774 |                     vma->vm_flags |= VM_DONTEXPAND | VM_DONTDUMP;
      |                                   ^~
cc1: some warnings being treated as errors
make[3]: *** [scripts/Makefile.build:251: /var/lib/dkms/virtualbox/6.1.38/build/vboxdrv/r0drv/linux/memobj-r0drv-linux.o] Error 1
make[3]: *** Waiting for unfinished jobs....
/var/lib/dkms/virtualbox/6.1.38/build/vboxdrv/r0drv/linux/memuserkernel-r0drv-linux.o: warning: objtool: VBoxHost_RTR0MemKernelCopyTo+0x13: redundant CLD
/var/lib/dkms/virtualbox/6.1.38/build/vboxdrv/r0drv/linux/memuserkernel-r0drv-linux.o: warning: objtool: VBoxHost_RTR0MemKernelCopyFrom+0x13: redundant CLD
make[2]: *** [scripts/Makefile.build:488: /var/lib/dkms/virtualbox/6.1.38/build/vboxdrv] Error 2
make[1]: *** [/usr/src/linux-headers-6.5.0-14-generic/Makefile:2037: /var/lib/dkms/virtualbox/6.1.38/build] Error 2
make: *** [Makefile:234: __sub-make] Error 2
make: Leaving directory '/usr/src/linux-headers-6.5.0-14-generic'

---

### Post by BicyclerBoy on 2024-01-13
You can downloaded virtualbox 7.0.13 from Oracle that does work fine with kernel 6.5  (still loads of "ubsan" spam in dmesg logs)

---

### Post by propaneacc on 2024-01-13
Yeah, it must be that kernel 6.5 doesn't work with Virtualbox 6.1. Ubuntu 23.10 runs kernel 6.5.0-9 out of the box and has Virtualbox 7.0.10 and works fine. I wonder if there is any plans for a patch on 22.04, would be nice to just use apt instead of installing virtualbox 7 outside of apt. Kernel 6.5 seems to run a lot better on my system then 6.2.
I want to correct my original post as well I was previously running kernel 6.2 not 6.1 (I got mixed up with Virtualbox version and kernel version).

---

### Post by ajgreeny on 2024-01-13
This problem has been seen by other users and as suggested it is certainly VBox 6.1 that is your problem.

Uninstall all your current VBox packages with ```
sudo apt remove virtualbox*
``` to make sure any related packages installed are removed then go to the Virtualbox website and download the Ubuntu 22.04 version from &#8203;ttps://www.virtualbox.org/wiki/Linux_Downloads
All your VMs will still run fine using that version  but don't forget to install the guest additions for version 7 as I presume you did for version 6.1.

Don't bother trying to install any other virtualbox packages such as virtualbox-dkms; none are required and when I used virtualbox I never installed anything else except the guest additions.

Good luck!

---

### Post by BicyclerBoy on 2024-01-13
I'm on unity 23.10 & now have kernel 6.5.0-14 and as I recall VirtualBox 7.0.10 was a problem as well or it was the UBSAN spam in logs.
Yes, I would prefer to stay inside package management as well.

---

### Post by ajgreeny on 2024-01-13
> **BicyclerBoy said:**
> I'm on unity 23.10 & now have kernel 6.5.0-14 and as I recall VirtualBox 7.0.10 was a problem as well or it was the UBSAN spam in logs.
Yes, I would prefer to stay inside package management as well.
This is, I believe, one time when it is most definitely worth moving out of the Ubuntu repos and downloading the developer's later version; it works much better than your current version.

---

### Post by SeijiSensei on 2024-01-13
First, use apt to remove the official release from the Ubuntu repository. Next, add the Oracle VirtualBox repository as described in the section called "Debian-based Linux distributions" at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads). New updates will be downloaded as needed and installed with the active kernels using DKMS. It's basically transparent.

---

### Post by BicyclerBoy on 2024-01-13
I'm fairly sure that 7.0.12 was still a problem.
But the problem may have just been the volume of UBSAN warnings in startup logs.
virtualbox 7.0.13 is a special testbuild with potential fixes for this or similar.

[https://www.virtualbox.org/wiki/Testbuilds](https://www.virtualbox.org/wiki/Testbuilds)

But I still see UBSAN warnings (exceptions?)  in logs.

I had been using that "normal" Oracle repo before 23.10 upgrade..

---

### Post by propaneacc on 2024-01-13
I didn't know about the Oracle repo, thanks SeijiSensei.  I just added it to my sources list and installed virtualbox-7.0 and it works. BicyclerBoy, it did install 7.0.12 and I do have the UBSAN spam in my dmesg but I can live with that. Hopefully it gets cleared up in a future update.

---

### Post by jgalvao on 2024-01-15
Well, I had the same problem and spent a few weeks trying to solve it.
For me the solution was pretty simple, just install gcc-12 and you are on.

I'm using Ubuntu 22.04 with VBox 7.0.12

This is what I did:

sudo apt purge virtualbox*

sudo apt update

sudo apt upgrade

sudo apt install gcc-12

sudo apt install virtualbox-7.0

And my machines started working again...

Hope this helps someone.

---

### Post by ajgreeny on 2024-01-15
Until very recently the VirtualBox repos which I had alwsys enabled when I used VBox did not have  version 7 but only version 6.1.

The information on their website still suggests that it has only 6.1 available but I see now that 7 is available, perhaps because 6.1 is no longer supported.  They obviously need to update the information on the website.

---

### Post by noctis13 on 2024-01-23
> **jgalvao said:**
> Well, I had the same problem and spent a few weeks trying to solve it.
For me the solution was pretty simple, just install gcc-12 and you are on.

I'm using Ubuntu 22.04 with VBox 7.0.12

This is what I did:

sudo apt purge virtualbox*

sudo apt update

sudo apt upgrade

sudo apt install gcc-12

sudo apt install virtualbox-7.0

And my machines started working again...

Hope this helps someone.

I can confirm this is what worked for me.

---

