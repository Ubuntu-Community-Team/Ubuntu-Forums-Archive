---
title: "LightDM Breakage: &quot;if it ain't broke you haven't tweaked it enough&quot;"
date: 2015-06-06
forum: Ubuntu Development Version
---

### Post by VinDSL on 2015-06-06
Yesterday's upgrade broke Wily, on this machine.

I'm using my 10.10 backup, right now...

15.10 is stopping @ boot, while loading LightDM.  The display just flashes a LightDM command.

Anyone else experiencing this???

I have a *feeling* it's one of those 'bad timing' things where the repo wasn't fully populated with recent updates/upgrades.

---

### Post by zika on 2015-06-06
Add **systemd.unit=multi-user.target (**if You use SystemD) or **text** (if You use UpStart) to kernel-boot-line and boot machine into nonGUI mode. Then check logs for package-update/upgrade-system_You_use and see what was last upgraded and have to do with Your symptoms. Also try with commands for reconfiguring/finishing upgrade process that might have been interrupted...

---

### Post by ajgreeny on 2015-06-06
I have just updated my virtual install of Wily in VBox (Xubuntu 14.04 64bit host) and had no problems at all; after reboot it is running fine.
Hardware is i5-3750K with Intel HD4000 IGP, 8GB ram, but using all four cores, 4GB ram, and 128MB graphics memory, if that makes any difference in a VM.

---

### Post by VinDSL on 2015-06-06
Okay, I tracked it down...

xserver-xorg-core is crashing with SIGBRT during the Unity support test.

@zika...

```
/usr/bin/X-core :0 -seat seat0 -auth/var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
```

Alrighty, then.  Time to tweak it... :)

---

### Post by VinDSL on 2015-06-06
Hrm...

```
~ VinDSL Unity Debug Script 15.02.13 (vindsl.com) ~
Current Date/Time: Sat Jun  6 23:02:46 UTC 2015
Distro Release: Ubuntu Wily Werewolf (development branch)
Kernel Release: Linux 4.1.0-040100rc2-generic
Gnome Release: GNOME Shell 3.14.4
Unity Release: unity 7.3.2

OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.6, 128 bits)
OpenGL version string:  3.0 Mesa 10.5.2

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no

Browser Release: Chromium ver.Using PPAPI flash.
43.0.2357.81

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 123
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.2.0-1build1
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Homepage: http://mesa3d.org/

Package: mesa-common-dev
 Version: 10.5.2-0ubuntu1

Package: xserver-xorg-core
  Installed: 2:1.17.1-0ubuntu4

Package: xserver-common
  Installed: 2:1.17.1-0ubuntu4

Package: xserver-xephyr
  Installed: 2:1.17.1-0ubuntu4

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82875P/E7210 Memory Controller Hub
           +-01.0-[01]----00.0  NVIDIA Corporation G73 [GeForce 7600 GT]
           +-03.0-[02]----01.0  Intel Corporation 82547EI Gigabit Ethernet Controller
           +-06.0  Intel Corporation 82875P/E7210 Processor to I/O Memory Interface
           +-1d.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
           +-1e.0-[03]----0c.0  Lite-On Communications Inc LNE100TX
           +-1f.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801EB (ICH5) SATA Controller
           +-1f.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller
           \-1f.5  Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller

Display Properties:
 lcd monitor:    Dell UltraSharp 1907FP (analog input)
  dimensions:    1024x768 pixels (271x203 millimeters)
  resolution:    96x96 dots per inch

vindsl@Zuul:~$ 

```

Looks like Nouveau went janky.

---

### Post by VinDSL on 2015-06-06
Okay, I tried this, and that, and everything else - danced on the keyboard for awhile - and all that sort of thing.

Luckily, there is a bug in Linux 4.1 that allowed me to break out of recovery mode and directly into the login screen - thus, bypassing plymouth. (hack wouldn't work on Linux 4.0 BTW)

I got rid of LightDM and switched to GDM, which made no difference - thus, not a LightDM prob.

Everything kept pointing to a video card driver issue, so I reinstalled Nouveau, to no avail.

Finally, I switched to nVidia 304 current -- which hasn't worked on this legacy card, ever since I can remember -- and BINGO!

Anyhoo, onward and upward!

Keep the breakage coming.  This is fun!!!  :p

---

### Post by VinDSL on 2015-06-06
Oh, yeah... ;)

```
~ VinDSL Unity Debug Script 15.02.13 (vindsl.com) ~
Current Date/Time: Sun Jun  7 00:22:35 UTC 2015
Distro Release: Ubuntu Wily Werewolf (development branch)
Kernel Release: Linux 4.1.0-040100rc2-generic
Gnome Release: GNOME Shell 3.14.4
Unity Release: unity 7.3.2

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.125

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Browser Release: Chromium ver.Using PPAPI flash.
43.0.2357.81

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 123
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.2.0-1build1
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Homepage: http://mesa3d.org/

Package: mesa-common-dev
 Version: 10.5.2-0ubuntu1

Package: xserver-xorg-core
  Installed: 2:1.17.1-0ubuntu4

Package: xserver-common
  Installed: 2:1.17.1-0ubuntu4

Package: xserver-xephyr
  Installed: 2:1.17.1-0ubuntu4

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82875P/E7210 Memory Controller Hub
           +-01.0-[01]----00.0  NVIDIA Corporation G73 [GeForce 7600 GT]
           +-03.0-[02]----01.0  Intel Corporation 82547EI Gigabit Ethernet Controller
           +-06.0  Intel Corporation 82875P/E7210 Processor to I/O Memory Interface
           +-1d.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
           +-1e.0-[03]----0c.0  Lite-On Communications Inc LNE100TX
           +-1f.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801EB (ICH5) SATA Controller
           +-1f.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller
           \-1f.5  Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller

Display Properties:
 lcd monitor:    Dell UltraSharp 1907FP (analog input)
  dimensions:    1280x1024 pixels (339x271 millimeters)
  resolution:    96x96 dots per inch

vindsl@Zuul:~$ 

```

---

### Post by ventrical on 2015-06-06
Every time I get that llvmpipe thingy I just want to yell out .. "To the moon Alice !" :) lol

regards..

---

### Post by rrnbtter on 2015-06-06
Greetings,
My lightdm failed last week and I could only get to a terminal with a graphics selection box that failed to give me a desktop. My solution was to "apt-get install gdm" and when the install finishes it will ask if you want to run gnome desktop manager or lightdm and I choose lightdm and haven't had any problems since. The problem is that a problem with the updates causes Lightdm to lose its setup. Installing gdm just restores the setup. Hope this helps someone.

PS I'm just using Intel onboard video.

---

### Post by zika on 2015-06-07
> **rrnbtter said:**
> Greetings,
My lightdm failed last week and I could only get to a terminal with a graphics selection box that failed to give me a desktop. My solution was to "apt-get install gdm" and when the install finishes it will ask if you want to run gnome desktop manager or lightdm and I choose lightdm and haven't had any problems since. The problem is that a problem with the updates causes Lightdm to lose its setup. Installing gdm just restores the setup. Hope this helps someone.

PS I'm just using Intel onboard video.```
sudo dpkg-reconfigure lightdm
```will give You option of picking which DM You want. No need to go through whole install.

---

### Post by rrnbtter on 2015-06-07
Greetings,
In addition to everything else in this thread, if you are running an upgrade to Wily and have experimented with x-mir in the past you may want to open "/etc/lightdm/lightdm.conf.d/10-unity-system-compositor.conf" and comment out the Unity default. 
[SeatDefaults]
# type=unity
Having the unity system compositor enabled will break Lightdm at this point (at least on my system).

---

### Post by zika on 2015-06-07
> **rrnbtter said:**
> Greetings,
In addition to everything else in this thread, if you are running an upgrade to Wily and have experimented with x-mir in the past you may want to open "/etc/lightdm/lightdm.conf.d/10-unity-system-compositor.conf" and comment out the Unity default. 
[SeatDefaults]
# type=unity
Having the unity system compositor enabled will break Lightdm at this point (at least on my system).Folder You mention was moved early this year... It should be non-existent, let alone empty... ;)
Since it is Sunday (if I'm right) I'll just give URL to random discussion about that... ;)
[http://ubuntuforums.org/showthread.php?t=2205637](http://ubuntuforums.org/showthread.php?t=2205637)

---

### Post by rrnbtter on 2015-06-07
Greetings,

> **zika said:**
> Folder You mention was moved early this year... It should be non-existent, let alone empty... ;)


If it is a new Wily install perhaps, but my system is an upgrade from  Vivid and the folder is definitely there and will definitely break  Lightdm. All I have to do in remove the comment and I will lose my  desktop. I am only posting this for those that have the problem. It  doesn't affect those that don't have the problem, and they can ignore  all of this.

---

### Post by zika on 2015-06-07
> **rrnbtter said:**
> Greetings,
If it is a new Wily install perhaps, but my system is an upgrade from  Vivid and the folder is definitely there and will definitely break  Lightdm. All I have to do in remove the comment and I will lose my  desktop. I am only posting this for those that have the problem. It  doesn't affect those that don't have the problem, and they can ignore  all of this.I'm talking/writing about Vivid>Wily upgraded system. You've got warning about that folder not empty at some point in Vivid life, early this year, when LDM changed foder structure, but You did not react on that warning, I presume... File did not get erases since You've took care/ownership (not in real meaning, *nix style) of it. It should break LDM because it is in wrong place at wrong time.
I'm just writing, on the other side, because that folder should not exist, so casual reader would not get a wrong idea. ;)

---

### Post by rrnbtter on 2015-06-07
Greetings,

> **zika said:**
> 
I'm just writing, on the other side, because that folder should not exist, so casual reader would not get a wrong idea. ;)

If it ain't broke they haven't tweaked it enough!

---

### Post by zika on 2015-06-07
> **rrnbtter said:**
> Greetings,
If it ain't broke they haven't tweaked it enough!Axiom... ;)

---

### Post by ventrical on 2015-06-07
> **rrnbtter said:**
> Greetings,



If it ain't broke they haven't tweaked it enough!

On both my upgraded  and fresh wily installs I have had no problems with lightdm so it certainly applies to me.:)

Regards..

---

### Post by rrnbtter on 2015-06-09
Greetings,
This problem appears to have been fixed with today's updates. If the casual reader finds this confusing I will reiterate, I am only talking about my own personal computer, yours may still be muck (or not).

---

