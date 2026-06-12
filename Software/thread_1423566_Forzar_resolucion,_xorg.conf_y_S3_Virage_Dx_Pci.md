---
title: "Forzar resolucion, xorg.conf y S3 Virage Dx Pci"
date: 2010-03-06
forum: Software
---

### Post by NickCis on 2010-03-06
Hola, Recien instale Ubuntu 9.10 en mi pc.
No tuve ningun problema mayor. Solo encontre qe la resoluciones qeu podia usar eran muy pequeñas. Entonces quise forzar la resolucion, haciendo el boot alternativo que me da a terminal de root. Dsp: "Xorg -configure", Le agregue los Modes "1024x768" y lo copie donde debia estar. El problema es que no veo ninguna modificacion, la resolucion sigue siendo la misma de antes. Alguna ayuda?

Mi pc:
Pentium III 700mhz
Mem 315mb (ni idea esto salio de cat /proc/meminfo xD)
Placa de video S3 Virage Dx (Pci)

Adjunto lspci:
```

oficina@oficina:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:08.0 VGA compatible controller: S3 Inc. ViRGE/DX or /GX (rev 01)
00:09.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)
oficina@oficina:~$ 

```

Adjunto xorg.conf
```

oficina@oficina:~$ cat /etc/X11/xorg.conf
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
	Load  "dri2"
	Load  "extmod"
	Load  "record"
	Load  "dri"
	Load  "dbe"
	Load  "glx"
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
	#DisplaySize	  330   250	# mm
	Identifier   "Monitor0"
	VendorName   "CPQ"
	ModelName    "&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 100.0
	Option	    "DPMS"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "slow_edodram"       	# [<bool>]
        #Option     "slow_dram"          	# [<bool>]
        #Option     "fast_dram"          	# [<bool>]
        #Option     "fpm_vram"           	# [<bool>]
        #Option     "pci_burst"          	# [<bool>]
        #Option     "fifo_conservative"  	# [<bool>]
        #Option     "fifo_moderate"      	# [<bool>]
        #Option     "fifo_aggressive"    	# [<bool>]
        #Option     "pci_retry"          	# [<bool>]
        #Option     "NoAccel"            	# [<bool>]
        #Option     "early_ras_precharge" 	# [<bool>]
        #Option     "late_ras_precharge" 	# [<bool>]
        #Option     "lcd_center"         	# [<bool>]
        #Option     "set_lcdclk"         	# <i>
        #Option     "set_mclk"           	# <freq>
        #Option     "set_refclk"         	# <freq>
        #Option     "show_cache"         	# [<bool>]
        #Option     "HWCursor"           	# [<bool>]
        #Option     "SWCursor"           	# [<bool>]
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "Rotate"             	# [<str>]
        #Option     "mxcr3afix"          	# [<bool>]
        #Option     "XVideo"             	# [<bool>]
	Identifier  "Card0"
	Driver      "s3virge"
	VendorName  "S3 Inc."
	BoardName   "ViRGE/DX or /GX"
	BusID       "PCI:0:8:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
		Modes "1024x768"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
		Modes "1024x768"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
		Modes "1024x768"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
		Modes "1024x768"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
		Modes "1024x768"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes "1024x768"
	EndSubSection
EndSection

oficina@oficina:~$ 

```

Saludos y muchas gracias =P

---

