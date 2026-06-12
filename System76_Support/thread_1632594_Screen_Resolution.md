---
title: "Screen Resolution"
date: 2010-11-28
forum: System76 Support
---

### Post by natibo on 2010-11-28
I did a fresh install of Ubuntu 10.10 before I saw your recommendation just to do an upgrade.

That being said, I am not given the option of a 1440x900 screen resolution or a 75 refresh rate.

How can I fix this?

Here is my system:

[INDENT]Sable Performance
Options
*Hard Drive : 750 GB SATA II 300 Mbps - 7200 R
+ $180.00
*Hardware Warranty : 1 Yr. Ltd. Warranty and Technica
+ $0.00
*Keyboard and Mouse : Logitech Cordless Desktop EX 110
+ $39.00
*LCD Monitor : 19” LG Widescreen LCD (1440 x 90
+ $235.00
*Memory : 4 GB - 4 x 1 GB - DDR 2 - 800 MH
+ $119.00
*Operating System : Ubuntu 7.10 64 Bit (Gutsy Gibbon
+ $0.00
*Optical Drive : CD-RW / DVD-RW
+ $19.00
*Portable Flash Drive : no flash drive
+ $0.00
*Processor : Core 2 Duo E6750 2.66 GHz FSB 13
+ $210.00
*Speakers : 2.1 - Logitech X-230 - 2 Satelli
+ $49.00[/INDENT]

---

### Post by matt_symes on 2010-11-28
Hi  

Open a terminal and type

xrandr

Post the results back here.

Kind regards

---

### Post by natibo on 2010-11-28
here it is:

[INDENT]Screen 0: minimum 320 x 200, current 1360 x 768, maximum 4096 x 4096
VGA1 disconnected (normal left inverted right x axis y axis)
VGA2 connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8* 
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9     59.9  
[/INDENT]

---

### Post by matt_symes on 2010-11-28
Hi

> **natibo said:**
> here it is:
[INDENT]Screen 0: minimum 320 x 200, current 1360 x 768, maximum 4096 x 4096
VGA1 disconnected (normal left inverted right x axis y axis)
VGA2 connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8* 
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9     59.9  
[/INDENT]

You will need to add a new screen resolution. Have a look at this thread.

[http://ubuntuforums.org/showthread.php?t=1112186](http://ubuntuforums.org/showthread.php?t=1112186)

Kind regards

---

### Post by natibo on 2010-11-28
I get an error:

[INDENT]natibo@natibo:~$ xrandr --addmode VGA 1440x900_59.90
xrandr: cannot find output "VGA"
[/INDENT]


In addition, how can I make the changes persistent if my Xorg file is blank?

---

### Post by matt_symes on 2010-11-28
Hi

Open a terminal and type 

xrandr --verbose

Post the output back here. (Between code tags)

Kind regards

---

### Post by natibo on 2010-11-28
Here it is. I eventually followed the instructions on the initial thread using "VGA1". In the end, it crashed the system.

[INDENT]Screen 0: minimum 320 x 200, current 1360 x 768, maximum 4096 x 4096
VGA1 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x41
	Timestamp:  15151
	Subpixel:   unknown
	Clones:     VGA2
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
VGA2 connected 1360x768+0+0 (0x43) normal (normal left inverted right x axis y axis) 0mm x 0mm
	Identifier: 0x42
	Timestamp:  15151
	Subpixel:   horizontal rgb
	Gamma:      1.0:1.0:1.0
	Brightness: 1.0
	Clones:     VGA1
	CRTC:       0
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
  1360x768 (0x43)   84.8MHz -HSync +VSync *current
        h: width  1360 start 1432 end 1568 total 1776 skew    0 clock   47.7KHz
        v: height  768 start  771 end  781 total  798           clock   59.8Hz
  1024x768 (0x44)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x45)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  800x600 (0x46)   36.0MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock   35.2KHz
        v: height  600 start  601 end  603 total  625           clock   56.2Hz
  848x480 (0x47)   33.8MHz +HSync +VSync
        h: width   848 start  864 end  976 total 1088 skew    0 clock   31.0KHz
        v: height  480 start  486 end  494 total  517           clock   60.0Hz
  640x480 (0x48)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  489 end  492 total  525           clock   59.9Hz
  640x480 (0x49)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
[/INDENT]

---

### Post by matt_symes on 2010-11-28
Hi

> In the end, it crashed the system.

Blimy, It should not have crashed your system. There might be some info in the xorg.0.log file to suggest why it crashed.

System->Administration->Log File Viewer.

Kind regards

---

### Post by natibo on 2010-11-28
This is what was in there. Should I just install 10.04 and then upgrade. I cant believe that I bought a computer for use with Ubuntu and it will not work with a fresh install. It reduces my optimism about Linux.


[    11.817] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    11.817] X Protocol Version 11, Revision 0
[    11.817] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[    11.817] Current Operating System: Linux natibo 2.6.35-23-generic #40-Ubuntu SMP Wed Nov 17 22:14:33 UTC 2010 x86_64
[    11.817] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-23-generic root=UUID=d82b31f5-e795-47dd-8805-fff50a3cc8c7 ro quiet splash
[    11.817] Build Date: 16 September 2010  06:18:41PM
[    11.817] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    11.817] Current version of pixman: 0.18.4
[    11.817] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    11.817] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    11.817] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Nov 28 08:49:01 2010
[    11.835] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    11.835] (==) No Layout section.  Using the first Screen section.
[    11.835] (==) No screen section available. Using defaults.
[    11.835] (**) |-->Screen "Default Screen Section" (0)
[    11.835] (**) |   |-->Monitor "<default monitor>"
[    11.835] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    11.835] (==) Automatically adding devices
[    11.835] (==) Automatically enabling devices
[    11.835] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    11.835] 	Entry deleted from font path.
[    11.835] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    11.835] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    11.835] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    11.835] (II) Loader magic: 0x7d0200
[    11.835] (II) Module ABI versions:
[    11.835] 	X.Org ANSI C Emulation: 0.4
[    11.835] 	X.Org Video Driver: 8.0
[    11.835] 	X.Org XInput driver : 11.0
[    11.835] 	X.Org Server Extension : 4.0
[    11.836] (--) PCI:*(0:0:2:0) 8086:29c2:1043:8276 rev 2, Mem @ 0xfe900000/524288, 0xd0000000/268435456, 0xfe800000/1048576, I/O @ 0x0000bc00/8
[    11.836] (--) PCI: (0:0:2:1) 8086:29c3:1043:8276 rev 2, Mem @ 0xfe980000/524288
[    11.836] (II) Open ACPI successful (/var/run/acpid.socket)
[    11.836] (II) LoadModule: "extmod"
[    11.848] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    11.848] (II) Module extmod: vendor="X.Org Foundation"
[    11.848] 	compiled for 1.9.0, module version = 1.0.0
[    11.848] 	Module class: X.Org Server Extension
[    11.848] 	ABI class: X.Org Server Extension, version 4.0
[    11.848] (II) Loading extension MIT-SCREEN-SAVER
[    11.848] (II) Loading extension XFree86-VidModeExtension
[    11.848] (II) Loading extension XFree86-DGA
[    11.848] (II) Loading extension DPMS
[    11.848] (II) Loading extension XVideo
[    11.848] (II) Loading extension XVideo-MotionCompensation
[    11.848] (II) Loading extension X-Resource
[    11.848] (II) LoadModule: "dbe"
[    11.848] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    11.848] (II) Module dbe: vendor="X.Org Foundation"
[    11.848] 	compiled for 1.9.0, module version = 1.0.0
[    11.848] 	Module class: X.Org Server Extension
[    11.848] 	ABI class: X.Org Server Extension, version 4.0
[    11.848] (II) Loading extension DOUBLE-BUFFER
[    11.848] (II) LoadModule: "glx"
[    11.849] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    11.849] (II) Module glx: vendor="X.Org Foundation"
[    11.849] 	compiled for 1.9.0, module version = 1.0.0
[    11.849] 	ABI class: X.Org Server Extension, version 4.0
[    11.849] (==) AIGLX enabled
[    11.849] (II) Loading extension GLX
[    11.849] (II) LoadModule: "record"
[    11.849] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    11.849] (II) Module record: vendor="X.Org Foundation"
[    11.849] 	compiled for 1.9.0, module version = 1.13.0
[    11.849] 	Module class: X.Org Server Extension
[    11.849] 	ABI class: X.Org Server Extension, version 4.0
[    11.849] (II) Loading extension RECORD
[    11.849] (II) LoadModule: "dri"
[    11.849] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    11.850] (II) Module dri: vendor="X.Org Foundation"
[    11.850] 	compiled for 1.9.0, module version = 1.0.0
[    11.850] 	ABI class: X.Org Server Extension, version 4.0
[    11.850] (II) Loading extension XFree86-DRI
[    11.850] (II) LoadModule: "dri2"
[    11.850] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    11.850] (II) Module dri2: vendor="X.Org Foundation"
[    11.850] 	compiled for 1.9.0, module version = 1.2.0
[    11.850] 	ABI class: X.Org Server Extension, version 4.0
[    11.850] (II) Loading extension DRI2
[    11.850] (==) Matched intel as autoconfigured driver 0
[    11.850] (==) Matched vesa as autoconfigured driver 1
[    11.850] (==) Matched fbdev as autoconfigured driver 2
[    11.850] (==) Assigned the driver to the xf86ConfigLayout
[    11.850] (II) LoadModule: "intel"
[    11.850] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    11.850] (II) Module intel: vendor="X.Org Foundation"
[    11.850] 	compiled for 1.9.0, module version = 2.12.0
[    11.850] 	Module class: X.Org Video Driver
[    11.850] 	ABI class: X.Org Video Driver, version 8.0
[    11.850] (II) LoadModule: "vesa"
[    11.851] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    11.851] (II) Module vesa: vendor="X.Org Foundation"
[    11.851] 	compiled for 1.8.99.905, module version = 2.3.0
[    11.851] 	Module class: X.Org Video Driver
[    11.851] 	ABI class: X.Org Video Driver, version 8.0
[    11.851] (II) LoadModule: "fbdev"
[    11.851] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    11.851] (II) Module fbdev: vendor="X.Org Foundation"
[    11.851] 	compiled for 1.8.99.905, module version = 0.4.2
[    11.851] 	ABI class: X.Org Video Driver, version 8.0
[    11.851] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[    11.851] (II) VESA: driver for VESA chipsets: vesa
[    11.851] (II) FBDEV: driver for framebuffer: fbdev
[    11.851] (++) using VT number 7

[    11.851] (WW) Falling back to old probe method for vesa
[    11.851] (WW) Falling back to old probe method for fbdev
[    11.851] (II) Loading sub module "fbdevhw"
[    11.851] (II) LoadModule: "fbdevhw"
[    11.852] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    11.852] (II) Module fbdevhw: vendor="X.Org Foundation"
[    11.852] 	compiled for 1.9.0, module version = 0.0.2
[    11.852] 	ABI class: X.Org Video Driver, version 8.0
[    11.854] drmOpenDevice: node name is /dev/dri/card0
[    11.854] drmOpenDevice: open result is 9, (OK)
[    11.854] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    11.854] drmOpenDevice: node name is /dev/dri/card0
[    11.854] drmOpenDevice: open result is 9, (OK)
[    11.854] drmOpenByBusid: drmOpenMinor returns 9
[    11.854] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    11.854] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    11.854] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    11.854] (==) intel(0): RGB weight 888
[    11.854] (==) intel(0): Default visual is TrueColor
[    11.854] (II) intel(0): Integrated Graphics Chipset: Intel(R) G33
[    11.854] (--) intel(0): Chipset: "G33"
[    11.854] (==) intel(0): video overlay key set to 0x101fe
[    11.900] (II) intel(0): Output VGA1 has no monitor section
[    12.385] (II) intel(0): Output VGA2 has no monitor section
[    12.420] (II) intel(0): EDID for output VGA1
[    12.915] (II) intel(0): EDID for output VGA2
[    12.915] (II) intel(0): Not using default mode "640x350" (vrefresh out of range)
[    12.915] (II) intel(0): Not using default mode "320x175" (doublescan mode not supported)
[    12.915] (II) intel(0): Not using default mode "640x400" (vrefresh out of range)
[    12.915] (II) intel(0): Not using default mode "320x200" (doublescan mode not supported)
[    12.915] (II) intel(0): Not using default mode "720x400" (vrefresh out of range)
[    12.915] (II) intel(0): Not using default mode "360x200" (doublescan mode not supported)
[    12.915] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    12.915] (II) intel(0): Not using default mode "640x480" (vrefresh out of range)
[    12.915] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    12.915] (II) intel(0): Not using default mode "640x480" (vrefresh out of range)
[    12.915] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "640x480" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "800x600" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "800x600" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "800x600" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1024x768i" (interlace mode not supported)
[    12.916] (II) intel(0): Not using default mode "512x384i" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1280x960" (hsync out of range)
[    12.916] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1280x960" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1280x1024" (hsync out of range)
[    12.916] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1600x1200" (hsync out of range)
[    12.916] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1792x1344" (hsync out of range)
[    12.916] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1792x1344" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1856x1392" (hsync out of range)
[    12.916] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1856x1392" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1920x1440" (hsync out of range)
[    12.916] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "832x624" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "416x312" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1152x864" (hsync out of range)
[    12.916] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[    12.916] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1400x1050" (hsync out of range)
[    12.916] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1440x900" (hsync out of range)
[    12.916] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1600x1024" (hsync out of range)
[    12.916] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1680x1050" (hsync out of range)
[    12.916] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1680x1050" (hsync out of range)
[    12.916] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1920x1080" (hsync out of range)
[    12.916] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1920x1200" (hsync out of range)
[    12.916] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "2048x1536" (hsync out of range)
[    12.916] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    12.916] (II) intel(0): Printing probed modes for output VGA2
[    12.916] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    12.916] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    12.916] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    12.916] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    12.916] (II) intel(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz)
[    12.916] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz)
[    12.916] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    12.917] (II) intel(0): Output VGA1 disconnected
[    12.917] (II) intel(0): Output VGA2 connected
[    12.917] (II) intel(0): Using fuzzy aspect match for initial modes
[    12.91[    11.817] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    11.817] X Protocol Version 11, Revision 0
[    11.817] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[    11.817] Current Operating System: Linux natibo 2.6.35-23-generic #40-Ubuntu SMP Wed Nov 17 22:14:33 UTC 2010 x86_64
[    11.817] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-23-generic root=UUID=d82b31f5-e795-47dd-8805-fff50a3cc8c7 ro quiet splash
[    11.817] Build Date: 16 September 2010  06:18:41PM
[    11.817] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    11.817] Current version of pixman: 0.18.4
[    11.817] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    11.817] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    11.817] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Nov 28 08:49:01 2010
[    11.835] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    11.835] (==) No Layout section.  Using the first Screen section.
[    11.835] (==) No screen section available. Using defaults.
[    11.835] (**) |-->Screen "Default Screen Section" (0)
[    11.835] (**) |   |-->Monitor "<default monitor>"
[    11.835] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    11.835] (==) Automatically adding devices
[    11.835] (==) Automatically enabling devices
[    11.835] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    11.835] 	Entry deleted from font path.
[    11.835] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    11.835] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    11.835] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    11.835] (II) Loader magic: 0x7d0200
[    11.835] (II) Module ABI versions:
[    11.835] 	X.Org ANSI C Emulation: 0.4
[    11.835] 	X.Org Video Driver: 8.0
[    11.835] 	X.Org XInput driver : 11.0
[    11.835] 	X.Org Server Extension : 4.0
[    11.836] (--) PCI:*(0:0:2:0) 8086:29c2:1043:8276 rev 2, Mem @ 0xfe900000/524288, 0xd0000000/268435456, 0xfe800000/1048576, I/O @ 0x0000bc00/8
[    11.836] (--) PCI: (0:0:2:1) 8086:29c3:1043:8276 rev 2, Mem @ 0xfe980000/524288
[    11.836] (II) Open ACPI successful (/var/run/acpid.socket)
[    11.836] (II) LoadModule: "extmod"
[    11.848] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    11.848] (II) Module extmod: vendor="X.Org Foundation"
[    11.848] 	compiled for 1.9.0, module version = 1.0.0
[    11.848] 	Module class: X.Org Server Extension
[    11.848] 	ABI class: X.Org Server Extension, version 4.0
[    11.848] (II) Loading extension MIT-SCREEN-SAVER
[    11.848] (II) Loading extension XFree86-VidModeExtension
[    11.848] (II) Loading extension XFree86-DGA
[    11.848] (II) Loading extension DPMS
[    11.848] (II) Loading extension XVideo
[    11.848] (II) Loading extension XVideo-MotionCompensation
[    11.848] (II) Loading extension X-Resource
[    11.848] (II) LoadModule: "dbe"
[    11.848] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    11.848] (II) Module dbe: vendor="X.Org Foundation"
[    11.848] 	compiled for 1.9.0, module version = 1.0.0
[    11.848] 	Module class: X.Org Server Extension
[    11.848] 	ABI class: X.Org Server Extension, version 4.0
[    11.848] (II) Loading extension DOUBLE-BUFFER
[    11.848] (II) LoadModule: "glx"
[    11.849] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    11.849] (II) Module glx: vendor="X.Org Foundation"
[    11.849] 	compiled for 1.9.0, module version = 1.0.0
[    11.849] 	ABI class: X.Org Server Extension, version 4.0
[    11.849] (==) AIGLX enabled
[    11.849] (II) Loading extension GLX
[    11.849] (II) LoadModule: "record"
[    11.849] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    11.849] (II) Module record: vendor="X.Org Foundation"
[    11.849] 	compiled for 1.9.0, module version = 1.13.0
[    11.849] 	Module class: X.Org Server Extension
[    11.849] 	ABI class: X.Org Server Extension, version 4.0
[    11.849] (II) Loading extension RECORD
[    11.849] (II) LoadModule: "dri"
[    11.849] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    11.850] (II) Module dri: vendor="X.Org Foundation"
[    11.850] 	compiled for 1.9.0, module version = 1.0.0
[    11.850] 	ABI class: X.Org Server Extension, version 4.0
[    11.850] (II) Loading extension XFree86-DRI
[    11.850] (II) LoadModule: "dri2"
[    11.850] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    11.850] (II) Module dri2: vendor="X.Org Foundation"
[    11.850] 	compiled for 1.9.0, module version = 1.2.0
[    11.850] 	ABI class: X.Org Server Extension, version 4.0
[    11.850] (II) Loading extension DRI2
[    11.850] (==) Matched intel as autoconfigured driver 0
[    11.850] (==) Matched vesa as autoconfigured driver 1
[    11.850] (==) Matched fbdev as autoconfigured driver 2
[    11.850] (==) Assigned the driver to the xf86ConfigLayout
[    11.850] (II) LoadModule: "intel"
[    11.850] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    11.850] (II) Module intel: vendor="X.Org Foundation"
[    11.850] 	compiled for 1.9.0, module version = 2.12.0
[    11.850] 	Module class: X.Org Video Driver
[    11.850] 	ABI class: X.Org Video Driver, version 8.0
[    11.850] (II) LoadModule: "vesa"
[    11.851] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    11.851] (II) Module vesa: vendor="X.Org Foundation"
[    11.851] 	compiled for 1.8.99.905, module version = 2.3.0
[    11.851] 	Module class: X.Org Video Driver
[    11.851] 	ABI class: X.Org Video Driver, version 8.0
[    11.851] (II) LoadModule: "fbdev"
[    11.851] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    11.851] (II) Module fbdev: vendor="X.Org Foundation"
[    11.851] 	compiled for 1.8.99.905, module version = 0.4.2
[    11.851] 	ABI class: X.Org Video Driver, version 8.0
[    11.851] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[    11.851] (II) VESA: driver for VESA chipsets: vesa
[    11.851] (II) FBDEV: driver for framebuffer: fbdev
[    11.851] (++) using VT number 7

[    11.851] (WW) Falling back to old probe method for vesa
[    11.851] (WW) Falling back to old probe method for fbdev
[    11.851] (II) Loading sub module "fbdevhw"
[    11.851] (II) LoadModule: "fbdevhw"
[    11.852] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    11.852] (II) Module fbdevhw: vendor="X.Org Foundation"
[    11.852] 	compiled for 1.9.0, module version = 0.0.2
[    11.852] 	ABI class: X.Org Video Driver, version 8.0
[    11.854] drmOpenDevice: node name is /dev/dri/card0
[    11.854] drmOpenDevice: open result is 9, (OK)
[    11.854] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    11.854] drmOpenDevice: node name is /dev/dri/card0
[    11.854] drmOpenDevice: open result is 9, (OK)
[    11.854] drmOpenByBusid: drmOpenMinor returns 9
[    11.854] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    11.854] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    11.854] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    11.854] (==) intel(0): RGB weight 888
[    11.854] (==) intel(0): Default visual is TrueColor
[    11.854] (II) intel(0): Integrated Graphics Chipset: Intel(R) G33
[    11.854] (--) intel(0): Chipset: "G33"
[    11.854] (==) intel(0): video overlay key set to 0x101fe
[    11.900] (II) intel(0): Output VGA1 has no monitor section
[    12.385] (II) intel(0): Output VGA2 has no monitor section
[    12.420] (II) intel(0): EDID for output VGA1
[    12.915] (II) intel(0): EDID for output VGA2
[    12.915] (II) intel(0): Not using default mode "640x350" (vrefresh out of range)
[    12.915] (II) intel(0): Not using default mode "320x175" (doublescan mode not supported)
[    12.915] (II) intel(0): Not using default mode "640x400" (vrefresh out of range)
[    12.915] (II) intel(0): Not using default mode "320x200" (doublescan mode not supported)
[    12.915] (II) intel(0): Not using default mode "720x400" (vrefresh out of range)
[    12.915] (II) intel(0): Not using default mode "360x200" (doublescan mode not supported)
[    12.915] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    12.915] (II) intel(0): Not using default mode "640x480" (vrefresh out of range)
[    12.915] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    12.915] (II) intel(0): Not using default mode "640x480" (vrefresh out of range)
[    12.915] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "640x480" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "800x600" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "800x600" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "800x600" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1024x768i" (interlace mode not supported)
[    12.916] (II) intel(0): Not using default mode "512x384i" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1280x960" (hsync out of range)
[    12.916] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1280x960" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1280x1024" (hsync out of range)
[    12.916] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1600x1200" (hsync out of range)
[    12.916] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1792x1344" (hsync out of range)
[    12.916] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1792x1344" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1856x1392" (hsync out of range)
[    12.916] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1856x1392" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1920x1440" (hsync out of range)
[    12.916] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "832x624" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "416x312" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1152x864" (hsync out of range)
[    12.916] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[    12.916] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1400x1050" (hsync out of range)
[    12.916] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1440x900" (hsync out of range)
[    12.916] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1600x1024" (hsync out of range)
[    12.916] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1680x1050" (hsync out of range)
[    12.916] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1680x1050" (hsync out of range)
[    12.916] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1920x1080" (hsync out of range)
[    12.916] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1920x1200" (hsync out of range)
[    12.916] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "2048x1536" (hsync out of range)
[    12.916] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    12.916] (II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
[    12.916] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    12.916] (II) intel(0): Printing probed modes for output VGA2
[    12.916] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    12.916] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    12.916] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    12.916] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    12.916] (II) intel(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz)
[    12.916] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz)
[    12.916] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    12.917] (II) intel(0): Output VGA1 disconnected
[    12.917] (II) intel(0): Output VGA2 connected
[    12.917] (II) intel(0): Using fuzzy aspect match for initial modes
[    12.917] (II) intel(0): Output VGA2 using initial mode 1024x768
[    12.917] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    12.917] (II) intel(0): Kernel page flipping support detected, but forcibly disabled.
[    12.917] (==) intel(0): DPI set to (96, 96)
[    12.917] (II) Loading sub module "fb"
[    12.917] (II) LoadModule: "fb"
[    12.917] (II) Loading /usr/lib/xorg/modules/libfb.so
[    12.917] (II) Module fb: vendor="X.Org Foundation"
[    12.917] 	compiled for 1.9.0, module version = 1.0.0
[    12.917] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    12.917] (II) UnloadModule: "vesa"
[    12.917] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    12.917] (II) UnloadModule: "fbdev"
[    12.917] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    12.917] (II) UnloadModule: "fbdevhw"
[    12.917] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    12.917] (==) Depth 24 pixmap format is 32 bpp
[    12.917] (II) intel(0): [DRI2] Setup complete
[    12.917] (II) intel(0): [DRI2]   DRI driver: i915
[    12.917] (**) intel(0): Tiling enabled
[    12.917] (**) intel(0): SwapBuffers wait enabled
[    12.917] (==) intel(0): VideoRam: 262144 KB
[    12.917] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[    12.917] (II) UXA(0): Driver registered support for the following operations:
[    12.917] (II)         solid
[    12.917] (II)         copy
[    12.917] (II)         composite (RENDER acceleration)
[    12.917] (II)         put_image
[    12.917] (II)         get_image
[    12.917] (==) intel(0): Backing store disabled
[    12.917] (==) intel(0): Silken mouse enabled
[    12.917] (II) intel(0): Initializing HW Cursor
[    12.951] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    12.951] (==) intel(0): DPMS enabled
[    12.951] (==) intel(0): Intel XvMC decoder disabled
[    12.951] (II) intel(0): Set up textured video
[    12.951] (II) intel(0): Set up overlay video
[    12.951] (II) intel(0): direct rendering: DRI2 Enabled
[    12.951] (--) RandR disabled
[    12.951] (II) Initializing built-in extension Generic Event Extension
[    12.951] (II) Initializing built-in extension SHAPE
[    12.951] (II) Initializing built-in extension MIT-SHM
[    12.951] (II) Initializing built-in extension XInputExtension
[    12.951] (II) Initializing built-in extension XTEST
[    12.951] (II) Initializing built-in extension BIG-REQUESTS
[    12.951] (II) Initializing built-in extension SYNC
[    12.951] (II) Initializing built-in extension XKEYBOARD
[    12.951] (II) Initializing built-in extension XC-MISC
[    12.951] (II) Initializing built-in extension SECURITY
[    12.951] (II) Initializing built-in extension XINERAMA
[    12.951] (II) Initializing built-in extension XFIXES
[    12.951] (II) Initializing built-in extension RENDER
[    12.951] (II) Initializing built-in extension RANDR
[    12.951] (II) Initializing built-in extension COMPOSITE
[    12.951] (II) Initializing built-in extension DAMAGE
[    12.951] (II) Initializing built-in extension GESTURE
[    12.958] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    12.958] (II) AIGLX: enabled GLX_INTEL_swap_event
[    12.958] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    12.958] (II) AIGLX: enabled GLX_SGI_make_current_read
[    12.958] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    12.958] (II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
[    12.958] (II) GLX: Initialized DRI2 GL provider for screen 0
[    12.958] (II) intel(0): Setting screen physical size to 270 x 203
[    12.971] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    12.978] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    12.978] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    12.978] (II) LoadModule: "evdev"
[    12.978] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    12.978] (II) Module evdev: vendor="X.Org Foundation"
[    12.978] 	compiled for 1.9.0, module version = 2.3.2
[    12.978] 	Module class: X.Org XInput Driver
[    12.978] 	ABI class: X.Org XInput driver, version 11.0
[    12.978] (**) Power Button: always reports core events
[    12.978] (**) Power Button: Device: "/dev/input/event1"
[    13.011] (II) Power Button: Found keys
[    13.011] (II) Power Button: Configuring as keyboard
[    13.011] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    13.011] (**) Option "xkb_rules" "evdev"
[    13.011] (**) Option "xkb_model" "pc105"
[    13.011] (**) Option "xkb_layout" "us"
[    13.012] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    13.012] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    13.012] (**) Power Button: always reports core events
[    13.012] (**) Power Button: Device: "/dev/input/event0"
[    13.041] (II) Power Button: Found keys
[    13.041] (II) Power Button: Configuring as keyboard
[    13.041] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    13.041] (**) Option "xkb_rules" "evdev"
[    13.041] (**) Option "xkb_model" "pc105"
[    13.041] (**) Option "xkb_layout" "us"
[    13.042] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
[    13.042] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    13.042] (**) Logitech USB Receiver: always reports core events
[    13.042] (**) Logitech USB Receiver: Device: "/dev/input/event2"
[    13.071] (II) Logitech USB Receiver: Found keys
[    13.071] (II) Logitech USB Receiver: Configuring as keyboard
[    13.071] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    13.071] (**) Option "xkb_rules" "evdev"
[    13.071] (**) Option "xkb_model" "pc105"
[    13.071] (**) Option "xkb_layout" "us"
[    13.071] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[    13.071] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    13.071] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    13.071] (**) Logitech USB Receiver: always reports core events
[    13.071] (**) Logitech USB Receiver: Device: "/dev/input/event3"
[    13.101] (II) Logitech USB Receiver: Found 12 mouse buttons
[    13.101] (II) Logitech USB Receiver: Found scroll wheel(s)
[    13.101] (II) Logitech USB Receiver: Found relative axes
[    13.101] (II) Logitech USB Receiver: Found x and y relative axes
[    13.101] (II) Logitech USB Receiver: Found absolute axes
[    13.101] (II) evdev-grail: failed to open grail, no gesture support
[    13.101] (II) Logitech USB Receiver: Found keys
[    13.101] (II) Logitech USB Receiver: Configuring as mouse
[    13.101] (II) Logitech USB Receiver: Configuring as keyboard
[    13.101] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    13.101] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    13.101] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    13.101] (**) Option "xkb_rules" "evdev"
[    13.101] (**) Option "xkb_model" "pc105"
[    13.101] (**) Option "xkb_layout" "us"
[    13.101] (II) Logitech USB Receiver: initialized for relative axes.
[    13.101] (WW) Logitech USB Receiver: ignoring absolute axes.
[    13.101] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    13.101] (II) No input driver/identifier specified (ignoring)
[    13.102] (II) config/udev: Adding input device UVC Camera (046d:081a) (/dev/input/event4)
[    13.102] (**) UVC Camera (046d:081a): Applying InputClass "evdev keyboard catchall"
[    13.102] (**) UVC Camera (046d:081a): always reports core events
[    13.102] (**) UVC Camera (046d:081a): Device: "/dev/input/event4"
[    13.131] (II) UVC Camera (046d:081a): Found keys
[    13.131] (II) UVC Camera (046d:081a): Configuring as keyboard
[    13.131] (II) XINPUT: Adding extended input device "UVC Camera (046d:081a)" (type: KEYBOARD)
[    13.131] (**) Option "xkb_rules" "evdev"
[    13.131] (**) Option "xkb_model" "pc105"
[    13.131] (**) Option "xkb_layout" "us"
[    15.116] (II) intel(0): Allocated new frame buffer 1408x768 stride 8192, tiled
[ 15876.782] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
7] (II) intel(0): Output VGA2 using initial mode 1024x768
[    12.917] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    12.917] (II) intel(0): Kernel page flipping support detected, but forcibly disabled.
[    12.917] (==) intel(0): DPI set to (96, 96)
[    12.917] (II) Loading sub module "fb"
[    12.917] (II) LoadModule: "fb"
[    12.917] (II) Loading /usr/lib/xorg/modules/libfb.so
[    12.917] (II) Module fb: vendor="X.Org Foundation"
[    12.917] 	compiled for 1.9.0, module version = 1.0.0
[    12.917] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    12.917] (II) UnloadModule: "vesa"
[    12.917] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    12.917] (II) UnloadModule: "fbdev"
[    12.917] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    12.917] (II) UnloadModule: "fbdevhw"
[    12.917] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    12.917] (==) Depth 24 pixmap format is 32 bpp
[    12.917] (II) intel(0): [DRI2] Setup complete
[    12.917] (II) intel(0): [DRI2]   DRI driver: i915
[    12.917] (**) intel(0): Tiling enabled
[    12.917] (**) intel(0): SwapBuffers wait enabled
[    12.917] (==) intel(0): VideoRam: 262144 KB
[    12.917] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[    12.917] (II) UXA(0): Driver registered support for the following operations:
[    12.917] (II)         solid
[    12.917] (II)         copy
[    12.917] (II)         composite (RENDER acceleration)
[    12.917] (II)         put_image
[    12.917] (II)         get_image
[    12.917] (==) intel(0): Backing store disabled
[    12.917] (==) intel(0): Silken mouse enabled
[    12.917] (II) intel(0): Initializing HW Cursor
[    12.951] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    12.951] (==) intel(0): DPMS enabled
[    12.951] (==) intel(0): Intel XvMC decoder disabled
[    12.951] (II) intel(0): Set up textured video
[    12.951] (II) intel(0): Set up overlay video
[    12.951] (II) intel(0): direct rendering: DRI2 Enabled
[    12.951] (--) RandR disabled
[    12.951] (II) Initializing built-in extension Generic Event Extension
[    12.951] (II) Initializing built-in extension SHAPE
[    12.951] (II) Initializing built-in extension MIT-SHM
[    12.951] (II) Initializing built-in extension XInputExtension
[    12.951] (II) Initializing built-in extension XTEST
[    12.951] (II) Initializing built-in extension BIG-REQUESTS
[    12.951] (II) Initializing built-in extension SYNC
[    12.951] (II) Initializing built-in extension XKEYBOARD
[    12.951] (II) Initializing built-in extension XC-MISC
[    12.951] (II) Initializing built-in extension SECURITY
[    12.951] (II) Initializing built-in extension XINERAMA
[    12.951] (II) Initializing built-in extension XFIXES
[    12.951] (II) Initializing built-in extension RENDER
[    12.951] (II) Initializing built-in extension RANDR
[    12.951] (II) Initializing built-in extension COMPOSITE
[    12.951] (II) Initializing built-in extension DAMAGE
[    12.951] (II) Initializing built-in extension GESTURE
[    12.958] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    12.958] (II) AIGLX: enabled GLX_INTEL_swap_event
[    12.958] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    12.958] (II) AIGLX: enabled GLX_SGI_make_current_read
[    12.958] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    12.958] (II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
[    12.958] (II) GLX: Initialized DRI2 GL provider for screen 0
[    12.958] (II) intel(0): Setting screen physical size to 270 x 203
[    12.971] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    12.978] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    12.978] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    12.978] (II) LoadModule: "evdev"
[    12.978] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    12.978] (II) Module evdev: vendor="X.Org Foundation"
[    12.978] 	compiled for 1.9.0, module version = 2.3.2
[    12.978] 	Module class: X.Org XInput Driver
[    12.978] 	ABI class: X.Org XInput driver, version 11.0
[    12.978] (**) Power Button: always reports core events
[    12.978] (**) Power Button: Device: "/dev/input/event1"
[    13.011] (II) Power Button: Found keys
[    13.011] (II) Power Button: Configuring as keyboard
[    13.011] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    13.011] (**) Option "xkb_rules" "evdev"
[    13.011] (**) Option "xkb_model" "pc105"
[    13.011] (**) Option "xkb_layout" "us"
[    13.012] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    13.012] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    13.012] (**) Power Button: always reports core events
[    13.012] (**) Power Button: Device: "/dev/input/event0"
[    13.041] (II) Power Button: Found keys
[    13.041] (II) Power Button: Configuring as keyboard
[    13.041] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    13.041] (**) Option "xkb_rules" "evdev"
[    13.041] (**) Option "xkb_model" "pc105"
[    13.041] (**) Option "xkb_layout" "us"
[    13.042] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
[    13.042] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    13.042] (**) Logitech USB Receiver: always reports core events
[    13.042] (**) Logitech USB Receiver: Device: "/dev/input/event2"
[    13.071] (II) Logitech USB Receiver: Found keys
[    13.071] (II) Logitech USB Receiver: Configuring as keyboard
[    13.071] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    13.071] (**) Option "xkb_rules" "evdev"
[    13.071] (**) Option "xkb_model" "pc105"
[    13.071] (**) Option "xkb_layout" "us"
[    13.071] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[    13.071] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    13.071] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    13.071] (**) Logitech USB Receiver: always reports core events
[    13.071] (**) Logitech USB Receiver: Device: "/dev/input/event3"
[    13.101] (II) Logitech USB Receiver: Found 12 mouse buttons
[    13.101] (II) Logitech USB Receiver: Found scroll wheel(s)
[    13.101] (II) Logitech USB Receiver: Found relative axes
[    13.101] (II) Logitech USB Receiver: Found x and y relative axes
[    13.101] (II) Logitech USB Receiver: Found absolute axes
[    13.101] (II) evdev-grail: failed to open grail, no gesture support
[    13.101] (II) Logitech USB Receiver: Found keys
[    13.101] (II) Logitech USB Receiver: Configuring as mouse
[    13.101] (II) Logitech USB Receiver: Configuring as keyboard
[    13.101] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    13.101] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    13.101] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    13.101] (**) Option "xkb_rules" "evdev"
[    13.101] (**) Option "xkb_model" "pc105"
[    13.101] (**) Option "xkb_layout" "us"
[    13.101] (II) Logitech USB Receiver: initialized for relative axes.
[    13.101] (WW) Logitech USB Receiver: ignoring absolute axes.
[    13.101] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    13.101] (II) No input driver/identifier specified (ignoring)
[    13.102] (II) config/udev: Adding input device UVC Camera (046d:081a) (/dev/input/event4)
[    13.102] (**) UVC Camera (046d:081a): Applying InputClass "evdev keyboard catchall"
[    13.102] (**) UVC Camera (046d:081a): always reports core events
[    13.102] (**) UVC Camera (046d:081a): Device: "/dev/input/event4"
[    13.131] (II) UVC Camera (046d:081a): Found keys
[    13.131] (II) UVC Camera (046d:081a): Configuring as keyboard
[    13.131] (II) XINPUT: Adding extended input device "UVC Camera (046d:081a)" (type: KEYBOARD)
[    13.131] (**) Option "xkb_rules" "evdev"
[    13.131] (**) Option "xkb_model" "pc105"
[    13.131] (**) Option "xkb_layout" "us"
[    15.116] (II) intel(0): Allocated new frame buffer 1408x768 stride 8192, tiled
[ 15876.782] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled

---

### Post by matt_symes on 2010-11-28
Hi

Have a look at this.

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

I will look through your log file when i get time.

Kind regards

---

### Post by isantop on 2010-12-01
What type of video card do you have? Additionally, what type of connection do you have from the video card to the cable to the monitor? If you're using DVI to VGA adapters, they may not allow the resolution to be properly reported to the monitor.

---

