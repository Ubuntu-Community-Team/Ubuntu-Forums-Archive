---
title: "Vbox guest additions problem"
date: 2012-11-17
forum: Virtualisation
---

### Post by efflandt on 2012-11-17
Host: 64-bit Ubuntu 12.04 i5 650 3.2 GHz 8 GB
VBox: 4.2.4 r81684

I am new to VirtualBox, originally for a real basic Debian guest, starting with base system with no gui to adding lxde, etc. to become familiar with how to operate Raspian on a backordered Raspberry Pi ($35US 512 MB ARM computer on credit card size board).  Removing the default older guest additions and adding 4.2.4 version was no problem (apparently kernal headers and source installed by default).  The only problem was that I also had to install another Debian guest with its default gui to figure out how to get alsa audio working on the basic system (works now).

But I also decided to try 64-bit Ubuntu 12.10 guest.  I found the mouse flaky on the virtual live/install iso (often flashing to edge of window when cursor was in middle) and no scroll wheel function.  Mouse was better, but still no scroll wheel on installed guest (had not noticed that guest additions did not compile first attempt).

After I installed linux-headers-generic it still complains, but apparently does compile guest additions because now mouse cursor is stable with 3D video and scroll wheel works in 12.10 guest.

```
efflandt@U1210-VBox:/media/efflandt/VBOXADDITIONS_4.2.4_81684$ sudo sh ./VBoxLinuxAdditions.run
Verifying archive integrity... All good.
Uncompressing VirtualBox 4.2.4 Guest Additions for Linux..........
VirtualBox Guest Additions installer
Removing installed version 4.2.4 of VirtualBox Guest Additions...
Removing existing VirtualBox non-DKMS kernel modules ...done.
Building the VirtualBox Guest Additions kernel modules
[COLOR=DarkRed][B]The headers for the current running kernel were not found. If the following
module compilation fails then this could be the reason.[/B][/COLOR]

Building the main Guest Additions module ...done.
Building the shared folder support module ...done.
Building the OpenGL support module ...done.
Doing non-kernel setup of the Guest Additions ...done.
You should restart your guest to make sure the new modules are actually used

Installing the Window System drivers
Installing X.Org Server 1.13 modules ...done.
Setting up the Window System to use the Guest Additions ...done.
You may need to restart the hal service and the Window System (or just restart
the guest system) to enable the Guest Additions.

Installing graphics libraries and desktop services components ...done.

efflandt@U1210-VBox:~$ uname -a
Linux U1210-VBox 3.5.0-18-generic #29-Ubuntu SMP Fri Oct 19 10:26:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

efflandt@U1210-VBox:~$ ls /usr/src
linux-headers-3.5.0-17  linux-headers-3.5.0-18  linux-headers-3.5.0-18-generic  vboxguest-4.2.4
```PS: I should have read more carefully before replying because VMWare may be different than VirtualBox, although, it apparently has the same problem finding kernel headers.

---

### Post by cariboo on 2012-11-18
Moved to a thread of it's own, as it had nothing to do with the vmware thread it was in.

---

### Post by pkadeel on 2012-11-18
> **efflandt said:**
> Host: 64-bit Ubuntu 12.04 i5 650 3.2 GHz 8 GB
VBox: 4.2.4 r81684

I am new to VirtualBox, originally for a real basic Debian guest, starting with base system with no gui to adding lxde, etc. to become familiar with how to operate Raspian on a backordered Raspberry Pi ($35US 512 MB ARM computer on credit card size board).  Removing the default older guest additions and adding 4.2.4 version was no problem (apparently kernal headers and source installed by default).  The only problem was that I also had to install another Debian guest with its default gui to figure out how to get alsa audio working on the basic system (works now).

But I also decided to try 64-bit Ubuntu 12.10 guest.  I found the mouse flaky on the virtual live/install iso (often flashing to edge of window when cursor was in middle) and no scroll wheel function.  Mouse was better, but still no scroll wheel on installed guest (had not noticed that guest additions did not compile first attempt).

After I installed linux-headers-generic it still complains, but apparently does compile guest additions because now mouse cursor is stable with 3D video and scroll wheel works in 12.10 guest.

```
efflandt@U1210-VBox:/media/efflandt/VBOXADDITIONS_4.2.4_81684$ sudo sh ./VBoxLinuxAdditions.run
Verifying archive integrity... All good.
Uncompressing VirtualBox 4.2.4 Guest Additions for Linux..........
VirtualBox Guest Additions installer
Removing installed version 4.2.4 of VirtualBox Guest Additions...
Removing existing VirtualBox non-DKMS kernel modules ...done.
Building the VirtualBox Guest Additions kernel modules
[COLOR=DarkRed][B]The headers for the current running kernel were not found. If the following
module compilation fails then this could be the reason.[/B][/COLOR]

Building the main Guest Additions module ...done.
Building the shared folder support module ...done.
Building the OpenGL support module ...done.
Doing non-kernel setup of the Guest Additions ...done.
You should restart your guest to make sure the new modules are actually used

Installing the Window System drivers
Installing X.Org Server 1.13 modules ...done.
Setting up the Window System to use the Guest Additions ...done.
You may need to restart the hal service and the Window System (or just restart
the guest system) to enable the Guest Additions.

Installing graphics libraries and desktop services components ...done.

efflandt@U1210-VBox:~$ uname -a
Linux U1210-VBox 3.5.0-18-generic #29-Ubuntu SMP Fri Oct 19 10:26:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

efflandt@U1210-VBox:~$ ls /usr/src
linux-headers-3.5.0-17  linux-headers-3.5.0-18  linux-headers-3.5.0-18-generic  vboxguest-4.2.4
```PS: I should have read more carefully before replying because VMWare may be different than VirtualBox, although, it apparently has the same problem finding kernel headers.
Vbox guest additions are currently not fully compatible with ubuntu 12.10
If you are having problems with the guest OS, you will have to use ubuntu 12.04

---

