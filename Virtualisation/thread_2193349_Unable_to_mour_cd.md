---
title: "Unable to mour cd"
date: 2013-12-12
forum: Virtualisation
---

### Post by satimis on 2013-12-12
Hi all,

Host  Ubuntu 12.04
Guest  12.04

All Ubuntu 12.04 guests get the same problem unable to mount CD with following warning:
```

Unable to mount the CD/DVD image
~/VBoxGuestAdditions_4.1.12.iso on the machine ub1204dkc8_00.  
Would you like to force mounting of this medium?

Could not mount the media/drive
~/VBoxGuestAdditions_4.1.12.iso
(VERR_PDM_MEDIA_LOCKED)

```

The GuestAddition on Ubuntu repository can't work.  Please help.

Thanks

satimis

---

### Post by steeldriver on 2013-12-12
Yes this is an annoyance thanks to the default automounting of CDs (even virtual ones) and in my experience the option to force unmount does nothing - you can try opening a terminal in the guest OS, navigating to the mounted directory, and running the installer directly from there e.g.

```
steeldriver@steeldriver-VirtualBox:~$ [COLOR=#0000ff]**cd /media/VBOXADDITIONS_4.2.18_88780/**[/COLOR]
```

(you actual path will be different depending on the version number of the iso - use tab completion to save typos)

```

steeldriver@steeldriver-VirtualBox:/media/VBOXADDITIONS_4.2.18_88780$ [COLOR=#0000ff]**ls**[/COLOR]
32Bit  AUTORUN.INF  cert  runasroot.sh            VBoxSolarisAdditions.pkg        VBoxWindowsAdditions.exe
64Bit  autorun.sh   OS2   VBoxLinuxAdditions.run  VBoxWindowsAdditions-amd64.exe  VBoxWindowsAdditions-x86.exe

```

For a Linux guest, you want the .run file i.e.

```

steeldriver@steeldriver-VirtualBox:/media/VBOXADDITIONS_4.2.18_88780$ [COLOR=#0000ff]**sudo ./VBoxLinuxAdditions.run**[/COLOR] 
[sudo] password for steeldriver: 
Verifying archive integrity... All good.
Uncompressing VirtualBox 4.2.18 Guest Additions for Linux............
VirtualBox Guest Additions installer
Removing installed version 4.2.12 of VirtualBox Guest Additions...
Copying additional installer modules ...
Installing additional modules ...
Removing existing VirtualBox DKMS kernel modules ...done.
Removing existing VirtualBox non-DKMS kernel modules ...done.
Building the VirtualBox Guest Additions kernel modules ...done.
Doing non-kernel setup of the Guest Additions ...done.
You should restart your guest to make sure the new modules are actually used

Installing the Window System drivers
Installing X.Org Server 1.11 modules ...done.
Setting up the Window System to use the Guest Additions ...done.
You may need to restart the hal service and the Window System (or just restart
the guest system) to enable the Guest Additions.

Installing graphics libraries and desktop services components ...done.
steeldriver@steeldriver-VirtualBox:/media/VBOXADDITIONS_4.2.18_88780$ 

```

---

### Post by satimis on 2013-12-12
> **steeldriver said:**
> Yes this is an annoyance thanks to the default automounting of CDs (even virtual ones) and in my experience the option to force unmount does nothing - you can try opening a terminal in the guest OS, navigating to the mounted directory, and running the installer directly from there e.g.

```
steeldriver@steeldriver-VirtualBox:~$ [COLOR=#0000ff]**cd /media/VBOXADDITIONS_4.2.18_88780/**[/COLOR]
```

(you actual path will be different depending on the version number of the iso - use tab completion to save typos)

```

steeldriver@steeldriver-VirtualBox:/media/VBOXADDITIONS_4.2.18_88780$ [COLOR=#0000ff]**ls**[/COLOR]
32Bit  AUTORUN.INF  cert  runasroot.sh            VBoxSolarisAdditions.pkg        VBoxWindowsAdditions.exe
64Bit  autorun.sh   OS2   VBoxLinuxAdditions.run  VBoxWindowsAdditions-amd64.exe  VBoxWindowsAdditions-x86.exe

```

For a Linux guest, you want the .run file i.e.

```

steeldriver@steeldriver-VirtualBox:/media/VBOXADDITIONS_4.2.18_88780$ [COLOR=#0000ff]**sudo ./VBoxLinuxAdditions.run**[/COLOR] 
[sudo] password for steeldriver: 
Verifying archive integrity... All good.
Uncompressing VirtualBox 4.2.18 Guest Additions for Linux............
VirtualBox Guest Additions installer
Removing installed version 4.2.12 of VirtualBox Guest Additions...
Copying additional installer modules ...
Installing additional modules ...
Removing existing VirtualBox DKMS kernel modules ...done.
Removing existing VirtualBox non-DKMS kernel modules ...done.
Building the VirtualBox Guest Additions kernel modules ...done.
Doing non-kernel setup of the Guest Additions ...done.
You should restart your guest to make sure the new modules are actually used

Installing the Window System drivers
Installing X.Org Server 1.11 modules ...done.
Setting up the Window System to use the Guest Additions ...done.
You may need to restart the hal service and the Window System (or just restart
the guest system) to enable the Guest Additions.

Installing graphics libraries and desktop services components ...done.
steeldriver@steeldriver-VirtualBox:/media/VBOXADDITIONS_4.2.18_88780$ 

```
Hi ,

Thanks for your advice.

Yes it looks quite funny to me.  As you said it is on /media/VBOXADDITIONS_4.2.18_88780/

But I couldn't install it complaining;
header of running version not found. linux-headers-3.5.0.44-generic already installed and dkms and gcc also installed.

Warning: unknow version of the X Window system installed.

$ uname -a
Linux localhost 3.5.0-44-generic

Rgds
satimis

---

