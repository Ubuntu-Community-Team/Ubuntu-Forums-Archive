---
title: "Wacom tablet kills mouse in Gimp and Inkscape"
date: 2008-06-05
forum: Ubuntu Studio
---

### Post by sigdrifa on 2008-06-05
Hi all

Since the Hardy upgrade I have a problem with my Volito2 Wacom tablet in
Gimp and Inkscape.

When I start the software (either one) for the first time after boot up, the mouse works perfectly normal. But after using the tablet once, it stops working correctly. I can still use the menus with the mouse, and selecting tools and tool options or tuning settings in any of the palettes work - but when I click into the image with any tool nothing happens - until the next
reboot. This doesn't affect other programs or the rest of the desktop.

The tablet itself works fine, though.

Any help would be appreciated.

```

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
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

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:7:0:0"
EndSection

[snip]

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
		InputDevice     "stylus"	"SendCoreEvents"
		InputDevice     "cursor"	"SendCoreEvents"
		InputDevice     "eraser"	"SendCoreEvents"
EndSection

[snip]

```

---

### Post by Sabru on 2008-06-08
I have almost the identical problem in gimp with my wacom bamboo. I believe it has something to do with a bug in GTK. If anyone else can offer insight into this, it would be much appreciated.

---

### Post by lenzoid on 2009-07-07
*bump* SAME PROBLEM! I use Wacom Sapphire. Pressure sensitive wacom AND a working mouse are impossible to configure here. The mouse0 devices "key" events in the Mouse0 page of the input devices window just disappear when activating stylus & cursor.

---

### Post by padeco on 2009-07-09
hy guys,

i have installed the wacom bamboo tablet following the hints in this forum:
[http://ubuntuforums.org/showthread.php?t=765915]("http://ubuntuforums.org/showthread.php?t=765915") 

there are some great hints. my system is working quite fine, no major issues. i hope this helps you out.

cheers,
padeco

---

### Post by o akire on 2012-06-03
Hi all,
Finally my pen works again after configuring out all day long.
But then I can only use brush in gimp. Other Gimp tools are inactive. 

I reinstalled Gimp, but still no change

Thank you if any ideas


PS. I use my pen to anotate with Compiz and it doesnt conflict with mouse

---

### Post by Favux on 2012-06-03
Hi o akire,

Welcome to Ubuntu forums!

Which release of Ubuntu are you using?  Precise Pangolin 12.04?

Which Wacom tablet?

---

