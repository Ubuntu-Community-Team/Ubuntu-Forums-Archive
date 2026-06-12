---
title: "Dual Head X with creator3d?"
date: 2006-07-11
forum: Sun Sparc Users
---

### Post by DarkHelmet on 2006-07-11
I have been trying to get accelerated X working with 6.06 using 2 Creator 3d cards.  Dual head X works, and it says it's accelerated, but I cannot change the display resultion.  The primary display can be set in the bios from what I have been reading, but it looks like the second display cannot.

Does anyone have a hack to get this working?  I know under Solaris you can use the ffbconfig to set the FB settings on the second card.  linux has fbset, but this does not work on this card.

Will this work if I use Elite 3d cards instead of the creator 3d cards?  Anyone know how to program this to make it happen, I have spare ultra60's....

---

### Post by netztier on 2006-07-12
> **DarkHelmet said:**
> Dual head X works, and it says it's accelerated,

Hm.. how can you tell that it is accelerated? How does one verify?

> **DarkHelmet said:**
>  Will this work if I use Elite 3d cards instead of the creator 3d cards?  Anyone know how to program this to make it happen, I have spare ultra60's....

I have Xinerama running on a pair of Creator 3Ds at home, I will post my xorg.conf in the next few days - won't get to work on  that machine for a few days, alas. Maybe I was just lucky with the OBP's default setting matching the resolution of my screens (1280x1024@60Hz).

I've been googleing for parameters for the setenv command at the boot prompt, but so far I haven't found anything that'd hint how to configure a second video card. I even doubt that there will be such a command, since OBP seems to be aware of only one display - or *output-device*, for that matter. I concluded this from reading here:. [Frame Buffer FAQ]("http://www.sunshack.org/data/fbfaq/FrameBuffer.html#7")

If you have a spare hard disk with Solaris, you could boot into Solaris and work with ffbconfig, then boot Linux again... this might help.

kind regards

Marc

---

### Post by netztier on 2006-07-15
> **DarkHelmet said:**
> 
Does anyone have a hack to get this working?

Below's an excerpt from my x.org conf (with Xinerama enabled). It took some fiddling and reading the output of **dmesg | grep ffb** and **sudo grep ffb /var/log/Xorg.0.log** to determine de BusIDs of the cards. 

```
marc@grill:/etc/X11$ **dmesg | grep ffb**
[    1.877066] ffb: FFB at 000001fc00000000 type 51 DAC 10
[    1.877870] ffb: FFB at 000001fa00000000 type 51 DAC 10
```
```
marc@grill:~$ **sudo grep ffb /var/log/Xorg.0.log**
(--) SBUS:(0xf006e4d0) Sun FFB2+ Vertical Creator 3D at [COLOR="Red"]/SUNW,ffb@1e,0[/COLOR]
(--) SBUS:(0xf007669c) Sun FFB2+ Vertical Creator 3D at [COLOR="Red"]/SUNW,ffb@1d,0[/COLOR]
(II) LoadModule: "sunffb"
(II) Loading /usr/lib/xorg/modules/drivers/sunffb_drv.so
(II) Module sunffb: vendor="X.Org Foundation"
(--) Assigning device section with no busID to SBUS:/SUNW,ffb@1d,0

```
Interestingly enough, it wouldn't work when setting the BusID for both devices. So I left one without, the other with BusID setting.
```

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
[COLOR="Red"]	Load	"cfb"
        Load    "cfb32"
[/COLOR]EndSection
...

Section "Device"
	Identifier	"Sun Creator3D-0"
	Driver		"sunffb"
[COLOR="Red"]	BusID		"SBUS:/SUNW,ffb@1e,0"[/COLOR]
#	Option		"UseFBDev" "true"
EndSection

Section "Device"
        Identifier      "Sun Creator3D-1"
        Driver          "sunffb"
[COLOR="Red"]#	BusID		"SBUS:/SUNW.ffb@1d,0"[/COLOR]
#       Option          "UseFBDev" "true"
EndSection


Section "Monitor"
	Identifier	"EIZO L568-left"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Monitor"
        Identifier      "EIZO L568-right"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection



Section "Screen"
	Identifier	"Left Screen"
	Device		"Sun Creator3D-0"
	Monitor		"EIZO L568-left"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection


Section "Screen"
        Identifier      "Right Screen"
        Device          "Sun Creator3D-1"
        Monitor         "EIZO L568-right"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024"
        EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Left Screen"
	Screen		"Right Screen" RightOf "Left Screen"
	Option		"Xinerama"	"On"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

```

Since I only ever use one resolution, I have configured only the 1280x1024 modes. What resolutions will you require?

Saying that you have spare U60s... are there any with Elite3D Cards? now that'd be interesting :-)

kind regards

Marc

---

### Post by DarkHelmet on 2006-07-26
I was able to get the cards initalized via OBP setting the nvramrc to nvramrc=probe-all
" /SUNW,ffb@1e,0:r1600x1200x75" select-dev
" /SUNW,ffb@1d,0:r1600x1200x75" select-dev

and 
use-nvramrc?=true

using the eeprom command from linux or the same commands in OBP.

Under solaris you would use the ffbset command to change the resultion of the screen on the fly.  I would say the acceleration of the sun creator 3d cards does not appear to be working with linux, and my only other option would be an elite 3d card but the max resultion on those cards is 1280x1024 :-(.

If somone can make the XVR-1000 card work I can use that :-)  It seams that the video support under linux on sparc kinda sucks.  atleast if someone could write a ffbset program for linux that might help.

I am also noticing that when DPMS is turned on in X the normal VTY's will blank out after about 10 min and become unusable.  I'll add more info as I can get it, but right now the system load is at 10.20 since I have my D1000 drive cage working and am copying files to it via usb and NFS.  It's running LVM2 plus dm-crypt to encrypt the volume.

The system is still quite usable at the load it's at now too, yea for Sparc design.

---

