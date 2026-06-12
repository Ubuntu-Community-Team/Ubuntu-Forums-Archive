---
title: "SketchUp under Wine on Karmic crashes on mouse drag"
date: 2011-03-24
forum: Wine
---

### Post by desconocido on 2011-03-24
I had SketchUp 7.1 working fine under Wine on Hardy (with a fix to xorg.conf) on a machine with Intel graphics:> 
$ lspci
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)



I upgraded to Karmic (kernel 2.6.31-22) (with corresponding loss of xorg.conf):
 
SketchUp 7.1 (running under wine) crashes on startup with "Entered Unhandled Exception Filter"

I fixed this by creating an xorg.conf with added line
	Option          "DRI"                   "false"
and using regedit to make sure that
(HKEY_CURRENT_USER\Software\Google\SketchUp7\GLConfig\Display\HW_OK) or
(HKEY_CURRENT_USER\Software\Google\SketchUp8\GLConfig\Display\HW_OK)
exist and are set to 1

This results in SketchUp executing properly EXCEPT that if the Select tool is selected and the mouse is dragged, SketchUp crashes (happens with both versions).

Is there a setting in xorg.conf for the mouse that would help? This my current xorg.conf
```

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "glx"
	Load  "dri"
	Load  "extmod"
	Load  "record"
	Load  "dri2"
	Load  "dbe"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
	Option          "DRI"                   "false"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

Although I tried running SketchUp from a terminal and the crash output suggests a different problem:
```
fixme:shell:DllCanUnloadNow stub
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  73 (X_GetImage)
  Serial number of failed request:  673559
  Current serial number in output stream:  673559
```

---

### Post by desconocido on 2011-04-01
I solved this by upgrading Wine from the standard version with Karmic (1.1.31) to a more recent one (1.3.15). It also works without an xorg.conf file.

Getting recent Wines for Karmic used to be too mind-boggling complex for me, but the Ubuntu-Wine group have made it simple. Thanks. See:

[https://launchpad.net/~ubuntu-wine/+archive/ppa?field.series_filter=karmic](https://launchpad.net/~ubuntu-wine/+archive/ppa?field.series_filter=karmic)
[https://launchpad.net/+help/soyuz/ppa-sources-list.html](https://launchpad.net/+help/soyuz/ppa-sources-list.html) 
(the latter is how to make a ppa a repository under Karmic)

Process (starting with no xorg.conf) was

> sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
Synaptic - completely remove wine and wine-gecko
delete ~/.wine
Synaptic - Mark for install and Apply wine1.3, wine1.3-gecko & related packages
Doubleclick saved download of GoogleSketchUpWEN.exe to install SketchUp 7.1
regedit to re-create (HKEY_CURRENT_USER\Software\Google\SketchUp7\GLConfig\Display\HW_OK set to 1.

---

