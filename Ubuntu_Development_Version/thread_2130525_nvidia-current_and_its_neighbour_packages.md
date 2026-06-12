---
title: "nvidia-current and its neighbour packages"
date: 2013-03-29
forum: Ubuntu Development Version
---

### Post by Sworddragon on 2013-03-29
Lets make a short summary:

[list][*]nvidia-current is on 304.84-0ubuntu2.
[*]nvidia-current-updates is on 304.84-0ubuntu2.
[*]Then we have nvidia-310-updates (as I know its the legacy version for the GeForce 6 and 7 chips).
[*]But we have nvidia-313-updates too which doesn't provide any new legacy support as I know.[/list]

This constelation gives some questions and some problems:

[list][*]Why does we have nvidia-current and nvidia-current-updates (I remember one should be stable and the other beta but maybe this is wrong)?
[*]nvidia-current and nvidia-current-updates are older than the newest legacy version. There is also a newer non-legacy version. This behavior makes it difficult to keep the system up to date with the newest version. To do so I will have to manually check if there is a new nvidia-xxx-updates version. The last time I remember such manual checks was on my Windows time.[/list]

Does somebody know how this will continue in the future? Will nvidia-current[-updates] be the newest version again?

---

### Post by ronacc on 2013-03-29
according to the nvidia drivers page 304.84 is the latest that supports the 6 and 7 series gpu's the 310.xx supports series 8 and newer .

---

### Post by VinDSL on 2013-03-29
> **Sworddragon said:**
> Lets make a short summary:

[list][*]nvidia-current is on 304.84-0ubuntu2.
[*]nvidia-current-updates is on 304.84-0ubuntu2.
[*]Then we have nvidia-310-updates (as I know its the legacy version for the GeForce 6 and 7 chips).
[*]But we have nvidia-313-updates too which doesn't provide any new legacy support as I know.[/list]

This constelation gives some questions and some problems:

[list][*]Why does we have nvidia-current and nvidia-current-updates (I remember one should be stable and the other beta but maybe this is wrong)?
[*]nvidia-current and nvidia-current-updates are older than the newest legacy version. There is also a newer non-legacy version. This behavior makes it difficult to keep the system up to date with the newest version. To do so I will have to manually check if there is a new nvidia-xxx-updates version. The last time I remember such manual checks was on my Windows time.[/list]

Does somebody know how this will continue in the future? Will nvidia-current[-updates] be the newest version again?
> **ronacc said:**
> according to the nvidia drivers page 304.84 is the latest that supports the 6 and 7 series gpu's the 310.xx supports series 8 and newer .
AFAIK, 304.x is for Legacy Chips (that would be me).  ;)

Unless things have changed, trying to run 310.x is a no_go on Legacy Chips.

Don't have any idea what 313.x entails, because it doesn't affect me.

That said, all these various names mean nothing, in my mind.  The method I use, to determine which version of 304.x to use is totally based on the changelog.  I'm running the latest everything (nVidia drivers aside) on ancient iron, and if the changelog doesn't indicate that it will work with my current setup, I'm content to use somewhat stale nVidia drivers.

As of today, I'm running:

```
vindsl@Zuul:~$ apt-cache policy **[COLOR="#0000CD"]nvidia-304[/COLOR]**
  Installed: 304.84-0ubuntu2
  Candidate: 304.84-0ubuntu2
  Version table:
 *** 304.84-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ raring/restricted i386 Packages
        500 http://samaritan.ucmerced.edu/ubuntu/ raring/restricted i386 Packages
        100 /var/lib/dpkg/status
vindsl@Zuul:~$
```

Been working great, on this rig.

nvidia-current et al. hasn't worked on this machine, in quite a while...

```
~ VinDSL Unity Debug Script 12.12.06 (vindsl.com) ~
Current Date/Time: Fri Mar 29 15:30:53 MST 2013
Distro Release: Ubuntu Raring Ringtail (development branch)
[B][COLOR="#0000CD"]Kernel Release: Linux 3.9.0-030900rc4-generic
Gnome Release: GNOME Shell 3.8.0.1[/COLOR][/B]
Unity Release: unity 6.6.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.84

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

**[COLOR="#0000CD"]Package: mesa-utils[/COLOR]**
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 106
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
**[COLOR="#0000CD"]Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2+edgers[/COLOR]**
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

[B][COLOR="#0000CD"]Xserver Xorg Core Branch:
  Installed: 2:1.13.3-0ubuntu4[/COLOR][/B]

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
  dimensions:    1280x1024 pixels (339x271 millimeters)
  resolution:    96x96 dots per inch

```

Will this continue in the future?!?!?

My *guess* is yes.

---

### Post by mc4man on 2013-03-29
Use synaptic, read the various package descriptions, (11 for 3.xx), ect. & maybe it'll make some sense. 
(barely does here - I'm going to interpret that nvidia-current* is history, (transitional),  & packages will be named more directly
During dev the -updates packages always match the non -updates (ie, nvidia-310,  nvidia-310-updates

---

### Post by VinDSL on 2013-03-29
> **mc4man said:**
> I'm going to interpret that nvidia-current* is history [...]
As in... toast?  :)

---

### Post by mc4man on 2013-03-29
> **VinDSL said:**
> As in... toast?  :)
Yep, but *may* be around for a while if needed for upgraders, no clue here, did an upgrade once, decided never to revisit.

---

### Post by Sworddragon on 2013-03-30
> **mc4man said:**
> (barely does here - I'm going to interpret that nvidia-current* is history, (transitional),  & packages will be named more directly
During dev the -updates packages always match the non -updates (ie, nvidia-310,  nvidia-310-updates

In this case it would make sense if we would have a meta package that points to the newest version.

---

### Post by sgage on 2013-03-30
> **mc4man said:**
> Use synaptic, read the various package descriptions, (11 for 3.xx), ect. & maybe it'll make some sense. 
(barely does here - I'm going to interpret that nvidia-current* is history, (transitional),  & packages will be named more directly
During dev the -updates packages always match the non -updates (ie, nvidia-310,  nvidia-310-updates

The package descriptions really aren't that much help - the 173 description says 'for series 5 - 9". The descriptions for 304, 310 and 313 are identical, and say '6 or newer". The -updates packages show the same description. It's hard to know really what it all means from the package descriptions.

I have a series 8 card (GeForce 8500 GT). The 304 drivers appear to work fine, but don't allow me access to VT's. The 310 drivers work fine, and DO allow VT's. Haven't tried 313.

---

### Post by ronacc on 2013-03-30
the best and safest way to figure out which driver is right for your card is to check at nvidia .

---

### Post by VinDSL on 2013-03-30
> **ronacc said:**
> the best and safest way to figure out which driver is right for your card is to check at nvidia .
Agreed!  However...

I remember when 310 hit the bricks, the nVidia site listed my nVidia 7600GT AGP as certified/approved.  LoL!  :D

I installed 310 three times (no kidding) before realizing something was amiss -- took a few days for the official nVidia site to come up with an accurate list of legacy chipsets.

Just saying...  ;)

---

### Post by sgage on 2013-03-30
> **VinDSL said:**
> Agreed!  However...

I remember when 310 hit the bricks, the nVidia site listed my nVidia 7600GT AGP as certified/approved.  LoL!  :D

I installed 310 three times (no kidding) before realizing something was amiss -- took a few days for the official nVidia site to come up with an accurate list of legacy chipsets.

Just saying...  ;)

And yet the 310 Ubuntu package notes say 'series 6 and newer'. 310 works great on my 8500 GT, but it's PCIe, not AGP...

---

### Post by tjotser on 2013-03-31
I Also have a XFX-8500GT PCIe, and I´m running 313.26 on raringx64

---

