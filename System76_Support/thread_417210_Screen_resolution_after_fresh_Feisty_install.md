---
title: "Screen resolution after fresh Feisty install"
date: 2007-04-21
forum: System76 Support
---

### Post by jlhughes on 2007-04-21
I did a fresh install of Feisty on a Gazelle Value (Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller)

Everything (including sound) works EXCEPT the screen resolution is stuck at default VGA 1024x768.

I have tried manually changing the resolution, but XORG reports that the driver installed doesn't support the 1280x800 for this laptop.

What driver do I want to install?

Here's the relevant xorg.conf info:


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
EndSection


Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

---

### Post by tiiim on 2007-04-21
I had this problem but saw another post and this fixed it for me.

Open up a terminal and type in

>  sudo apt-get install 915resolution 

Reboot your machine and you will find your screen resolution option will have the higher option, change to that and enjoy. Worked a treat for me.:)

---

### Post by jlhughes on 2007-04-21
Excellent. That did the trick. Thanks

---

### Post by indrajeetak on 2007-04-21
Excellent. That worked for me too. Thanks  a lot :)

---

