---
title: "Xorg problems in 7.04 on Sunblade 100/150"
date: 2007-05-02
forum: Sun Sparc Users
---

### Post by cac on 2007-05-02
Looking for some help get xorg up an running on my Sunblade 100's & 150's.  I get the following error message when trying to start it:
```
Fatal server error:
xf86MapPciMem: Could not mmap PCI memory [base=0x426000,hostbase=0x426000,size=2000] (Inappropriate ioctl for device)
```

Currently here are the relevant bits of my xorg.conf:
```
<snip>

Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        #Load   "glx"
        Load    "int10"
        Load    "vbe"
EndSection

<snip>

Section "Device"
        Identifier      "ATI Technologies 3D Rage Pro or similar (ATY,RageXL)"
        Driver          "ati"
        BusID           "PCI:0:19:0"
        #VideoRam       8192
        Option          "UseFBDev"              "true"
        Option          "reference_clock"       "29.500MHz"
EndSection

Section "Monitor"
        Identifier      "Sun DP17MO"
        Option          "DPMS"
        HorizSync       30-75
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies 3D Rage Pro or similar (ATY,RageXL)"
        Monitor         "Sun DP17MO"
        DefaultDepth    24
        #SubSection "Display"
        #       Depth           1
        #       Modes           "1152x864" "1024x768"
        #EndSubSection
        #SubSection "Display"
        #       Depth           4
        #       Modes           "1152x864" "1024x768"
        #EndSubSection
        #SubSection "Display"
        #       Depth           8
        #       Modes           "1152x864" "1024x768"
        #EndSubSection
        #SubSection "Display"
        #       Depth           15
        #       Modes           "1152x864" "1024x768"
        #EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1152x864" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1152x864" "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection
```

I have Gentoo running xorg 7.1 on some other SB100's without problem so I would think running 7.2 on ubuntu would still be possible.  I tried using the xorg.conf from the gentoo boxes, but still no luck.

For what its worth, I started the ubuntu install using 6.06 and upgraded my way to 7.04 via the shell (6.06 > 6.10 > 7.04).  Once I reached 7.04 I pulled in ubuntu-desktop in an effort to avoid upgrade problems with the GUI.  Everything else seems to be running fine.  Not sure if this is playing a part in my xorg woes.

Anyone have any ideas, pointers, etc?

TIA,
-Chris

---

### Post by cac on 2007-05-02
Well I found a bug report for this: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/99221](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/99221).

---

### Post by jcastill on 2007-05-02
Got the same problem. Will try to see the bug report and check for any solutions.

Thanks

---

### Post by cac on 2007-05-02
I also found this bug on Gentoo's tracker: [http://bugs.gentoo.org/show_bug.cgi?id=167052](http://bugs.gentoo.org/show_bug.cgi?id=167052).  Appears to be a problem with xorg-server-1.2.0.

---

### Post by jdeisenberg on 2007-05-17
Can anyone point me to a repository where I might download xorg-server-1.1.1-r4 (which, according to the bug reports, solves the problem)?

---

### Post by cac on 2007-05-17
You can run ```
sudo apt-get install xorg=1:7.1.1ubuntu6
``` to downgrade xorg to 7.1.1.  I also had to add edgy repository to my /etc/apt/source.list.  I'll have to wait until tomorrow to see whether this worked or not though...

---

### Post by jcastill on 2007-05-17
> **cac said:**
> You can run ```
sudo apt-get install xorg=1:7.1.1ubuntu6
``` to downgrade xorg to 7.1.1.  I also had to add edgy repository to my /etc/apt/source.list.  I'll have to wait until tomorrow to see whether this worked or not though...

It did downgrade although it doesn't seem to fix the problem :confused: Thanks for the idea :)

---

### Post by jdeisenberg on 2007-06-13
I've posted this on another thread, but in case people are monitoring this one:
I did get it to work. For the record, here's what I did:

1) Reinstalled Ubuntu 7.04
2) Changed [FONT="Courier New"]/etc/apt/sources.list[/FONT] to use the unstable version of Debian:
```
deb http://mirror.anl.gov/debian/ sid main
```
3) Created a file called [FONT="Courier New"]15changecache[/FONT] in folder /[FONT="Courier New"]etc/apt/apt.conf.d[/FONT] with this line:
```
APT::Cache-Limit 33554432;
```
4) Did an [FONT="Courier New"]apt-get update[/FONT] followed by [FONT="Courier New"]apt-get install xserver-xorg[/FONT]
5) In order to avoid having the monitor go out of sync range, I had to add a line to the "Device" section of  [FONT="Courier New"]/etc/X11/xorg.conf[/FONT] 
```
Option "ReferenceClock" "29.5000MHz"
```
6) Restored [FONT="Courier New"]/etc/apt/sources.list[/FONT] to its former state, and re-ran [FONT="Courier New"]apt-get update[/FONT]

---

### Post by Sibre on 2007-06-15
Hi all, I managed to get this working on my SunBlade 100 with Ubuntu 7.04.

I had to unmount /sys before starting Xorg.  Have a look at:
[http://lists.debian.org/debian-x/2007/05/msg00233.html](http://lists.debian.org/debian-x/2007/05/msg00233.html)

Here is my xorg.conf file:
Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
	Load	"cfb"
	Load	"cfb32"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc101"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"ATI Technologies 3D Rage Pro or similar (ATY,RageXL)"
	Driver		"ati"
	BusID		"PCI:0:19:0"
	Option		"UseFBDev"		"true"
	Option		"referenceclock"		"28.636 MHz"
EndSection

Section "Monitor"
	Identifier	"Sun GDM-5510"
	Option		"DPMS"
	HorizSync	30-130
	VertRefresh	48-170
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies 3D Rage Pro or similar (ATY,RageXL)"
	Monitor		"Sun GDM-5510"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

Also see:
[http://sunsolve.sun.com/handbook_private/Devices/Graphics/GRAPH_PGX64.html](http://sunsolve.sun.com/handbook_private/Devices/Graphics/GRAPH_PGX64.html)
[http://sunsolve.sun.com/handbook_private/Devices/Monitor/MONITOR_Color_21_Prem_Flat_CRT_xena.html](http://sunsolve.sun.com/handbook_private/Devices/Monitor/MONITOR_Color_21_Prem_Flat_CRT_xena.html)

---

### Post by cac on 2007-09-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/99221](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/99221) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **Sibre said:**
> I had to unmount /sys before starting Xorg.

sysfs seems to be confirmed as the culprit, but unmounting /sys can lead to a lot more problems.  I've updated the bug as there is a patch from debian for xorg-server-1.3.0 and the Gentoo devs have a cleaned up one for 1.20.  I've been trying apply the patch to the xorg-server-1.2.0 source, but I'm not well versed in deb.  I can't seem to understand the proper way to patch the source package and compile it.  :confused:

It is also mentioned that this will should be resolved upstream in 1.5.

---

