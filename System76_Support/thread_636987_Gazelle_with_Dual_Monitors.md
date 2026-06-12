---
title: "Gazelle with /Dual Monitors"
date: 2007-12-10
forum: System76 Support
---

### Post by organicveggie on 2007-12-10
I have a Gazelle Performance laptop and an Acer LCD that I managed to get working with Xinerama today. However, I seem to have lost the ability to run Beryl... which suggest to me it's not recognizing my HW acceleration. I'm also having font weirdness with the external LCD. Here's my xorg.conf. Any suggestions would be greatly appreciated:

```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

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
	Load	"synaptics"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"1"
EndSection

Section "Device"
	Identifier	"nVidia1"
	Driver		"nvidia"
	Option		"NoLogo"
	BusID		"PCI:1:0:0"
	Screen		0
EndSection

Section "Device"
	Identifier	"nVidia2"
	Driver		"nvidia"
	Option		"NoLogo"
	BusID		"PCI:1:0:0"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"Laptop"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"NI LCD"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Laptop"
	Device		"nVidia1"
	Monitor		"Laptop"
	DefaultDepth	24
        Option          "AddARGBGLXVisuals" "True"
        Option          "DisableGLXRootClipping" "True"
	SubSection "Display"
		Depth		24
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"ExternalLCD"
	Device		"nVidia2"
	Monitor		"NI LCD"
	DefaultDepth	24
        Option          "AddARGBGLXVisuals" "True"
        Option          "DisableGLXRootClipping" "True"
	SubSection "Display"
		Depth	24
		Modes	"1680x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Xinerama"
	Screen 0 "Laptop" 0 0
	Screen 1 "ExternalLCD" LeftOf "Laptop"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	Option 		"Xinerama" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Thanks!

-Sean

---

### Post by thomasaaron on 2007-12-10
Which Gazelle Performance are you using?
(Go to System > Admin > Sys76 Driver to find out)

---

### Post by organicveggie on 2007-12-10
> Which Gazelle Performance are you using?

Name: Gazelle Performance
Model: gazp2

---

### Post by thomasaaron on 2007-12-11
I can try to do some testing on it. But you said you are running Beryl? So, you're still on Feisty? Or did you mean Compiz? Just want to make sure I have all my ducks in a row before testing.

---

### Post by organicveggie on 2007-12-12
> **thomasaaron said:**
> I can try to do some testing on it. But you said you are running Beryl? So, you're still on Feisty? Or did you mean Compiz? Just want to make sure I have all my ducks in a row before testing.

Apparently, I'm just not playing with a full deck these days...:) Alright. Let's try this again.

Machine: Gazelle Performance (gazp2) w/Nvidia 7300
OS: Ubuntu Feisty Fawn
Software: Beryl v0.2.1

Hopefully I'm not missing any critical information at this point... *laugh*

Thanks.

-Sean

---

