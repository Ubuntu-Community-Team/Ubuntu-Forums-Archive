---
title: "Linux 3.10 - rc1"
date: 2013-05-11
forum: Ubuntu Development Version
---

### Post by wnelson on 2013-05-11
Is now out. [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10-rc1-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10-rc1-precise/)

Walt

P.S. Really fast boot for being an rc1

---

### Post by tibere86 on 2013-05-12
Thanks for the heads up. There seems to be a few extra debs in this folder. Which of the amd64 debs do I need to install for my 64-bit Ubuntu 13.04 laptop?

---

### Post by wnelson on 2013-05-12
> **tibere86 said:**
> Thanks for the heads up. There seems to be a few extra debs in this folder. Which of the amd64 debs do I need to install for my 64-bit Ubuntu 13.04 laptop?

I did not use the virtual stuff. Just the large amd64 linux-image file. If you use virtualization then you install those files.

Walt

---

### Post by Rukiri on 2013-05-12
Just a pro tip, ubuntu ships with some bad kernels and generally everything is ticked if you decidedd to open menuconfig.
I always recommend for those that are capable to download the latest kernel from kernel.org and compile yourself, the system will boot quicker(quicker than any ubuntu kernel) and actually run better(if you know what you're doing).

With all that aside, it seems 3.10 will see some major improvements to audio, amd powermanagement, and so forth.

I just finished a fresh Futnoo install with 3.10 a few hrs ago and just finished compiling kde, I must say 3.10 is going to be a fast kernel and I'll even go out on a lim saying 3.10-rc1 is already stable (c'mon linus I miss my bandages)

Anyone think kernel 4.0 will be the next mainline?

---

### Post by cole.mickens on 2013-05-12
Sorry if I'm confused.

Where is the non-virtual package for image-extra? Has it simply not been built yet?

> 
linux-headers-3.10.0-031000rc1-generic depends on linux-headers-3.10.0-031000rc1;


Getting that as well.

Where's the usual linux-headers-[blah]-all ?

---

### Post by dmtr on 2013-05-12
Yes. +1 on that. Missing  linux-headers-[blah]-all.

---

### Post by JMB74 on 2013-05-12
Well, it's been built for the "precise" configs and packaging, so it's going to be a bit messed up or not with the same built packages as the recent ones for raring and saucy.

May be better to wait for versions built using raring or saucy packaging and configs to appear.

---

### Post by Rukiri on 2013-05-12
okay whenever you install a new kernel in ubuntu it SHOULD have a path of /usr/src/linux.
So like in every other distro just run make headers_install

---

### Post by zika on 2013-05-13
Full 3.10 rc1 is ready...
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10-rc1-saucy/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10-rc1-saucy/)

---

### Post by VinDSL on 2013-05-13
> **zika said:**
> Full 3.10 rc1 is ready...
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10-rc1-saucy/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10-rc1-saucy/)
Aye!

That's more like it...

I had was experiencing unmet dependencies, with the Precise build.

Thanks!  ;)

---

### Post by VinDSL on 2013-05-13
Oh, drat!  Now, the initial nVidia driver module is failing to build.

Guess I'll need to play the video driver shell game -- looking for nVidia drivers that recognize Linux 3.10

Hrm...

I had to patch my nVidia drivers, when Linux 3.9 hit_the_street.  Maybe, I'll try that again.

Anybody have any luck, getting nVidia legacy drivers, e.g. 304.x, working with Linux 3.10?!?!?

---

### Post by slickymaster on 2013-05-13
> **wnelson said:**
> Is now out. [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10-rc1-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10-rc1-precise/)

Walt

P.S. Really fast boot for being an rc1

```
~$ lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy
3.10.0-031000rc1-generic
```

Yeah, I was surprised with the boot time. So far it's working smoothly, like a charm.

---

### Post by deri on 2013-05-13
I noticed that there is saucy available now. Installed and ready to try. People have been saying that it's fast booting. Very curious too see if I see any change.

---

### Post by sgage on 2013-05-13
> **VinDSL said:**
> Oh, drat!  Now, the initial nVidia driver module is failing to build.

Guess I'll need to play the video driver shell game -- looking for nVidia drivers that recognize Linux 3.10

Hrm...

I had to patch my nVidia drivers, when Linux 3.9 hit_the_street.  Maybe, I'll try that again.

Anybody have any luck, getting nVidia legacy drivers, e.g. 304.x, working with Linux 3.10?!?!?

I'm having the same problem with nvidia-313-updates. I removed them for the time being just to be able to boot with 3.10. I do not notice a marked improvement in boot time, maybe a couple of seconds.

My 'shell game' is finding nvidia drivers that allow resuming from suspend and VT's. 313 seems to be it right now, but now there's a third shell - will the drivers work with Linux 3.10? Oh well, I'm sure it will all get straightened out by and by...

---

### Post by pqwoerituytrueiwoq on 2013-05-13
> **deri said:**
> I noticed that there is saucy available now. Installed and ready to try. People have been saying that it's fast booting. Very curious too see if I see any change.
boots fast on my desktop, but it does not like nvidia 313.30, but to be fair i installed it on raring not saucy
make log ([FONT=courier new]/var/lib/dkms/nvidia-313-updates/313.30/build/make.log[/FONT])
[http://pastebin.com/wtYkE2H0](http://pastebin.com/wtYkE2H0)
still able to post this from 3.10 though, not i need my nvidia driver on this box :(

---

### Post by cflow on 2013-05-13
[http://www.h-online.com/open/news/item/Feature-set-of-Linux-3-10-defined-1861273.html](http://www.h-online.com/open/news/item/Feature-set-of-Linux-3-10-defined-1861273.html)

> With 11,963 commits, Torvalds and his co-developers have integrated more  changes than have ever been processed in a merge window before,  prompting Torvalds to declare: "this is the biggest -rc1 in the last  several years (perhaps ever)". However, diffstat's number of new and  removed lines of code is only slightly higher than in Linux 3.9 and is  far from being a new record.

Very interesting...

Though i'm quite happy with 3.9, and not in a rush. I'll wait until the saucy updates come along.

---

### Post by deri on 2013-05-14
I don't see any difference 3.10 vs 3.9. Other than ati driver doesn't install as a module.

---

### Post by VinDSL on 2013-05-26
I'm in...  Flying like the wind, it is!

```
vindsl@Zuul:~$ echo && echo "~ VinDSL Unity Debug Script 12.12.06 (vindsl.com) ~" && echo -n "Current Date/Time: " && date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Gnome Release: " && gnome-shell --version && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Xserver Xorg Core Branch:" && apt-cache policy xserver-xorg-core | grep Installed && echo || echo && echo "Tree Map of PCI Devices:" && lspci -tv && echo || echo && echo "Display Properties:" && echo -n " lcd monitor:    Dell UltraSharp 1907FP (analog input)" && echo  && xdpyinfo | grep -E '(resolution|dimensions)' && echo

~ VinDSL Unity Debug Script 12.12.06 (vindsl.com) ~
Current Date/Time: Sun May 26 16:52:04 MST 2013
Distro Release: Ubuntu Saucy Salamander (development branch)
Kernel Release: Linux 3.10.0-031000rc2-generic
Gnome Release: GNOME Shell 3.9.1
Unity Release: unity 7.0.0

OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NV4B
OpenGL version string:  2.1 Mesa 9.2.0

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
Installed-Size: 106
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2+edgers
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

Xserver Xorg Core Branch:
  Installed: 2:1.13.4~git20130508+server-1.13-branch.10c42f57-0ubuntu0ricotz~raring

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82875P/E7210 Memory Controller Hub
           +-01.0-[01]----00.0  NVIDIA Corporation G73 [GeForce 7600 GT]
           +-06.0  Intel Corporation 82875P/E7210 Processor to I/O Memory Interface
           +-1d.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
           +-1e.0-[02]----0c.0  Lite-On Communications Inc LNE100TX
           +-1f.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801EB (ICH5) SATA Controller
           +-1f.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller
           \-1f.5  Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller

Display Properties:
 lcd monitor:    Dell UltraSharp 1907FP (analog input)
  dimensions:    1280x1024 pixels (338x270 millimeters)
  resolution:    96x96 dots per inch

vindsl@Zuul:~$ 

```

Had to use a workaround, of sorts -- got impatient and replaced nVidia-304 with Nouveau.  :)

Took a while to tweak Nouveau's performance to match nVidia-304.

EXTRA CREDIT READING:  [http://ubuntuforums.org/showthread.php?t=2097359&page=34&p=12664999&viewfull=1#post12664999](http://ubuntuforums.org/showthread.php?t=2097359&page=34&p=12664999&viewfull=1#post12664999)

---

### Post by GuenterErde on 2013-05-26
i was thinking about compling it myself. Have there been any driver issues (I use Nvidia)?

---

### Post by fooman on 2013-05-26
Current Date/Time: Sun May 26 23:01:57 EDT 2013
Distro Release: Ubuntu Saucy Salamander (development branch)
Kernel Release: Linux 3.10.0-031000rc3-generic
Gnome Release: GNOME Shell 3.6.3.1
Unity Release: unity 7.0.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GTX 480/PCIe/SSE2
OpenGL version string:  4.3.0 NVIDIA 319.23

:D

---

### Post by pqwoerituytrueiwoq on 2013-05-27
was going to say 3.10rc3 is here but fooman beet me to it
[http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D)
[URL="http://ubuntuforums.org/member.php?u=1399989"][B][COLOR=#000000]
@GuenterErde[/COLOR][/B][/URL] 
to my knowledge to use nvidia drivers with 3.10 you need to use the 319.23 driver

---

### Post by pqwoerituytrueiwoq on 2013-05-27
Using a Sandy Bridge Intel CPU here with using 3.10rc3 the cpu governor system seems broken
all i can use is performance and powersave, i am using raring, anyone able to confirm this in saucy

look in[FONT=courier new] /sys/devices/system/cpu/cpu*/cpufreq/[/FONT]

---

### Post by zika on 2013-05-27
[http://www.phoronix.com/scan.php?page=news_item&px=MTM3NDQ](http://www.phoronix.com/scan.php?page=news_item&px=MTM3NDQ)

---

