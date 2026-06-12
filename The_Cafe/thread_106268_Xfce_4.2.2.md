---
title: "Xfce 4.2.2"
date: 2005-12-20
forum: The Cafe
---

### Post by SpEcIeS on 2005-12-20
Never used this window manager, but I have to say, being a gnome lover, this one really is nice and fast. XFCE is slick and clean, and I hope that the Ubuntu team applies the 4.2.3 update soon.

Everything works great in XFCE, however I seem to have issues with xcompmgr. My system will randomly lockup, saving only the mouse. No keyboard. Too bad because I like the shadowing.

This window manager is a must try for those that have not experienced it. If you like gnome, then you will really enjoy XFCE. :)

---

### Post by localzuk on 2005-12-20
XFCE is my wm of choice. I have it running on ubuntu 5.10 on a IBM 560z laptop with 128Mb ram and 300Mhz processor (with a 10" screen at 800x600, bless) and it is speedy.

It works well with abiword, firefox and xterm - all I need...

---

### Post by Rotarychainsaw on 2005-12-20
Doesn't XFCE have a built in composite manager? I'm pretty sure you can get shadows and maybe transparancy without using xcompmgr.

---

### Post by SpEcIeS on 2005-12-20
Yeah I guess, but nevertheless it locked up randomly. Too bad because it really was the icing on the cake. :)

---

### Post by poofyhairguy on 2005-12-20
[QUOTE=Rotarychainsaw]Doesn't XFCE have a built in composite manager? I'm pretty sure you can get shadows and maybe transparancy without using xcompmgr.[/QUOTE]

Yeah it does, but I find it to be the most unstable composite manager of them all! Xcompmgr is better even.

---

### Post by localzuk on 2005-12-20
Personally, I looked into xcompmgr and its equivalent in kde and found them all the be unstable so disabled them and live without. For shadows etc... I use OSX and for everything else I use Ubuntu/XFCE

---

### Post by Rotarychainsaw on 2005-12-20
What I meant to add was that doesn't using xcompmgr over something that already has a composite manager (KDE, XFCE) make it way more unstable?

---

### Post by SpEcIeS on 2005-12-20
Well in my case I think that I am having some sort of hardware conflict. Not sure though. The last video card that I had was a nvidia type MX 400 64 VRAM, which locked up also. Now I have a 3D Fusion MX4000 (nVidia) 128VRAM, and this also locks up, sparatically.

The ironic part is, the person that I gave the MX 400 to uses SuSE 9.3 linux and has no problems. The only real difference in hardware in this case is the motherboard and memory. I am currently using PC133, which is a little old, but the other individual is using DDR RAM 333Mhz. Both processors are AMD Athlon, however his is an XP 1600. Little faster, but I cannot see this being the problem.

Somewhat odd. :confused:

---

### Post by localzuk on 2005-12-20
What is your xorg.conf file like? Could you post it here?

---

### Post by SpEcIeS on 2005-12-20
No problem...  here it is:
```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

#Section "Extensions" 
#	Option "Composite" "Enable" 
#EndSection

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
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	#Option		"RenderAccel" "true" 
	#Option		"AllowGLXWithComposite" "true"
EndSection

Section "Monitor"
	Identifier	"NEW PANDA 17"
	Option		"DPMS"
	Modeline	"1600x1200@65.36" 81.7 1280 1312 1624 1656 800 816 824 841
	#Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
	Monitor		"NEW PANDA 17"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
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
```

---

### Post by codejunkie on 2005-12-20
[QUOTE=SpEcIeS]No problem...  here it is:
```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

#Section "Extensions" 
#	Option "Composite" "Enable" 
#EndSection

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
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	#Option		"RenderAccel" "true" 
	#Option		"AllowGLXWithComposite" "true"
EndSection

Section "Monitor"
	Identifier	"NEW PANDA 17"
	Option		"DPMS"
	Modeline	"1600x1200@65.36" 81.7 1280 1312 1624 1656 800 816 824 841
	#Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
	Monitor		"NEW PANDA 17"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
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
```[/QUOTE]
you have the same kind of card that i have, i had some lockups with my card using the driver from synaptic but i upgraded to the latest driver from nvidia.com and i haven't had any problems with xfce's composite manager or xcompmgr i just can't use all the features at the same time with xcompmgr because it's to slow. what version of the nvidia driver are you using?

---

### Post by SpEcIeS on 2005-12-20
I am currently using the legacy drivers supplied with Ubuntu. Do you really think it is best to compile the latest drivers? The latest drivers are: **Version: 1.0-8174**. Are these the drivers you are using? If not what version so that I can match.


Thanks.. there is hope. :D

---

### Post by localzuk on 2005-12-20
Your xorg.conf seems fine... I would go with the suggestion to use the nvidia.com drivers. You don't have to compile them, just download the file from [http://www.nvidia.com/object/linux_display_ia32_1.0-8174.html](http://www.nvidia.com/object/linux_display_ia32_1.0-8174.html) and run it. There are also instructions available at [http://download.nvidia.com/XFree86/Linux-x86/1.0-8174/README/32bit_html/index.html](http://download.nvidia.com/XFree86/Linux-x86/1.0-8174/README/32bit_html/index.html)

---

### Post by Rackerz on 2005-12-20
Im a KDE user but I love Gnome. Is Xfce worth a try on Kubuntu? Will it be compatiable with most of the KDE apps?

---

### Post by codejunkie on 2005-12-20
[QUOTE=Rackerz]Im a KDE user but I love Gnome. Is Xfce worth a try on Kubuntu? Will it be compatiable with most of the KDE apps?[/QUOTE]
yes it should work just fine with kde and gnome apps.

---

### Post by codejunkie on 2005-12-20
[QUOTE=SpEcIeS]I am currently using the legacy drivers supplied with Ubuntu. Do you really think it is best to compile the latest drivers? The latest drivers are: **Version: 1.0-8174**. Are these the drivers you are using? If not what version so that I can match.


Thanks.. there is hope. :D[/QUOTE]
im using the 1.0-8174 driver from nvidia.com and there working just fine with my card and if your having lockups with xcompmgr and xfce it might help installing them.

---

### Post by SpEcIeS on 2005-12-20
Well I am back with the latest drivers, but I will have to wait and see if this works out. One program, for whatever reason, would consistantly lockup was anjuta. Odd, but that is how it was. It worked this time. :)

Thanks again for the tip, and I will see how it turns out. :D

---

### Post by SpEcIeS on 2005-12-20
Well xcompmgr works well under gnome now, shadows and tranlucency, however, everytimg I reboot I have to rebuild the drivers. Xserver errors out and indicates that there is not a suitable screen. This is crap because as soon as I recompile the drivers and install them.. back in business.

What is happening with this? :confused: 

It is nice to see gnome with shadow and translucencies. Seems to run really well also. :)

**_Update_**
It turns out that I had the nvdia-kernel-common and friends...  conflicting nvidia versions...  :) Works great. :)

---

### Post by Rackerz on 2005-12-20
I'm using XFCE right now. It seems a hell of a lot faster! Also are there any themes for XFCE?

---

### Post by ember on 2005-12-20
Well - I would definitely think about using XFCE ... if only the icons were not that ugly ...

---

### Post by localzuk on 2005-12-21
Xfce uses themes. You can change the icons in the bar at the bottom.

Take a look at [http://themes.freshmeat.net/browse/964/](http://themes.freshmeat.net/browse/964/) and [http://themes.freshmeat.net/browse/958/](http://themes.freshmeat.net/browse/958/) for xfce and gtk2 themes.

I agree that the default icons are nothing to be excited about - but that is a minor thing

---

### Post by SpEcIeS on 2005-12-21
Oddly enought I enjoy the default XFCE 4.2.2 setup... looks good to me. :)

---

### Post by ember on 2005-12-21
[QUOTE=localzuk]Xfce uses themes. You can change the icons in the bar at the bottom.

Take a look at [http://themes.freshmeat.net/browse/964/](http://themes.freshmeat.net/browse/964/) and [http://themes.freshmeat.net/browse/958/](http://themes.freshmeat.net/browse/958/) for xfce and gtk2 themes.

I agree that the default icons are nothing to be excited about - but that is a minor thing[/QUOTE]

Ah - great - I should bookmark that pages.

Thanks,
ember

---

