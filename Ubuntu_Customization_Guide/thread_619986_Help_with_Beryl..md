---
title: "Help with Beryl."
date: 2007-11-22
forum: Ubuntu Customization Guide
---

### Post by ndworecki on 2007-11-22
This is what is going on. I set the Window Manager for Beryl and I no longer have the top bar of each window. Any ideas???

My video card is the 7600gs. I am using the 64-bit version of Ubuntu.

Here is a screen shot:

[IMG]http://i3.tinypic.com/7xy6i4m.png[/IMG]

And here is my xorg.conf

```
# Fallback X.org config file
# FIXME: include the wacom devices (would only add noise at the current
#        development stage)

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
  screen 0 "screen1" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"NVIDIA GeForce 7 Series"
	Busid		"PCI:2:0:0"
	Driver		"nvidia"
	Screen	0
	Vendorname	"NVIDIA"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1280x1024@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x1024"
	Horizsync	31.5-64.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```


Thanks for the help!

---

### Post by ndworecki on 2007-11-22
I added a few things to my xorg.conf:

```
# Fallback X.org config file
# FIXME: include the wacom devices (would only add noise at the current
#        development stage)

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
  screen 0 "screen1" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"NVIDIA GeForce 7 Series"
	Busid		"PCI:2:0:0"
	Driver		"nvidia"
	Screen	0
	Vendorname	"NVIDIA"


# nvidia special options, use with care
  Option "CursorShadow" "1"
  Option "CursorShadowAlpha" "63"
  Option "CursorShadowYOffset" "2"
  Option "CursorShadowXOffset" "4"
  Option "FlatPanelProperties" "Scaling = native"
  Option "NoLogo" "false"
  Option "AddARGBGLXVisuals" "true"
  Option "RenderAccel" "true"
  Option "AllowGLXWithComposite" "true"


EndSection
Section "screen" # 
Option "AddARGBGLXVisuals" "true"
  Option "RenderAccel" "true"
  Option "AllowGLXWithComposite" "true"
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1280x1024@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x1024"
	Horizsync	31.5-64.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

This is from the Terminal:

```

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.4)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Reloading options
beryl: decoration: property ignored because version is 20070319 and decoration plugin version is 20061011
beryl: decoration: property ignored because version is 20070319 and decoration plugin version is 20061011
beryl: decoration: property ignored because version is 20070319 and decoration plugin version is 20061011
Initiating splash


```

---

### Post by seniorciz on 2008-01-09
Have you tried restarting? I was having the same problems with beryl and i just recived updates and restarted and thing are beack to normal. Kinda...

---

