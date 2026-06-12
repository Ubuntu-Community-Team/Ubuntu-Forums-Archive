---
title: "Ubuntu update killed direct rendering on my Koala Mini"
date: 2006-08-09
forum: System76 Support
---

### Post by Paradoxdruid on 2006-08-09
I've been using my Koala Mini as a media center (and enjoying it very much!), but a semi-recent update killed it's video performance, and I think I figured out why.

Direct rendering my the onboard i810 intel integrated graphics isn't on and working anymore, and I've been tearing my hair out trying to fix it.

My problems are briefly summarized in this post to the Ubuntu forums: [http://ubuntuforums.org/showthread.php?t=231901](http://ubuntuforums.org/showthread.php?t=231901)

In short, /var/log/Xorg.0.log says ```
I810(0): Direct Rendering: Failed
```

which means that glxinfo reports GLX isn't present, and video acceleration is off (and I can't run OpenGL stuff, like Stepmania).

lsmod | grep i8 shows that the i810 driver and drm are loaded in the kernel.  All my stuff is updated, and my xorg.conf is using the i810 driver and loading DRI and GLX modules.

How does System76 configure the Koala Mini's when they ship them?  A copy of their default xorg.conf, etc would be very helpful.

Thanks in advance for any help.  I'll cross-post this to the old System76 forum, too--  not sure which one is being looked at more.

---

### Post by Paradoxdruid on 2006-08-09
Side note to anyone reading this...  System76 has been a great company to buy from, with very active support, good default options, good speed, and great product.  If you're curious about it, you can read a little testimonial I did for them here:  [http://system76.com/forums/viewtopic.php?t=26](http://system76.com/forums/viewtopic.php?t=26)

I'm not affiliated with them in any way, just a happy customer (this current problem aside).

...  and if anyone has leads on this direct rendering issue, it's driving me crazy!

---

### Post by crichell on 2006-08-09
Hello Paradox,

try a quick:

```
sudo dpkg-reconfigure xserver-xorg
```

Let me know if that takes care of it.  Post your xorg.conf if that doesn't help - we'll cross reference.

Cheers, Carl

---

### Post by Paradoxdruid on 2006-08-09
Hi carl-

reconfiguring the xserver and/or apt-get --reinstall install for xserver-xorg-driver-i810 both don't change anything.  Below are the relevant portions of my xorg.conf.

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
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	VideoRam	65536
EndSection


Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection


Section "DRI"
	Mode	0666
EndSection
```

and the relevant bit of my /var/log/Xorg.0.log
```
(II) I810(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		12 256x256 slots
(==) I810(0): Backing store disabled
(==) I810(0): Silken mouse enabled
(II) I810(0): Initializing HW Cursor
(**) Option "dpms"
(**) I810(0): DPMS enabled
(II) I810(0): direct rendering: Failed
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
```

Thanks for any help!

---

### Post by crichell on 2006-08-09
Our xorg.conf doesn't look much different but our xlog does.

xorg.conf

```
Section "Module"
	Load	"i2c"
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

Section "Device"
	Identifier	"Intel Corporation Mobile Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

```


```
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
```

and the result:

```
(II) I810(0): [DRI] installation complete
(II) I810(0): direct rendering: Enabled
```

maybe our issue lies in libdri.so

---

### Post by Paradoxdruid on 2006-08-09
It looks like libdri.so is a component of [FONT="Courier New"]xserver-xorg-core[/font] in Dapper, so I'll try reinstalling that tonight when I have access to the Koala.

Thanks for the quick response.

---

### Post by Paradoxdruid on 2006-08-09
So, I edited my xorg.conf to more closely resemble the above, then reinstalled xserver-xorg-core and restarted the system.

Still no direct rendering, I'm afraid.  But dri loads fine:
from the /var/log/Xorg.0.log file:[code}(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2[/code]

But should my system be loading NVIDIA GLX modules?  Maybe I installed something bad on accident!  From the xlog:```
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8762
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
```
In any case, towards the end of the xlog:```
(II) I810(0): direct rendering: Failed
```

D'oh!

In any case, what GLX module should I have instead of the NVIDIA one?  That's my next thought on the matter.

Thanks again for any help, anyone reading!

---

### Post by Paradoxdruid on 2006-08-09
...So...

I'm apparently amnesiac or insane.

Indeed, the package nvidia-glx was installed for some reason, though I have no recollection of ever doing this.

A quick apt-get remove nvidia-glx and reinstall of libgl1-mesa-dri and libgl1-mesa and my system is back to normal.

Carl, anyone else who helped, I apologize for wasting your time.

Like usual, garbage in, garbage out--  the system was just fine.  I was just telling it to use the wrong modules.

Thanks!  Now, back to watching videos on my Koala!

---

### Post by crichell on 2006-08-09
I'm glad to hear your up and running.  Let us know if you need anything else.

---

### Post by LittleLebowski on 2007-04-04
This thread helped me out, thank you.

---

### Post by mustali on 2007-06-19
This helped me resolve the problem of Google Earth complaining 'Unknown Graphics Card'

I have no idea how nvidia-glx was installed on my Dell Inspiron 630m Laptop with Integrated 915GM Express Graphics Chipset. Removing it using the following cut the deal.
```

sudo apt-get remove nvidia-glx

glxinfo | grep "direct render"
direct rendering: Yes


```

Thanks!

---

