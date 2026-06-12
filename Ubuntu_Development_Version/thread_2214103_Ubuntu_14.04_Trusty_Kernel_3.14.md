---
title: "Ubuntu 14.04 Trusty Kernel 3.14"
date: 2014-03-30
forum: Ubuntu Development Version
---

### Post by Redalien0304 on 2014-03-30
Thinking About Installing Kernel 3.14 in Ubuntu Trusty. Has anyone done this & had any Problems?? Or is it pretty much safe to do??
Was going to Follow Instructions from here [http://linuxg.net/how-to-install-kernel-3-14-rc6-on-ubuntu-and-linux-mint/](http://linuxg.net/how-to-install-kernel-3-14-rc6-on-ubuntu-and-linux-mint/)
If there better site or Guide Plz let me Know. Thanks any Info is Welcome.

---

### Post by QDR06VV9 on 2014-03-30
> **Redalien0304 said:**
> Thinking About Installing Kernel 3.14 in Ubuntu Trusty. Has anyone done this & had any Problems?? Or is it pretty much safe to do??
Was going to Follow Instructions from here [http://linuxg.net/how-to-install-kernel-3-14-rc6-on-ubuntu-and-linux-mint/](http://linuxg.net/how-to-install-kernel-3-14-rc6-on-ubuntu-and-linux-mint/)
If there better site or Guide Plz let me Know. Thanks any Info is Welcome.
That should get you through it well enough. Been testing kernels for better part of 2 years now.
 Most are stable outside of not being patched for video drivers.
My method goes like this.
1. Build a folder in your home directory I name mine (kernels)
2.Go to mainline[ PPA ]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14-rc4-trusty/")& download your versions aka (32bit or64bit) and save them to new kernel folder.
More Info You will need headers (2) Debs either (32 or 64 bit) and all.deb ( So you will have 2 .deb files headers and al.deb)
3.Pull up a Terminal 
```
cd kernels
sudo dpkg -i *.deb
```
Then reboot into your newly installed kernel

---

### Post by Redalien0304 on 2014-03-30
Ok Installed Kernel 3.14 RC6 from [http://linuxg.net/how-to-install-kernel-3-14-rc6-on-ubuntu-and-linux-mint/](http://linuxg.net/how-to-install-kernel-3-14-rc6-on-ubuntu-and-linux-mint/)
but still booted into 3.13. checked using uname -a. Have 13.10 Installed Also, is Default Os for now. Any help is Appreciated. Thanks.

---

### Post by Redalien0304 on 2014-03-30
Ok Fixed by Changing Default OS Via Editing Grub in Etc/Default/ on 13.10 Partition.

---

### Post by Bibek on 2014-04-16
just wondering if we will be getting kernel 3.14 with trusty. is there a possibility ?

---

### Post by TenPlus1 on 2014-04-17
I followed this simple guide to install 3.14 kernel on my Lubuntu 14.04 install and it worked perfectly, even the nvidia binary drivers are a-ok...

[http://www.upubuntu.com/2014/04/installupgrade-to-linux-kernel-314.html](http://www.upubuntu.com/2014/04/installupgrade-to-linux-kernel-314.html)

---

### Post by Ian_Worrall on 2014-04-17
> **Bibek said:**
> just wondering if we will be getting kernel 3.14 with trusty. is there a possibility ?

Not until the release of Ubuntu 14.04.1 on 24th July.
3.15 will be stable by then (maybe even 3.16) so 3.14 may get skipped altogether in the official release.

---

### Post by sdowney717 on 2014-04-17
running it now.

following this
[http://www.upubuntu.com/2014/04/installupgrade-to-linux-kernel-314.html](http://www.upubuntu.com/2014/04/installupgrade-to-linux-kernel-314.html)

But I get strange errors at boot having to do with ram drive, cant create it and sdc which is my usb hard drive.
About 20 lines of errors run down the screen.

I am booting off a usb hard drive.
kernel 3.13 does not do this.

---

### Post by evan8 on 2014-04-17
my upgrade didn't go too well. display was messed up for 5 seconds then it went back to normal.

luckily this [http://www.upubuntu.com/2014/04/inst...ernel-314.html]("http://www.upubuntu.com/2014/04/installupgrade-to-linux-kernel-314.html")  also told me how to unistall it. so everything is fine now. I hope they work on the kernel more.

---

### Post by Redalien0304 on 2014-04-17
thought i saw or heard somewhere that Kernel 3.14 would get Backported to Ubuntu 14.404 Trusty? Since it came with Kernel 3.13

---

### Post by evan8 on 2014-04-17
I'd probably avoid this kernel for now. Doubt it will be forced on 14.04 final

---

### Post by Ian_Worrall on 2014-04-17
> **Redalien0304 said:**
> thought i saw or heard somewhere that Kernel 3.14 would get Backported to Ubuntu 14.404 Trusty? Since it came with Kernel 3.13

ISTR chunks of 3.14 have already been backported to 3.13. The whole thing may land late July, as I posted above.

---

### Post by Ian_Worrall on 2014-04-17
> **evan8 said:**
> I'd probably avoid this kernel for now. Doubt it will be forced on 14.04 final

It's not. Kernel Freeze was last week, and 3.14 final didn't make the cut.

---

### Post by su:bhatta on 2014-04-17
Well, for a week am running the 3.14.0-lowlatency , coz it lets my system 'Sleep'.
With 3.13 it wouldn't wake up.

3.14 I must add is running nice!

---

### Post by sdowney717 on 2014-04-17
```
boat@boat-MS-7529:~$ uname -r
3.14.0-031400-generic
boat@boat-MS-7529:~$ 

```

Runs ok,  although I never notice any noticeable difference one kernel to another.

This one does give me that ram drive error, but maybe the other did too and was not displaying the text on boot.

---

### Post by QDR06VV9 on 2014-04-17
Probably be a good idea to check over [mainline ppa]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.1-trusty/") [SIZE=3][SIZE=2]from time to time looks as if they will keep updates there[/SIZE][/SIZE][B][SIZE=3]
mainline/v3.14.1-trusty[/SIZE][/B]:D

```
Linux me-Aspire-M3300 3.14.1-031401-lowlatency #201404141220 SMP PREEMPT Mon Apr 14 16:29:57 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```
Regards
Oh almost forgot,  Once I am satisfied with the new kernel I remove the previous version.:)

---

### Post by su:bhatta on 2014-04-18
> **runrickus said:**
> Probably be a good idea to check over [mainline ppa]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.1-trusty/") [SIZE=3][SIZE=2]from time to time looks as if they will keep updates there[/SIZE][/SIZE][B][SIZE=3]
mainline/v3.14.1-trusty[/SIZE][/B]:D

```
Linux me-Aspire-M3300 3.14.1-031401-lowlatency #201404141220 SMP PREEMPT Mon Apr 14 16:29:57 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```
Regards
Oh almost forgot,  Once I am satisfied with the new kernel I remove the previous version.:)

Hey runrickus, I am also thinking of getting that 3.14.1 low-latency !

Do you keep a single kernel or one backup is also kept?

EDIT : Took the plunge already !
> :~$ uname -a
Linux nbe-42 3.14.1-031401-lowlatency #201404141220 SMP PREEMPT Mon Apr 14 16:29:57 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04 LTS
Release:        14.04
Codename:       trusty

This one lets my laptop 'Sleep' in peace too !

---

### Post by QDR06VV9 on 2014-04-18
> **su:bhatta said:**
> Hey runrickus, I am also thinking of getting that 3.14.1 low-latency !

Do you keep a single kernel or one backup is also kept?

EDIT : Took the plunge already !


This one lets my laptop 'Sleep' in peace too !
The only kernel I keep is the one that ships with distro
And the one that I am currently using 3.14.1., after i have run it for few days to see if it is a keeper.
Then I will UN-install 3.14.0
Hope that is clear.:)

---

### Post by VinDSL on 2014-04-20
Only 'problem' I've had with Linux 3.14 is, I keep getting this @ boot

```
vindsl@Zuul:~$ dmesg | grep MPU-401

[   11.195649] MPU-401 device not found or device busy

vindsl@Zuul:~$ 

```

Everything seems to work, so I ignore it.

Been happening all along, ever since the first RC...

---

### Post by QDR06VV9 on 2014-04-20
> **VinDSL said:**
> Only 'problem' I've had with Linux 3.14 is, I keep getting this @ boot

```
vindsl@Zuul:~$ dmesg | grep MPU-401

[   11.195649] MPU-401 device not found or device busy

vindsl@Zuul:~$ 

```

Everything seems to work, so I ignore it.

Been happening all along, ever since the first RC...
Hey VinDSL Good to see you peek in.
I get those also and same as you I just Ignore, Ive also seen the same on other threads.
You going to ride the next Devel Release?

---

### Post by VinDSL on 2014-04-20
> **runrickus said:**
> Hey VinDSL Good to see you peek in.
I get those also and same as you I just Ignore, Ive also seen the same on other threads.
You going to ride the next Devel Release?
Hi runrickus,

Thanks -- I've been busy in the Peppermint forums.

And, yes, I'll be riding the next dev release.

BTW, I just installed the Linux 3.15RC2 and it built just fine, even the nVidia legacy drivers.

```
vindsl@Zuul:~$ echo && echo "~ VinDSL Unity Debug Script 13.07.08 (vindsl.com) ~" && echo -n "Current Date/Time: " && TZ='UTC' date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Gnome Release: " && gnome-shell --version && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Package: mesa-common-dev" && dpkg -s mesa-common-dev | sed 's/^/  /' | grep Version && echo || echo && echo "Package: xserver-xorg-core" && apt-cache policy xserver-xorg-core | grep Installed && echo || echo && echo "Package: xserver-common" && apt-cache policy xserver-common | grep Installed && echo || echo && echo "Package: xserver-xephyr" && apt-cache policy xserver-xephyr | grep Installed && echo || echo && echo "Tree Map of PCI Devices:" && lspci -tv && echo || echo && echo "Display Properties:" && echo -n " lcd monitor:    Dell UltraSharp 1907FP (analog input)" && echo && xdpyinfo | grep -E '(resolution|dimensions)' && echo

~ VinDSL Unity Debug Script 13.07.08 (vindsl.com) ~
Current Date/Time: Sun Apr 20 21:29:03 UTC 2014
Distro Release: Ubuntu 14.04 LTS
Kernel Release: Linux 3.15.0-031500rc2-generic
Gnome Release: GNOME Shell 3.10.4
Unity Release: unity 7.2.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.117

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

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 115
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.1.0-2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Homepage: http://mesa3d.org/

Package: mesa-common-dev
  Version: 10.1.0-4ubuntu5

Package: xserver-xorg-core
  Installed: 2:1.15.1-0ubuntu2

Package: xserver-common
  Installed: 2:1.15.1-0ubuntu2

Package: xserver-xephyr
  Installed: 2:1.15.1-0ubuntu2

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

MPU-401 error is still there, though.  Think I'll compile it and see if something is missing...  ;)

---

