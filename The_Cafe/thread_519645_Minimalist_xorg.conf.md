---
title: "Minimalist xorg.conf"
date: 2007-08-07
forum: The Cafe
---

### Post by gav616 on 2007-08-07
pretty pointless but geeky thread,

how small can you get your xorg.conf without xserver error and everything working perfectly on your hardware :) ?

rules would be feisty only (gutsy .conf is smaller at default then feisty  because of fonts and modules loaded by default, plus its alpha, not recommended for tweaks like this)

post your xorg and hardware its on.

tweaks geeks only :lolflag:

mine;
```

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	#defoma
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
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device" "/dev/input/mice"
	Option		"Protocol" "ExplorerPS/2"
	Option		"Buttons" "7"
	Option		"ZAxisMapping" "4 5"
	Option		"ButtonMapping" "1 2 3 6 7"
	Option		"Emulate3Buttons" "false"
	Option		"Resolution" "2000"
    	Option		"SampleRate" "1000"
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV350 NJ [Radeon 9800 XT]"
	Driver		"fglrx"
	Option		"VideoOverlay" "on"
	Option		"OpenGLOverlay" "off"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 NJ [Radeon 9800 XT]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
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

Section "Extensions"
        Option  "Composite" "0"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "0"
EndSection
```

Hardware relative to xorg;

CPU: Athon XP 3200+
GPU: Radeon 9800XT
Mou: Razer Copperhead
Mon: 19" SyncMaster 940BF

---

### Post by igknighted on 2007-08-07
Yeah, Ubuntu puts way to much crap in xorg.conf... I don't think I've ever seen a distro that puts that much in.  This is the xorg.conf on my CentOS box:

```
# Xorg configuration created by pyxf86config

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "Screen0" 0 0
        InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
EndSection

Section "Device"
        Identifier  "Videocard0"
        Driver      "radeon"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Videocard0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection
```

I don't know if Ubuntu does this, but with Fedora/Red Hat distros you can delete the module section in xorg.conf and it will load what it needs automatically.

---

### Post by Nikron on 2007-08-07
Mine isn't minimal, because I like scroll wheel on my touch pad.  Also, swapping ctrl and caps lock is awesome.

```


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0"    "SendCoreEvents"
    InputDevice    "Touchpad"  "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Device" "/dev/input/mice"
    Option         "Emulate3Buttons" "false"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents"
    Option         "Device" "/dev/input/event0"
    Option         "Protocol" "auto-dev"
    Option         "SHMConfig" "on"
    Option         "LeftEdge" "1900"
    Option         "RightEdge" "5400"
    Option         "TopEdge" "1400"
    Option         "BottomEdge" "4500"
    Option         "FingerLow" "25"
    Option         "FingerHigh" "30"
    Option         "MaxTapTime" "180"
    Option         "MaxTapMove" "220"
    Option         "VertScrollDelta" "100"
    Option         "MinSpeed" "0.01"
    Option         "MaxSpeed" "0.15"
    Option         "AccelFactor" "0.0005"
EndSection


Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
    Option         "XkbOptions"  "ctrl:swapcaps"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Q@L"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 7300"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "DisableGLXRootClipping" "True"
    Option	   "RenderAccel" "true" 
    Option	   "AllowGLXWithComposite" "true"
    Option         "NvAGP" "1"
    Option         "NoLogo" "True"
    Option         "TwinView" "True"
    Option         "TwinViewOrientation" "Clone"
    Option	   "Metamodes" "1680x1050,680x480"
    SubSection     "Display"
        Depth       24
	Modes      "1680x1050"
    EndSubSection
EndSection

Section "DRI"
	 Mode 0666
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

---

### Post by gav616 on 2007-08-07
> **igknighted said:**
> Yeah, Ubuntu puts way to much crap in xorg.conf... I don't think I've ever seen a distro that puts that much in.  This is the xorg.conf on my CentOS box:

CODE

I don't know if Ubuntu does this, but with Fedora/Red Hat distros you can delete the module section in xorg.conf and it will load what it needs automatically.
thats exattally what i would like to see, virtually nothing in xorg just core stuff, and tweakables

its abit hard to fathom. some important core lines that you would think load by default don't and need inputting, but at-least gutsy (from what i have testing) is 1/3 of the size, thus telling me more is detected  and supported better...

---

### Post by mrazster on 2007-08-07
Here's mine...

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "se"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Emulate3Buttons" "false"
    Option         "Buttons" "7"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer AL2416W"
    HorizSync       24.0 - 80.0
    VertRefresh     49.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7900 GTO"
#    Option         "Coolbits" "1"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1920x1200_60 +0+0"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

---

