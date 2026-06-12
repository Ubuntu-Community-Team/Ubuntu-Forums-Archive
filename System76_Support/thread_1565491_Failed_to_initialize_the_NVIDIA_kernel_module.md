---
title: "Failed to initialize the NVIDIA kernel module"
date: 2010-09-01
forum: System76 Support
---

### Post by kbluck on 2010-09-01
I have a Wildebeest wilb1. Since a recent package update, I've been having a recurring problem with the NVIDIA graphics driver failing to start. I'm not sure exactly what was updated that started this, it was a normal update manager update.

When it happens, I get a dialog telling me that the nvidia driver failed to start and I'm going to be running in low-graphics mode. The error reported is:

```

Failed to initialize the NVIDIA kernel module. Please see the
system's kernel log for additional error messages and
consult the NVIDIA README for details.
Screen(s) found, but none have a usable configuration.
Fatal server error:
no screens found

```

It doesn't always happen. When it does happen, sometimes running nvidia-xconfig will fix it, sometimes not. Repeatedly running it does eventually fix it for a while, but every restart there is a risk of it happening again.

The x.conf file is whatever nvidia-xconfig auto-generates. I've never changed it.

Here's the full contents of the Xorg.log

```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux ubuntu-desktop 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=625ed789-1cb3-4081-9c7e-f812810b5126 ro quiet splash
Build Date: 21 July 2010  01:03:39PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug 31 22:07:28 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0a65:3842:1212 nVidia Corporation GT218 [GeForce 210] rev 162, Mem @ 0xe2000000/16777216, 0xd0000000/268435456, 0xe0000000/33554432, I/O @ 0x00001000/128, BIOS @ 0x????????/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  256.52  Wed Aug 25 14:35:26 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  256.52  Wed Aug 25 14:14:59 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) Aug 31 22:07:28 NVIDIA(0): Enabling RENDER acceleration
(II) Aug 31 22:07:28 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Aug 31 22:07:28 NVIDIA(0):     enabled.
(EE) Aug 31 22:07:28 NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) Aug 31 22:07:28 NVIDIA(0):     system's kernel log for additional error messages and
(EE) Aug 31 22:07:28 NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

ddxSigGiveUp: Closing log

```

---

### Post by kbluck on 2010-09-01
Some clarifications.

I can reliably get my graphics back for the current session with the following commands:

```

sudo nvidia-xconfig
sudo /etc/init.d/gdm restart

```

It may or may not stay fixed when I do a system restart or power on. Better than 50% chance it will break again every restart. Running nvidia-xconfig and then restarting rarely works. nvidia-xconfig often reports that it couldn't find an xorg.conf.

-- Kevin

---

### Post by isantop on 2010-09-01
Can you please open a terminal (Applications > Accessories > Terminal) and run the following command:
```
cat /etc/apt/sources.list
```

Then, post the output here.

---

### Post by kbluck on 2010-09-02
```

cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse

```

---

### Post by evilxsystems on 2010-09-10
I'm having a seemingly identical problem on my 21.5 inch Imac...i realize this is the wrong section of the forum but did you find a solution, restarting with 
```
sudo nvidia-xconfig
sudo /etc/init.d/gdm restart
```also works for me.....

here's my sources.list

```
jpitt@Sulfide-Linux:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
```

---

### Post by kbluck on 2010-09-10
Nope, haven't found any permanent solution yet. For now I just try to avoid restarting the computer and do the X re-config workaround when I do have to.

--
Kevin

---

### Post by isantop on 2010-09-13
Please go to System > Administration > Nvidia X Server Settings. There, you should see an option for "X Server Display Configuration. Click "Detect Displays", then "Apply," then finally "Save to X Configuration File. You may need to enter your password, and there may be an error about being unable to perse existing xorg.conf file. These are normal, and you can click through them.

If you get errors trying to start the Nvidia X Server Settings applet, then goto System > Administration > Hardware Drivers. It should detect the drivers available, then tell you that some version of the driver is already installed. Click on that version, then click on Remove. 

Reboot your system, then go back to System > Administration > Hardware Drivers, and re-activate the Version Current Nvidia Driver.

---

### Post by yh88 on 2010-10-01
Hello, I have that same problem,
tried the restart GDM :worked
tried the detect display:worked
tried the save the config file: worked
but after all that I still get the same message "failed yo initialize nvidia kernel.

May be we should look to dependencies.
Hope to get help..

---

### Post by kbluck on 2010-10-01
> **isantop said:**
> Please go to System > Administration > Nvidia X Server Settings....

Thanks for your reply and sorry for the slowness of mine.

I should have made clearer that I've already done all of those things you recommended, multiple times. This is how I discovered the technique of regenerating my xorg.conf file and restarting GDM whenever the failure occurs, which is my current workaround.

--
Kevin

---

### Post by isantop on 2010-10-01
Okay. Please try opening a terminal and running:

```
sudo rm -v /etc/X11/xorg.conf
```

This will remove the current X configuration file, causing it to load a default one when the server next starts.

After this, reboot your computer.

---

### Post by kbluck on 2010-10-01
> **isantop said:**
> Okay. Please try opening a terminal and running:

```
sudo rm -v /etc/X11/xorg.conf
```

Thanks again for your reply.

I have tried many, many permutations of messing with the xorg.conf file, including your above recommendation to delete the file altogether. I've also tried generating a default one using both xorg and nvidia tools, changing settings using both xorg and nvidia tools, and hand-editing various parameters in the file.

Given that nothing I do to the xorg.conf file makes any difference to the problem, and the fact that the problem first appeared following a package update with no config changes, makes me feel quite certain it is not a configuration problem, but rather a driver problem.

I will shortly be updating to the recent nvidia driver update. We'll see if that helps.

--
Kevin

---

### Post by yh88 on 2010-10-02
> Given that nothing I do to the xorg.conf file makes any difference to the problem, and the fact that the problem first appeared following a package update with no config changes, makes me feel quite certain it is not a configuration problem, but rather a driver problem.

I agree with you, but also I don't think it's the driver as it works when you restart GDM.
So I really think it's the connection between the kernel & Nvidia kernel module, or the Nvidia kernel itself.

Any ideas?

---

### Post by kbluck on 2010-10-03
Well, latest updates didn't help.

Maybe when Maverick comes out that will fix it.

--
Kevin

---

### Post by Objekt on 2010-10-03
I'm having similar problems with Ubuntu 10.04 on completely different hardware (list in signature).

I use two monitors, an NEC AccuSync 120 CRT and a Samsung BX2440X LCD.  By necessity (video card has only DVI inputs), they're both plugged in via straight DVI cable or (in the case of the CRT) a DVI adapter.  This is a configuration which has worked just fine for months, running Ubuntu 9.10 + Nvidia drivers + Xinerama turned on.

I had a grand total of a few days with Ubuntu 10.04 running smoothly, and was thinking about moving to it for good, then repurposing the disk space occupied by my Ubuntu 9.10 install.  Boy am I glad I didn't!  I simply don't bother running 10.04 now, because I am tired of having to reinstall the Nvidia drivers & restart Xserver every stinking time.

My sob story has its own thread here: [http://ubuntuforums.org/showthread.php?p=9920358#post9920358]("http://ubuntuforums.org/showthread.php?p=9920358#post9920358")

---

### Post by Objekt on 2010-10-06
Well, how do you like that!  There seems to be an incompatibility between the recent Nvidia binary drivers (256.53) and 10.04.  I uninstalled all drivers, then ran gtk-jockey (aka "Hardware Drivers" under System>Administration menu).  I had it install the 195.something drivers, rebooted, and all seems to be well with my 10.04 install.

That said, I still don't quite trust 10.04.  If it makes it to two weeks without another show-stopping glitch, I'll start migrating all my /home files, application preferences, Firefox profile, etc.  But I'm keeping my 9.10 install, at least until the official end of support.

---

### Post by yh88 on 2010-10-09
Well I just updated my system without doing any new thing, and it rebooted like charm.
Thank god

---

