---
title: "Kernel 3.12-rc4 is here"
date: 2013-10-06
forum: Ubuntu Development Version
---

### Post by paul_in_london on 2013-10-06
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-rc4-saucy/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-rc4-saucy/)

---

### Post by fyfe54 on 2013-10-06
Hmm.  Where is the all.deb file?  Missing?  Not needed?

---

### Post by paul_in_london on 2013-10-06
> **fyfe54 said:**
> Hmm.  Where is the all.deb file?  Missing?  Not needed?

Yes, you're right. I didn't bother checking that because I'd already compiled it.

Sometimes when this happens you need to wait for the next rc before all of the debs are there (no pun intended).

---

### Post by fyfe54 on 2013-10-06
> **paul_in_london said:**
> Yes, you're right. I didn't bother checking that because I'd already compiled it.

Sometimes when this happens you need to wait for the next rc before all of the debs are there (no pun intended).

Thanks, I'll check again later.  If you are in the UK, you should be asleep, so there is no rush.

---

### Post by Nick Payne on 2013-10-06
3.11.4 and 3.10.15 are also missing the all.deb file. Are there now just two files per architecture to download and install, or has there been a stuffup when the latest versions were uploaded to kernel.ubuntu.com?

---

### Post by VinDSL on 2013-10-06
My money is on 'stuffup'. ;)

You could try it, but it looks like 12MB, give_or_take, is missing without the all.deb file.

Or, you might try Paul's most-excellent localmodconfig compiling procedure, [over here]("http://ubuntuforums.org/showthread.php?t=2177674&p=12803771&viewfull=1#post12803771").

I've successfully used it twice today, on 3.10.15 & 3.12-rc4 (follow-up at end-of-thread)...


```
vindsl@Zuul:~$ echo && echo "~ VinDSL Unity Debug Script 13.07.08 (vindsl.com) ~" && echo -n "Current Date/Time: " && TZ='UTC' date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Gnome Release: " && gnome-shell --version && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Package: mesa-common-dev" && dpkg -s mesa-common-dev | sed 's/^/  /' | grep Version && echo || echo && echo "Package: xserver-xorg-core" && apt-cache policy xserver-xorg-core | grep Installed && echo || echo && echo "Package: xserver-common" && apt-cache policy xserver-common | grep Installed && echo || echo && echo "Package: xserver-xephyr" && apt-cache policy xserver-xephyr | grep Installed && echo || echo && echo "Tree Map of PCI Devices:" && lspci -tv && echo || echo && echo "Display Properties:" && echo -n " lcd monitor:    Dell UltraSharp 1907FP (analog input)" && echo && xdpyinfo | grep -E '(resolution|dimensions)' && echo

~ VinDSL Unity Debug Script 13.07.08 (vindsl.com) ~
Current Date/Time: Mon Oct  7 02:39:03 UTC 2013
Distro Release: Ubuntu Saucy Salamander (development branch)
**[COLOR="#0000CD"]Kernel Release: Linux 3.12.0-rc4-vindsl[/COLOR]**
Gnome Release: GNOME Shell 3.10.0.1
Unity Release: unity 7.1.1

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
  Version: 9.2.0~git20131002+9.2.2eb55601-0ubuntu0sarvatt

Package: xserver-xorg-core
  Installed: 2:1.14.3-3ubuntu1

Package: xserver-common
  Installed: 2:1.14.3-3ubuntu1

Package: xserver-xephyr
  Installed: 2:1.14.3-3ubuntu1

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

---

### Post by zika on 2013-10-07
999 994 work nicely from just two .deb-s...
My money is on two deb-s in future...
In rc4 I suspect that just a dependency is left by mistake...

---

### Post by QDR06VV9 on 2013-10-07
Just incase anybody is interested nvidia fails.
```
vmlinuz-3.12.0-031200rc4-generic
Error! Bad return status for module build on kernel: 3.12.0-031200rc4-generic (i686)


```

---

### Post by rimez on 2013-10-07
@Paul - In the RC3 thread you provided a great tutorial on compiling the kernel. The thing is, it doesn't produce the 'all' headers. Is there a way to compile that as well?  I really need to run virtualbox on my system... my VM's are not working and I assume it's because of the missing 'all' headers... I am a noob though so I could b wrong. 

Any advice on this would be appreciated.

EDIT: I've compiled the rc4 without issue and it seems I can run my virtuals without issue. I'm really digging 3.12 on my U430p :) Finally, I don't feel as if I wasted my money on this laptop. Now if I could just get the Nvidia card to work....

---

### Post by zika on 2013-10-08
Forgot yesterday to write: if You use --ignore-depends with dpkg rc4 installs fone and works OK... Same is applicable for 996...
Update&#8321;: Also remnant headers packages (from previous days for 996 994 999) should be purged... That would purge also headers-generic... It works even without them...

---

### Post by JMB74 on 2013-10-08
> **fyfe54 said:**
> Hmm.  Where is the all.deb file?  Missing?  Not needed?

They _should_ be there, but are not because the builds are failing before they can be produced, but after the other debs have been built.

Saying that, unless you have specific drivers or kernel modules that need a rebuild using the arch independent headers for each new kernel version, then you can run just fine without the _all package. 

If you do need it, looks like you will have to wait until the fix the mainline build script.

---

### Post by fyfe54 on 2013-10-08
> **JMB74 said:**
> They _should_ be there, but are not because the builds are failing before they can be produced, but after the other debs have been built.

Saying that, unless you have specific drivers or kernel modules that need a rebuild using the arch independent headers for each new kernel version, then you can run just fine without the _all package. 

If you do need it, looks like you will have to wait until the fix the mainline build script.

Thanks for the info, but I can wait for the next rc builds.

---

### Post by zika on 2013-10-08
rc4 is now complete...

It was nice to learn what my machine can do without... ;)

---

### Post by QDR06VV9 on 2013-10-08
Ya Baby! Nvidia worked..:D

```
Current Date/Time: Wed Oct  9 03:12:13 UTC 2013
Distro Release: Ubuntu Saucy Salamander (development branch)
Kernel Release: Linux 3.12.0-031200rc4-generic
Qt: 4.8.4
KDE Development Platform: 4.11.2
Dolphin: 4.11.2


```



I am realy likeing KDE 4.11!!
```
Package: xserver-xorg-core
  Installed: 2:1.14.3-3ubuntu1

Package: xserver-common
  Installed: 2:1.14.3-3ubuntu1

Package: xserver-xephyr
  Installed: 2:1.14.3-3ubuntu1

Tree Map of PCI Devices:
-[0000:00]-+-00.0  NVIDIA Corporation MCP61 Memory Controller
           +-01.0  NVIDIA Corporation MCP61 LPC Bridge
           +-01.1  NVIDIA Corporation MCP61 SMBus
           +-01.2  NVIDIA Corporation MCP61 Memory Controller
           +-02.0  NVIDIA Corporation MCP61 USB 1.1 Controller
           +-02.1  NVIDIA Corporation MCP61 USB 2.0 Controller
           +-04.0-[01]--+-06.0  Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+
           |            +-07.0  Creative Labs SB Audigy
           |            +-07.1  Creative Labs SB Audigy Game Port
           |            \-07.2  Creative Labs SB Audigy FireWire Port
           +-06.0  NVIDIA Corporation MCP61 IDE
           +-08.0  NVIDIA Corporation MCP61 SATA Controller
           +-09.0-[02]----00.0  NVIDIA Corporation G96 [GeForce 9500 GT]
           +-18.0  Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
           +-18.1  Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
           +-18.2  Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
           \-18.3  Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

Display Properties:
 lcd monitor:    Dell UltraSharp 1907FP (analog input)
  dimensions:    1920x1080 pixels (513x292 millimeters)
  resolution:    95x94 dots per inch


```

---

