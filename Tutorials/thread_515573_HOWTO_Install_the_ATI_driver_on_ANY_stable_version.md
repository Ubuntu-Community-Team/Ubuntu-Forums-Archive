---
title: "HOWTO: Install the ATI driver on ANY stable version of Ubuntu"
date: 2007-08-02
forum: Tutorials
---

### Post by tseliot on 2007-08-02
If you want to install ATI's proprietary driver you can follow this guide:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)


[COLOR="Red"]**Please, remember that only the installation of the driver from Ubuntu's repositories is officially supported by Ubuntu.**[/COLOR]

Should you want an easier but not supported method to install the ATI driver you can try [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") (**at your very own risk**)

---

### Post by gmanr26 on 2007-08-04
I just followed these simple instructions and yet my card is not working.  When you drag windows around in Ubuntu the movement is shaky which tells me that the graphics card is not being used.  My card is the ATI Radeon 9550 (x8 AGP) ... any help.

---

### Post by tseliot on 2007-08-04
> **gmanr26 said:**
> I just followed these simple instructions and yet my card is not working.  When you drag windows around in Ubuntu the movement is shaky which tells me that the graphics card is not being used.  My card is the ATI Radeon 9550 (x8 AGP) ... any help.

which method did you try?

---

### Post by gmanr26 on 2007-08-04
> **tseliot said:**
> which method did you try?

I fixed it.  Apparently it was installed and working it's just the ATI sucks in Linux because they are proprietary.  Now running Compiz (sp) :)

---

### Post by ag65151 on 2007-08-09
I tried the instructions for Feisty, but whenever I start X I got "No Screen found." I must admit to being a noob when it comes to X. There is a Screen defined in xorg.info using the proper driver. I don't know how to continue.

---

### Post by maxrisc on 2007-08-10
No screens found could mean that the resolution or vertical refresh rate you have selected are out of range.

On my lappy if I select 1440x900@75 I get the error.  When I set it to 1440x900@60 X starts.

---

### Post by aouie on 2007-08-16
There are some known issues and no ideas about the HD 2000 series. Also, this hasn't been tested. But, hopefully someone will test the method described in [my other post]("http://http://ubuntuforums.org/showthread.php?t=527333") and put it in a neater format and make it a sticky.

It should be as simple as

Starting with a *** **CLEAN SYSTEM WITH DEFAULT VESA DRIVERS FOR THE ATI CARD** *** (and the **libstdC++ 5** and updated "mesa" packages)
[**Download ATI's drivers**]("http://ati.amd.com/support/driver.html") for Linux.
```
**sudo sh ./ati-driver-installer-8.40.4-x86.x86_64.run**
```
Follow the prompts for the **automatic install**.
```
**sudo aticonfig --initial=dual-head --screen-layout=left** --vrefresh=1,85
```
**Restart X**.
You should now have a *** **WORKING DUAL HEAD SYSTEM WITH PROPRIETARY ATI DRIVERS** ***,

Sincerely,
Aouie

---

### Post by digital_exhaust on 2007-08-20
Gave it a try and I get...

```
digital@digital-desktop:~$ sudo sh ./ati-driver-installer-8.40.4-x86.x86_64.run
sh: Can't open ./ati-driver-installer-8.40.4-x86.x86_64.run
digital@digital-desktop:~$ 
```

Downloaded the drivers three separate times and got the same results each time... on a clean updated install... 

Any ideas?

---

### Post by tseliot on 2007-08-21
> **digital_exhaust said:**
> Gave it a try and I get...

```
digital@digital-desktop:~$ sudo sh ./ati-driver-installer-8.40.4-x86.x86_64.run
sh: Can't open ./ati-driver-installer-8.40.4-x86.x86_64.run
digital@digital-desktop:~$ 
```

Downloaded the drivers three separate times and got the same results each time... on a clean updated install... 

Any ideas?

the guide says:
```
      Perform the following commands (where <version> is the version number of the installer):

sudo ln -sf bash /bin/sh
bash ./ati-driver-installer-<version>.run --buildpkg Ubuntu/edgy
sudo ln -sf dash /bin/sh
You may need to wait a few mintues for this to complete.

```

therefore you will have to type:
```
sudo ln -sf bash /bin/sh
bash ./ati-driver-installer-8.40.4-x86.x86_64.run --buildpkg Ubuntu/feisty
sudo ln -sf dash /bin/sh
```

---

### Post by kipman725 on 2007-08-21
Hello I installed the latest ATI drivers and they are working well but some of the information in the howto is not correct for all users:
control center works fine on my Pc
I didn't have to do any editing of linux-restricted-moduals-common file to have the latest driver

still don't have AGP DMA in any form working  so performance is still kind of neutered (this is a motherboard issue) but alot better than what I was getting with the apt-get drivers (I don't think they installed properly).  Thanks :D

---

### Post by Dark Star on 2007-08-21
Thanks nice How To will help most of my frnds :D

---

### Post by digital_exhaust on 2007-08-21
> **tseliot said:**
> <snip>

Thank you!!!

---

### Post by Lazai on 2007-08-22
Howdy folks, nice thread so far, it has been a great help. Following the instructions in 2 different wiki articles (clean install between both) and even trying envy as a last ditch effort (again after a clean install) I find myself with the same road block. After the reboot to use fglrx over vesa my system hangs when attempting to load X (at least i think that is where its hanging, going back into my xorg.conf file i can change the device back to vesa and load just fine) I am unable to swap "desktops" ctrl+alt+f1 through f7 don't respond and numlock doesn't toggle (oldschool hardware lock test heh) I had to throw the acpi=off and pnpbios=off into my grub file to get Linux loaded at all (an overload of info is often better than a lack) at this point i am floundering attempting to get this card up and running. below i will list my system specs, and an example of my xorg.conf file (at least the pertinent parts). Any help you kind folks can offer will be greatly appreciated.

Video Card: ATI X1950XTX 512mb PCIe
Display:[22" Viewsonic Flat panel LCD vx2245wm]("http://www.viewsonic.com/products/desktopdisplays/lcddisplays/xseries/vx2245wm/")
MotherBoard: Asus M2R32-MVP
Memory: 4 GB Crucial 667 DDR
CPU: AMD Athlon AM2 64 4800+



```
Section "Monitor"
	Identifier   "VX2245wm"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "Generic Video Card"
	Driver	"vesa"
	Option	"VideoOverlay" "on"
	Option	"OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Generic Video Card"
	Monitor    "VX2245wm"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1680x1050" "1600x1200" "1440x1440" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1680x1050" "1600x1200" "1440x1440" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1680x1050" "1600x1200" "1440x1440" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1680x1050" "1600x1200" "1440x1440" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1680x1050" "1600x1200" "1440x1440" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1680x1050" "1600x1200" "1440x1440" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection



Section "Extensions"
	Option "Composite" "Disable"
EndSection
```

---

### Post by Lazai on 2007-08-22
WOOT! Got it fixed, sadly, that driver has a real big problem with having a second x1950 attached via the crossfire controller cable. removing the second card resolved my issue.

---

### Post by zamolxis on 2007-08-22
I was able to install the .40 drivers, and CCC works fine on my system. I was even able to set up some sort of big_desktop. However, it's not accelerated, the drivers don't seem to be used and big_desktop works strangely. It seems as if each monitor is completely separate. I can move the mouse from one monitor to the other, but I cannot move windows/applications the way I can in Windoze. What gives?

Here's my xorg:```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        Screen         "aticonfig-Screen[1]" RightOf "aticonfig-Screen[0]"
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
EndSection

Section "Files"

        # path to defoma fonts
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/usr/share/fonts/X11/cyrillic"
        FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/Type1"
        FontPath     "/usr/share/fonts/X11/100dpi"
        FontPath     "/usr/share/fonts/X11/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "vbe"
EndSection

Section "ServerFlags"
        Option      "AIGLX" "off"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc104"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ImPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "Monitor"
        Identifier   "Generic Monitor"
        HorizSync    30.0 - 70.0
        VertRefresh  50.0 - 160.0
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[1]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "ATI RADEON 9600XT"
        Driver      "ati"
        VideoRam    131072
        BusID       "PCI:2:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        BusID       "PCI:3:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[1]"
        Driver      "fglrx"
        BusID       "PCI:3:0:0"
        Screen      1
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI RADEON 9600XT"
        Monitor    "Generic Monitor"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[1]"
        Device     "aticonfig-Device[1]"
        Monitor    "aticonfig-Monitor[1]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "Disable"
EndSection

```

glxgears results in 400FPS (very low -> no acceleration)

fglrxinfo:
```
Xlib:  extension "XFree86-DRI" missing on display ":0.1".
Xlib:  extension "XFree86-DRI" missing on display ":0.1".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)



display: :0.0  screen: 1
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

```

---

### Post by MrChips on 2007-08-23
Remove these sections which I have copied from your xorg.conf:

```
Section "Monitor"
        Identifier   "Generic Monitor"
        HorizSync    30.0 - 70.0
        VertRefresh  50.0 - 160.0
        Option      "DPMS"
EndSection

Section "Device"
        Identifier  "ATI RADEON 9600XT"
        Driver      "ati"
        VideoRam    131072
        BusID       "PCI:2:0:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI RADEON 9600XT"
        Monitor    "Generic Monitor"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection


```

For some reason these lines were not deleted when you reconfigured your aticonfig.  This has happened to me before.  Although later on I tried this guide:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

And finally things were all good in ATI land. :)

---

### Post by tseliot on 2007-08-24
> **MrChips said:**
> Although later on I tried this guide:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

And finally things were all good in ATI land. :)

This is the guide I suggest in this thread...

I'm glad it worked for you.

---

### Post by darkpark on 2007-09-03
I'm having a hard time getting the ATI fglrx driver to work with my ati x1950pro AGP.   It *seems* to load fine since I can't find any errors after having combed through the system logs **(cat *|grep fglrx in /var/log)** but every time I boot up Fiesty I get a black screen.   By the way,  I used the restricted driver manager to install/enable the fglrx driver.   I'm back to using the Vesa driver.
As a side note, I originally installed gusty and I had the same results.  I have used err.. tried both the fglrx restricted driver from the ubuntu repositories and the one from ATI ( x86 8.40.0).  I had the same results: black screen.  

please help.   :)

```
I added a snippet from my log(s):
(==) fglrx(0): NoAccel = NO
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000001f
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb7cce000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.34.8
(II) fglrx(0):     Date: Feb 20 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.20-16-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): [pci] find AGP GART
(II) fglrx(0): [agp] Mode=0x1f00421b bridge: 0x10de/0x00e1
(II) fglrx(0): [agp] AGP v1/2 disable mask 0x00000000
(II) fglrx(0): [agp] AGP v3 disable mask   0x00000000
(II) fglrx(0): [agp] enabling AGP with mode=0x1f00431a
(II) fglrx(0): [agp] Remapping MC AGP space (new MCAGPBase = 0xde000000)
(II) fglrx(0): [agp] AGP protocol is enabled for graphics board. (cmd=0x1f004312)
(II) fglrx(0): [agp] graphics chipset has AGP v3.0 (native mode)
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] texture shared area handle = 0x00008000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xe0000000 FBMappedSize: 0x00954000
(II) fglrx(0): FBMM initialized for area (0,0)-(1600,1528)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1600,1200) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1600 x 328
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
```

---

### Post by tseliot on 2007-09-04
> **darkpark said:**
> I'm having a hard time getting the ATI fglrx driver to work with my ati x1950pro AGP.   It *seems* to load fine since I can't find any errors after having combed through the system logs **(cat *|grep fglrx in /var/log)** but every time I boot up Fiesty I get a black screen
can you post the entire log?

---

### Post by darkpark on 2007-09-04
I'm at work now, so I cannot provide the log in its entirety but perhaps I failed to mention that I do get the Ubuntu boot-up screen with the progress indicator.  I'm mentioning it because I have seen some posts that indicate that the blank screen appears immediately after the grub menu.  

By the way, is there another driver that's better than the standard Vesa driver  and will work with the ATI radeon video cards?   I don't need 3d acceleration but I would like something better/faster than the Vesa driver.


```
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux bluebox 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Sep  4 22:15:43 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "SyncMaster"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) Ignoring unrecognized extension "Direct Rendering"
(**) Extension "Composite" is disabled
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,00e1 card 0000,0000 rev a1 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 10de,00e0 card 1458,0c11 rev a2 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,00e4 card 1458,0c11 rev a1 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,00e7 card 1458,5004 rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,00e7 card 1458,5004 rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,00e8 card 1458,5004 rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:08:0: chip 10de,00e5 card 1458,5002 rev a2 class 01,01,8a hdr 00
(II) PCI: 00:0a:0: chip 10de,00e3 card 1458,b002 rev a2 class 01,01,85 hdr 00
(II) PCI: 00:0b:0: chip 10de,00e2 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,00ed card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 1002,7280 card 174b,e250 rev 9a class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,72a0 card 174b,e251 rev 9a class 03,80,00 hdr 00
(II) PCI: 02:08:0: chip 1412,1724 card 1412,3630 rev 01 class 04,01,00 hdr 00
(II) PCI: 02:09:0: chip 1102,0005 card 1102,0021 rev 00 class 04,01,00 hdr 00
(II) PCI: 02:0b:0: chip 11ab,4320 card 1458,e000 rev 13 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:11:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[1] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[2] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[3] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf2000000 - 0xf3ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:14:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[1] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[2] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[3] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xf4000000 - 0xf5ffffff (0x2000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xf6100000 - 0xf61fffff (0x100000) MX[B]
(--) PCI:*(1:0:0) ATI Technologies Inc ATI Radeon X1950 Pro Primary (PCIE) rev 154, Mem @ 0xe0000000/28, 0xf3000000/16, I/O @ 0xa000/8
(--) PCI: (1:0:1) ATI Technologies Inc ATI Radeon X1950 Pro Secondary (PCIE) rev 154, Mem @ 0xf3010000/16
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf0000000 from 0xf1ffffff to 0xefffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xf5400000 - 0xf5403fff (0x4000) MX[B]
	[1] -1	0	0xf5000000 - 0xf51fffff (0x200000) MX[B]
	[2] -1	0	0xf5200000 - 0xf53fffff (0x200000) MX[B]
	[3] -1	0	0xf6004000 - 0xf60040ff (0x100) MX[B]
	[4] -1	0	0xf6003000 - 0xf6003fff (0x1000) MX[B]
	[5] -1	0	0xf6002000 - 0xf6002fff (0x1000) MX[B]
	[6] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[7] -1	0	0xf3010000 - 0xf301ffff (0x10000) MX[B](B)
	[8] -1	0	0xf3000000 - 0xf300ffff (0x10000) MX[B](B)
	[9] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[10] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[11] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[12] -1	0	0x0000b400 - 0x0000b47f (0x80) IX[B]
	[13] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[14] -1	0	0x0000e400 - 0x0000e47f (0x80) IX[B]
	[15] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[16] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[17] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[18] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[19] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[20] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[21] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[22] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[23] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[24] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf5400000 - 0xf5403fff (0x4000) MX[B]
	[1] -1	0	0xf5000000 - 0xf51fffff (0x200000) MX[B]
	[2] -1	0	0xf5200000 - 0xf53fffff (0x200000) MX[B]
	[3] -1	0	0xf6004000 - 0xf60040ff (0x100) MX[B]
	[4] -1	0	0xf6003000 - 0xf6003fff (0x1000) MX[B]
	[5] -1	0	0xf6002000 - 0xf6002fff (0x1000) MX[B]
	[6] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[7] -1	0	0xf3010000 - 0xf301ffff (0x10000) MX[B](B)
	[8] -1	0	0xf3000000 - 0xf300ffff (0x10000) MX[B](B)
	[9] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[10] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[11] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[12] -1	0	0x0000b400 - 0x0000b47f (0x80) IX[B]
	[13] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[14] -1	0	0x0000e400 - 0x0000e47f (0x80) IX[B]
	[15] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[16] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[17] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[18] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[19] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[20] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[21] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[22] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[23] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[24] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf5400000 - 0xf5403fff (0x4000) MX[B]
	[5] -1	0	0xf5000000 - 0xf51fffff (0x200000) MX[B]
	[6] -1	0	0xf5200000 - 0xf53fffff (0x200000) MX[B]
	[7] -1	0	0xf6004000 - 0xf60040ff (0x100) MX[B]
	[8] -1	0	0xf6003000 - 0xf6003fff (0x1000) MX[B]
	[9] -1	0	0xf6002000 - 0xf6002fff (0x1000) MX[B]
	[10] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[11] -1	0	0xf3010000 - 0xf301ffff (0x10000) MX[B](B)
	[12] -1	0	0xf3000000 - 0xf300ffff (0x10000) MX[B](B)
	[13] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[17] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[18] -1	0	0x0000b400 - 0x0000b47f (0x80) IX[B]
	[19] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[20] -1	0	0x0000e400 - 0x0000e47f (0x80) IX[B]
	[21] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[22] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[23] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[24] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[25] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[26] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[27] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[28] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[29] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[30] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.34.8
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.34.8
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.34g1                           
(II) ATI Proprietary Linux Driver Build Date: Feb 20 2007 11:49:19
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.34.1.1.2.3-driver-lnx-x86-x86_64-327152
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x7280) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf5400000 - 0xf5403fff (0x4000) MX[B]
	[5] -1	0	0xf5000000 - 0xf51fffff (0x200000) MX[B]
	[6] -1	0	0xf5200000 - 0xf53fffff (0x200000) MX[B]
	[7] -1	0	0xf6004000 - 0xf60040ff (0x100) MX[B]
	[8] -1	0	0xf6003000 - 0xf6003fff (0x1000) MX[B]
	[9] -1	0	0xf6002000 - 0xf6002fff (0x1000) MX[B]
	[10] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[11] -1	0	0xf3010000 - 0xf301ffff (0x10000) MX[B](B)
	[12] -1	0	0xf3000000 - 0xf300ffff (0x10000) MX[B](B)
	[13] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[17] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[18] -1	0	0x0000b400 - 0x0000b47f (0x80) IX[B]
	[19] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[20] -1	0	0x0000e400 - 0x0000e47f (0x80) IX[B]
	[21] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[22] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[23] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[24] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[25] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[26] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[27] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[28] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[29] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[30] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x81e4c48
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf5400000 - 0xf5403fff (0x4000) MX[B]
	[5] -1	0	0xf5000000 - 0xf51fffff (0x200000) MX[B]
	[6] -1	0	0xf5200000 - 0xf53fffff (0x200000) MX[B]
	[7] -1	0	0xf6004000 - 0xf60040ff (0x100) MX[B]
	[8] -1	0	0xf6003000 - 0xf6003fff (0x1000) MX[B]
	[9] -1	0	0xf6002000 - 0xf6002fff (0x1000) MX[B]
	[10] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[11] -1	0	0xf3010000 - 0xf301ffff (0x10000) MX[B](B)
	[12] -1	0	0xf3000000 - 0xf300ffff (0x10000) MX[B](B)
	[13] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[20] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[21] -1	0	0x0000b400 - 0x0000b47f (0x80) IX[B]
	[22] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e47f (0x80) IX[B]
	[24] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[25] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[26] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[27] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[28] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[29] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[30] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[31] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[32] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[33] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 32, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 32 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS"
(EE) fglrx(0): Weight given (000) is inconsistent with the depth (32)
(EE) fglrx(0): PreInitWeight failed
SetVBEMode failed
(EE) fglrx(0): PreInit failed
(II) fglrx(0): === [atiddxPreInit] === end
(II) UnloadModule: "fglrx"
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules//libvgahw.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

In my particular case, the following two lines seem to be the show stoppers:
EE) fglrx(0): Weight given (000) is inconsistent with the depth (32)
(EE) fglrx(0): PreInitWeight failed

Hmm... so where is this "Weight" supposed to be specified?   In my xorg.conf (posted below), I have a default bit depth.

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

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


Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"SyncMaster"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1600x1200"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1600x1200"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1600x1200"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1600x1200"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1600x1200"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1600x1200"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	32
		Modes		"1600x1200"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "Extensions"
	Option	"Direct Rendering"	"true"
	Option		"Composite"	"false"
EndSection
```

---

### Post by darkpark on 2007-09-05
welps!  I'm happy to say that I **finally** got the dog-gone fglrx driver to work, but I had to use the version 8.38.6 ati driver (from their site: check their archive section).  I also forced x8 agp speed (auto is the default) in my motherboard settings, although I'm not sure if that made a difference.  anyway...
Yippe!!!

For the sake of completion and system comparison....

**CPU:**  AMD Athlon X2 64 4400+
**Video:** Sapphire X1950Pro AGP 512MB
**Audio card**: Creative Labs X-FI xtreme-music
**motherboard:** Gigabyte K8NSC-939  nforce3 250 chipset

correction:
The fglrx driver does seem to work, but DRI doesn't and I MESA is being used for opengl.  

```

(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.34.8
(II) fglrx(0):     Date: Feb 20 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb7cdb000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```

---

### Post by zamolxis on 2007-09-05
> **MrChips said:**
> Remove these sections which I have copied from your xorg.conf:
(...)
And finally things were all good in ATI land. :)

AWESOME!
Thank you, MrChips, I'm finally using the binary drivers.
glxgears gives me 2600-4400 FPS, hope this is normal
can't wait for the overhyped new drivers :)
still couldn't get beryl, etc, but at least now i have a starting point

I can't help but wonder: why was it necessary to remove those lines, what was wrong with them?

tia

---

### Post by another_sam on 2007-09-07
an ATI X1400 will work out of the box on Gutsy Gibbon (ubuntu 7.10)? at least to let me configure the wifi graphically and then, if i want, be able to download a better driver...

thanks

---

### Post by .evan on 2007-09-08
I'm new to linux (first post here) and after a week of tinkering with a dual head set up I finally have two monitors working well.  The only lingering pain in the neck is that I can't drag windows from one monitor to the next.

I posted the relevant parts of my xorg.conf file on my blog along with a few images of the screens in action.

[http://hobbylobby.wordpress.com/2007/09/08/dual-monitors-in-ubuntu-xorgconf-driver-ati-card/](http://hobbylobby.wordpress.com/2007/09/08/dual-monitors-in-ubuntu-xorgconf-driver-ati-card/)

My linux teacher suggested that I post the link to that here to give back to the community after having learned so much from all of you thus far.

 Section “Device”
# Crucial to give each Device a unique ID
Identifier “0 ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)”
Driver “fglrx”
# In my case, there’s only one PCI BusID
Busid “PCI:1:5:0&#8243;
Screen 0
EndSection

Section “Device”
Identifier “1 ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)”
Driver “fglrx”
Busid “PCI:1:5:0&#8243;
Screen 1
EndSection

Section “Monitor”
Identifier “Laptop Monitor”
Option “DPMS”
EndSection

Section “Monitor”
Identifier “Samsung Monitor”
Option “DPMS”
EndSection

Section “Screen”
Identifier “Laptop Screen”
Device “0 ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)”
Monitor “Laptop Monitor”
Defaultdepth 24
SubSection “Display”
Depth 24
# Despite not including any more modes, there are many more options in the GUI
Modes “1680×1050&#8243; “1280×800&#8243;
EndSubSection
EndSection

Section “Screen”
Identifier “Samsung Screen”
Device “1 ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)”
Monitor “Samsung Monitor”
Defaultdepth 24
SubSection “Display”
Depth 24
Modes “1680×1050&#8243;
EndSubSection
EndSection

# Enabling the Xinerama caused problems every time -
# but it sounds like getting that working is the last step
# in having true interacting monitors.

#Section “ServerFlags”
# Option “Xinerama” “true”
# Option “DefaultServerLayout” “DualHead”
#EndSection

Section “ServerLayout”
Identifier “Default Layout”
Screen 0 “Laptop Screen” 0 0
Screen 1 “Samsung Screen” RightOf “Laptop Screen”
# DualHead means two monitors
Option “DualHead” “true”
Inputdevice “Generic Keyboard”
Inputdevice “Configured Mouse”
Inputdevice “stylus” “SendCoreEvents”
Inputdevice “cursor” “SendCoreEvents”
Inputdevice “eraser” “SendCoreEvents”
Inputdevice “Synaptics Touchpad”
EndSection

---

### Post by JoePits on 2007-09-09
> **another_sam said:**
> an ATI X1400 will work out of the box on Gutsy Gibbon (ubuntu 7.10)? at least to let me configure the wifi graphically and then, if i want, be able to download a better driver...

thanks

i used the gutsy daily today and x1400 worked on its own after installing.

---

### Post by kaktuskatta on 2007-09-12
I have the drivers successfully installed, but I'm only able to get the correct info from fgrlxinfo when I run the command as superuser!

when I type fglrxinfo, this comes up:

libGL error: failed to open DRM: Operation not permitted
libGL error: reverting to (slow) indirect rendering
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

when I type sudo fglrxinfo, this comes up:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X600
OpenGL version string: 2.0.6473 (8.37.6)

Same thing with glxgears:

libGL error: failed to open DRM: Operation not permitted
libGL error: reverting to (slow) indirect rendering
1455 frames in 5.2 seconds = 281.140 FPS
1356 frames in 5.5 seconds = 244.854 FPS
1356 frames in 5.3 seconds = 257.310 FPS
1356 frames in 5.2 seconds = 261.399 FPS
1130 frames in 5.0 seconds = 225.353 FPS
X connection to :0.0 broken (explicit kill or server shutdown).

output from sudo glxgears:

11212 frames in 5.0 seconds = 2242.262 FPS
11308 frames in 5.0 seconds = 2257.913 FPS
11302 frames in 5.0 seconds = 2257.020 FPS
11251 frames in 5.0 seconds = 2244.817 FPS
11313 frames in 5.0 seconds = 2257.681 FPS
11256 frames in 5.0 seconds = 2245.015 FPS

Ehh....a huge difference, so I assume that there's a permission issue. Does anybody know where I change this permission, and how?

Thanks in advance

---

### Post by .evan on 2007-09-12
[QUOTE=kaktuskatta;3352756]I have the drivers successfully installed, but I'm only able to get the correct info from fgrlxinfo when I run the command as superuser!

output from sudo glxgears:

11212 frames in 5.0 seconds = 2242.262 FPS
11308 frames in 5.0 seconds = 2257.913 FPS
11302 frames in 5.0 seconds = 2257.020 FPS
11251 frames in 5.0 seconds = 2244.817 FPS
11313 frames in 5.0 seconds = 2257.681 FPS
11256 frames in 5.0 seconds = 2245.015 FPS

I'm new here - so forgive the question if it's obvious to everyone else, but what does
the glxgears have to do with setting up the graphics card drivers?

.evan

---

### Post by kaktuskatta on 2007-09-13
The point is that the openGL setup is not working as it should be, the graphic is lagging, which means that the card is not set up correctly. I need some help with this, and this is the place to ask. Hope this answered your question. P.S: glxgears is a small application that can tell you whether everything is working or not. That's why I posted the FPS from the terminal :)

---

### Post by Thecoldfrost on 2007-09-13
The problem I have isn't that fglrx doesn't work, infact the one I get from "sudo apt-get install" works very well, if a little slowly. The problem I have is installing any driver downloaded from ati's site.

Following guides from this forum, and from cchtml also (or using envy, or just running the .run file), it doesn't matter, the install goes perfectly. however amdcccle doesn't work (I don't know if its meant to work before the first reboot), aticonfig works though. So from default xorg.conf I run aticonfig, and it makes the changes. I restart X or reboot completely.  Following possible fixes from this forum and others just do nothing.

Everything goes nicely, the Ubuntu loading screen comes up, the orange bar moves up, but after than the screen doesn't move to the login screen, rather it "flashes" two shades of black infinately. ctrl+alt+f1 etc don't work. At this point I should point out I have found a thread with exactly the same error, however it was never replies to at all.

I am at my wits end, i thought since 8.40.4 wouldn't work, maybe with all the changes 8.41.7 would. Its exactly the same. I have literarly reinstalled ubuntu as many times as there are drivers, since using one from ati.com stops me being able to reinstall the one on the repositories. (The number of reinstalls is x2 because I tried, and am still on 32bit now, whereas I was using 64bit)

It isn't a problem with xorg.conf. I have tried the same xorg.conf I am using now, with any other driver version and above problem occurs. Unless its a refresh rate issue, which I tried to play about with, but I don't know if I had it right for my screen.

Is there something different about the repositories driver from ati.com's?

Could it be that the card isn't being detected correctly? 

My system is:
Athlon x2 3800+
1.5gb ram
sapphire x1950pro 512mb agp
Abit AV8-3rd eye
Sound Blaster Audigy SE
Sony SDM-HS75P Monitor (1280x1024 @ 75hz)

The reason I want to install from ATI's site, is because I would like catalyst control center. Its not so bad for gaming with the driver already installed, everything works fine, only a little slower than I used to play them. I don't really like to ask for help, I prefer to persevere with something untill I fix it, but this is beyond me. 

In summary -> Having tryed both ubuntu 32bit and 64bit the only fglrx driver I can install is the one from apt-get. Any from ati.com will boot me into a screen flashing between two shades of black. I am 99% sure its something I am doing wrong, as I refuse to believe the problem can be so persistant as going though so many driver releases.

---

### Post by Harry789 on 2007-09-13
I used envy and get

laan97ac@laan97ac-laptop:~$ glxgears
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
3755 frames in 5.0 seconds = 744.296 FPS
3840 frames in 5.0 seconds = 762.530 FPS
3840 frames in 5.0 seconds = 761.791 FPS
3840 frames in 5.1 seconds = 760.374 FPS

How do I fix the DRI thing?

Actually I had higher FPS before install (ATI radeon x600)

---

### Post by Harry789 on 2007-09-13
ok here is part of my problem:

laan97ac@laan97ac-laptop:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

---

### Post by tonbuntu on 2007-09-15
I have the x300 card and the following problems:

In Feisty, when using the open source driver, the resolution is correct 1280 x 1024, but the refresh rate isn't (60 instead of 70) and Compiz works;

When using the proprietary driver, the resolution and refresh rate are correct, but Compiz doesn't work ("extension not available").

Can't I just quickly somehow manually change the refresh rate for the open source driver (I like to use Compiz)?

Thanks
Tony

---

### Post by Proteasome on 2007-09-15
Total noob, just installed feisty, have RV350 (see below)

simon@Macrophallus:~$ lspci | grep
VGA01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]

I followed the posted guide to the letter, including the troubleshooting section, but still have
the same problem with Mesa: 

simon@Macrophallus:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

Trying to enable 3d rendering, install compiz, but can't get past this. Any suggestions highly appreciated.

---

### Post by bootsbradford on 2007-09-15
I have tried to install the ATI driver but something is not working. 

The command 'fglrxinfo' returns the following info:
> display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)


Can anyone help? I've read around a bit but just ended up confused as to why I still can't get the ATI info displayed. :(

---

### Post by Harry789 on 2007-09-17
bootsbradford, I have the exact same problem as you.

---

### Post by mjpolifka on 2007-09-18
On a fresh install, I downloaded the newest version (8.40), ran 

sudo sh ./ati-driver-installer-8.40.4-x86.x86_64.run
sudo aticonfig --initial --force

rebooted, and now everything works.  I have been messing around with the Binary HOWTO for a week and searching Google for an answer, but this simple solution is the only one that worked for me, and to be honest I'm not sure why.  Before I did this, DRI was not found and I had no direct rendering.

Card: Radeon X1650 PRO AGP 512MB
Intel P4 2.66GHz 2.5GB Memory
Getting ~1500FPS

---

### Post by bootsbradford on 2007-09-18
> **mjpolifka said:**
> 
sudo aticonfig --initial --force


At last! This is the command that did the job for me. Again, not sure why I've read pages and pages of wiki instructions but this was never proposed.

Anyway, this is the answer for me. Thanks, mjpolifka! Harry789, I wonder if this will do the job for you as well? :)

---

### Post by HokeyFry on 2007-09-19
i have the the ATI driver successfully installed, but i need 3d accelleration enabled. how do i do this?

if this helps, this is what 'lspci' returns about my card

```
VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
```

thanks in advance for any help

---

### Post by pdusen on 2007-09-20
Help me! I am an HD 2900 owner who drifted off Linux for a while when I upgraded cards, but I am trying to get back into it now that 8.41 is available. But no matter what I do or what guide I follow, I am absolutely unable to get the driver to set up properly! It consistently fails to load X whenever I reboot after installing. I have to keep reverting to my backup.

Does anybody have a method that they know for a fact works with this card and driver?

---

### Post by Lolo Uila on 2007-09-23
Okay, I've run older ATI cards under Linux before, and while the fglrx driver has never been easy to set up I have been successful... until now. :(

I am trying to get a Radeon X1950 Pro AGP card running in Feisty and I've been beating on this thing for over a week now. I have tried the last 4 or 5 driver versions as well as the one in the Ubuntu restricted repositories and I just can't get it to work.

After installing any driver version I either boot into the Linux (gnome) desktop, but fglrxinfo says mesa, or I get a black screen and hard locked computer (have to use the reset button to reboot). I have tried the guide here; I have tried envy, and I've tried both the install and trouble shooting guides below:

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)
[http://wiki.cchtml.com/index.php/Troubleshooting](http://wiki.cchtml.com/index.php/Troubleshooting)

I have googled around and found loads of hits about the "ATI Black Screen of Death" for people running Athlon 64 hardware on 64 bit Linux, but I'm running 32 bit on Intel hardware (although I tried those fixes as well with no results).

System specs:
Shuttle fb75 motherboard (Intel 875P chipset) on-board sound and Ethernet
Intel P4 3.4GHz (not overclocked currently)
2GB OCZ Platinum PC3200 RAM (2-3-2-5)
Diamond MM Radeon X1950 Pro AGP 8X (512MB)
ATI HD TV Wonder tuner card
Seagate 750GB IDE HD
Pioneer DVR-111D IDE DVD burner
2x100GB Hitachi SATA HD (RAID-0)
Shuttle (Prism) USB WiFi adapter
Mitsumi FA404M combination floppy drive & 8-in-1 card reader

I've got XP Pro and Linux Mint Celena (Ubuntu Feisty) dual booting from the RAID volume and the X1950 card works perfectly under Winblows. In Linux, however, only the vesa driver works.

I'm beginning to think the ATI driver doesn't support the AGP X1k cards (which are actually PCI-E cards with a bridge chip). Can anyone tell me if these cards are supported?

If they are then I need help to get this thing going. I know a lot about computer hardware, and I'm familiar enough with Linux to work in the terminal. Are there any logs I can look in to figure out what's locking the system, or why fglrx isn't loading?

Thanks a bunch for any help anyone can offer!

Aloha, Tim

---

### Post by Yellow Pasque on 2007-09-23
Lolo Uila:

Try looking at var/log/Xorg.0.log (it's something like this, do an ls to get the correct filename).

Then, look in your /etc/X11/xorg.conf file to see if it's set up correctly. Also, make sure the bus ID of your vid card matches the output of lspci -v (you can do a sudo update-pciids to get the right name strings).

---

### Post by Lolo Uila on 2007-09-23
There are no (EE) error entries in the log.  Then again, I am hard locking before X fully starts, so it's possible the error is not logged before the system hangs.

There is something interesting in the log however...

```
(--) PCI:*(1:0:0) ATI Technologies Inc ATI Radeon X1950 Pro Primary (PCIE) rev 0, Mem @ 0xe0000000/28, 0xfc030000/16, I/O @ 0xc000/8
(--) PCI: (1:0:1) ATI Technologies Inc ATI Radeon X1950 Pro Secondary (PCIE) rev 0, Mem @ 0xfc020000/16

(--) fglrx(0): VideoRAM: 262144 kByte, Type: DDR3
(II) fglrx(0): PCIE card detected
```

It seems my AGP card is being detected as PCI-E, and only half of the 512MB of video RAM is detected. Odd?

The end of the log looks like:

```
(II) fglrx(0): Acceleration enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
```
So it looks like fglrx is loading alright, but something is crashing X and hard locking the system.

Any ideas?

Thanks, Tim

---

### Post by Lolo Uila on 2007-09-24
Okay, I'm back to an install that I can boot, but mesa is being used instead of fglrx.

/var/log/Xorg.0.log now shows some (EE) error & (WW) warning messages:

```
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.13
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RV570
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
[COLOR="Red"][I]drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed[/I][/COLOR]
[B][drm] failed to load kernel module "fglrx"
(WW) fglrx(0): Failed to open DRM connection[/B]
(--) fglrx(0): VideoRAM: 262144 kByte, Type: DDR3
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
```
Looked in /dev/dri/ and there is no card0 device defined (the /dev/dri/ path is empty).

```
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 128 MB
**(WW) fglrx(0): No DRM connection for driver fglrx.**
```
```
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
**[COLOR="Red"](EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized.[/COLOR]**
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
```
I looked for any entries with GPS in them and found nothing.

Currently **lsmod | grep fglrx** returns nothing

**fglrxinfo** returns:
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

**glxinfo | grep vendor** returns:
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
server glx vendor string: SGI
client glx vendor string: ATI
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)

So, did I find anything useful?

Thanks again for any help!!

Aloha, Tim

---

### Post by Lolo Uila on 2007-09-24
So basically it looks like whenever fglrx loads without errors (well, without logged errors) I get hard locked when X is started.

I get all the boot messages and the loading stuff, but it hangs right when I'd expect the Gnome login screen to appear. At that point my screen is black, but my monitor detects a signal on whatever port I have it plugged into and it doesn't go into power save mode. It seems like the card is actually sending a black screen to the display. I have tried both ports with both DVI and Analog connections and the results are the same.

The system is hard locked as far as I can tell. Typing in my login info gets me nowhere (no login sounds or change to the black screen). Trying to exit to the shell with ctrl+alt+f1 does nothing. Hitting ctrl+alt+delete does make the hard drive busy light flash a few times, but nothing happens. No shutdown or reboot.

[sigh] I'd really like to get this working because there isn't an acceptable nVidia card to substitute. The only AGP card that offers comparable performance is the XFX 7950GT, which would cost me over $250, and has a very notorious reputation for failing due to inadequate cooling and generally poor design.

Thanks again. If there are any other logs or info needed just let me know.

Aloha, Tim

---

### Post by fizz on 2007-09-25
to the people having problems with Mesa GLX, i was having this problem to.

The first thing i checked was from a command line CTRL/ALT/F1
sudo modprobe fglrx

In my case, after i ran envy, there was no created fglrx.ko, so I had to run envy again from command line (sudo envy -t) and install ati driver again, i said no to config, no to reboot

I then sudo modprobe fglrx
No errors this time, i did startx opened terminal glxinfo to verify that it was the ATI driver, logged out, and started GDM and evertything is cool now. I hope this made some sort of sense.

---

### Post by hoborocket on 2007-09-27
Both Envy and the instructions on the wiki there just break my xorg. :( I'm out of options, really.

[http://ubuntuforums.org/showthread.php?p=3433396#post3433396](http://ubuntuforums.org/showthread.php?p=3433396#post3433396)

---

### Post by Juleshu on 2007-09-27
I tried this method:
Instructions for 7.04 (Feisty)
Note: If you use Kubuntu then follow the instructions for 6.10 (Edgy)-- 

* Install linux-restricted-modules and restricted-manager provied in the restricted repositories: 

sudo apt-get update 
sudo apt-get install linux-restricted-modules-generic restricted-managerOpen the restricted drivers manager included in 7.04 "System -> Administration -> Restricted Drivers Manager" and select "ATI accelerated graphics driver". This will hopefully enable fglrx in a painless way. If not, follow the instructions for Edgy. 




And I get the message "failed to start the x server" when I restart. 

I have the newest 64bit ubuntu (Q6600) and an ATI 2600xt.

I just reinstalled ubuntu (It only takes 15 minutes on the Q6600), what should I try next?

Somewhere online I found this: sudo dpkg-reconfigure xserver-xorg -phigh
Will this command work to fix things if it happens again so I do not have to reinstall?

I just completely erased vista 64bit off of my PC. I just did not like it. I'd like to get ubuntu up and running properly so I can use dual monitors, otherwise I'm going back to windows XP for a bit. 


Thanks in advance for any assistance. I'm a linux newb, but my first PC was a 386 running dos, so I'm picking up the basics pretty quickly.

---

### Post by Juleshu on 2007-09-27
I installed and ran Envy and I got the same problem.

---

### Post by Juleshu on 2007-09-27
I got it to work. I used the method in this thread for those who are having trouble:
[http://forums.scotsnewsletter.com/index.php?showtopic=19436&st=0](http://forums.scotsnewsletter.com/index.php?showtopic=19436&st=0)

---

### Post by kaktuskatta on 2007-10-02
I've finally figured out how to solve the DRI-problem. The problem I had were related to lack of permissions, which lead to loading of the softwarebased slow and indirect rendering from the MESA drivers. I solved the problem by editing /etc/X11/xorg.conf, and at the end of this file add the following strings: 

#allows anyone to access DRI settings
Section "DRI"
    Mode  0666
EndSection

And that's it! When I type fglrxinfo in the terminal now, I get: 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X600
OpenGL version string: 2.0.6747 (8.40.4)

glxgears gives:

21108 frames in 5.0 seconds = 4221.464 FPS
28122 frames in 5.0 seconds = 5624.303 FPS
27651 frames in 5.0 seconds = 5530.020 FPS
27569 frames in 5.0 seconds = 5513.712 FPS
28012 frames in 5.0 seconds = 5602.231 FPS

etc etc etc......

And that's all! Hope this helped somebody else but me :) 

Enjoy! :guitar:

---

### Post by nixie21 on 2007-10-02
Trying to do this now with my radeon 9600

got this error

 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/feisty
./packages/Ubuntu/ati-packager.sh: line 58: dpkg-architecture: command not found
Error: unsupported architecture: 
Removing temporary directory: fglrx-install.Qw9332
nixie21@Main:~/Desktop$ 


Any ideas?

---

### Post by nixie21 on 2007-10-02
All good now...fixed...

---

### Post by Lolo Uila on 2007-10-04
Umm nixie21, that's not fixed. Your flgrxinfo output should say ATI for the driver, not tungsten and mesa.

---

### Post by nixie21 on 2007-10-04
nixie21@Main:~$ glxinfo | grep vendorserver glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.


Hmm, what do i do???

---

### Post by haemphyst on 2007-10-08
SWEET!!!  Worked like a champ on the X1550 256MB PCI-e card!  Ubuntu 6.06LTS  (Dapper?)

Once I figured out how to navigate the directory paths in the terminal...  And figured out that directory names are case sensitive...  And two reboots later...  And realizing that 75Hz on the DVI was too high a refresh rate for my older (only 2 and a half years, sad...  "older"...  sheesh!) LCD...

:KS:KS:KS  Three gold stars for Dave!  BWAHAHAHA

Seriously, though, thanks!  Now, to tackle Beryl.

---

### Post by mgazb on 2007-10-09
I'm really struggling getting the acceleration going on a RV280 (Radeon 9200 PRO) card with my Feisty  system.
It runs with the Driver set to "ATI", but if I set it to "fglrx" I can't start X. 
I have tried using the restricted driver manager (both command line and from the toolbar)  and it says "No hardware that needs restricted drivers present"/

My xorg.conf after running
```

aticonfig --initial
aticonfig --overlay-type=Xv

```
reads as follows
```


# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Sep 12 14:29:35 PDT 2007
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "gb"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "SyncMaster"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "nVidia Corporation NV34 [GeForce FX 5200]"
	Driver      "nvidia"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
        Option      "BusType" "PCI"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "nVidia Corporation NV34 [GeForce FX 5200]"
	Monitor    "SyncMaster"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

The Xorg.0.log from this is 
```



X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux q-console 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Oct  9 09:33:06 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig-Screen[0]" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]"
(**) |   |-->Device "aticonfig-Device[0]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,0204 card 1106,0204 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 1106,1204 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:2: chip 1106,2204 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:3: chip 1106,3204 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:4: chip 1106,4204 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:7: chip 1106,7204 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b188 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:0f:0: chip 1106,0571 card 1458,5002 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1458,5004 rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1458,5004 rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1458,5004 rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3038 card 1458,5004 rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:4: chip 1106,3104 card 1458,5004 rev 86 class 0c,03,20 hdr 80
(II) PCI: 00:11:0: chip 1106,3227 card 1458,5001 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:5: chip 1106,3059 card 1458,a002 rev 60 class 04,01,00 hdr 00
(II) PCI: 00:13:0: chip 10ec,8139 card 1458,e000 rev 10 class 02,00,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 1002,5960 card 1002,5960 rev 01 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,5940 card 1002,5961 rev 01 class 03,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[1] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[2] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[3] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe2000000 - 0xe3ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc RV280 [Radeon 9200 PRO] rev 1, Mem @ 0xd0000000/27, 0xe3000000/16, I/O @ 0xc000/8
(--) PCI: (1:0:1) ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) rev 1, Mem @ 0xd8000000/27, 0xe3010000/16
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe1ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe4001000 - 0xe40010ff (0x100) MX[B]
	[1] -1	0	0xe4000000 - 0xe40000ff (0x100) MX[B]
	[2] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[3] -1	0	0xe3010000 - 0xe301ffff (0x10000) MX[B](B)
	[4] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[5] -1	0	0xe3000000 - 0xe300ffff (0x10000) MX[B](B)
	[6] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[7] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[8] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[9] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[10] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[11] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[12] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[13] -1	0	0x0000d000 - 0x0000d00f (0x10) IX[B]
	[14] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe4001000 - 0xe40010ff (0x100) MX[B]
	[1] -1	0	0xe4000000 - 0xe40000ff (0x100) MX[B]
	[2] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[3] -1	0	0xe3010000 - 0xe301ffff (0x10000) MX[B](B)
	[4] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[5] -1	0	0xe3000000 - 0xe300ffff (0x10000) MX[B](B)
	[6] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[7] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[8] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[9] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[10] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[11] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[12] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[13] -1	0	0x0000d000 - 0x0000d00f (0x10) IX[B]
	[14] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe4001000 - 0xe40010ff (0x100) MX[B]
	[5] -1	0	0xe4000000 - 0xe40000ff (0x100) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xe3010000 - 0xe301ffff (0x10000) MX[B](B)
	[8] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[9] -1	0	0xe3000000 - 0xe300ffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[14] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[15] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[16] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[17] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[18] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[19] -1	0	0x0000d000 - 0x0000d00f (0x10) IX[B]
	[20] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.34.8
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.34.8
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.34g1                           
(II) ATI Proprietary Linux Driver Build Date: Feb 20 2007 11:49:19
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.34.1.1.2.3-driver-lnx-x86-x86_64-327152
(--) Assigning device section with no busID to primary device
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(EE) No devices detected.

Fatal server error:
no screens found

```

---

### Post by mgazb on 2007-10-10
I can get the graphics card working using the "ati" driver, but this does all the rendering in software on the host. I'm trying to get the hardware acceleration working.
8.28 is the last version of fglrx for this hardware. I can't build it out of the box for 7.04 as this driver doesn't have an option for Feisty. If I try to build it for Edgy, I get errors in the driver code that I can't easily resolve.

---

### Post by chikin03 on 2007-10-10
I'm having the same problem, mgazb.  Radeon 8500 is apparently "pre-r200", and so 8.40 ATI drivers are not out (only a set which apparently supports 7.1).  When I try to install them, the screen gets garbled on bootup, and even ctrl-shift-bkspc doesn't get me to a command-line.  I have to boot up recovery, change back xorg.conf, and try again...  Only error on log is No Device Detected.

To be honest, I'm not sure I need these drivers.  I want Ubuntu for productive stuff...and for MythTV.  Now, from what I'd recalled from Edgy, I thought I needed fglrx [and in fact, when I thought I had installed MythTV with my PVR-150, all I got out of the tuner was a black, blank screen--whereas it certainly works in XP].  Does anyone know otherwise?  Mythfrontend won't even start up again, because of some libGL.so error.  I don't mind completely reformatting, I just hate to do it without any sense of direction as to where I should go now.  

Is the solution just to buy a $25 nvidia card?

---

### Post by chikin03 on 2007-10-10
Update: got it to work.  Just had to remove the ati drivers, I think.  In answer to my question, hardware acceleration is not needed to run mythtv.  I guess I'll never have compiz/beryl though.

---

### Post by Tzimbar on 2007-10-13
As far as I can understand, new kernels (2.6.20 or newer) are not supported by the "old" ATI 8.28.8 drivers... :(
So, if we want to use Feisty and OpenGL, we will have to use open source drivers (which have the sadly famous bug causing the entire system to hang when an OpenGL application is run...) :(

---

### Post by Sim777 on 2007-10-13
After searching for 2 days and going through many guides, I'm stuck. I'm rather new to linux, so please treat me kindly. 
I have basic Inspiron 1501 with dreaded ATI Xpress card. After following one guide, I got blackscreen. After fixing that using liveCD, and trying another guide, I have following problem.


\[PHP]fglrxinfo
fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
[/PHP]


Here's Xorg.0.log

```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux sim-laptop 2.6.20-16-generic #2 SMP Sun Sep 23 18:31:23 UTC 2007 x86_64
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Oct 13 15:45:37 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig-Screen[0]" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]"
(**) |   |-->Device "aticonfig-Device[0]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "AIGLX" "off"
(**) Extension "Composite" is disabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7a16e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1002,5950 card 1028,01f5 rev 10 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1002,5a3f card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:05:0: chip 1002,5a37 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:06:0: chip 1002,5a38 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:12:0: chip 1002,4380 card 1028,01f5 rev 00 class 01,06,01 hdr 00
(II) PCI: 00:13:0: chip 1002,4387 card 1028,01f5 rev 00 class 0c,03,10 hdr 80
(II) PCI: 00:13:1: chip 1002,4388 card 1028,01f5 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:2: chip 1002,4389 card 1028,01f5 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:3: chip 1002,438a card 1028,01f5 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:4: chip 1002,438b card 1028,01f5 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:5: chip 1002,4386 card 1028,01f5 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:14:0: chip 1002,4385 card 1028,01f5 rev 13 class 0c,05,00 hdr 80
(II) PCI: 00:14:1: chip 1002,438c card 1028,01f5 rev 00 class 01,01,8a hdr 00
(II) PCI: 00:14:2: chip 1002,4383 card 1028,01f5 rev 00 class 04,03,00 hdr 00
(II) PCI: 00:14:3: chip 1002,438d card 1028,01f5 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:14:4: chip 1002,4384 card 0000,0000 rev 00 class 06,04,01 hdr 81
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:05:0: chip 1002,5975 card 1028,01f5 rev 00 class 03,00,00 hdr 00
(II) PCI: 05:00:0: chip 14e4,4311 card 1028,0007 rev 01 class 02,80,00 hdr 00
(II) PCI: 08:00:0: chip 14e4,170c card 1028,01f5 rev 02 class 02,00,00 hdr 00
(II) PCI: 08:01:0: chip 1180,0822 card 1028,01f5 rev 19 class 08,05,00 hdr 80
(II) PCI: 08:01:1: chip 1180,0843 card 1028,01f5 rev 01 class 08,80,00 hdr 80
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,8), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xc0100000 - 0xc01fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:5:0), (0,2,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:6:0), (0,5,7), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xc0200000 - 0xc02fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:20:3), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 8: bridge is at (0:20:4), (0,8,10), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 8 non-prefetchable memory range:
	[0] -1	0	0xc0300000 - 0xc03fffff (0x100000) MX[B]
(--) PCI:*(1:5:0) ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP] rev 0, Mem @ 0xc8000000/27, 0xc0100000/16, I/O @ 0x9000/8
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xc0302400 - 0xc03024ff (0x100) MX[B]
	[1] -1	0	0xc0302000 - 0xc03020ff (0x100) MX[B]
	[2] -1	0	0xc0300000 - 0xc0301fff (0x2000) MX[B]
	[3] -1	0	0xc0200000 - 0xc0203fff (0x4000) MX[B]
	[4] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[5] -1	0	0xc0004800 - 0xc0004bff (0x400) MX[B]
	[6] -1	0	0xc0004400 - 0xc00044ff (0x100) MX[B]
	[7] -1	0	0xc0009000 - 0xc0009fff (0x1000) MX[B]
	[8] -1	0	0xc0008000 - 0xc0008fff (0x1000) MX[B]
	[9] -1	0	0xc0007000 - 0xc0007fff (0x1000) MX[B]
	[10] -1	0	0xc0006000 - 0xc0006fff (0x1000) MX[B]
	[11] -1	0	0xc0005000 - 0xc0005fff (0x1000) MX[B]
	[12] -1	0	0xc0004000 - 0xc00043ff (0x400) MX[B]
	[13] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[14] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[15] -1	0	0x00008420 - 0x0000842f (0x10) IX[B]
	[16] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[17] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[18] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[21] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[22] -1	0	0x00008450 - 0x00008453 (0x4) IX[B]
	[23] -1	0	0x00008430 - 0x00008437 (0x8) IX[B]
	[24] -1	0	0x00008454 - 0x00008457 (0x4) IX[B]
	[25] -1	0	0x00008438 - 0x0000843f (0x8) IX[B]
	[26] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xc0302400 - 0xc03024ff (0x100) MX[B]
	[1] -1	0	0xc0302000 - 0xc03020ff (0x100) MX[B]
	[2] -1	0	0xc0300000 - 0xc0301fff (0x2000) MX[B]
	[3] -1	0	0xc0200000 - 0xc0203fff (0x4000) MX[B]
	[4] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[5] -1	0	0xc0004800 - 0xc0004bff (0x400) MX[B]
	[6] -1	0	0xc0004400 - 0xc00044ff (0x100) MX[B]
	[7] -1	0	0xc0009000 - 0xc0009fff (0x1000) MX[B]
	[8] -1	0	0xc0008000 - 0xc0008fff (0x1000) MX[B]
	[9] -1	0	0xc0007000 - 0xc0007fff (0x1000) MX[B]
	[10] -1	0	0xc0006000 - 0xc0006fff (0x1000) MX[B]
	[11] -1	0	0xc0005000 - 0xc0005fff (0x1000) MX[B]
	[12] -1	0	0xc0004000 - 0xc00043ff (0x400) MX[B]
	[13] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[14] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[15] -1	0	0x00008420 - 0x0000842f (0x10) IX[B]
	[16] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[17] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[18] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[21] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[22] -1	0	0x00008450 - 0x00008453 (0x4) IX[B]
	[23] -1	0	0x00008430 - 0x00008437 (0x8) IX[B]
	[24] -1	0	0x00008454 - 0x00008457 (0x4) IX[B]
	[25] -1	0	0x00008438 - 0x0000843f (0x8) IX[B]
	[26] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc0302400 - 0xc03024ff (0x100) MX[B]
	[5] -1	0	0xc0302000 - 0xc03020ff (0x100) MX[B]
	[6] -1	0	0xc0300000 - 0xc0301fff (0x2000) MX[B]
	[7] -1	0	0xc0200000 - 0xc0203fff (0x4000) MX[B]
	[8] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[9] -1	0	0xc0004800 - 0xc0004bff (0x400) MX[B]
	[10] -1	0	0xc0004400 - 0xc00044ff (0x100) MX[B]
	[11] -1	0	0xc0009000 - 0xc0009fff (0x1000) MX[B]
	[12] -1	0	0xc0008000 - 0xc0008fff (0x1000) MX[B]
	[13] -1	0	0xc0007000 - 0xc0007fff (0x1000) MX[B]
	[14] -1	0	0xc0006000 - 0xc0006fff (0x1000) MX[B]
	[15] -1	0	0xc0005000 - 0xc0005fff (0x1000) MX[B]
	[16] -1	0	0xc0004000 - 0xc00043ff (0x400) MX[B]
	[17] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[18] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00008420 - 0x0000842f (0x10) IX[B]
	[22] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[23] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[24] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[27] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[28] -1	0	0x00008450 - 0x00008453 (0x4) IX[B]
	[29] -1	0	0x00008430 - 0x00008437 (0x8) IX[B]
	[30] -1	0	0x00008454 - 0x00008457 (0x4) IX[B]
	[31] -1	0	0x00008438 - 0x0000843f (0x8) IX[B]
	[32] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(**) AIGLX disabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.41.7
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) Primary Device is: PCI 01:05:0
(II) ATI Proprietary Linux Driver Version Identifier:8.41.7
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.413.1                  
(II) ATI Proprietary Linux Driver Build Date: Sep  7 2007 22:36:05
(--) Assigning device section with no busID to primary device
(--) Chipset Supported AMD Graphics Processor (0x5975) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc0302400 - 0xc03024ff (0x100) MX[B]
	[5] -1	0	0xc0302000 - 0xc03020ff (0x100) MX[B]
	[6] -1	0	0xc0300000 - 0xc0301fff (0x2000) MX[B]
	[7] -1	0	0xc0200000 - 0xc0203fff (0x4000) MX[B]
	[8] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[9] -1	0	0xc0004800 - 0xc0004bff (0x400) MX[B]
	[10] -1	0	0xc0004400 - 0xc00044ff (0x100) MX[B]
	[11] -1	0	0xc0009000 - 0xc0009fff (0x1000) MX[B]
	[12] -1	0	0xc0008000 - 0xc0008fff (0x1000) MX[B]
	[13] -1	0	0xc0007000 - 0xc0007fff (0x1000) MX[B]
	[14] -1	0	0xc0006000 - 0xc0006fff (0x1000) MX[B]
	[15] -1	0	0xc0005000 - 0xc0005fff (0x1000) MX[B]
	[16] -1	0	0xc0004000 - 0xc00043ff (0x400) MX[B]
	[17] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[18] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00008420 - 0x0000842f (0x10) IX[B]
	[22] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[23] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[24] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[27] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[28] -1	0	0x00008450 - 0x00008453 (0x4) IX[B]
	[29] -1	0	0x00008430 - 0x00008437 (0x8) IX[B]
	[30] -1	0	0x00008454 - 0x00008457 (0x4) IX[B]
	[31] -1	0	0x00008438 - 0x0000843f (0x8) IX[B]
	[32] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x7c4850
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc0302400 - 0xc03024ff (0x100) MX[B]
	[5] -1	0	0xc0302000 - 0xc03020ff (0x100) MX[B]
	[6] -1	0	0xc0300000 - 0xc0301fff (0x2000) MX[B]
	[7] -1	0	0xc0200000 - 0xc0203fff (0x4000) MX[B]
	[8] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[9] -1	0	0xc0004800 - 0xc0004bff (0x400) MX[B]
	[10] -1	0	0xc0004400 - 0xc00044ff (0x100) MX[B]
	[11] -1	0	0xc0009000 - 0xc0009fff (0x1000) MX[B]
	[12] -1	0	0xc0008000 - 0xc0008fff (0x1000) MX[B]
	[13] -1	0	0xc0007000 - 0xc0007fff (0x1000) MX[B]
	[14] -1	0	0xc0006000 - 0xc0006fff (0x1000) MX[B]
	[15] -1	0	0xc0005000 - 0xc0005fff (0x1000) MX[B]
	[16] -1	0	0xc0004000 - 0xc00043ff (0x400) MX[B]
	[17] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[18] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x00008420 - 0x0000842f (0x10) IX[B]
	[25] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[26] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[27] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[30] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[31] -1	0	0x00008450 - 0x00008453 (0x4) IX[B]
	[32] -1	0	0x00008430 - 0x00008437 (0x8) IX[B]
	[33] -1	0	0x00008454 - 0x00008457 (0x4) IX[B]
	[34] -1	0	0x00008438 - 0x0000843f (0x8) IX[B]
	[35] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[36] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[37] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): PCI bus 1 card 5 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "ATI Radeon Xpress Series" (Chipset = 0x5975)
(--) fglrx(0): (PciSubVendor = 0x1028, PciSubDevice = 0x01f5)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc8000000
(--) fglrx(0): MMIO registers at 0xc0100000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI Radeon® Xpress 1150    
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: MS48
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.41.7
	ABI class: X.Org Server Extension, version 0.3
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) fglrx(0): Connected Display1: LCD on internal LVDS [lvds]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: AUO  Model: 1c74  Serial#: 0
(II) fglrx(0): Year: 2005  Week: 1
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 33  vert.: 21
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.600 redY: 0.350   greenX: 0.310 greenY: 0.550
(II) fglrx(0): blueX: 0.155 blueY: 0.115   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) fglrx(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1440 h_border: 0
(II) fglrx(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 823 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 59.3 MHz   Image Size:  331 x 207 mm
(II) fglrx(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1440 h_border: 0
(II) fglrx(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 823 v_border: 0
(II) fglrx(0):  FF059
(II) fglrx(0):  0AMWx€Ìø
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff0006af741c00000000
(II) fglrx(0): 	010f0103802115780aa7e599594f8c27
(II) fglrx(0): 	1d505400000001010101010101010101
(II) fglrx(0): 	010101010101c71b00a0502017301520
(II) fglrx(0): 	44004bcf10000018261700a050201730
(II) fglrx(0): 	152044004bcf10000000000000fe0046
(II) fglrx(0): 	463035390042313534455731000000fe
(II) fglrx(0): 	0030414d5778a4ccf801010a202000e9
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay version 3.  2 power states available:
(II) fglrx(0):   1. 401/401MHz @ 60Hz []
(II) fglrx(0):   2. 100/133MHz @ 60Hz [low voltage]
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 13 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x800 (pitch 0)
(**) fglrx(0): *Mode "1280x800": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"   71.11  1280 1296 1328 1440  800 804 808 823
(**) fglrx(0): *Mode "1280x768": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"   71.11  1280 1296 1328 1440  768 788 792 823
(**) fglrx(0): *Mode "1024x768": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   71.11  1024 1168 1200 1440  768 788 792 823
(**) fglrx(0): *Mode "848x480": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   71.11  848 1080 1112 1440  480 644 648 823
(**) fglrx(0): *Mode "800x600": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   71.11  800 1056 1088 1440  600 704 708 823
(**) fglrx(0): *Mode "720x480": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   71.11  720 1016 1048 1440  480 644 648 823
(**) fglrx(0): *Mode "640x480": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   71.11  640 976 1008 1440  480 644 648 823
(**) fglrx(0):  Default mode "640x400": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   71.11  640 976 1008 1440  400 604 608 823
(**) fglrx(0):  Default mode "640x350": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x350"   71.11  640 976 1008 1440  350 579 583 823
(**) fglrx(0):  Default mode "512x384": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   71.11  512 912 944 1440  384 596 600 823
(**) fglrx(0):  Default mode "400x300": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   71.11  400 856 888 1440  300 704 708 823 doublescan
(**) fglrx(0):  Default mode "320x240": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   71.11  320 816 848 1440  240 644 648 823 doublescan
(**) fglrx(0):  Default mode "320x200": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   71.11  320 816 848 1440  200 604 608 823 doublescan
(--) fglrx(0): Display dimensions: (330, 210) mm
(--) fglrx(0): DPI set to (98, 96)
(--) fglrx(0): Virtual size is 1280x800 (pitch 1280)
(**) fglrx(0): *Mode "1280x800": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"   71.11  1280 1296 1328 1440  800 804 808 823
(**) fglrx(0): *Mode "1280x768": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"   71.11  1280 1296 1328 1440  768 788 792 823
(**) fglrx(0): *Mode "1024x768": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   71.11  1024 1168 1200 1440  768 788 792 823
(**) fglrx(0): *Mode "848x480": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   71.11  848 1080 1112 1440  480 644 648 823
(**) fglrx(0): *Mode "800x600": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   71.11  800 1056 1088 1440  600 704 708 823
(**) fglrx(0): *Mode "720x480": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   71.11  720 1016 1048 1440  480 644 648 823
(**) fglrx(0): *Mode "640x480": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   71.11  640 976 1008 1440  480 644 648 823
(**) fglrx(0):  Default mode "640x400": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   71.11  640 976 1008 1440  400 604 608 823
(**) fglrx(0):  Default mode "640x350": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x350"   71.11  640 976 1008 1440  350 579 583 823
(**) fglrx(0):  Default mode "512x384": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   71.11  512 912 944 1440  384 596 600 823
(**) fglrx(0):  Default mode "400x300": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   71.11  400 856 888 1440  300 704 708 823 doublescan
(**) fglrx(0):  Default mode "320x240": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   71.11  320 816 848 1440  240 644 648 823 doublescan
(**) fglrx(0):  Default mode "320x200": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   71.11  320 816 848 1440  200 604 608 823 doublescan
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000001f
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 256 MB
(II) fglrx(0): [pcie] 258048 kB allocated with handle 0xdeadbeef
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xc0100000 - 0xc010ffff (0x10000) MX[B]
	[1] 0	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xc0302400 - 0xc03024ff (0x100) MX[B]
	[7] -1	0	0xc0302000 - 0xc03020ff (0x100) MX[B]
	[8] -1	0	0xc0300000 - 0xc0301fff (0x2000) MX[B]
	[9] -1	0	0xc0200000 - 0xc0203fff (0x4000) MX[B]
	[10] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[11] -1	0	0xc0004800 - 0xc0004bff (0x400) MX[B]
	[12] -1	0	0xc0004400 - 0xc00044ff (0x100) MX[B]
	[13] -1	0	0xc0009000 - 0xc0009fff (0x1000) MX[B]
	[14] -1	0	0xc0008000 - 0xc0008fff (0x1000) MX[B]
	[15] -1	0	0xc0007000 - 0xc0007fff (0x1000) MX[B]
	[16] -1	0	0xc0006000 - 0xc0006fff (0x1000) MX[B]
	[17] -1	0	0xc0005000 - 0xc0005fff (0x1000) MX[B]
	[18] -1	0	0xc0004000 - 0xc00043ff (0x400) MX[B]
	[19] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[20] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[21] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[22] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[23] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[24] 0	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[25] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[26] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[27] -1	0	0x00008420 - 0x0000842f (0x10) IX[B]
	[28] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[29] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[30] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[33] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[34] -1	0	0x00008450 - 0x00008453 (0x4) IX[B]
	[35] -1	0	0x00008430 - 0x00008437 (0x8) IX[B]
	[36] -1	0	0x00008454 - 0x00008457 (0x4) IX[B]
	[37] -1	0	0x00008438 - 0x0000843f (0x8) IX[B]
	[38] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[39] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[40] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:5:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0x2b4e90780000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.41.7
(II) fglrx(0):     Date: Sep  7 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.20-16-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): Interrupt handler installed at IRQ 17.
(II) fglrx(0): Exposed events to the /proc interface
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0x38000000 FBMappedSize: 0x005e9c00
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,1211)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,800) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 411
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Solid Lines
	Dashed Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		30 128x128 slots
(II) fglrx(0): Acceleration enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(==) fglrx(0): Using hardware cursor
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event4
(**) Option "Device" "/dev/input/event4"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Invalid argument
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Invalid argument
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Invalid argument
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event4
(**) Option "Device" "/dev/input/event4"
(--) Synaptics Touchpad touchpad found
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
ProcXCloseDevice to close or not ?
```

Here's part of zorg.conf

```
       Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "Disable"
EndSection

```

---

### Post by toggle on 2007-10-14
Hello there,

I have read many of the posts in this thread looking for someone having a problem similar to mine but have not found any. I have an ATI X1600 card and have followed the "easy" version of the instructions to the letter. 

The result for me is that video's play without lagging but now the tint is all wrong on them... i.e. skin tones are all purple. Any clue as to what might solve this? 

Any help appreciated.

---

### Post by toggle on 2007-10-14
Oh, I should have included this:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 2.0.6334 (8.34.8)

---

### Post by Schrammel on 2007-10-15
> **Tzimbar said:**
> As far as I can understand, new kernels (2.6.20 or newer) are not supported by the "old" ATI 8.28.8 drivers... :(
So, if we want to use Feisty and OpenGL, we will have to use open source drivers (which have the sadly famous bug causing the entire system to hang when an OpenGL application is run...) :(

I finally got my Ati 9800pro working, glxinfo says DRI=yes and so on, but if i start glxgears my System freezes 1sec after. 
First i thought maybe my card is broken, but then i read this.
Can someone post me a link to a more detailed post about this bug ?

I'm running 7.04 on a 2.6.23 kernel.

---

### Post by barrymoves on 2007-10-20
Well I don't feel alone atleast.

Q6600 and 2900XT, 64bit Gutsy.

Same problem as most other ATI owners - whichever installation method that I try, or whichever driver - black screen instead of Gnome login.  I managed to get Fiesty to "work" - had my 1920x1200 resolution (unsure of hardware acceleration) - but it wasn't refreshing properly/text/menus/icons not appearing so I gave it the heave-ho.  I tried for most of today using the various methods found in wikis/forums to get the latest ATI drivers to work on my new Gutsy install - but to no avail (or rather, teh black screen!)

My solution is to continue using Vista until ATI release the next lot of drivers - what's another month or so when I've already been waiting for support of the 2900XT since August already.


> **Juleshu said:**
> 
Somewhere online I found this: sudo dpkg-reconfigure xserver-xorg -phigh
Will this command work to fix things if it happens again so I do not have to reinstall?

I'm a linux noob and that's what I've been using to prevent a reinstall - seems to work fine (it's actually written in the xorg.conf file).  If someone could confirm that would be swell...

---

### Post by Madvil on 2007-10-20
Hello, I prefered to post this problem hear instead of opening a new thread but,
when I tried to install the restricted drivers and rebooted fine, I am not able to do some of the tasks that I was able to do before, like right-clicking to the desktop to pick a wallpaper. Also all the shortcuts from the Places menu throw an error that the paths are invalid, but I can browse in them from a terminal.

Please tell me I don't have to reinstall GNOME... :(

---

### Post by benefit on 2007-10-21
Ok i'm having very nasty problem with my Ati Radeon 9800 Pro. 

I have been editing and backupping my xorg.conf many times and I'm getting sick.
I've been checking almost every guide here and it still doesnt work. I think I have some none needed packages and corrupted xorg.conf // linux-restricted-modules. I have a custom kernel, 2.6.23.1-custom, and everytime I try to open Restricted Drivers Manager it says: 

*You need to install the package "linux-restricted-modules-2.6.23.1-custom" for this program to work.*

Anyway.. I downloaded and chmoded the ati driver installation package from their site.. the file is **"ati-driver-installer-8.40.4-x86.x86_64"**. 

When I type: 
> glxinfo | grep direct && glxinfo | grep glx && glxinfo | grep OpenGL

the output is:
> direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
OpenGL extensions:

I had some kind of 3d rendering when I used 'default' ati drivers but resolution didnt work. Now it works (1248x1024) but I am using fglrx. 
This is my xorg.conf graphic related output:

> Section "Monitor"

        # 1280x1024 @ 70.00 Hz (GTF) hsync: 74.62 kHz; pclk: 128.94 MHz
        Identifier   "Generic Monitor"
        HorizSync    28.0 - 51.0
        VertRefresh  43.0 - 60.0
        ModeLine     "1280x1024_70.00" 128.9 1280 1368 1504 1728 1024 1025 1028 1066 -hsync +vsync
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier  "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "Generic Video Card"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "Generic Video Card"
        Monitor    "Generic Monitor"
        DefaultDepth     24
        SubSection "Display"
                Depth     16
                Modes    "1280x1024" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1280x1024" "1024x768" "800x600"
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option  "Composite" "Disable"
EndSection


 Also some things are duplicated.. I don't get it.. there is something really wrong.

Thanks in advance for help!

---

### Post by bhouncy on 2007-10-22
ATI Radeon 9800pro that has never worked with any linux for as long as I've had it. It's a bit disheartening when you have tried every guide and searched google till it's oogles fell off. From what I can gather it's not a graphics driver fault. It's something to do with agpgart not being loaded or missing. I really want to love linux but every time I think I'm getting somewhere with her she turns cold on me.

---

### Post by benefit on 2007-10-22
> **bhouncy said:**
> ATI Radeon 9800pro that has never worked with any linux for as long as I've had it. It's a bit disheartening when you have tried every guide and searched google till it's oogles fell off. From what I can gather it's not a graphics driver fault. It's something to do with agpgart not being loaded or missing. I really want to love linux but every time I think I'm getting somewhere with her she turns cold on me.

Aaaammmhhhmmhmhh.. I really don't know what to think now. I just installed the driver and changed xorg.conf to original but now the resolution won't work anymore. I don't get it..

> glxinfo | grep direct
..and quess what? NO direct rendering! \o/

---

### Post by Cirion75 on 2007-10-22
How do I install the ATI driver for FireGL T2 Mobility?

I have downloaded the driver from the ati site and tried to install like this:
bash ./ati-driver-installer-8.35.5-x86.x86_64.run --buildpkg Ubuntu/gutsy

But it is not supported:
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/gutsy
Requested package is not supported.

Newer drivers will not work, since they do not support FireGL T2 Mobility, is there another way to install this driver?

---

### Post by don_kostone on 2007-10-22
Hi,

I'm trying for 2-3 days to get my ATI Radeon Mobility 9000 (rv250) working, but I got the following problems. I want to use just my external output (CRT) on my Eixo screen ( 1280x1024) I have tried all solutions including this one for each driver on each ubuntu but it simply doesn\t work for me. Ubuntu 6.06 detects on boot just my external monitor and after setting the correct resolution in xortg.conf I can change to higher resolution from the Gnome manager. Ubuntu 7.10 starts on both displays ( LCD 1280x800 ) and external using the same resolution - 1280x800. And I simply can't change to higher resolution. It is confusing to have 2 different tools doing theoretically the same thing - Screens and Resolutions and the Resolution manager. I have tried to edit the .conf file by myself, but it simply doesn't works. I have tried the opensource ati driver and the fglrx driver but they don't work at all. Can anyone give me a tip please, or I should really install 6.06 :) Thanks in advice.

---

### Post by Oli-hero on 2007-10-22
Hi, i'm new to linux, for about 2 days.. I've read many post on how to install ati driver and everything.. none have worked. last one i tried is this one, i tried to install manually the driver like they say, but i get a nice error at the beginning, here it is:

hero@hero-pc:~/Desktop$ bash ./ati-driver-installer-8.40.4-x86.x86_64*.run --buildpkg Ubuntu
Created directory fglrx-install.Nj6331
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.40.4...........................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu
Requested package is not supported.
Removing temporary directory: fglrx-install.Nj6331

Anyone as any ideas on how to get it working??

Video card: Ati radeon 8550
Monitor: Philips 170s 17"

---

### Post by RDV on 2007-10-22
Oli-hero.
You did not properly specify which of the many distributions of Ubuntu you wanted to create packages for (e.g. Fiesty or Gutsy ... etc). So the package specified should be for example. "Ubuntu/Gutsy"

A less painful installation method is to use the utility "Envy" from [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) 

Scroll down the web page to find the Envy utility version that matches your Ubuntu version. This utility does the complete ATI install including downloading the latest ATI driver and any package dependencies. 

If you already have ATI drivers installed make sure you uninstall and remove those packages before using Envy. Envy does uninstalls but only of packages it installed itself. 

I note this as I did a fresh install of Ubuntu 7.10 Gutsy and it had installed an old ATI driver (8.39). Even though  I used the Envy uninstall the old package ended up causing errors. So do the following:

a) Install Envy from [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

b) Use the "Applications>Add/Remove..." search for any "fglrx" packages then uninstall and completely remove from your PC (the package manager does both) (package named to uninstall is likely to be "ATI binary X.org Driver" leave the package "Restricted Driver Manager" installed)

c) reboot

d) Use the Envy utility to install the latest ATI drivers and dependencies

e) reboot

f) Turn on your ATI Restricted driver "System>Administration>Restricted Drivers Manager" and check/enable the ATI driver then reboot

g) Check your xorg log at "/var/log/xorg.0.log" for errors (any line that starts with "(EE)" )

h) You may find an error for AIGLX. This is to be ignored as it has something to due with the state of the ATI drivers which may be corrected in future driver releases. 

i) Also go to a terminal and type "fglrxinfo" to prove that you have fglrx running. For an example here are my fglrxinfo results:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1800 Series
OpenGL version string: 2.0.6747 (8.40.4)


Good Luck

---

### Post by Sim777 on 2007-10-22
(Re my previous post in this thread)

Fresh install of 7.10 and restricted drivers install without any problems. Compiz looks very pretty :D

---

### Post by Zakk Walid on 2007-10-22
if this tutorial will actualy work... 

will the desktop effects and compiz fusion work properly too?

---

### Post by Ehtetur on 2007-10-22
I followed the instructions and was able to get my ATI Radeon X200M card working..

Pretty good since AMD/ATI's linux support sux...

Forgot to mention, got Compiz-Fusion & Emerald themes working

---

### Post by don_kostone on 2007-10-23
I can't get my compaq presario x1000 with radeon Mobility 9000 working on dual-head or single head on the external monitor ... Any Ideas ...

---

### Post by ricardisimo on 2007-10-23
I have an RV280, Radeon 9200 SE card, which I think is working just fine via the "ati" driver. No Compiz or Beryl is possible with an older card like this, at least as I understand it, but otherwise all is well. Tell me: What are the clear advantages, if any, of loading the proprietary drivers instead? Just curious. Thanks.

---

### Post by nkessler2000 on 2007-10-23
Well I eventually got it to work, but it works incredibly suckily. Slow, flickery, unusable. I´m reverting to the old driver for now.

---

### Post by drystan1 on 2007-10-26
Hi I followed the guide but I seam to have mesa enabled instead of flglx ? I didsabled flglx in the restricted modules. Could that effect it ? heres my xorg.conf 

ection "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

x
Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

drystan@Angelmedia:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

org.log 

(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.12
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RV530
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(WW) fglrx(0): Failed to open DRM connection

 any ideas ?

---

### Post by djscantron on 2007-10-26
X1900XT user here, and I kept getting a black screen on starup with 8.42 like so many other X1900 series users until I did the following:

1. Start Ubuntu in safe mode (press escape when GRUB tell you to)
at the command prompt(you will be the root user now), type startx then hit enter.

2. once gnome/kde has started run the atidriverinstaller.run and choose a standard install.

3. after that is complete hit  Ctrl+Alt+Backspace to exit X and get back to the command promt.

4. run startx again.

5. this time once logged into gnome/kde, run the atidriverinstaller.run file, but choose custom install.

6. after THAT'S done, run aticonfig --initial, or edit xorg.conf to use fglrx driver.

7. reboot, and pray.

This was the only way I could install it and not get a black screen. I don't know why I had to do both the normal and advanced install, but I did and I now have 3D support and compiz running with a X1900XT.

---

### Post by mate84 on 2007-10-28
Hello,
I have a Dell vostro 1000 laptop with ATI 1150. In the restricted drivers manager I got this error: xorg-driver-fglrx is missing and after when I install it I get this information: fix broken packages first. And in the terminal:
mate@mate-laptop:~$ fglrxinfo
The program 'fglrxinfo' is currently not installed. You can install it by typing:
sudo apt-get install xorg-driver-fglrx
bash: fglrxinfo: command not found
mate@mate-laptop:~$ sudo apt-get install xorg-driver-fglrx
[sudo] password for mate:
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
xorg-driver-fglrx: Depends: libstdc++5 (>= 1:3.3.4-1) but it is not installable
E: Broken packages
mate@mate-laptop:~$

At the moment I have large icons.....
Can anybody help me?

---

### Post by Noiano on 2007-11-02
I have tried both the «ubuntu way» and the manual method but I got nothing. I followed cchtml wiki. When I type fglrxinfo I get
```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

```

And when I type glxinfo | grep direct I get
```
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

```

I also had a look to xorg log and I got strange message....i looked ant Xorg.0.log | grep fglrx...I have attached the output.

Can anyone please help me? I really can't have the whole thing working.

---

### Post by bthoward on 2007-11-02
I've been through several full rebuilds on this machine now and I'm pretty much confused now.  I've installed the ATI drivers using both methods (and have gotten them to "work" with both methods).  By work I mean I can get X to load and things seem to work.

But the thing is after doing a clean install if I go through the trouble of getting all the compiz stuff working all looks good (yet slightly choppy) and it works.  When I play a video I can play things and it looks good and I can full screen the video with out having problems. 

As soon as I install the fglrx drivers I start having troubles playing videos.  The desktop works wonderfully smooth (moving windows and rotating desktops around) but when playing a video the processor hits the roof.  Well if I leave the window in normal size the cpu will hit somewhere around 60 to 80% if I full screen it and its trying to stretch things its hitting 100% all the time.  Also I'll start getting errors saying that my computer is too slow from mplayer.  I get this error using -vo xv, -vo x11 (what have you...).  It either works (yet slow) or is mo screwed up (some of the gl ones are pretty interesting what they do).  

I'm not even really all that sure what logs I should post or anything.  When I run fglrxinfo I get that its an ATI driver...  When I have the stock config (like now) the fglrxinfo isn't there....  

I spose just so Im posting something I'll post my Xorg.conf as things are now... I'm going to stay here for now until I have a better solution.  I can take a bit of glitchyness on the window movement and what not in exchange for being able to play movies.

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"

        Identifier      "Alps Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"

        Option  "LeftEdge"              "120"
        Option  "RightEdge"             "830"
        Option  "TopEdge"               "120"
        Option  "BottomEdge"            "650"
        Option  "FingerLow"             "14"
        Option  "FingerHigh"            "15"
        Option  "MaxTapTime"            "0"

        Option  "EmulateMidButtonTime"  "75"
        Option  "VertScrollDelta"       "20"
        Option  "HorizScrollDelta"      "20"
        Option  "MinSpeed"              "0.6"
        Option  "MaxSpeed"              "1.5"
        Option  "AccelFactor"           "0.03"
        Option  "EdgeMotionMinZ"        "30"
        Option  "EdgeMotionMaxZ"        "160"
        Option  "EdgeMotionMinSpeed"    "15"
        Option  "EdgeMotionMaxSpeed"    "15"
        Option  "EdgeMotionUseAlways"   "0"
        Option  "UpDownScrolling"       "1"
        Option  "LeftRightScrolling"    "0"
        Option  "CircularScrolling"     "0"
        Option  "CircScrollDelta"       "0.1"
        Option  "CircScrollTrigger"     "0"

EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc M22 [Mobility Radeon X300]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc M22 [Mobility Radeon X300]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1400x1050"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Alps Touchpad"
EndSection

```

System is a Dell Latitude D600 with Radeon Mobility X300 video card.  It really is quite incredible that with this configuration mplayer takes very little cpu cycles to play a video at full screen.  Yet as soon as the fglrx drivers are installed anything having to do with video is SLOW!  Now if I could only get that nice smooth OS functionality and the low cpu usage for video playing to happen at the same time I'd be a happy camper. :)

---

### Post by TedGarvin on 2007-11-03
HI, I just installed the ati drivers (as it turns out, it was very simple) and I have no accelerated desktop.  I don't know what to do.  glxinfo | grep direct tells me I have direct rendering.

fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.0.6958 Release

glxinfo 
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.0.6958 Release
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_shader, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shader_objects, GL_ARB_shading_language_100, GL_ARB_shadow, 
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, 
    GL_ATI_fragment_shader, GL_ATI_meminfo, GL_ATI_separate_stencil, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_EXT_vertex_array, 
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_texgen_reflection, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, 
    GL_WIN_swap_hint, WGL_EXT_swap_control

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x43 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x44 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x45 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x46 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x47 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x48 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x49 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x4a 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x63 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x64 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x65 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x66 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x67 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x68 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x69 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x6a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x6b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6f 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x70 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x71 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x72 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x85 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
```


Here is my copy of xorg.conf
```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	Option	    "AIGLX" "true"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "DELL D1226H"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"

#	Option          "XAANoOffscreenPixmaps"
	Identifier  "ATI Technologies Inc M10 NQ [Radeon Mobility 9600]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc M10 NQ [Radeon Mobility 9600]"
	Monitor    "DELL D1226H"
	DefaultDepth     24
	SubSection "Display"
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection

```

I know the procedure to turn on compiz, but it can't start.  I'm beyond a newbie, but I'm willing to learn. Can anyone please just give a clue as to what I may be doing wrong?
When I try to start compiz I get this error message

```
Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald

(emerald:7095): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed
/usr/bin/compiz.real (core) - Fatal: No composite extension
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

But ati is whitelisted.

---

### Post by Yellow Pasque on 2007-11-04
TedGarvin, you have two "Device" and two "Screen" sections defined in your xorg.conf. Also, in the Server section, you're using the Screen defined with the fglrx driver (aticonfig[0]). Add fglrx to the whitelist section as well.

---

### Post by nixie21 on 2007-11-05
> **Temüjin said:**
> TedGarvin, you have two "Device" and two "Screen" sections defined in your xorg.conf. Also, in the Server section, you're using the Screen defined with the fglrx driver (aticonfig[0]). Add fglrx to the whitelist section as well.

Mine also has 2 entries?? Is that bad or wrong?  In another thread I am having problems with compiz.  I have the latest ATI drivers all installed, no compiz.  If I install xserver-xgl, I have compiz, but the system is not stable.  If I switch user, or try to do something that is graphic intense, X crashes, most of the time I need to do a hard reset of the computer to restart. So I uninstalled xserver-xgl.

xorg = 
xorg.conf =

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
Identifier "Default Layout"
Screen 0 "aticonfig-Screen[0]" 0 0
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
EndSection

Section "Files"

# path to defoma fonts
FontPath "/usr/share/fonts/X11/misc"
FontPath "/usr/share/fonts/X11/cyrillic"
FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
FontPath "/usr/share/fonts/X11/Type1"
FontPath "/usr/share/fonts/X11/100dpi"
FontPath "/usr/share/fonts/X11/75dpi"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Identifier "stylus"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Identifier "eraser"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Identifier "cursor"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Monitor"
Identifier "EN9110"
Option "DPMS"
EndSection

Section "Monitor"
Identifier "aticonfig-Monitor[0]"
Option "VendorName" "ATI Proprietary Driver"
Option "ModelName" "Generic Autodetecting Monitor"
Option "DPMS" "true"
EndSection

Section "Device"
Identifier "ATI Technologies Inc RV350 AR [Radeon 9600]"
Driver "fglrx"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
BusID "PCI:1:0:0"
EndSection

Section "Device"
Identifier "aticonfig-Device[0]"
Driver "fglrx"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc RV350 AR [Radeon 9600]"
Monitor "EN9110"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
EndSection

Section "Screen"
Identifier "aticonfig-Screen[0]"
Device "aticonfig-Device[0]"
Monitor "aticonfig-Monitor[0]"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
EndSubSection
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "1"
EndSection

Other info:
nixie21@Main:~$ glxinfo | grep direct && glxinfo | grep glx && glxinfo | grep OpenGL
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.0.6958 Release
OpenGL extensions:
nixie21@Main:~$ fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.0.6958 Release

Thanks

---

### Post by Yellow Pasque on 2007-11-05
> **nixie21 said:**
> Mine also has 2 entries?? Is that bad or wrong?  
Not inherently. In your case, the devices are the same, but with different names.

---

### Post by nixie21 on 2007-11-05
thanks, just wish I can get compiz working without the problems

---

### Post by rcmn on 2007-11-06
> **tseliot said:**
> 

[COLOR="Red"]**Please, remember that only the installation of the driver from Ubuntu's repositories is officially supported by Ubuntu.**[/COLOR]



And it's the only one that work for my kunbutu ,ati 9600 pro Config .Does anyone know if they plan on releasing a newer version of the ATI drivers(i'm talking about the Ubuntu's repositories) ?

---

### Post by nixie21 on 2007-11-06
> **rcmn said:**
> And it's the only one that work for my kunbutu ,ati 9600 pro Config .Does anyone know if they plan on releasing a newer version of the ATI drivers(i'm talking about the Ubuntu's repositories) ?

Do you have compiz working?

---

### Post by rcmn on 2007-11-06
i don't know about compiz I'm not really interested.But i have ETQW (game) running just fine except that some element of the game are invisible.And this problem should be fixed with a newer version of the driver.
I've tried all howto's available and i end up having to reinstall (mesa nightmare) .The worst of all was the Envy tool. I wasn't able to get X to restart with the ati or vesa(i always manage to get X to restart but this tool just killed it for good LOL).

---

### Post by Yellow Pasque on 2007-11-06
For those having trouble with xorg.conf, I thought I would post my working xorg.conf for reference. Your mouse section may be a bit different. If in doubt, copy your current one (just make sure the Identifier name matches the one in the ServerLayout section).

Note that I'm using the 8.40.4 driver and have Compositing and AIGLX disabled. If you're using 8.42.3 and want to give Compiz a shot, enable them. 

Also note that you'll probably need to change your PCI bus ID. To get the PCI bus ID, run ```
sudo update-pciids
lspci -v
```. 
For example, mine says:
```
01:05.0 VGA compatible controller: ATI Technologies Inc RS690 [Radeon X1200 Series]
``` and it maps to ```
Busid		"PCI:1:5:0"
```

Here it is, remember you may need to change the lines/sections in bold to match your preference or hardware.
```
Section "ServerLayout"
	Identifier	"Default Layout"
  	Screen 		"Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "Files"
        Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"fglrx"
	Load		"dbe"
	Load		"extmod"
	Load		"fbdevhw"
	Load		"glx"
	Load		"record"
	Load		"freetype"
	Load		"type1"
	Load		"dri"
        Load            "i2c"
        Load            "vbe"
EndSection

Section "ServerFlags"
	**Option		"AIGLX"	"off"**
EndSection

Section "Extensions"
	**Option		"Composite"	"Disable"**
EndSection

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
	[B]Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"[/B]
EndSection

Section "Monitor"
	Identifier	"VX2025wm"
	Option		"DPMS"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
	**Busid		"PCI:1:5:0"**
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"VX2025wm"
	Defaultdepth	24
	SubSection "Display"
		**Modes		"1680x1050"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x640"	"640x480"**
	EndSubSection
EndSection

Section "DRI"
	Group	0
	Mode	0666
EndSection

```

---

### Post by Pulshion on 2007-11-07
Does my xorg.conf look right? i cant get the drivers to work...they worked before but i reinstalled gutsy.


```

linux@linux:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)


```

```


# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"glx"
EndSection

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

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Horizsync	30.0	-	70.0
	Vertrefresh	50.0	-	160.0
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc R480 [Radeon X850Pro]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc R480 [Radeon X850Pro]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection


```

---

### Post by Arituay on 2007-11-08
Hello all.  I posted this in a thread in the Desktop Effects & Customization forum, but shortly after I posted it the resident expert in the thread posted that he was going on vacation for two weeks and wouldn't be able to check the forums.  So here goes.

I am unable to get fglrx working correctly.  With Feisty I had fglrx and Big Desktop working fine (no compiz or anything like that though).  Now that I upgraded I can't get dual monitors working.  The Ubuntu Screens and Graphics interface doesn't work at all, it doesn't recognize that fglrx is the driver for my card even though in the restricted driver screen it is enabled and active as well as the fact that it is the driver specified in my xorg.conf.  No changes attempted in Screens and Graphics interface remain after the required restart.

So I tried using my xorg.conf that worked under Feisty (see below) and that won't work either.


```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
# 
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "off"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "EnablePrivateBackZ" "yes"
	Option	    "HSync2" "65"
	Option	    "VRefresh2" "60"
	Option	    "PairModes" "1024x768+1024x768"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1024x768" "1024x768"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

```

When I do aticonfig --query-monitor I get:

```

Connected monitors: none
Enabled monitors: none

```

The xrandr command yields:
```

Screen 0: minimum 1280 x 1024, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024      60.0* 

```

fglrxinfo yields:
```

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

```

glxinfo -display :0 yields:
```

name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 16 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x39 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

```

uname -r :
```
2.6.22-14-generic
```

dpkg -l linux-restricted-modules-2.6.22-14-generic :
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  linux-restrict 2.6.22.4-14.9  Non-free Linux 2.6.22 modules on x86/x86_64

```

dpkg -l linux-image-2.6.22-14-generic :
```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  linux-image-2. 2.6.22-14.46   Linux kernel image for version 2.6.22 on x86
```


lsmod | grep fglrx :
```
fglrx                 656352  0 
agpgart                35016  1 fglrx

```

modinfo fglrx :```

filename:       /lib/modules/2.6.22-14-generic/volatile/fglrx.ko
depends:        agpgart
vermagic:       2.6.22-14-generic SMP mod_unload 586 
license:        Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY
description:    ATI Fire GL
author:         Fire GL - ATI Research GmbH, Germany
parm:           firegl:charp
```

dpkg -l xorg-driver-fglrx :
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  xorg-driver-fg 7.1.0-8.37.6+2 Video driver for ATI graphics accelerators

```




Any help on this is much appreciated, thanks,

Arituay

---

### Post by rcmn on 2007-11-08
> **rcmn said:**
> 
[QUOTE=tseliot;3120607]

[COLOR="Red"]**Please, remember that only the installation of the driver from Ubuntu's repositories is officially supported by Ubuntu.**[/COLOR]



And it's the only one that work for my kunbutu ,ati 9600 pro Config .Does anyone know if they plan on releasing a newer version of the ATI drivers(i'm talking about the Ubuntu's repositories) ?[/QUOTE]

does anyone know what is the time frame for newer drivers to come into repository ?

---

### Post by Yellow Pasque on 2007-11-08
> **Pulshion said:**
> Does my xorg.conf look right? i cant get the drivers to work...they worked before but i reinstalled gutsy.
Try copying my Modules section from the post above yours. Also make sure fglrx is enabled in the Restricted Driver Manager.

EDIT: If you're still having issues, I'll be on AIM the rest of of the night.

---

### Post by Yellow Pasque on 2007-11-08
Arituay,
Your drivers don't appear to be installed correctly. Make sure the Restricted Driver Manager shows you proprietary driver in use.

Also, you should add "1280x1024" to this line
```
Modes    "1024x768" "1024x768"
```

I don't know much about dual monitors, but I do know there's a recent thread on it if you dig back a few pages.

---

### Post by Arituay on 2007-11-08
My restricted driver manager shows that ATI accelerated graphics driver is enabled and In use.

I will try adding the additional resolution.

---

### Post by Yellow Pasque on 2007-11-08
err, nvm

---

### Post by redwarrior on 2007-11-09
Ok, deep breath here.  I am fresh/rusty to linux and Ubuntu in particular, but I'm doing my best to learn and enjoying the trip.  I've gone through the forums as best I can, but I can't seem to find my exact problem replicated, so I have already posted it in the Ubuntu Dell Support forum and thought it might be a good idea to post it here to the ATI gods.

I am running gutsy on a Dell Dimension XPS 400 with a ATI Radeon X300 PCIe video card.  The install went fine until, like the newbie I am, I allowed the restricted ATI driver to be installed.  Since then, I can boot fine past GRUB and then the initial Ubuntu boot screen loads.  Once I "hear the drums," the screen goes black with the error "2:  Digital Input Cannot Display This Video Mode".  (Yes, I do have a digital cable connecting the card to my monitor, but it runs fine in XP.)

After going through the forums and how-to's here, I was able to get into /var/log/xorg.0.log and have a look.  The only (EE) error entry was the following:

AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/$
AIGLX: reverting to software rendering

Other than that, after combing through all the fixes I could find, I can't find anything amiss in the log or in my xorg.conf .  It appears that it is finding the ATI card properly and having no problems identifying it.  Any advice would be most appreciated.  I will try to get details from my xorg.conf to post here as well, but without the ability to copy and paste, it's going to be tough.  I'll also see what some googling turns up, but I figured this place was my best shot.

Thanks!

---

### Post by redwarrior on 2007-11-10
Ok, I have figured out that my error was coming from the fact that I needed to configure the monitor portion of the xorg.conf to match the horizontal and vertical synch rates for my particular monitor...they did not match the standard, but the info was easy enough to find on Dell's website, so that error is gone.  Now I am just left with the AIGLX error for hardware acceleration...I'll go at it again tomorrow.

---

### Post by hatebreeder on 2007-11-10
PLEASE HELP!!!

i have a ati radion xpress 1100
i have a wide screen laptop, 15 inches
***stupid me***, i changed my graphics driver in hope that i could get 3d to work, just in case, i did that thing that you can save your settings (i dunno what its called, ask me to describe it if u don't know what i mean)... then, i changed my driver to somthing else (forgot what). after that i had to log off and came back on and now the res is as if it was not widescreen its at 1024x768, which is for a regular monotor...

now it looks like crap...

i don't want to boot into vista, its so slow and fail

when i tried to recall my saved setting it did nothing

i tried to guess which driver i had but when i try to use it it always ends up as 1024x768, and thats the max display setting

i don't even care about 3d now(though it would be cool), i just want it to be the right res

info:
ubuntu 7.10 32 bit
acer aspire 5100


PLEASE HELP!!!

---

### Post by irober02 on 2007-11-12
I've just followed the method pointed to above that involved downloading ati-driver-installer-8.42.3-x86.x86_64.run from the ATI website, building the packages and installing. All went according to the instructions and I now have direct rendering. :-)

However, I still have a problem...

When I try to watch digital TV in kaffeine the X session restarts! :-(

Looking at /var/log/messages makes me suspect that the ATI driver is the culprit:

[fglrx] PCIe has already been initialized. Reinitializing ...
[fglrx] Reserve Block - 0 offset =  0X7ffb000 length = 0X5000
[fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
[fglrx] Reserve Block - 2 offset =  0X7fbb000 length = 0X40000

This group of 4 lines seems to be logged each time I try.

I've added the following to my xorg.conf file:

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

The device stanza is pretty basic:

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
EndSection

Any suggestions?

ian

---

### Post by chiefbearclaw on 2007-11-14
[http://ubuntuforums.org/showthread.php?t=575843]("http://ubuntuforums.org/showthread.php?t=575843") (My post in this thread in on page 23)

---

### Post by Yellow Pasque on 2007-11-14
> **chiefbearclaw said:**
> [http://ubuntuforums.org/showthread.php?t=575843]("http://ubuntuforums.org/showthread.php?t=575843") (My post in this thread in on page 23)
See my reply in that thread: [http://ubuntuforums.org/showpost.php?p=3768746&postcount=225](http://ubuntuforums.org/showpost.php?p=3768746&postcount=225)

---

### Post by mech7 on 2007-11-14
Does anybody know how to fix the new ATI drivers they are sooo slow and AIGLX doenst even work :(

---

### Post by Yellow Pasque on 2007-11-14
> **mech7 said:**
> Does anybody know how to fix the new ATI drivers they are sooo slow and AIGLX doenst even work :(

AIGLX DOES work in the latest drivers. As for the speed, we're just going to have to wait until ATI gets its act together. It's embarrassing when low-end nvidia cards and integrated intel graphics can run compiz effects faster than high-end ati cards.

---

### Post by mech7 on 2007-11-16
> **Temüjin said:**
> AIGLX DOES work in the latest drivers. As for the speed, we're just going to have to wait until ATI gets its act together. It's embarrassing when low-end nvidia cards and integrated intel graphics can run compiz effects faster than high-end ati cards.

AIGLX does not work on X700 mobile :( and even scrolling a webpage is unbearable to watch :(

---

### Post by citydog on 2007-11-19
For those who can't get their OPENGL vendor to show ATI or lsmod | grep fglrx returns nothing, the problem is that fglrx kernel module is not loaded.

My gusty install/8.42.3 driver/compiz was working fine until after reboot.  The reason I found is that both modprobe and X are trying to load this kernel module from /lib/modules/2.6.22-14-generic/volatile/fglrx.ko instead of /lib/modules/2.6.22-14-generic/misc/fglrx.ko.

It seems to be a modprobe issue.  I am new to ubuntu so not sure how this can be fixed.  A workaround would be to use insmod <module path>.

insmod /lib/modules/2.6.22-14-generic/misc/fglrx.ko

Restart your session or restart X and you should get DRI and OPENGL.

---

### Post by shaggly on 2007-11-20
BUMP

I have this self same problem. The Volatile link seems to get deleted during a reboot, which then causes DRI to fail.

There must be a way to force the loading of the module from /lib/modules/$(uname -r)/misc/fglrx.ko instead ???

I read on the unofficial ATI wiki that the writer tried this fix:

> NOTE : On my Gutsy install, after a reboot this link was always removed automatically leaving me without an fglrx module loaded, and thus no ATI rendering. There have been several ways of getting around this suggested here, but my experience with recent installs and updates still leads to a MESA driver being installed. This became very frustrating as I tried every method and step here with no success. A new way around this is to let the old MESA fglrx load, then as a final step in the boot process, edit rc.local :

sudo gedit /etc/rc.local

copy these two line at the beginning of the file right on top of the command "set 0" :

rmmod fglrx
insmod /lib/modules/$(uname -r)/misc/fglrx.ko

This removes the Ubuntu fglrx module in the first line, and then the second line loads the newly installed one. This should now force the ATI module in and you should get the correct results in the following steps. 

However, when I edit my rc.local file as suggested, it doesn't seem to do the trick. In fact the rc.local file states that by default it does nothing.

I'm running Kubuntu 7.10

---

### Post by carlosjuero on 2007-11-21
Just a note all, the new ATI drivers are out - they changed the numbering scheme on us, the new version is 7.11 [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

---

### Post by Melcar on 2007-11-21
Trying out the new driver and I have not notice any improvements from the previous release or fixes to my problems.  I still have screen tearing, and Compiz continues to be unusable when using AIGLX (massive screen flickering on 3D apps., slow scrolling on FF, no opengl support for video playback).

---

### Post by Callius on 2007-11-21
Melcar, do you know any way to get all of those issues resolved on an ATI card?

I'm not really picky about what drivers I use, so long as I can get the compiz + firefox issues resolved.

---

### Post by Melcar on 2007-11-21
> **Callius said:**
> Melcar, do you know any way to get all of those issues resolved on an ATI card?

I'm not really picky about what drivers I use, so long as I can get the compiz + firefox issues resolved.


No, not really.  You can go back to using XGL, but that also brings other problems, most notably, slow 3D acceleration in things like games.  The scrolling in FF is not that bad and I was able to alleviate the issue a bit by turning off AA and AF in the CCC.  Compiz doesn't really bug me since all of my PCs are running either KDE or XFCE, which have their own eyecandy of sorts.  Still, I was really hoping that this issues would have been resolved by this release.

---

### Post by Cosmic_Crusader on 2007-11-22
I just installed the 7.11 driver on a Gutsy laptop with a Radeon Mobility X700.

Slow 2d performance (firefox smooth scrolling is anything but) and suspend does not work.

However fgl_glxgears gives a constant 1013 frames per second!
Compiz-fusion effects appear to be ok.

So for me I have a new issue of slow 2D acceleration and still have the problem of not being able to suspend.

I hope that someone out there figures out the problem, cos I don't have time at the moment to investigate further.

ADDITION: Oh I forgot to mention that video playback only works in fullscreen mode.  In window mode I see a frame of the video before it goes to black (sound is of course fine)
2ND ADDITION: 2D performance goes back to excellent with desktop effects disabled (not sure if it suspends though - haven't tested that)

---

### Post by delphiguy on 2007-11-22
Cheers,

Can somebody here help me.  I installed Kubuntu on my laptop it has 
ATI Radeon Mobility X1300 card, but I cant seem to change my screen 
resolution, its stuck at 800x600, and it says that I only have 256kb of videoram.

heres my xorg.conf file
```

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"    "/dev/input/mice"
    Option        "Protocol"    "ImPS/2"
    Option        "ZAxisMapping"    "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"    "/dev/psaux"
    Option        "Protocol"    "auto-dev"
    Option        "HorizEdgeScroll"    "0"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "stylus"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "eraser"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "cursor"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "Generic Video Card"
    Driver        "fglrx"
    Busid        "PCI:1:0:0"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Generic Video Card"
    Monitor        "Generic Monitor"
    Defaultdepth    24
    SubSection "Display"
        Modes        "800x600"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
  screen "Default Screen"
    Inputdevice    "Generic Keyboard"
    Inputdevice    "Configured Mouse"
    
    # Uncomment if you have a wacom tablet
    #    InputDevice     "stylus"    "SendCoreEvents"
    #    InputDevice     "cursor"    "SendCoreEvents"
    #    InputDevice     "eraser"    "SendCoreEvents"
    Inputdevice    "Synaptics Touchpad"
EndSection
Section "Module"
    Load        "glx"
EndSection
Section "Extensions"
    Option        "Composite"    "0"
EndSection

```any idea on how to fix this? I am not even aiming to have compiz work I 
just want to have a better screen resolution, of course having compizfusion
work is also nice.

---

### Post by abds on 2007-11-22
Need help. Just tried to install the latest ATI drivers. I ahve an ATI X200. Somehow managed to mess up everything. When I rebooted the pc, all I saw was a while screen. So i uninstalled the drivers. Right now am running on low res mode. Could anyone give me hints on how to go about fixing stuff. I dun really play any games or anything. Just need compiz and everything else to work fine. 

Please help. I am really sick of all these driver issues by now!

---

### Post by delphiguy on 2007-11-22
Got it, its just a matter of changing the Monitor, somehow the Plug and Play 
monitor only supports 800x600, so I have to change it to 1280x800.

Now to get Beryl to work.

---

### Post by Callius on 2007-11-23
> **Melcar said:**
> No, not really.  You can go back to using XGL, but that also brings other problems, most notably, slow 3D acceleration in things like games.  The scrolling in FF is not that bad and I was able to alleviate the issue a bit by turning off AA and AF in the CCC.  Compiz doesn't really bug me since all of my PCs are running either KDE or XFCE, which have their own eyecandy of sorts.  Still, I was really hoping that this issues would have been resolved by this release.

I'm still quite a bit of a newbie, so please pardon my ignorance, but how do I "go back to using XGL?"

---

### Post by Fabio K on 2007-11-23
Hi,
I need help to install ATI radeon drivers. I have followed many tutorials, and many wiki pages, but it all failed. Once I followed a tutorial, it worked, showed my video card name, not that Mesa thing in the fglrxinfo, compiz worked, 3d games too (I played Half-life using Wine, I got 60fps), but it just worked one day. Next day I booted my pc and everything failed, including Xserver. I was using XGL with the "sudo apt-get install xorg-driver-fglrx", compiz-fusion and "sudo apt-get install xserver-xgl".

I'm using:
ATI Radeon 9550 AGP 8x 128mb
Samsung Syncmaster 940BW (DVI)
AMD Athlon 64 2.01ghz 3000+
1024mb RAM
Asus K8N motherboard

I fresh installed many times Ubuntu 7.10 (32bit), just once it worked and again, for one day (one boot, the second boot it stopped working). I do not really care if I need to reinstall it again (I have nothing at my hard drive except ubuntu right now).
By the way, I am using ndiswrapper (I don't know if this affects something as I am a newbie at linux, I started using it a week ago)

thx in advance,
Fabio K

Edit: I forgot to mention that I'm not using the Plug n Play driver, I'm using the generic 1440x900 panel, located in the same section of Plug n Play.
Edit2: fglrxinfo shows Mesa drivers instead of "ATI Radeon 9550 / X1050"

---

### Post by gonzolono on 2007-11-23
Hi
Noob (partial idiot variety)  here and muddled.

I have an ATI Radeon x1300 and have followed this guide [here]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Configure_the_Driver")
but I still cannot:

- use advanced desktop effects (complains with cannot use desktop effects)
- configure card: in screen and graphics preferences, the graphics driver is fgrlx and it fails on configuration
- play movies in VLC


I thought it was my monitor ( Relisys TL766) as the screen setting is Generic PLug n Pray but of course can I find a driver specific to it. Can I buggery!


pciinfo lists this:

01:00.0 VGA compatible controller: ATI Technologies Inc RV515 PRO [Radeon X1300/X1550 Series]
01:00.1 Display controller: ATI Technologies Inc RV515 PRO [Radeon X1300/X1550 Series] (Secondary)

fglrxinfo lists this:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300 / X1550 Series
OpenGL version string: 2.0.6473 (8.37.6)

Please help

Ben

---

### Post by devosion on 2007-11-24
I installed the driver manually from the ATI web site using the tutorial here.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I edited xorg.conf to enable Composite and when I attempt to enable desktop effects I get the "Desktop Effects could not be enabled screen." Not quite sure what I should do from here on out but I could use some help. Still pretty much a noob at Ubuntu.

Im using a X1950 Pro, btw.

---

### Post by Yellow Pasque on 2007-11-24
gonzolono and devosion:
Have you added fglrx to the WHITELIST string in the /usr/bin/compiz file?

---

### Post by devosion on 2007-11-24
I just did and performed a restart. When I attempted to enable desktop effects I received the same error.

I went ahead and checked my xorg.conf file to verify that I did enable composite and strangely enough I found two entries for it now...

> Section "Extensions"
	Option		"Composite"	"1"
	Option		"Composite"	"1"
EndSection

I went ahead and updated both, but im guessing I should delete one anyway right?

---

### Post by Cammy on 2007-11-24
Well, after spending all morning on this, I've had it.  I'm off to pick up a new video card today.  I just can't get any of the methods here to work, and if I run "sudo aticonfig --initial" it just core dumps.

When I try to use the Restricted Drivers Manager, it says I don't need any restricted drivers. :roll:

All this just to get 1280x1024.  I almost wish I'd just stuck with dapper.

---

### Post by gonzolono on 2007-11-24
yep did that and still no joy.
Is this also why I can´t play DVDs through vlc?

---

### Post by devosion on 2007-11-24
Not quite sure. I just installed Cedega and it confirmed my woe's for the third time today, that im not getting any OpenGL support or 3d Acceleration. What a pain in the butt. :(

---

### Post by Callius on 2007-11-24
Yeah, at this point I'm thinking of just getting an NVidia card and tossing the ATI to the wolves.

---

### Post by gonzolono on 2007-11-24
problem is I still need to use winblows xp so am loathe to change my video card. It's odd, with Ubuntu I've finally got proper 6.1  surround sound with my audigy card that winblows can't fully handle. If only I could get the ati card to work properly it would seriously reduce the amount of time I would need to spend using winblow(itoutmyar)s. 
I would be temporarily appeased if I could watch DVDs without having to go back to W*$??£s.

The search goes on...

Ben

---

### Post by Melcar on 2007-11-24
For desktop effects to work you need to make sure fglrx is whitelisted as well as your cards not excluded from the /usr/bin/compiz file.  As for the VLC issue, make sure you have all the proper codecs and that the output video driver is set to X11 for better compatibility.

---

### Post by gonzolono on 2007-11-24
ok so I followed the unofficial ati driver wiki and have solved the issue of libGL.so.1 
and now:
ati control centre works
amarok works
BUT desktop effects only works on one quarter of the screen (the rest is black)

is this because my Relisys TL766 monitor&#347; resolution not being good enough to support it?

any thoughts would be very welcome

Ben

---

### Post by carlosjuero on 2007-11-25
I fooled around with compiz a few weeks ago; and just friday found out that somehow, during my removal of all things compiz, my video driver got reset to VESA (No Direct Rendering/OpenGL/etc). It didn't actually hit me until I tried to play with getting WoW set up to run under Ubuntu - the -opengl switch was throwing me an error. I didn't think to check the driver status because City of Heroes worked fine under Cedega, so it had to be a WoW thing right? Nope - did an fglrxinfo and had the dreaded Mesa (after having it display the proper ATI information a week earlier [or whenever I last played with Compiz]). So I checked my restricted drivers manager.. unchecked for ATI. I went the route of enabling the restricted, making sure that X was using the ATI and the whole reboot X server thing.. not a thing worked.

A tad more frustrated I uninstalled the ATI driver (with the fglrx-uninstall.sh script in /usr/share/ati) and then reinstalled it again (still @ 8.42.3 at that point, 7.11 hadn't been released yet).. no go. I rebooted into Windows Friday evening with a headache and a desire to go over to ATI's coders office and beat the living [long string of beeps] out of their programmers. I know one thing for sure, as soon as I can afford it I am going to head over to nVidias territory and stay away from ATI for video cards for the near (and distant) future.

---

### Post by gonzolono on 2007-11-25
hi, noob (idiot flavour) here,

does anyone know why, after successfully installing the new ATI driver (3 days to find out the right way of doing it), I can only get the desktop effects to work on precisely one quarter of my screen,  the rest is black; my resolution is limited to 1280x1024; and I still have a mouse point that can run over the black area of the screen?

any help would be greatly appreciated.

Ben

---

### Post by Fabio K on 2007-11-27
Hello again,
I googled a bit about xorg configuration file, and I found one that said that for older Radeon video cards, use "radeon" driver not "fglrx". In fact, fglrxinfo showed me other thing:
> fabio@Fabio:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 AGP 8x x86/MMX+/3DNow!+/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.1

fabio@Fabio:~$ 

But 3D accel isn't working. (XGL is not installed)

Any ideas?

Fabio K

Note: The page I found is [http://www.gentoo.org/doc/en/xorg-config.xml](http://www.gentoo.org/doc/en/xorg-config.xml)

---

### Post by Fabio K on 2007-11-27
> **carlosjuero said:**
> so it had to be a WoW thing right? Nope - did an fglrxinfo and had the dreaded Mesa (after having it display the proper ATI information a week earlier [or whenever I last played with Compiz]). So I checked my restricted drivers manager.. unchecked for ATI. I went the route of enabling the restricted, making sure that X was using the ATI and the whole reboot X server thing.. not a thing worked.

This happened to me too... (my first post here...) When I last used ubuntu, was working. The next time I booted up, every single thing failed to openg. Mesa appeared again and never more I was able to repair it. I guess it must be something linked to an "auto enable" while it is loading linux? (I was able to use it after a 'reboot', but not after a 'shutdown').
I'm with a Radeon 9550 AGP 8x 128mb

I removed "fglrx" and tried "radeon", It showed another information (last post), I checked back on my Windows instalation and the information showed is *almost* correct. It's just missing the video card model. By doing that, it made it faster (not much faster - no 3D or compiz), but it helps.

Fabio K

---

### Post by Dynar on 2007-11-27
I got the same card as you Fabio, I tried practically everything that's been thrown my way, changing xong.conf. I opened a Thread somewhere, the response I got, was just to wait 'till the next driver comes out. It seems that the drivers for 9550 is bugged or something. 

I think I can vouch for that.. Nothing really seems to be helping. Either way I'm not getting any direct rendering. First my DVD's were like FPS hell, but I at least got that running normal. I really want to start installing games on this.. That'd be an unreal feeling, games outside of WinXP.

---

### Post by Fabio K on 2007-11-27
Me again
Dynar, it IS possible to get direct rendering working on 9550, but it is REALLY hard.
I have already managed to enable it, but I lost it, and I did it again now!! But unfortunately it is on display 0 not in 1 (I don`t have a clue about what is display 0).
Right after my last post, I changed my video card driver to "radeon". It made things easier, but no 3d at all. Then I removed xorg-driver-fglrx with the help of carlosjuero "fglrx-uninstall.sh script in /usr/share/ati". After that I made lots of things that threw me into vesa and "safe mode". But I think that all you need to do is put these lines in xorg.conf I found in safe mode (I don`t know why or HOW it auto-configured to direct rendering) > Section "Module" 
	Load		"GLcore"
	Load		"glx"
	Load		"dbe"
	Load		"v4l"
EndSection
It wasn`t like this before safe mode, (I have a backup of my xorg.conf everytime it changes) but now look what happens when I type fglrxinfo: > fabio@Fabio:~$ glxinfo -display :1 | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
fabio@Fabio:~$ glxinfo -display :0 | grep direct
direct rendering: Yes
fabio@Fabio:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon 9550 / X1050 Series
OpenGL version string: 2.0.6473 (8.37.6)

fabio@Fabio:~$ fglrxinfo -display :1
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon 9550 / X1050 Series
OpenGL version string: 1.2 (2.0.6473 (8.37.6))

fabio@Fabio:~$ 

All I think I need to do is to remove display 1 that has no direct rendering and use 0.

If anyone knows how to remove display 1, drop a post :)

Fabio K

---

### Post by Dynar on 2007-11-27
I have the exact same results as you Fabio. However, I needed the 8.40.4 driver from Envy to get my DVD displaying smoothly. The 7.11 doesn't work at all. I tried the latest one from ATi also with no results. 

Anyway, did you be able to get display 0 installed? Any idea how, or to tell the system to use those settings. It says it has direct rendering.

```
 glxinfo -display :0 | grep direct
direct rendering: Yes
``` 

and

```
$ fglrxinfo -display :1
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon 9550 / X1050 Series
OpenGL version string: 1.2 (2.0.6747 (8.40.4)
```


Odd?

---

### Post by Dynar on 2007-11-27
Guess what, I got a bit of fortunate accidental crash which might as well saved me loads of trouble. I tried solving something and I couldn't log in, safe mode couldn't fix it and I know nothing really specific commands to alter anything I've done..So I done a fresh install. 

I didn't touch the Restricted Device Manager. Start out fresh and use this tutorial or, it seems I got direct rendering now and display at 0. No clue to why it changed to 0 to 1.

Well, try this one if you want it working properly.

[http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support#]("http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support#")

Here are my results:

```
dynar@Einstein:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon 9550 / X1050 Series
OpenGL version string: 2.0.6958 Release
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_shader, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shader_objects, GL_ARB_shading_language_100, GL_ARB_shadow, 
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, 
    GL_ATI_fragment_shader, GL_ATI_meminfo, GL_ATI_separate_stencil, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_EXT_vertex_array, 
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_texgen_reflection, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, 
    GL_WIN_swap_hint, WGL_EXT_swap_control

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x43 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x44 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x45 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x46 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x47 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x48 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x49 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x4a 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x63 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x64 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x65 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x66 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x67 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x68 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x69 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x6a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x6b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6f 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x70 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x71 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x72 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x84 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

fgl_glxgears

```
dynar@Einstein:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
2450 frames in 5.0 seconds = 490.000 FPS
2690 frames in 5.0 seconds = 538.000 FPS
2712 frames in 5.0 seconds = 542.400 FPS
2689 frames in 5.0 seconds = 537.800 FPS
2715 frames in 5.0 seconds = 543.000 FPS
2689 frames in 5.0 seconds = 537.800 FPS

```

glxgears

```
dynar@Einstein:~$ glxgears
12610 frames in 5.0 seconds = 2521.943 FPS
12607 frames in 5.0 seconds = 2521.389 FPS
12599 frames in 5.0 seconds = 2519.777 FPS
12595 frames in 5.0 seconds = 2518.924 FPS
12604 frames in 5.0 seconds = 2520.707 FPS

```

Remember, I started out with a fresh install, don't do anything but what's said in that tutorial. I never knew it would be that simple. I can't really believe it myself.

---

### Post by carlosjuero on 2007-11-28
Well, after some hair pulling I got fglrx working again [7.11 drivers]; kinda annoying process to get there though :/

First I followed the tutorial at the unofficial ATI wiki ([http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide))

That didn't work out of the 'box' so then I installed the drivers AGAIN using the default GUI installer. When I restarted my X server after that I had direct rendering working just beautifully.
```

~$ fgl_glxgears
Using GLX_SGIX_pbuffer
8505 frames in 5.0 seconds = 1701.000 FPS
8673 frames in 5.0 seconds = 1734.600 FPS
8501 frames in 5.0 seconds = 1700.200 FPS
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 108976 requests (108974 known processed) with 0 events remaining.

~$ glxgears
27613 frames in 5.0 seconds = 5522.429 FPS
30146 frames in 5.0 seconds = 6029.161 FPS
27506 frames in 5.0 seconds = 5501.079 FPS
29270 frames in 5.0 seconds = 5853.953 FPS
29330 frames in 5.0 seconds = 5865.958 FPS
29630 frames in 5.0 seconds = 5925.943 FPS
29599 frames in 5.0 seconds = 5919.792 FPS
28399 frames in 5.0 seconds = 5679.699 FPS

~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1650 Series
OpenGL version string: 2.1.7059 Release

```

Lots of loopholes to jump through; I just hope that it won't break on me again by itself [I think it might have been one of the recent round of Ubuntu updates that 'broke' my previous driver install]

---

### Post by Fabio K on 2007-11-28
Hello,
I must say that I am very angry with the results I had today... Again Mesa took over and there goes my direct rendering... Turned on my computer and this happened again.

But, I am not going to quit on trying, so (thanks Dynar for the link) I am going to fresh install linux, and try the tutorial, see if it works.

Fabio K

EDIT: By the way, mesa just took over after my computer was turned off. When it's a restart, nothing changes. See if happens the same.

---

### Post by carlosjuero on 2007-11-28
> **Fabio K said:**
> Hello,
I must say that I am very angry with the results I had today... Again Mesa took over and there goes my direct rendering... Turned on my computer and this happened again.

But, I am not going to quit on trying, so (thanks Dynar for the link) I am going to fresh install linux, and try the tutorial, see if it works.

Fabio K

EDIT: By the way, mesa just took over after my computer was turned off. When it's a restart, nothing changes. See if happens the same.
I sure as heck hope a power off doesn't reset me to Mesa; that will sorta make me a tad angry. I know it is ATI's shoddy drivers, but having Direct rendering disabled lowers the # of things I can do on Ubuntu and forces me to use my Windows install for more things :/

---

### Post by Dynar on 2007-11-28
> **Fabio K said:**
> Hello,
I must say that I am very angry with the results I had today... Again Mesa took over and there goes my direct rendering... Turned on my computer and this happened again.

But, I am not going to quit on trying, so (thanks Dynar for the link) I am going to fresh install linux, and try the tutorial, see if it works.

Fabio K

EDIT: By the way, mesa just took over after my computer was turned off. When it's a restart, nothing changes. See if happens the same.

Well, I have Direct Rendering with this driver and such, I can play games, use Wine and stuff like that. But it's not stable. My screen seems to flicker and scrolling in Firefox and even filebrowsing is kind of flickering. Like if you press "File" things go weird. Hard to explore and play games.. If you are epileptic, I don't recommend using the method I mentioned..

Anyone know any sollutions to the unstability of the rendering. Everything seems fine, except what I mentioned, also, watching any video in full screen is FPS hell, it's like 1 frame per second.

---

### Post by Fabio K on 2007-11-28
> **Dynar said:**
> Everything seems fine, except what I mentioned, also, watching any video in full screen is FPS hell, it's like 1 frame per second.

Try using VLC with OpenGL video rendering or another renderer. This is in Preferences>Video>Output modules. **Must enable Advanced mode to see this**. Works for me in Default. (I'm not with fglrx driver, I'm using "radeon"** without 3D rendering support** and no XGL)

[CENTER]~Still trying to find a way of enabling full support for 3D and 2D on radeon 9550 video cards with the fglrx driver~[/CENTER]

Fabio K

---

### Post by lostcause64 on 2007-11-29
Has anyone tried this with an ATI X850XT yet? I'm about to try 7.10 version of Ubuntu, since I had no luck with previous versions of Ubuntu and this graphics card. I'm really hopeful that this new version will let me start using Ubuntu in a dual boot setup with XP Pro... I'm a gamer as well as a pc tech, so I need both...

---

### Post by whistlerspa on 2007-11-30
My suggestion is give upon ATI propriety, they seem to be rubbish on Linux and Vista  - is my experience.  Compiz and Aero worked with default drivers but not with propriety.

---

### Post by El Zoido on 2007-11-30
> **lostcause64 said:**
> Has anyone tried this with an ATI X850XT yet? I'm about to try 7.10 version of Ubuntu, since I had no luck with previous versions of Ubuntu and this graphics card. I'm really hopeful that this new version will let me start using Ubuntu in a dual boot setup with XP Pro... I'm a gamer as well as a pc tech, so I need both...


I just got a X850 XT because my old card (GeForce 6600 GT) broke. For some other reasons I did a complete reinstal of Ubuntu 7.10.
The graphics and desktop-effects seem to work out of the box with the radeon drivers, but I get frequent lockups and I suspect its because of the drivers.
So eventually I'm going to try the restricted fglrx drivers.

---

### Post by lostcause64 on 2007-11-30
Still can not boot to the Ubuntu disk.  :(  Just tried a new download of 7.10, disk verified and all.

If I take the ATI card out, I can do pretty much anything I want with Ubuntu. Otherwise, I boot to the disk, tell it to "Start or Install Ubuntu", it will begin loading, then just hang at the "loading bar" underneath the Ubuntu logo. Same with Safe Graphics mode.

Maybe this weekend I'll work up the patience to pull the ATI card, which is a Sapphire build, do the install of Ubuntu, and see if I can get it to work under this thread's recommendation. Or maybe my friend with the old 7800 nVidia card will come through and I won't have to worry about it...

---

### Post by vladislavko on 2007-12-01
Please, I need your help.
I am new to Ubuntu and have only small experience with linux
I have Fujitsu Siemens Amilo Pi 2530 notebook with ATI RADEON MOBILITY HD 2300
What can I do to make my graphic card working right?
I have to download any drivers? I guess yes..

Thanks for all
Vladi

---

### Post by Yellow Pasque on 2007-12-03
> **vladislavko said:**
> Please, I need your help.
I am new to Ubuntu and have only small experience with linux
I have Fujitsu Siemens Amilo Pi 2530 notebook with ATI RADEON MOBILITY HD 2300
What can I do to make my graphic card working right?
I have to download any drivers? I guess yes..

Thanks for all
Vladi
Use the RadeonHD support for basic 2d support.
[http://www.phoronix.com/scan.php?page=article&item=843&num=1](http://www.phoronix.com/scan.php?page=article&item=843&num=1)

---

### Post by gonzolono on 2007-12-03
Now I don't fully understand how and why BUT I have got my ATI radeon x1300 pro driver working as properly as I understand it.

I used this:

[http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support#]("http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support#")

and the ati wiki (where it made sense)

I also got a reply from someone who told me that my screen was only displaying in exactly one quarter because the compiz screen reso settings were telling it to. So i deleted it and hey presto it works.

What I need now is some suggestions to test my driver's settings to make sure that I'm not cheering too soon.  Also I'd like to get VLC playing DVDs a little smoother.  Any ideas?

any rendering settings that may help this?  There is a slight diagonal patterning when the film has a lot of fast scene changes.

---

### Post by Fabio K on 2007-12-03
EDIT: Sorry, it was updated to mesa 7.0.2 but when I turned off my pc, it got back to mesa 7.0.1. Updating mesa to 7.0.2 with fglrx installed enables direct rendering, but I don't know why it got back to 7.0.1.

Hey everyone!!
I think I found a way!!
Right now, I made something incredible (but i'm not sure because I have just read the info shown on screen. *not tested*).

It was showing mesa before. I was just wasting time then I got this idea: Why not update Mesa drivers? I done it following the instructions to compile it in the FAQ of mesa3d.org, compiled using some options, but I'm sure they were 'linux-dri' and 'linux-x86'. I have not rebooted my computer or did anything after that.

> fabio@Fabio:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon 9550 / X1050 Series
OpenGL version string: 2.0.6958 Release

fabio@Fabio:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon 9550 / X1050 Series
OpenGL version string: 2.0.6958 Release
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_shader, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shader_objects, GL_ARB_shading_language_100, GL_ARB_shadow, 
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, 
    GL_ATI_fragment_shader, GL_ATI_meminfo, GL_ATI_separate_stencil, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_EXT_vertex_array, 
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_texgen_reflection, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, 
    GL_WIN_swap_hint, WGL_EXT_swap_control

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x43 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x44 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x45 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x46 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x47 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x48 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x49 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x4a 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x63 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x64 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x65 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x66 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x67 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x68 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x69 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x6a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x6b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6f 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x70 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x71 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x72 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x84 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
fabio@Fabio:~$ 


Used fglrx from restricted drivers >> now I'm going to see if it doesn't disable after I turn off my pc.

Fabio K

---

### Post by lostcause64 on 2007-12-04
Ok, still no luck...:(

If my Sapphire built ATI X850XT is connected to the pc, Ubuntu 7.10 will freeze after the 3rd bar fills in under the Ubuntu logo. If I remove the card, installs, boots, and works normally with the integrated Intel card.

UUUUUUUUUUUURRRRRRRGGGGGGGGGG!!!

---

### Post by z-itou16 on 2007-12-05
hi guys how are you?
i am not really pro into linux yet, hope with experiences and studies get me better since i really want to learn a lot of this. 

i have a x1950GT. right now using i am using kubuntu 7.04 feisty, which is so nice. 

i followed this guide here[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide") i did have to build distro pkg, config kernel module, edit xorg.conf and other stuff which is in the guide and it worked for me.

maybe you can try it out. failure is part of the learning so keep it up and keep trying. 

peace to all guys

---

### Post by z-itou16 on 2007-12-05
why dont you try the fail-mode, usually it appear before it boots to os. grub if you have it.

i have the entries and when i have prob with it i tried that option to conf stuff. 


maybe that may help

---

### Post by MozartlovesUbun2 on 2007-12-05
ouch
it all becomes very jerky from time to time for no reason at all, aargh

---

### Post by solidsteel144 on 2007-12-05
Does this driver support the HD 2900 Pro? (R600).

---

### Post by devosion on 2007-12-06
On a hunch I checked my glxinfo and fglrxinfo. And I found out that both are working on separate displays...

> :~$ fglrxinfo
display: :**0.0**  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.0.6473 (8.37.6)


> :~$ glxinfo
name of display: :**1.0**
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 1.2 (2.0.6473 (8.37.6))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon


Im not exactly sure how this happened but considering how I havent been able to load anything requiring OpenGL, like Tremulous, its beginning to make sense. How can I change this so that both fglrx and glx operate on the same display?

Here is my xorg.conf if it helps at all.

> Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "DELL 1704FPT"
	Option	     "DPMS"
	HorizSync    30-81 
	VertRefresh  56-76 

EndSection

Section "Device"
	Identifier  "Generic Video Card"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Generic Video Card"
	Monitor    "DELL 1704FPT"
	DefaultDepth     24
	SubSection "Display"
		Modes    "1280x1024" "1024x768" "800x600" 
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection


And also is it necessary to use aticonfig since from what I understand all it does is edit xorg.conf? Or does it make other changes?

---

### Post by lostcause64 on 2007-12-06
Since I seem to be a glutton for punishment, I stripped out Gutsy in favor of installing the Alt CD version of Gutsy to try and get this Sapphire built X850XT (R480) going.  Everything went fine throughout the install, set the desired resolution to 1280x1024, but the exact same fraggin' thing happens when it boots...  I get to the dual boot menu, selected 7.10 and hit enter.  It begins booting, but hangs at the exact same point - the 3rd bar under the Ubuntu graphic logo - with no error messages what so ever.  

Is there a way to change the graphic settings from the Grub loader?  Perhaps an instruction manual to do so?  Without removing the card, I can't get into Ubuntu at the Terminal or anything else except Grub.  If I remove the card, I can go to the Restricted Drivers info, but it states I have no hardware requiring those drivers.  Might just be me, but I think the fix for this has to be with the card installed... but what do I know, I'm a noob to Ubuntu/Linux...

Thanks for everyone's help so far...

John

---

### Post by Melcar on 2007-12-06
> **devosion said:**
> ...


And also is it necessary to use aticonfig since from what I understand all it does is edit xorg.conf? Or does it make other changes?

Instead of using aticonfig to initialize the driver, just make the following additions/changes under the "device" section of the xorg.conf:



Section "Device"
	Driver		"fglrx"
	Option		"VideoOverlay"		"on"
	Option		"OpenGLOverlay"		"off"
EndSection

You may also want to add in the option "XaaNoOffscreenPixmaps" since that seems to fix the corrupted mouse pointer issue many are experiencing with these drivers.

---

### Post by lostcause64 on 2007-12-06
Well, that's that...

I now no longer have to worry about this issue as my ATI card just failed outright.  Saw it coming, I did.  I was afraid that changing out the card that much would cause a problem, and it did.

Gee, guess I can run Ubuntu now... just can't game anymore...

John

---

### Post by devosion on 2007-12-06
> **Melcar said:**
> Instead of using aticonfig to initialize the driver, just make the following additions/changes under the "device" section of the xorg.conf:



Section "Device"
	Driver		"fglrx"
	Option		"VideoOverlay"		"on"
	Option		"OpenGLOverlay"		"off"
EndSection

You may also want to add in the option "XaaNoOffscreenPixmaps" since that seems to fix the corrupted mouse pointer issue many are experiencing with these drivers.

I already have those included in my xorg.conf, well except the "XaaNoOffscreenPixmaps" since I have not have any problems with a corrupted mouse pointer yet.

---

### Post by MozartlovesUbun2 on 2007-12-08
suspend hibernate still not working under new envy

user switching causes a crash

jerky slow scrolling and animation

i am not a happy bunny

---

### Post by _UsUrPeR_ on 2007-12-11
I am running an ATI Radeon 9800 Pro with 128 RAM.

I have also tried Envy, no dice. It seemed to boot properly with the 7-10 manually installed drivers, but then covers the entire desktop with a white screen. The only thing being visible is the mouse cursor. 

I tried "The easy way", just checking the box for "restricted drivers" installs everything, but comes up with both screens mirrored instead of an expanded desktop. When I try to assign a placement to the monitors in "Screens & Graphics" and reboot, it comes back in the graphics safe mode. 

I am trying to get my Dell 2405fpw and SGI 20E21 to dual-desktop.

when trying to run the following:

```
root~# aticonfig --initial=dual-head --screen-layout=left
```

I get the following error:

```
*** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0xbfd1fa03 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7d0092b]
aticonfig[0x805c5c7]
aticonfig[0x805c875]
aticonfig[0x8054528]
aticonfig[0x804985e]
aticonfig[0x80496cb]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7ca9050]
aticonfig[0x8049601]
======= Memory map: ========
08048000-08067000 r-xp 00000000 03:02 12469510   /usr/bin/aticonfig
08067000-0806a000 rw-p 0001e000 03:02 12469510   /usr/bin/aticonfig
0806a000-0808b000 rw-p 0806a000 00:00 0          [heap]
b7c85000-b7c86000 rw-p b7c85000 00:00 0 
b7c86000-b7c88000 r-xp 00000000 03:02 9831374    /lib/tls/i686/cmov/libdl-2.6.1.so
b7c88000-b7c8a000 rw-p 00001000 03:02 9831374    /lib/tls/i686/cmov/libdl-2.6.1.so
b7c8a000-b7c8e000 r-xp 00000000 03:02 12469555   /usr/lib/libXdmcp.so.6.0.0
b7c8e000-b7c8f000 rw-p 00003000 03:02 12469555   /usr/lib/libXdmcp.so.6.0.0
b7c8f000-b7c91000 r-xp 00000000 03:02 12469544   /usr/lib/libXau.so.6.0.0
b7c91000-b7c92000 rw-p 00001000 03:02 12469544   /usr/lib/libXau.so.6.0.0
b7c92000-b7c93000 rw-p b7c92000 00:00 0 
b7c93000-b7dd7000 r-xp 00000000 03:02 9831371    /lib/tls/i686/cmov/libc-2.6.1.so
b7dd7000-b7dd8000 r--p 00143000 03:02 9831371    /lib/tls/i686/cmov/libc-2.6.1.so
b7dd8000-b7dda000 rw-p 00144000 03:02 9831371    /lib/tls/i686/cmov/libc-2.6.1.so
b7dda000-b7ddd000 rw-p b7dda000 00:00 0 
b7ddd000-b7e00000 r-xp 00000000 03:02 9831375    /lib/tls/i686/cmov/libm-2.6.1.so
b7e00000-b7e02000 rw-p 00023000 03:02 9831375    /lib/tls/i686/cmov/libm-2.6.1.so
b7e02000-b7eef000 r-xp 00000000 03:02 12469538   /usr/lib/libX11.so.6.2.0
b7eef000-b7ef3000 rw-p 000ed000 03:02 12469538   /usr/lib/libX11.so.6.2.0
b7ef3000-b7f00000 r-xp 00000000 03:02 12469559   /usr/lib/libXext.so.6.4.0
b7f00000-b7f01000 rw-p 0000d000 03:02 12469559   /usr/lib/libXext.so.6.4.0
b7f01000-b7f08000 r-xp 00000000 03:02 12469581   /usr/lib/libXrender.so.1.3.0
b7f08000-b7f09000 rw-p 00006000 03:02 12469581   /usr/lib/libXrender.so.1.3.0
b7f09000-b7f0e000 r-xp 00000000 03:02 12469579   /usr/lib/libXrandr.so.2.1.0
b7f0e000-b7f0f000 rw-p 00005000 03:02 12469579   /usr/lib/libXrandr.so.2.1.0
b7f0f000-b7f10000 rw-p b7f0f000 00:00 0 
b7f13000-b7f1d000 r-xp 00000000 03:02 9797699    /lib/libgcc_s.so.1
b7f1d000-b7f1e000 rw-p 0000a000 03:02 9797699    /lib/libgcc_s.so.1
b7f1e000-b7f20000 rw-p b7f1e000 00:00 0 
b7f20000-b7f3a000 r-xp 00000000 03:02 9797645    /lib/ld-2.6.1.so
b7f3a000-b7f3c000 rw-p 00019000 03:02 9797645    /lib/ld-2.6.1.so
bfd0b000-bfd20000 rw-p bfd0b000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)
```


The same error occurs when I try to run aticonfig --initial without the dual-head 
Any suggestions would greatly be appreciated.

---

### Post by Melcar on 2007-12-11
> **joelkillspeople said:**
> I am running an ATI Radeon 9800 Pro with 128 RAM.

I have also tried Envy, no dice. It seemed to boot properly with the 7-10 manually installed drivers, but then covers the entire desktop with a white screen. The only thing being visible is the mouse cursor. 

I tried "The easy way", just checking the box for "restricted drivers" installs everything, but comes up with both screens mirrored instead of an expanded desktop. When I try to assign a placement to the monitors in "Screens & Graphics" and reboot, it comes back in the graphics safe mode. 

I am trying to get my Dell 2405fpw and SGI 20E21 to dual-desktop.

when trying to run the following:

```
root~# aticonfig --initial=dual-head --screen-layout=left
```

I get the following error:

```
*** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0xbfd1fa03 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7d0092b]
aticonfig[0x805c5c7]
aticonfig[0x805c875]
aticonfig[0x8054528]
aticonfig[0x804985e]
aticonfig[0x80496cb]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7ca9050]
aticonfig[0x8049601]
======= Memory map: ========
08048000-08067000 r-xp 00000000 03:02 12469510   /usr/bin/aticonfig
08067000-0806a000 rw-p 0001e000 03:02 12469510   /usr/bin/aticonfig
0806a000-0808b000 rw-p 0806a000 00:00 0          [heap]
b7c85000-b7c86000 rw-p b7c85000 00:00 0 
b7c86000-b7c88000 r-xp 00000000 03:02 9831374    /lib/tls/i686/cmov/libdl-2.6.1.so
b7c88000-b7c8a000 rw-p 00001000 03:02 9831374    /lib/tls/i686/cmov/libdl-2.6.1.so
b7c8a000-b7c8e000 r-xp 00000000 03:02 12469555   /usr/lib/libXdmcp.so.6.0.0
b7c8e000-b7c8f000 rw-p 00003000 03:02 12469555   /usr/lib/libXdmcp.so.6.0.0
b7c8f000-b7c91000 r-xp 00000000 03:02 12469544   /usr/lib/libXau.so.6.0.0
b7c91000-b7c92000 rw-p 00001000 03:02 12469544   /usr/lib/libXau.so.6.0.0
b7c92000-b7c93000 rw-p b7c92000 00:00 0 
b7c93000-b7dd7000 r-xp 00000000 03:02 9831371    /lib/tls/i686/cmov/libc-2.6.1.so
b7dd7000-b7dd8000 r--p 00143000 03:02 9831371    /lib/tls/i686/cmov/libc-2.6.1.so
b7dd8000-b7dda000 rw-p 00144000 03:02 9831371    /lib/tls/i686/cmov/libc-2.6.1.so
b7dda000-b7ddd000 rw-p b7dda000 00:00 0 
b7ddd000-b7e00000 r-xp 00000000 03:02 9831375    /lib/tls/i686/cmov/libm-2.6.1.so
b7e00000-b7e02000 rw-p 00023000 03:02 9831375    /lib/tls/i686/cmov/libm-2.6.1.so
b7e02000-b7eef000 r-xp 00000000 03:02 12469538   /usr/lib/libX11.so.6.2.0
b7eef000-b7ef3000 rw-p 000ed000 03:02 12469538   /usr/lib/libX11.so.6.2.0
b7ef3000-b7f00000 r-xp 00000000 03:02 12469559   /usr/lib/libXext.so.6.4.0
b7f00000-b7f01000 rw-p 0000d000 03:02 12469559   /usr/lib/libXext.so.6.4.0
b7f01000-b7f08000 r-xp 00000000 03:02 12469581   /usr/lib/libXrender.so.1.3.0
b7f08000-b7f09000 rw-p 00006000 03:02 12469581   /usr/lib/libXrender.so.1.3.0
b7f09000-b7f0e000 r-xp 00000000 03:02 12469579   /usr/lib/libXrandr.so.2.1.0
b7f0e000-b7f0f000 rw-p 00005000 03:02 12469579   /usr/lib/libXrandr.so.2.1.0
b7f0f000-b7f10000 rw-p b7f0f000 00:00 0 
b7f13000-b7f1d000 r-xp 00000000 03:02 9797699    /lib/libgcc_s.so.1
b7f1d000-b7f1e000 rw-p 0000a000 03:02 9797699    /lib/libgcc_s.so.1
b7f1e000-b7f20000 rw-p b7f1e000 00:00 0 
b7f20000-b7f3a000 r-xp 00000000 03:02 9797645    /lib/ld-2.6.1.so
b7f3a000-b7f3c000 rw-p 00019000 03:02 9797645    /lib/ld-2.6.1.so
bfd0b000-bfd20000 rw-p bfd0b000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)
```


The same error occurs when I try to run aticonfig --initial without the dual-head 
Any suggestions would greatly be appreciated.

Try to initialize the driver manually.  Go into /etc/X11/xorg.conf and make the proper changes yourself.

Section "Device"
Driver "fglrx"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
EndSection

---

### Post by terribletrouble on 2007-12-12
Would anyone know, why when using the fglrx driver, for an ATI card in a laptop, as soon as I add a modeline for specific timings that are not automatically recognized, X will not start, and actually freezes the machine (need to physically power off and boot into single to get back again)?

I have an IBM laptop, with ATI Mobile 9600 card, I am trying to get dual head, with laptop display as primary, and samsung 226bw as second. The samsung does 1920x1200 and 1600x1200 or 1024x768, but to get to the optimum, you need 1680x1050.

Each time you have a modeline entry, bang, X crashes. Yet, in Kubuntu, you can manually set the 1680x1050 resolution just fine, and it rewrites the xorg.conf file with what you would think looks correct, but as I said, reboot and you have had it.

Does anyone know of a reason why adding a modeline would cause this?

---

### Post by morozj on 2007-12-13
> **Temüjin said:**
> Use the RadeonHD support for basic 2d support.
[http://www.phoronix.com/scan.php?page=article&item=843&num=1](http://www.phoronix.com/scan.php?page=article&item=843&num=1)

I was struggling with my HP Pavillion with ATI Radeon HD2350 when I came across this link and it worked fine for me. I was going to post it but have been beaten to it! Thanks.

---

### Post by _UsUrPeR_ on 2007-12-13
I am still having issues. Once I added the following:

```
Section "Device"
Driver "fglrx"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
EndSection
```

It still went into protected mode, and came up with the vesa drivers and a standard 640x480 screen size.

This seems to almost have worked:

```
Section "Files"
EndSection

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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
	Driver		"fglrx"
	BusID		"PCI:2:0:0"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-80
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1600x1200" "1280x1024" "1280x492" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
```

The log on screen comes up ok, but after that, it goes to a white screen and all I can see is the mouse cursor :( This would have been the closest I came to having properly working video. It even detected that I had two monitors.

---

### Post by Yellow Pasque on 2007-12-13
joel,
Try looking at the Xorg logs in the /var/log/ directory. See if you can find the log where fglrx failed. That might give you a clue as to why things failed.

---

### Post by Fabio K on 2007-12-14
Hey everyone,

Maybe I discovered how to enable direct rendering with an ATI Radeon video card!
I've tried many things, but only this one worked to me. I am using 'radeon' video driver in a fresh install. fglrx is NOT installed.
I think it's just needed to update mesa drivers from 7.0.1 to 7.0.2!

There is just one thing I have not mentioned: I'm trying another distro that comes with Mesa 7.0.2 pre-installed. I have already done this in ubuntu 7.10, but mesa automatically downgraded to 7.0.1 when I rebooted my machine.
If someone knows how to upgrade mesa to 7.0.2, then try and see if works. (I'm a Linux noob)

Fabio K

---

### Post by Matheon on 2007-12-14
All,

I'm a real newbie to Linux & Ubuntu (user for about a week). I've had a heck of a time because of the ATI drivers that Gutsy insists that I install from the restricted area. I've concluded that there is no real support for my particular video card.

I have a ATI Radeon X1050. Everything so far as I can tell works great as long as I only use the drivers off of the original install from the Live CD. When I install the new driver from the [restricted driver available] prompt my video gets all screwed up, and I have to re-install again from the CD.

How do I ban the new driver update so the prompt goes away?

Thanks!

---

### Post by solidsteel144 on 2007-12-20
Any news on R600/670 drivers?

---

### Post by luka78 on 2007-12-25
Hi...

This is my card:
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

I use this manual to install driver for it, is this ok, i have problems in Totem, flickering etc, so could it be driver problem:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

how to check did i install it good?

Thank you


p.s.
here you have one test, i'm new in this so, i really need little help

luka@luka:~$ LIBGL_DEBUG=verbose glxinfo
name of display: :0.0
libGL: XF86DRIGetClientDriverName: 5.2.0 radeon (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/radeon_dri.so
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
libGL warning: 3D driver claims to not support visual 0x4b
libGL error: 
Can't open configuration file /etc/drirc: No such file or directory.
libGL error: 
Can't open configuration file /home/luka/.drirc: No such file or directory.
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20061018 AGP 1x x86/MMX+/3DNow!+/SSE NO-TCL
OpenGL version string: 1.3 Mesa 6.5.2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_logic_op, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_histogram, 
    GL_EXT_packed_pixels, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_MESA_ycbcr_texture, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x4b 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

---

### Post by BogusJoe on 2007-12-29
This may be more info than some may need but will give you guys a heads up of what I hope we can work with.  This message is geared mainly towards tseliot asking for help and hopefully to help others with the same type of video  setup.

Have a New system and would really like to get the Video hardware working correctly. 
Main objective: to play 64 bit games and especially Enemy Territory: Quake Wars!

System:  Spider Platform
Mobo:     Asus M3A32-MVP with AMD 790FX chipset  (Bios Ver. 0704)
Proc:      AMD 64 X2 Black Edition 5000+
Mem:     currently 2 gig Crucial BallistiX DDR2 PC2-8500 (1 gig sticks)
Video:    2 x HIS Radeon HD3870 512 meg

Goal:  Hoping to get this system to work in 64bit mode with CrossFire mainly to play ETQW  I would also like to play with Compiz.

General Notes
Have four of the BallistiX 1gig memory modules.  Only 2 will work either in the black slots or yellow slots.  Was able to get 3 gig to work one time.  1 in the yellow slot and 1 each in the black.  I think some other guys may had some success with all memory slots full.  When all four are filled with the above memory, the system will not post.  Going to upgrade to only 2 x 2 gig sticks.

The Black Edition 5000+ is unlocked.  (This comes from AMD like this) Normal speed is 2.6ghz, easily over-clocked to 3.1 and 3.3 with only minor voltage increase and cooling only with air. Current speed 3.3ghz with CPU voltage at 1.4125

Current operating systems 64bit only (fresh install on all)
Ubuntu Hardy Heron 8.04
Ubuntu Gutsy 7.10
Fedora Core 8

Fedora is just something I play with from time to time, but mainly interested in making things work correctly (Video Games and Compiz) with the Ubuntu Style.  My knowledge of  the general Linux  OS is very little except for creating game servers and storage/file  servers or making use of Samba.  Played and tinkered with Linux since RedHat 6.0

I have tried ENVY with Gutsy 7.10 64  from a clean install but all I got was a blank screen.   Edited  xorg.conf  and disabled Composite.  Also noticed there was no statement for DRI.  First tried as is. Did not edit xorg.conf, then edited and disabled composite, then again and added the statement for DRI. 


Current 12-29-07 with a clean install (Ubuntu/Gutsy 7.10 64bit) and only updates from Ubuntu with ATI package :

 ATI binary X.Org driver
Video driver for ATI graphics accelerators
Video driver for the ATI Radeon and FireGL graphics accelerators.
This version of the ATI driver officially supports:
* FireGL: V7350, V7300, V7200, V7100, V5200, V5100, V5000, V3400, V3300, V3200, V3100, X3-256, X3, X2-256, Z1-128, T2-128, X1-128, X1-256p
* FireMV: 2200 (Single card PCI-e configuration)
* Mobility FireGL: V5000, T2
* Mobility Radeon: X1800, X1600, X1400, X1300, X800, X700, X600, X300, 9800, 9600, 9550, 9500
* Radeon Xpress: 200M series, 1250 IGP, 200 series
* Radeon: X1900, X1800, X1600, X1300, X850, X800, X700, X600, X550, X300, 9800, 9700, 9600, 9550, 9500
ATI All-in-Wonder variants of the above cards/chips are also supported, but video capture is not.
This package provides 2D display drivers and hardware accelerated OpenGL.

I do understand the above package does not include any info or driver info for the Radeon HD3870, tried it just to see what would happen.


bogusjoe@gutsy64-710:~$ **fglrxinfo**
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
bogusjoe@gutsy64-710:~$

bogusjoe@gutsy64-710:~$ **glxinfo | grep direct**
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
bogusjoe@gutsy64-710:~$

bogusjoe@gutsy64-710:~$ **glxinfo | grep direct && glxinfo | grep glx && glxinfo | grep OpenGL**
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
OpenGL extensions:
bogusjoe@gutsy64-710:~$

```

xorg.conf

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc ATI Default Card"
        Driver          "vesa"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Sceptre"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc ATI Default Card"
        Monitor         "Sceptre"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1920x1080" "1600x1200" "1280x1024" "1024x768" "832x624" "800x$
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
EndSection

```

```

bogusjoe@gutsy64-710:~$ lspci -v
00:00.0 Host bridge: ATI Technologies Inc RD790 Northbridge only dual slot PCI-e_GFX and HT3 K8 part
        Subsystem: ATI Technologies Inc RD790 Northbridge only dual slot PCI-e_GFX and HT3 K8 part
        Flags: bus master, 66MHz, medium devsel, latency 0
        Memory at <ignored> (64-bit, non-prefetchable)
        Capabilities: <access denied>

00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00007000-00007fff
        Memory behind bridge: f7a00000-f7afffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
        Capabilities: <access denied>

00:04.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port A) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00008000-00009fff
        Memory behind bridge: f7b00000-f7bfffff
        Capabilities: <access denied>

00:06.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port C) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: f7c00000-f7cfffff
        Capabilities: <access denied>

00:07.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port D) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 0000b000-0000cfff
        Memory behind bridge: f7d00000-f7dfffff
        Capabilities: <access denied>

00:09.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port E) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        Memory behind bridge: f7e00000-f7efffff
        Capabilities: <access denied>

00:0b.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx1 port A) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: f7f00000-f7ffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: <access denied>

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01 [AHCI 1.0])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81ef
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
        I/O ports at 6000 [size=8]
        I/O ports at 5000 [size=4]
        I/O ports at 4000 [size=8]
        I/O ports at 3000 [size=4]
        I/O ports at 2000 [size=16]
        Memory at f79ff800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8288
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        Memory at f79fe000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8288
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at f79fd000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8288
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at f79fc000 (32-bit, non-prefetchable) [size=4K]

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8288
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at f79fb000 (32-bit, non-prefetchable) [size=4K]

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8288
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at f79fa000 (32-bit, non-prefetchable) [size=4K]

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8288
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        Memory at f79ff000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
        Subsystem: ASUSTeK Computer Inc. Unknown device 8288
        Flags: 66MHz, medium devsel
        I/O ports at 0b00 [size=16]
        Capabilities: <access denied>

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8288
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 16
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at ff00 [size=16]

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
        Subsystem: ASUSTeK Computer Inc. Unknown device 8288
        Flags: bus master, slow devsel, latency 64, IRQ 16
        Memory at f79f4000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
        Subsystem: ASUSTeK Computer Inc. Unknown device 8288
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=07, subordinate=07, sec-latency=64
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: f8000000-febfffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 9501 (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Unknown device 2542
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at f7af0000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at 7000 [size=256]
        Expansion ROM at f7ac0000 [disabled] [size=128K]
        Capabilities: <access denied>

01:00.1 Audio device: ATI Technologies Inc Unknown device aa18
        Subsystem: ATI Technologies Inc Unknown device aa18
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at f7aec000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

02:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b1) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Marvell Technology Group Ltd. 88SE6121 SATA II Controller
        Flags: bus master, fast devsel, latency 0, IRQ 16
        I/O ports at 9800 [size=8]
        I/O ports at 9400 [size=4]
        I/O ports at 9000 [size=8]
        I/O ports at 8800 [size=4]
        I/O ports at 8400 [size=16]
        Memory at f7bffc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81f8
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at f7cfc000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at a800 [size=256]
        Expansion ROM at f7cc0000 [disabled] [size=128K]
        Capabilities: <access denied>

04:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b2) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Marvell Technology Group Ltd. 88SE6121 SATA II Controller
        Flags: bus master, fast devsel, latency 0, IRQ 19
        I/O ports at c800 [size=8]
        I/O ports at c400 [size=4]
        I/O ports at c000 [size=8]
        I/O ports at b800 [size=4]
        I/O ports at b400 [size=16]
        Memory at f7dffc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

05:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
        Subsystem: Unknown device 1a3b:1034
        Flags: fast devsel, IRQ 16
        Memory at f7ef0000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>

06:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 9501 (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Unknown device 2542
        Flags: fast devsel, IRQ 10
        Memory at d0000000 (64-bit, prefetchable) [disabled] [size=256M]
        Memory at f7ff0000 (64-bit, non-prefetchable) [disabled] [size=64K]
        I/O ports at d000 [disabled] [size=256]
        Expansion ROM at f7fc0000 [disabled] [size=128K]
        Capabilities: <access denied>

06:00.1 Audio device: ATI Technologies Inc Unknown device aa18
        Subsystem: ATI Technologies Inc Unknown device aa18
        Flags: bus master, fast devsel, latency 0, IRQ 5
        Memory at f7fec000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

07:06.0 Multimedia audio controller: Creative Labs SB X-Fi
        Subsystem: Creative Labs Unknown device 002c
        Flags: bus master, medium devsel, latency 64, IRQ 9
        I/O ports at e800 [size=32]
        Memory at fea00000 (64-bit, non-prefetchable) [size=2M]
        Memory at f8000000 (64-bit, non-prefetchable) [size=64M]
        Capabilities: <access denied>

07:08.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8294
        Flags: bus master, medium devsel, latency 64, IRQ 22
        Memory at fe9ff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

bogusjoe@gutsy64-710:~$
00:00.0 Host bridge: ATI Technologies Inc RD790 Northbridge only dual slot PCI-e_GFX and HT3 K8 part
        Subsystem: ATI Technologies Inc RD790 Northbridge only dual slot PCI-e_GFX and HT3 K8 part
        Flags: bus master, 66MHz, medium devsel, latency 0
        Memory at <ignored> (64-bit, non-prefetchable)
        Capabilities: <access denied>

00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00007000-00007fff
        Memory behind bridge: f7a00000-f7afffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
        Capabilities: <access denied>

00:04.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port A) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00008000-00009fff
        Memory behind bridge: f7b00000-f7bfffff
        Capabilities: <access denied>

00:06.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port C) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: f7c00000-f7cfffff
        Capabilities: <access denied>

00:07.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port D) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 0000b000-0000cfff
        Memory behind bridge: f7d00000-f7dfffff
        Capabilities: <access denied>

00:09.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port E) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        Memory behind bridge: f7e00000-f7efffff
        Capabilities: <access denied>

00:0b.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx1 port A) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: f7f00000-f7ffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: <access denied>

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01 [AHCI 1.0])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81ef
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
        I/O ports at 6000 [size=8]
        I/O ports at 5000 [size=4]
        I/O ports at 4000 [size=8]
        I/O ports at 3000 [size=4]
        I/O ports at 2000 [size=16]
        Memory at f79ff800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8288
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        Memory at f79fe000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8288
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at f79fd000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8288
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at f79fc000 (32-bit, non-prefetchable) [size=4K]

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8288
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at f79fb000 (32-bit, non-prefetchable) [size=4K]

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8288
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at f79fa000 (32-bit, non-prefetchable) [size=4K]

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8288
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        Memory at f79ff000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
        Subsystem: ASUSTeK Computer Inc. Unknown device 8288
        Flags: 66MHz, medium devsel
        I/O ports at 0b00 [size=16]
        Capabilities: <access denied>

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8288
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 16
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at ff00 [size=16]

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
        Subsystem: ASUSTeK Computer Inc. Unknown device 8288
        Flags: bus master, slow devsel, latency 64, IRQ 16
        Memory at f79f4000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
        Subsystem: ASUSTeK Computer Inc. Unknown device 8288
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=07, subordinate=07, sec-latency=64
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: f8000000-febfffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 9501 (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Unknown device 2542
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at f7af0000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at 7000 [size=256]
        Expansion ROM at f7ac0000 [disabled] [size=128K]
        Capabilities: <access denied>

01:00.1 Audio device: ATI Technologies Inc Unknown device aa18
        Subsystem: ATI Technologies Inc Unknown device aa18
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at f7aec000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

02:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b1) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Marvell Technology Group Ltd. 88SE6121 SATA II Controller
        Flags: bus master, fast devsel, latency 0, IRQ 16
        I/O ports at 9800 [size=8]
        I/O ports at 9400 [size=4]
        I/O ports at 9000 [size=8]
        I/O ports at 8800 [size=4]
        I/O ports at 8400 [size=16]
        Memory at f7bffc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81f8
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at f7cfc000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at a800 [size=256]
        Expansion ROM at f7cc0000 [disabled] [size=128K]
        Capabilities: <access denied>

04:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b2) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Marvell Technology Group Ltd. 88SE6121 SATA II Controller
        Flags: bus master, fast devsel, latency 0, IRQ 19
        I/O ports at c800 [size=8]
        I/O ports at c400 [size=4]
        I/O ports at c000 [size=8]
        I/O ports at b800 [size=4]
        I/O ports at b400 [size=16]
        Memory at f7dffc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

05:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
        Subsystem: Unknown device 1a3b:1034
        Flags: fast devsel, IRQ 16
        Memory at f7ef0000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>

06:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 9501 (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Unknown device 2542
        Flags: fast devsel, IRQ 10
        Memory at d0000000 (64-bit, prefetchable) [disabled] [size=256M]
        Memory at f7ff0000 (64-bit, non-prefetchable) [disabled] [size=64K]
        I/O ports at d000 [disabled] [size=256]
        Expansion ROM at f7fc0000 [disabled] [size=128K]
        Capabilities: <access denied>

06:00.1 Audio device: ATI Technologies Inc Unknown device aa18
        Subsystem: ATI Technologies Inc Unknown device aa18
        Flags: bus master, fast devsel, latency 0, IRQ 5
        Memory at f7fec000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

07:06.0 Multimedia audio controller: Creative Labs SB X-Fi
        Subsystem: Creative Labs Unknown device 002c
        Flags: bus master, medium devsel, latency 64, IRQ 9
        I/O ports at e800 [size=32]
        Memory at fea00000 (64-bit, non-prefetchable) [size=2M]
        Memory at f8000000 (64-bit, non-prefetchable) [size=64M]
        Capabilities: <access denied>

07:08.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8294
        Flags: bus master, medium devsel, latency 64, IRQ 22
        Memory at fe9ff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

```

```

bogusjoe@gutsy64-710:~$ glxinfo
name of display: :0.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x3d 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
bogusjoe@gutsy64-710:~$

```

---

### Post by lurkus ignoramus on 2007-12-29
I have a similar system to the above poster, and similar problems getting my hardware to function (no Crossfire, at least!). I'm a Linux newbie, and I would appreciate explicit instructions with any assistance. My hardware in question looks something like this:

Motherboard: ASUS M2R32-MVP
Processor: AMD Athlon 64 X2 Black Edition 6400+ (3.2ghz)
Video Card: Sapphire Radeon HD2900 512mb

I doubt the processor is much of a problem, but the 64-bit architecture may be significant (I am using Gutsy Gibbon 64).  The motherboard, at times during various installations, seemed to have compatibility issues of its own, but I seem to have managed to get sound and other ports all functioning as of now.

While I currently have flgrx installed as my device driver, I have tried the other ATI compatible drivers with little luck.  At one point everything seemed to work fine, but at that very moment, I decided to test another setting.  The latest flgrx drivers I had downloaded and installed from AMD were uninstalled and I was told to reboot.  After doing so, X-Windows would not load, giving me nothing but evil black screens.

Using the console and my Ubuntu Live CD, I was able to revert my xorg.conf and get X-Windows started.  I then reinstalled the packages I had previously built and installed them. Now, Catalyst had worked previously, but this time around it does not function. Additionally, my window movements became very choppy, as did scrolling text. Watching the System Monitor while moving windows shows that the CPUs are definitely doing all the work. flgrx is still the installed driver, and Ubuntu is using the restricted driver... At one point (I believe this is when things were working the best) the restricted driver light was green, but unchecked, now it is checked. I believe I restarted the PC at some point, and Ubuntu 'updated' the restricted driver, reverting back to the repository's version of flgrx.

Does that seem plausible? 

What do I do at this point in order to get my video card working at least semi-properly?  I would like to be able to utilize 2D acceleration, run 3D screen savers or visualizations, etc. Currently, my video card doesn't seem to function as much more than a pass-through to the monitor... I don't believe it is being used for video playback either. If there is any other information I can provide that will help please let me know.

```
fglrxinfo
fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```

```
glxinfo
glxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```

```
lspci -v
00:00.0 Host bridge: ATI Technologies Inc RD580 [CrossFire Xpress 3200] Chipset Host Bridge
        Subsystem: ATI Technologies Inc RD580 [CrossFire Xpress 3200] Chipset Host Bridge
        Flags: bus master, 66MHz, medium devsel, latency 0

00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fbd00000-fbdfffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: <access denied>

00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fbe00000-fbefffff
        Capabilities: <access denied>

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01 [AHCI 1.0])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81ef
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 21
        I/O ports at b000 [size=8]
        I/O ports at a000 [size=4]
        I/O ports at 9000 [size=8]
        I/O ports at 8000 [size=4]
        I/O ports at 7000 [size=16]
        Memory at fbcffc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10 [OHCI])
        Subsystem: ATI Technologies Inc SB600 USB (OHCI0)
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        Memory at fbcfe000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10 [OHCI])
        Subsystem: ATI Technologies Inc SB600 USB (OHCI1)
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at fbcfd000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10 [OHCI])
        Subsystem: ATI Technologies Inc SB600 USB (OHCI2)
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at fbcfc000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10 [OHCI])
        Subsystem: ATI Technologies Inc SB600 USB (OHCI3)
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at fbcfb000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10 [OHCI])
        Subsystem: ATI Technologies Inc SB600 USB (OHCI4)
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at fbcfa000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20 [EHCI])
        Subsystem: ATI Technologies Inc SB600 USB Controller (EHCI)
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        Memory at fbcff800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
        Subsystem: ASUSTeK Computer Inc. Unknown device 4385
        Flags: 66MHz, medium devsel
        I/O ports at 0b00 [size=16]
        Memory at fed00000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
        Subsystem: ATI Technologies Inc SB600 IDE
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 16
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at ff00 [size=16]
        Capabilities: <access denied>

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
        Subsystem: ATI Technologies Inc SBx00 Azalia
        Flags: bus master, slow devsel, latency 64, IRQ 16
        Memory at fbcf4000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
        Subsystem: ATI Technologies Inc SB600 PCI to LPC Bridge
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=64
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fbf00000-fbffffff
        Prefetchable memory behind bridge: 88000000-880fffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 9400 (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Unknown device 3000
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at fbdf0000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at c000 [size=256]
        Expansion ROM at fbdc0000 [disabled] [size=128K]
        Capabilities: <access denied>

01:00.1 Audio device: ATI Technologies Inc Unknown device aa00
        Subsystem: ATI Technologies Inc Unknown device aa00
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at fbdec000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8202
        Flags: bus master, fast devsel, latency 0, IRQ 17
        I/O ports at dc00 [size=8]
        I/O ports at d880 [size=4]
        I/O ports at d800 [size=8]
        I/O ports at d480 [size=4]
        I/O ports at d400 [size=16]
        Memory at fbefe000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

03:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81fe
        Flags: bus master, medium devsel, latency 64, IRQ 22
        Memory at fbfff800 (32-bit, non-prefetchable) [size=2K]
        I/O ports at ec00 [size=128]
        Capabilities: <access denied>

03:04.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
        Subsystem: ASUSTeK Computer Inc. Marvell 88E8001 Gigabit Ethernet Controller (Asus)
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 23
        Memory at fbff8000 (32-bit, non-prefetchable) [size=16K]
        I/O ports at e800 [size=256]
        Expansion ROM at 88000000 [disabled] [size=128K]
        Capabilities: <access denied>

```

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"glx"
EndSection

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

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc ATI Default Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc ATI Default Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
EndSection

Section "Extensions"
	Option		"Composite"	"0"
	Option		"Composite"	"0"
EndSection
```

---

### Post by djezzer on 2007-12-30
Hi,

After having installed Ubuntu 7.10 (on my new computer, I am used to version 6 LTS) I discovered issues with my broad screen, not running in 1650x1080@60hz resolution.

Hardware: Acer M5620 computer, with ATI Radeon HD 2600 Pro, Samsung 206BW LCD monitor.

Software: Ubuntu 7.10, ATI closed source videodrivers (most recent, 20th december 2007).

Already tried the following solutions (sorry for not giving source urls):
- xorg.conf edited by hand, to accept resolution 1650x1080
- xorg.conf edited by hand, with homemade modeline, based on EDID information
- multiple re-installations of the ATI drivers
- many of the suggested solutions here and in other fora

My question is: what can I do to get my hardware combination running in broadscreen resolution? I am linux user since 1996, coming from Suse through Slackware and Gentoo to Ubuntu. Which means I know how to edit some settings - and I am not too afraid to get my hands dirty ;-)

Thanks in advance, any help is appreciated.

Greetz, dJezzer :cool:

---

### Post by Yellow Pasque on 2007-12-30
**djezzer**, the resolution should be 1680x1050, not 1650x1080.
If all else fails, you can use the open-source radeonHD drivers (see link in my signature) right now and at least you'll get full 2D support and full resolutions.

**lurkus**, run:
```
sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1
``` and see if that helps.

**BogusJoe** There's no 3870 support in the fglrx driver right now, much less crossfire support for 2 of them. You can use the open-source radeonHD driver (see link in my sig) for basic 2D support at this time.

---

### Post by alhasan on 2007-12-30
Somehow my video driver is corrupted and I can't get into XWindows at all. What should I do in this case? I tried to reconfigure xorg.conf, still get an error msg like:
AIGLX: Screen 0 is not DRI capable.

My machine is IBM Thinkpad T60, driver is ATI Raedon X1400 and I am using ubuntu 7.10.
Please help!

Thanks,
Hasan

---

### Post by Yellow Pasque on 2007-12-30
alhasan, please post your xorg,conf file.

---

### Post by lurkus ignoramus on 2007-12-31
Linking the libraries doesn't seem to have a discernible effect.  I'm not sure what to do at this point...

I would like to try uninstalling the flgrx drivers that I have installed, including catalyst, blacklist them from being automatically updated, and attempt a fresh install from the package I built from the newest release from AMD.  Unfortunately, I'm not sure how to uninstall the drivers and associated programs or utilize blacklisting (though I remember reading about it somewhere). :?

 I could be mistaken, but it seems like window operation was smoothest with the initial setup. Could I really be achieving the best results through VESA? I know this card can achieve much better results than what I am seeing, but I feel like I'm going to need a lot of assistance to get it there.  Also, it seems like every time I test out a different setting I break things a little more. Uninstalling and reinstalling seems to cause issues, but I could be imagining things...

Thanks in advance for more help, please?

---

### Post by Yellow Pasque on 2007-12-31
lurkus: Sorry that didn't work for you.
To uninstall the ATI drivers installed from ATI site:
```
cd /usr/share/ati
sudo sh ./fglrx-uninstall.sh
```

If it's the one from the Ubuntu repo:
```
sudo dpkg -P xorg-driver-fglrx
```

---

### Post by lurkus ignoramus on 2007-12-31
Temüjin, thanks again for all the help, both direct and indirect...

I should clarify and say that after linking the libraries I -was- able to load Catalyst... There just seems to be little point, as I can change no options, and it seems to do nothing to alter performance...

I uninstalled the repository drivers and reinstalled the ones I built from the AMD site, but I'm still not sure if any of it was done correctly... This didn't seem to change performance, so I attempted to revert to VESA, but am unable.  I decided to attempt to install the open source radeonhd driver, and found the instructions to be lacking... I did get the driver installed, by adding 'sudo' before -all- the commands.  After installation, my windows moved fluidly and my scrolling was beautiful.  Unfortunately, I was also using 100% of both cores 100% of the time, and the CPU was running at 66c (compared to the current 34c)... Since that seemed too hot, and didn't allow me to do much with the PC, I reverted (after a few attempts) to *some* fglrx config, and I believe I successfully blacklisted the fglrx restricted driver updating. Now I'm back at the same situation, where my graphics card doesn't seem to do much, and even moving windows maxes out my CPU.

So... While I'm sure there is no easy answer, my next round of questioning involves my xorg.conf. First, if there are multiple 'monitor', 'screen', or 'device' sections how is it determined which is used? Can I remove the unused ones? Is the correct one being used? If I have composite '0', that is the same as 'off', right? There is no AIGLX information, is it supported by the fglrx driver? Can I manually turn composite 'on' and add AIGLX to xorg.conf with the newest version of fglrx, and, if so, how?

Here is my latest monstrosity of a xorg.conf:
```

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"dbe"
	Load		"v4l"
EndSection

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

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc ATI Default Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Screen	0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc ATI Default Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1400	1050
		Modes		"1400x1050@60"	"1280x1024@60"	"1280x960@60"	"1152x864@75"	"1024x768@43"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"1024x768@85"	"832x624@75"	"800x600@60"	"800x600@85"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@85"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "Extensions"
	Option		"Composite"	"0"
	Option		"Composite"	"0"
EndSection
Section "ServerFlags"
EndSection
```

```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
```

```
glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_fragment_program, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texgen_reflection, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
azurescens@azurescens:/$ glxinfo -v
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_fragment_program, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texgen_reflection, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

Visual ID: 23  depth=24  class=TrueColor
    bufferSize=24 level=0 renderType=rgba doubleBuffer=1 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=0
    auxBuffers=0 depthSize=16 stencilSize=0
    accum: redSize=0 greenSize=0 blueSize=0 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    visualCaveat=None
    Opaque.
Visual ID: 24  depth=24  class=TrueColor
    bufferSize=24 level=0 renderType=rgba doubleBuffer=1 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=0
    auxBuffers=0 depthSize=16 stencilSize=8
    accum: redSize=16 greenSize=16 blueSize=16 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    visualCaveat=None
    Opaque.
Visual ID: 25  depth=24  class=TrueColor
    bufferSize=32 level=0 renderType=rgba doubleBuffer=1 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=8
    auxBuffers=0 depthSize=16 stencilSize=8
    accum: redSize=16 greenSize=16 blueSize=16 alphaSize=16
    multiSample=0  multiSampleBuffers=0
    visualCaveat=None
    Opaque.
Visual ID: 26  depth=24  class=TrueColor
    bufferSize=32 level=0 renderType=rgba doubleBuffer=0 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=8
    auxBuffers=0 depthSize=16 stencilSize=8
    accum: redSize=16 greenSize=16 blueSize=16 alphaSize=16
    multiSample=0  multiSampleBuffers=0
    visualCaveat=None
    Opaque.
Visual ID: 27  depth=24  class=DirectColor
    bufferSize=24 level=0 renderType=rgba doubleBuffer=1 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=0
    auxBuffers=0 depthSize=16 stencilSize=0
    accum: redSize=0 greenSize=0 blueSize=0 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    visualCaveat=None
    Opaque.
Visual ID: 28  depth=24  class=DirectColor
    bufferSize=24 level=0 renderType=rgba doubleBuffer=1 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=0
    auxBuffers=0 depthSize=16 stencilSize=8
    accum: redSize=16 greenSize=16 blueSize=16 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    visualCaveat=None
    Opaque.
Visual ID: 29  depth=24  class=DirectColor
    bufferSize=32 level=0 renderType=rgba doubleBuffer=1 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=8
    auxBuffers=0 depthSize=16 stencilSize=8
    accum: redSize=16 greenSize=16 blueSize=16 alphaSize=16
    multiSample=0  multiSampleBuffers=0
    visualCaveat=None
    Opaque.
Visual ID: 2a  depth=24  class=DirectColor
    bufferSize=32 level=0 renderType=rgba doubleBuffer=0 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=8
    auxBuffers=0 depthSize=16 stencilSize=8
    accum: redSize=16 greenSize=16 blueSize=16 alphaSize=16
    multiSample=0  multiSampleBuffers=0
    visualCaveat=None
    Opaque.
```

---

### Post by djezzer on 2008-01-01
> djezzer, the resolution should be 1680x1050, not 1650x1080.
I'm sorry, a typo :(
> 
If all else fails, you can use the open-source radeonHD drivers (see link in my signature) right now and at least you'll get full 2D support and full resolutions.

Temüjin , thanks for your help, I got the radeonhd driver at work. It's pleasant to see a real bw screen on linux ;-)

After activating a new issue popped up: the "gksu displayconfig-gtk" program stopped working. It pulls a draft of 77% of processorpower on my quadcore6600 and still gives nothing to show. Since a made no other modifications on my system I think the radeonhd drivers might have something to do with it.

Do you happen to have any suggestions how I can solve this issue? (if it is indeed an issue).

Thanks anyway, best wishes,

Greetz, dJezzer  :cool:

---

### Post by bluebrew on 2008-01-01
Can somebody please help me with my ATI driver issue?

[http://ubuntuforums.org/showthread.php?t=655074](http://ubuntuforums.org/showthread.php?t=655074)

I started discussing it here [http://ubuntuforums.org/showthread.php?t=648549&page=2](http://ubuntuforums.org/showthread.php?t=648549&page=2)
then made a new thread about it as instructed

I'm totally lost and still new with Ubuntu

any advise or guidance is and will be appreciated
Thank you

---

### Post by KailasNarendran on 2008-01-02
I followed the instructions at [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide) and they seemed to work well for me.

I still can't get the HDMI output from my GA-MA69GM-S2h Motherboard (with integrated RAdeon x1250) working.  or the analog output for that matter..

anyone have any ideas or experience on that front? trying to make a HTPC

---

### Post by Dezinteres on 2008-01-02
Hello , 
I have a little problem myself.I have a sapphire hd2600xt and ubuntu 7.10 64 bits.
I instaled the driver with envy and i get direct rendering yes but i cannot enable desktop effects from compiz.If i install xserver-xgl i can enable the desktop effects but i have no direct rendering .
So .. it is like i have to choose between the desktop effects or the direct rendering.
Is there any way that i could have both ? 
Thank u 


adi@ubuntu:~$ fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2600 XT
OpenGL version string: 2.1.7170 Release


adi@ubuntu:~$ glxinfo | grep direct
direct rendering: Yes


adi@ubuntu:~$ compiz
Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

---

### Post by Yellow Pasque on 2008-01-02
> **Dezinteres said:**
> Hello , 
I have a little problem myself.I have a sapphire hd2600xt and ubuntu 7.10 64 bits.
I instaled the driver with envy and i get direct rendering yes but i cannot enable desktop effects from compiz.

As i posted to your other thread:
> **Temüjin said:**
> ```
sudo gedit /usr/bin/compiz
```

Put fglrx in the line that says WHITELIST=" "

---

### Post by Dezinteres on 2008-01-02
Thank you so much.Everything is ok now ;) Again .. thank u

---

### Post by Yellow Pasque on 2008-01-02
EDIT: Thanks staff.

---

### Post by cyberanth on 2008-01-02
Hello,

I'm new to Ubuntu so you may not know everything yet.

Anyway, I have been having some trouble installing drivers and such, I was wounding if their are ATI drivers for ATI Wounder TV cards. I have one of the old models but if I can get Ubuntu to access it then thats one less reason to reinstall Windows as a dual boot.

Can you help with codec as well?

Thanks.

---

### Post by new2gutsy on 2008-01-06
I wish it was that easy for me,I was trying to install mine now I am running in low graphics mode upon a restart
I was originally trying to get my driver as I couldn't use no effects
I'm very new to Linux so I would appreciate some step by step instructions on what to do to get mine working

I downloaded the appropriate driver from the ati site,ran the command as stated from the quoted comments and just got this: 
joey@joey-desktop:~$ sudo sh ./ati-driver-installer-8.28.8.run
[sudo] password for joey:
sh: ./ati-driver-installer-8.28.8.run: No such file or directory
joey@joey-desktop:~$ 

I have the driver installer saved to my desktop....need more assistance please???
and note I installed and tried Envy and that didn't work,said that my system as not supported or sumthing

Also I cannot open the Restricted Drivers manager,says that "Your hardware does not need any restricted drivers"


I need some guidance please?
Thank you



> **mjpolifka said:**
> On a fresh install, I downloaded the newest version (8.40), ran 

sudo sh ./ati-driver-installer-8.40.4-x86.x86_64.run
sudo aticonfig --initial --force

rebooted, and now everything works.  I have been messing around with the Binary HOWTO for a week and searching Google for an answer, but this simple solution is the only one that worked for me, and to be honest I'm not sure why.  Before I did this, DRI was not found and I had no direct rendering.

Card: Radeon X1650 PRO AGP 512MB
Intel P4 2.66GHz 2.5GB Memory
Getting ~1500FPS

---

### Post by Yellow Pasque on 2008-01-06
new2gutsy: what video card do you have? I'm guessing it's older than a Radeon 9500 since the ATI site told you to download an old, outdated driver (8.28.8). If so, fglrx does not support your card and you don't want to run an old version. You should easily be able to do desktop effects with the "radeon" driver.

Press Ctrl+Alt+F1, login to the terminal and run:
```
sudo dpkg-reconfigure xserver-xorg
```
Pick the radeon driver. Restart and you should be out of low graphics mode.

---

### Post by handy on 2008-01-07
Thanks Alberto, Envy worked beautifully on my 24" iMac ATi sporting a Radeon HD 2600 Pro, making Ubuntu 7.10 behave at it's best. :-D

---

### Post by new2gutsy on 2008-01-07
Yes my card is a 9250se
So I done exactly as you posted however it said that "package xserver-org is not installed and no info is available"
What do I do now?

Thank you 


> **Temüjin said:**
> new2gutsy: what video card do you have? I'm guessing it's older than a Radeon 9500 since the ATI site told you to download an old, outdated driver (8.28.8). If so, fglrx does not support your card and you don't want to run an old version. You should easily be able to do desktop effects with the "radeon" driver.

Press Ctrl+Alt+F1, login to the terminal and run:
```
sudo dpkg-reconfigure xserver-xorg
```
Pick the radeon driver. Restart and you should be out of low graphics mode.

---

### Post by Yellow Pasque on 2008-01-07
new2gutsy,
Read carefully, it's **x**org, not org.

---

### Post by new2gutsy on 2008-01-07
Ohh thanks but now I feel dumb
I shall check when I get home from work to see if I typed it wrong in the terminal or when I posted it

Thanks again


> **Temüjin said:**
> new2gutsy,
Read carefully, it's **x**org, not org.

---

### Post by ipellant on 2008-01-08
G'Day fellow ATI sufferers,

I used UNIX and CLIX many years ago. In mid December I started looking at Linux... and with an ATI X1650 Pro AGP card, this has proven to the be the biggest time consumer I have ever encountered.

Unleashing the Ubuntu Restricted Drivers usually causes a lock up on reboot. Familiar to many of us !?

The latest ATI proprietary drivers 8.44.3 install fairly easily and the Catalyst Control Center works fine on Ubuntu 7.10 64 bit... except for the lack of 3D acceleration... OK, I've tried all the posted hacks and patches and nothing works. I've tried similar on openSUSE 10.3. Much the same problem.

In a parallel unvierse, other distros such as Sabayon, lock up completely on boot up with the X1650 Pro card installed.

My clues so far are in Catalyst indicating "Bus Type AGP" with a" Bus Setting 0x". (plus the hauntingly annoying Mesa drivers).

Run: dmesg|grep aperture and it shows:

[   43.643684] Checking aperture...
[   43.643687] CPU 0: aperture @ f0000000 size 32 MB
[   43.643702] Your BIOS doesn't leave a aperture memory hole
[   43.700151] Mapping aperture over 65536 KB of RAM @ 4000000
[   44.259005] agpgart: No usable aperture found.
[   44.259036] agpgart: Consider rebooting with iommu=memaper=2 to get a good aperture.

Ah Ha! On bootup, as Ubuntu starts, there is a brief flash of a message that also suggests setting iommu=memaper=2 to enable an AGP aperture. I've tried. Doesn't help.

The base problem may be in the motherboard: Gigabyte GA-K8N@ (rev. 2.0) BIOS rev: 19 not having any AGP aperture settings. It relies on the OS setting up the hardware. (Sempron 3400+, 1GB RAM)

This computer is my experimental / test beast and on it's other two drives, I boot Win 2K and Win XP. No problems with the X1650 Pro under Winders (except for ATI not officially supporting Win 2K for the card... the Powercolor web site has the 2K drivers, as did their OEM CD)

My suspicion is that the 7.10 Gutsy kernel is not building with an AGP aperture or hardware acceleration port. I'm still trying to decode that one... AGPGART is being outmoded ? The X1650 has an AGP bridge to PCI-E internals? I don't know. There are many red herrings on this trail.

At this point, I am very disappointed with Linux on the X1650 Pro card. Before all the recent attempts, the box hosted an ancient ATI All in Wonder Pro (Radeon 7200). That card would not boot the Ubuntu 7.10 CD... but did boot the Sabayon distro. Now the reverse boot lockups.

Please, if any users are struggling with an X1650 Pro AGP card, please try: # dmesg | grep aperture 
and see if you have an aperture problem... and let me know... and is there a guru with a solution?

Cheers, Ian

---

### Post by ipellant on 2008-01-08
G'Day fellow ATI sufferers,

I used UNIX and CLIX many years ago. In mid December I started looking at Linux... and with an ATI X1650 Pro AGP card, this has proven to the be the biggest time consumer I have ever encountered.

Unleashing the Ubuntu Restricted Drivers usually causes a lock up on reboot. Familiar to many of us !?

The latest ATI proprietary drivers 8.44.3 install fairly easily and the Catalyst Control Center works fine on Ubuntu 7.10 64 bit... except for the lack of 3D acceleration... OK, I've tried all the posted hacks and patches and nothing works. I've tried similar on openSUSE 10.3. Much the same problem.

In a parallel unvierse, other distros such as Sabayon, lock up completely on boot up with the X1650 Pro card installed.

My clues so far are in Catalyst indicating "Bus Type AGP" with a" Bus Setting 0x". (plus the hauntingly annoying Mesa drivers).

Run: dmesg|grep aperture and it shows:

[   43.643684] Checking aperture...
[   43.643687] CPU 0: aperture @ f0000000 size 32 MB
[   43.643702] Your BIOS doesn't leave a aperture memory hole
[   43.700151] Mapping aperture over 65536 KB of RAM @ 4000000
[   44.259005] agpgart: No usable aperture found.
[   44.259036] agpgart: Consider rebooting with iommu=memaper=2 to get a good aperture.

Ah Ha! On bootup, as Ubuntu starts, there is a brief flash of a message that also suggests setting iommu=memaper=2 to enable an AGP aperture. I've tried. Doesn't help.

The base problem may be in the motherboard: Gigabyte GA-K8N@ (rev. 2.0) BIOS rev: 19 not having any AGP aperture settings. It relies on the OS setting up the hardware. (Sempron 3400+, 1GB RAM)

This computer is my experimental / test beast and on it's other two drives, I boot Win 2K and Win XP. No problems with the X1650 Pro under Winders (except for ATI not officially supporting Win 2K for the card... the Powercolor web site has the 2K drivers, as did their OEM CD)

My suspicion is that the 7.10 Gutsy kernel is not building with an AGP aperture or hardware acceleration port. I'm still trying to decode that one... AGPGART is being outmoded ? The X1650 has an AGP bridge to PCI-E internals? I don't know. There are many red herrings on this trail.

At this point, I am very disappointed with Linux on the X1650 Pro card. Before all the recent attempts, the box hosted an ancient ATI All in Wonder Pro (Radeon 7200). That card would not boot the Ubuntu 7.10 CD... but did boot the Sabayon distro. Now the reverse boot lockups.

Please, if any users are struggling with an X1650 Pro AGP card, please try: # dmesg | grep aperture 
and see if you have an aperture problem... and let me know... and is there a guru with a solution?

Cheers, Ian

---

### Post by new2gutsy on 2008-01-08
Ok I think I got it but not sure
I'm not in low graphic mode no more but yet still can not enable even the normal desktop effects
because i'm not sure is cause the last prompt was to select the color mode and I selected 24bit,after doing that it just opened up the terminal again,not sure what to put ofcourse so I restarted,
Do I have it right now that I'm out of low graphics mode? or is there a way to enable atleast the desktop affects,just concerned as I doubt I could play any games like that can I?

Thank again



> **Temüjin said:**
> new2gutsy: what video card do you have? I'm guessing it's older than a Radeon 9500 since the ATI site told you to download an old, outdated driver (8.28.8). If so, fglrx does not support your card and you don't want to run an old version. You should easily be able to do desktop effects with the "radeon" driver.

Press Ctrl+Alt+F1, login to the terminal and run:
```
sudo dpkg-reconfigure xserver-xorg
```
Pick the radeon driver. Restart and you should be out of low graphics mode.

---

### Post by handy on 2008-01-08
> **ipellant said:**
> G'Day fellow ATI sufferers,

I used UNIX and CLIX many years ago. In mid December I started looking at Linux... and with an ATI X1650 Pro AGP card, this has proven to the be the biggest time consumer I have ever encountered.

Unleashing the Ubuntu Restricted Drivers usually causes a lock up on reboot. Familiar to many of us !?

The latest ATI proprietary drivers 8.44.3 install fairly easily and the Catalyst Control Center works fine on Ubuntu 7.10 64 bit... except for the lack of 3D acceleration... OK, I've tried all the posted hacks and patches and nothing works. I've tried similar on openSUSE 10.3. Much the same problem.

In a parallel unvierse, other distros such as Sabayon, lock up completely on boot up with the X1650 Pro card installed.

My clues so far are in Catalyst indicating "Bus Type AGP" with a" Bus Setting 0x". (plus the hauntingly annoying Mesa drivers).

Run: dmesg|grep aperture and it shows:

[   43.643684] Checking aperture...
[   43.643687] CPU 0: aperture @ f0000000 size 32 MB
[   43.643702] Your BIOS doesn't leave a aperture memory hole
[   43.700151] Mapping aperture over 65536 KB of RAM @ 4000000
[   44.259005] agpgart: No usable aperture found.
[   44.259036] agpgart: Consider rebooting with iommu=memaper=2 to get a good aperture.

Ah Ha! On bootup, as Ubuntu starts, there is a brief flash of a message that also suggests setting iommu=memaper=2 to enable an AGP aperture. I've tried. Doesn't help.

The base problem may be in the motherboard: Gigabyte GA-K8N@ (rev. 2.0) BIOS rev: 19 not having any AGP aperture settings. It relies on the OS setting up the hardware. (Sempron 3400+, 1GB RAM)

This computer is my experimental / test beast and on it's other two drives, I boot Win 2K and Win XP. No problems with the X1650 Pro under Winders (except for ATI not officially supporting Win 2K for the card... the Powercolor web site has the 2K drivers, as did their OEM CD)

My suspicion is that the 7.10 Gutsy kernel is not building with an AGP aperture or hardware acceleration port. I'm still trying to decode that one... AGPGART is being outmoded ? The X1650 has an AGP bridge to PCI-E internals? I don't know. There are many red herrings on this trail.

At this point, I am very disappointed with Linux on the X1650 Pro card. Before all the recent attempts, the box hosted an ancient ATI All in Wonder Pro (Radeon 7200). That card would not boot the Ubuntu 7.10 CD... but did boot the Sabayon distro. Now the reverse boot lockups.

Please, if any users are struggling with an X1650 Pro AGP card, please try: # dmesg | grep aperture 
and see if you have an aperture problem... and let me know... and is there a guru with a solution?

Cheers, Ian

I have a GA-K8NS Ultra-939, which would not accept the X server when trying to install Gentoo, someone in a forum told me that it was due to a bug in the motherboard / BIOS regarding the AGP aperture.  Which was over my head, & I gave up on Gentoo & that machine.

So, I offer no help, it just gives me a chance to trot that AGP aperture stuff out again...

Good luck!

---

### Post by new2gutsy on 2008-01-08
BUMP BUMP :)


> **new2gutsy said:**
> Ok I think I got it but not sure
I'm not in low graphic mode no more but yet still can not enable even the normal desktop effects
because i'm not sure is cause the last prompt was to select the color mode and I selected 24bit,after doing that it just opened up the terminal again,not sure what to put ofcourse so I restarted,
Do I have it right now that I'm out of low graphics mode? or is there a way to enable atleast the desktop affects,just concerned as I doubt I could play any games like that can I?

Thank again

Quote:
Originally Posted by Temüjin View Post
new2gutsy: what video card do you have? I'm guessing it's older than a Radeon 9500 since the ATI site told you to download an old, outdated driver (8.28.. If so, fglrx does not support your card and you don't want to run an old version. You should easily be able to do desktop effects with the "radeon" driver.

Press Ctrl+Alt+F1, login to the terminal and run:
Code:

sudo dpkg-reconfigure xserver-xorg

Pick the radeon driver. Restart and you should be out of low graphics mode.

---

### Post by jdmelton on 2008-01-08
Thanks for this post! It helped me.

My experience with Ubuntu 7.10 desktop on an eMachines T6212 with an AMD Athlon 64 3200 with an ATI Radeon X200 IGP:

1. Installed Gutsy (32 bit), rebooted.

2. Screen was 680x480 with vesa drivers. I set my default screen to my actual monitor in System - Administration - Screens and Graphics.

3. Went to [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

4. Selected Linux x86 - Integrated/Motherboard - Radeon Xpress 200

5. Downloaded. Note! You need to know where it is downloaded to!!! Normally, for a default Gutsy install, this is your desktop.

6. Copied down the instructions above.

7. Rebooted. At the Grub prompt, pressed ESC key, then selected the recovery mode kernel. This boots to a root only mode. This is much easier, in my opinion, for the install.
The 640x480 was not very friendly for the graphical install.

Ran
cd /home/myusername/Desktop (where I downloaded to)
ls (list the directory contents so that I could see the file name)
sh ati-driver-installer-8.443.1-x86.x86_64.run (the version I downloaded)

At the prompts, use the tab key and arrow keys to move around.
Follow the prompts.
Unless you know how to use the text-based web browser, I recommend you choose no to the prompt to start a web browser.

After the install finished, I ran
sudo aticonfig --initial=dual-head --screen-layout=left

8. Rebooted.

Worked!

---

### Post by unshareef on 2008-01-09
Dear Ubuntu Scholars.

I am very excited about Ubuntu and I am beginning to get to grips with it :) Installed Gutsy.

However I am having a few problems. I have a Dell Inspiron 6400 laptop with an ATI X1300 graphics card.

I've been trying to install the latest ATI driver, and I finally succeeded yesterday when my true screen resolution finally appeared along with catalyst control centre.

The problem is: I wanted to make the appearance look a whole lot cooler. So I went to preferences, appearance and tried to switch on visual effects. However, an error appears saying "The composite extension is not available". It says this whether I put it on medium or full.

Any ideas on what the problem could be and how to solve?

Also, how can I check if my intel core duo has been correctly installed. I ask you this because some of the screensavers appear slow and juddery.

Hope you can help, thanks!

---

### Post by Yellow Pasque on 2008-01-09
unshareef, assuming you have compiz installed:
> **Temüjin said:**
> ```
sudo gedit /usr/bin/compiz
```

Put fglrx in the line that says WHITELIST=" "

For your processor, do:
```
sudo dmidecode -t 4
```
and look at the core enabled field.

---

### Post by lurkus ignoramus on 2008-01-10
After many frustrating days attempting to get my **Radeon HD2900 Pro** properly functional under **64-bit Ubuntu 7.10**, I wiped my xorg.conf and let the OS do what it would... Strangely, everything has been running noticeably smoother with no prior configuration.  Since it is functional, I have been working on other issues, beginning the process of file migration, etc. However, the time when I will need to utilize my video card is drawing near, and I find myself puzzling over it once again.

In **'Restricted Drivers Manager'**, **"ATI Accelerated Graphics Driver"** is *not* checked as being enabled, *but is green and labeled "in use"*.  However, in **'Screens and Graphics'** it is apparent that the **"VESA"** driver is being used. This seems strange to me.  Does it mean the card is somehow now being used for 2d acceleration?  I can rationalize the performance difference in no other way... Unfortunately, there is no xorg.conf being written, so I have no idea what settings are being used.

I'm really at a loss... I need to be able to more fully utilize my video card... But I have found no way to get things running as well as with no xorg.conf at all.  When I try various alternatives I'm either confronted with no acceleration and reduced performance, a blank screen that I have to use the LIVE CD to fix, or a strange warped screen wrapping type issue (it's like the desktop is broken up and "word-wrapped" around the monitor) that makes it impossible to use the GUI (ENVY produces this effect).

Any ideas what I can do?

---

### Post by lurkus ignoramus on 2008-01-10
I'm not to the point where I'm attempting to enable Compiz at all, but I'm curious about this nonetheless.

> Put fglrx in the line that says WHITELIST=" "

My file looks like this:

```
# Driver whitelist
WHITELIST="nvidia intel ati radeon fglrx i810"
```

I've never edited this file myself... Is this a common default whitelisting?  Could ENVY have set it this way?  More importantly, should there be some sort of seperator between the drivers?

---

### Post by audiored on 2008-01-11
I can't figure out if I'm just that ignorant or if getting Ubuntu installed and configured really is this difficult. 

Anyway, I have an ATI Radeon X300 SE 128 MB.  I've scoured the forums and google and tried nearly every walk through and faq and forum post that has promised me some solution.  Every time i get one problem fixed I'm just stumped by the very next one.  And it all stems from my apparently crappy graphics card. 

I guess my questions is, is there some other distribution of linux that I should check into?  Is this completely unique to Ubuntu or am I going to run into these problems with any distribution of linux?

Should I just reinstall Windows?  

I guess I'm just a bit disappointed, I really did want to have my desktop set up on linux.

---

### Post by Yellow Pasque on 2008-01-11
> **audiored said:**
> I guess my questions is, is there some other distribution of linux that I should check into?  Is this completely unique to Ubuntu or am I going to run into these problems with any distribution of linux? Should I just reinstall Windows? I guess I'm just a bit disappointed, I really did want to have my desktop set up on linux.
The ATI driver is going to suck equally on each Linux distro. All that should be required for a regular setup with the Ubuntu driver is a simple:
```
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial -f --overlay-type=Xv
```
And reboot.

---

### Post by unshareef on 2008-01-11
Dear Temujin,

I am not sure if I have compiz or not but I must have because when I typed >  sudo gedit /usr/bin/compiz 

it did indeed open a text document and I typed fglrx in to the WHITELIST line as you instructed.

However this did not solve the problem unfortunately :-(

Any other ideas?

Also I check how many cores I have and it said I have 2, as it should. But the screensavers are still so slow? for example spirographX screensaver - is like 1fps.

Thanks for the help

---

### Post by jdb1981 on 2008-01-11
OK, I'm trying to install a Sapphire Radeon 2600 XT on Gutsy. I've tried everything at both the following links, including Envy:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Pre-Installation_Checks](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Pre-Installation_Checks)

  Nothing worked, and now my system is not even recognizing my installation of Ubuntu at all. 
  At first, I just plugged it in, and got a terminal. So I followed the directions for Method #1 on the second link, re-booted, and nothing.  I had to boot into recovery mode just to get a terminal. So, I followed the directions for Method #2 in same link. This at least got me a screen, but it was in limited graphics mode. Then I found the first link, but it was basically the same thing. I tried poking around and doing some of the "If this doesn't work for you" options after the instructions, without results. 
  When I got to the section about editing my xorg.conf file, I kept getting errors because the file didn't exist. I tried to find it in my X11 folder, and it's not there. There are various other filenames, like xorg.config.234927498274, or xorg.config.fglrx-1, or whatever. Issuing fglrxinfo gave me nothing. 
  So, I tried Envy, uninstalled, re-installed, and it seemed to work, at least it brought up my screen in the resolution I expected. But when I tried to enable enhanced effects, it failed. When I issued fglrxinfo, it was still showing Mesa drivers. Also, still no xorg.conf file. All the rest of the fixes I can see seem to revolve around making changes to xorg.conf, and I still don't have one. I don't just want to make one up and stick it in there as root, because I worry I'd screw up something in the settings. 
  Anyway, it's a moot point, because in my quest to fix things, I ran through Envy a couple times, uninstalling and re-installing. Then I tried the Manual option, and tried the last driver option, I think it was 8.0.24 or something, whatever the last option was. 
  This officially killed my system on reboot. No operating system detected, no recovery mode, nothing. So I used gParted and just went ahead and installed WinXP on half my hard drive. When I tried to boot back into Ubuntu to re-install GRUB, (after re-setting it as the boot partition) it still can't find the operating system. Something has gone seriously wrong, obviously. 
  I guess my question is: How do I use the Live CD to just fix my broken Ubuntu installation so it will at least boot? At this point I've given up on using the ATI card, I'm happy to set Ubuntu to just ignore it and use onboard video, if that's even possible. I can watch movies and whatever on Windoze. I think maybe there's a hardware issue between my mobo and video card that Ubuntu just can't handle, and that's fine, but can anyone tell me how to undo everything that all of the above might have done, and just get back to a working installation, or (I can dream) actually get this stupid thing to work? I apologize for the lengthy post, but I wanted to try and detail what I did as much as possible. 
  Thanks in advance!

*/edit*-   If I would be better off just starting a new thread about this, either here, or some other section, please let me know, and I will.

---

### Post by predator on 2008-01-12
I'm having some troubles.. I've followed the guide and not much luck.. problem seems to be with DRI (direct interface?) and the 3D part and getting this setup..

```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```

I am running an ATI X850-PE card in an nvidia2 motherboard, and AMD XP3200+ processor. Running Xubuntu 7.10 Gutsy Gibbon.

I have ensured "load" "DRI" is specified in the "modules" part of my xorg.conf

I have done the symbolic link specified in the howto, and made sure the /usr/X11R6/lib/modules/dri/ directory exists

In my Xorg.0.log file I see:

```
(==) RandR enabled
(WW) fglrx(1): ***********************************
(WW) fglrx(1): * DRI initialization disabled!    *
(WW) fglrx(1): * 2D acceleraton available (MMIO) *
(WW) fglrx(1): * no 3D acceleration available    *
(WW) fglrx(1): ***********************************
(II) fglrx(1): FBADPhys: 0xd4000000 FBMappedSize: 0x04000000
(==) fglrx(1): Write-combining range (0xd4000000,0x4000000)
(II) fglrx(1): FBMM initialized for area (0,0)-(1024,8191)
(II) fglrx(1): FBMM auto alloc for area (0,0)-(1024,768) (front color buffer - $
(II) fglrx(1): Largest offscreen area available: 1024 x 7423
(==) fglrx(1): Backing store disabled
(==) fglrx(1): Silken mouse enabled
(II) fglrx(1): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        Solid Horizontal and Vertical Lines
        Offscreen Pixmaps
        Setting up tile and stipple cache:
                32 128x128 slots
                32 256x256 slots
                16 512x512 slots
(II) fglrx(1): Acceleration enabled
(II) fglrx(1): Direct rendering disabled
(==) fglrx(1): Using hardware cursor


```

A little later, it seems it's having trouble...

```
glesx] __glESXExtensionInit: No GL ES2.0 capable screen found!
**(EE) AIGLX: Screen 0 is not DRI capable**
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
**(EE) AIGLX: Screen 1 is not DRI capable**
(II) GLX: Initialized MESA-PROXY GL provider for screen 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"


```

Here is my lsmod output:

```
Module                  Size  Used by
fglrx                 656352  0 
ppdev                  10244  0 
cpufreq_conservative     8072  0 
cpufreq_stats           7232  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5280  0 
cpufreq_powersave       2688  0 
sbs                    19592  0 
video                  18060  0 
button                  8976  0 
ac                      6148  0 
dock                   10656  0 
container               5504  0 
battery                11012  0 
lp                     12580  0 
snd_intel8x0           34972  4 
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
analog                 13344  0 
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_pcm,snd_seq
xpad                    9988  0 
pcspkr                  4224  0 
gameport               16776  1 analog
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                39952  0 
snd                    54660  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
serio_raw               8068  0 
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
i2c_nforce2             7040  0 
i2c_core               26112  1 i2c_nforce2
nvidia_agp              9756  1 
agpgart                35016  2 fglrx,nvidia_agp
ipv6                  273892  14 
evdev                  11136  3 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
ide_disk               18560  3 
8139cp                 25088  0 
usbhid                 29536  0 
hid                    28928  1 usbhid
amd74xx                15260  0 [permanent]
ide_core              116804  3 ide_cd,ide_disk,amd74xx
8139too                27776  0 
mii                     6528  2 8139cp,8139too
ata_generic             8452  0 
libata                125168  1 ata_generic
scsi_mod              147084  1 libata
ehci_hcd               36492  0 
ohci_hcd               22916  0 
usbcore               138632  5 xpad,usbhid,ehci_hcd,ohci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

```

Here is my xorg.conf - setup for dual monitors, which seems to be working fine.. 

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "screen0" 0 0
  screen 1 "screen1" leftof "screen0"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
	Load		"dri"
EndSection

Section "ServerFlags"
	Option		"Xinerama"	"true"
EndSection

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

Section "Monitor"
	
	Option 		"DPMS"
	Identifier	"CRT"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
	Gamma	1
EndSection

Section "Monitor"
	Identifier	"FP222W"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1680x1050"
	Gamma	1
	Option		"DPMS"
EndSection

Section "Device"
	Identifier	"device1"
	Driver		"fglrx"
	Boardname	"ati"
	Busid		"PCI:2:0:0"
	Screen	1
EndSection

Section "Device"
	Identifier	"device0"
	Driver		"fglrx"
	Boardname	"ati"
#	Option		"OverlayOnCRTC2"	"1"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"Off"
	Busid		"PCI:2:0:0"
	#	Option "SWcursor" "true"
	Screen 0
EndSection

Section "Screen"
	Identifier	"screen1"
	Device		"device1"
	Monitor		"CRT"
	Defaultdepth	24
	SubSection "Display"
		
		#"1024x768@60" "1152x864@75"	"832x624@75"	"1280x1024@75"	"800x600@60"	"1280x960@60"	"800x600@75"	"1280x1024@60"	"800x600@72"	"1280x960@75"	"800x600@56"	"1400x1050@60"	"640x480@75"	"1600x1200@65"	"640x480@72"	"1600x1200@60"	"640x480@60"
		Depth	24
		Modes		"1024x768@75"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"screen0"
	Device		"device0"
	Monitor		"FP222W"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1680x1050@60"	"1600x1024@60"	"1440x900@60"	"1280x800@60"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@56"
	EndSubSection
EndSection

Section "Extensions"
	Option		"Composite"	"false"
EndSection

Section "DRI"
	Group	0
	Mode	0666
EndSection

```

---

### Post by ipellant on 2008-01-13
G'Day Again,

A wet weekend in far north tropical Australia... so back to the X1650 Pro AGP challenge (or dash out and buy an NVidia card type of day).

The problem really is in the AGPGart module not being able to allocate an aperture. I browsed the Gigabyte web site; and under the BIOS FAQ discovered that for some reason, Gigabyte had hidden the AGP settings under Advanced BIOS mode that needs to be toggled into by using <Ctrl> F1.

Duhh... there be the AGP Aperture size and FastWrite options. Default aperture of 32MB is hopeless for the X1650 Pro with 512MB on board. Setting the aperture to 512MB and a reboot and after a rethink by X-Org on boot, the Catalyst driver now shows AGP 8x and the ATI drivers instead of the Mesa drivers...!!

It now steams along. Of course, on the web forums somewhere I had found a note saying that AGP aperture size and fastwrite BIOS settings were critical. It's just that Gigabyte hide the darn things and it needs a <Ctrl> <F1> at the root setup screen to enable the AGP settings. Live and learn.

So... if you have tried all the advice on this forum and still can't get an ATI card working, if it is AGP, check to see if Ubuntu (or any other Linux) failed to set the aperture size. It's all in the BIOS (which may be hidden!)

Cheers, Ian.

---

### Post by unshareef on 2008-01-13
Dear Temujin,

I am not sure if I have compiz or not but I must have because when I typed
Quote:
sudo gedit /usr/bin/compiz
it did indeed open a text document and I typed fglrx in to the WHITELIST line as you instructed.

However this did not solve the problem unfortunately

Any other ideas?

Also I check how many cores I have and it said I have 2, as it should. But the screensavers are still so slow? for example spirographX screensaver - is like 1fps.

Thanks for the help

---

### Post by predator on 2008-01-13
After further investigation, it appears that the problem I was having was with setting in xorg.conf

Option		"Xinerama"	"true"

When set to off, all DRI works, and acceleration instantly turns on.. and I get 10000fps in glxgears. 

Instead I set "MergedFB" "true" under the device settings, which is supposed to be the ATI setting. This enables dual screen pretty well, however I cannot drag any applications between the two monitors, making it a little useless :(

Is it possible the ATI driver is not compatible with Xinerama? 

Any solution? Surely others must have experienced a similar problem..

---

### Post by kakaballi on 2008-01-16
yeah it works.try it

---------------------------------

[Free magazines and music]("http://www.paaspk.com")

---

### Post by jdb1981 on 2008-01-16
Well, forget it. I re-installed Windoze, and I'm just going to have to wait until ATI or Ubuntu or whoever's responsible for this nonsense gets it worked out, I don't have unlimited time to screw around with the computer for something that should be supported out of the box. I wish I had something to contribute to that effort, but if I did, I'd have either picked a better card, or known how to install this one. 
From some of the reading I'm doing, it appears Hardy may natively support ATI and NVIDIA with the manufacturer-supplied drivers, so maybe I'll give it a shot then. This was supposed to be a HTPC, and I can't very well play HD content on my new TV if I can't even get the thing to 1024x768 on a VGA monitor after a week of work and crashing and re-installing and waiting.  It sucks because I really LIKE Ubuntu, but this will be the third time (going back to Dapper) I've installed it, only to eventually have to pull the plug because it didn't yet do what I needed it to. 
Here's hoping that eventually Beryl/Compiz goodness will be mine. Thanks anyway. If anyone has any further ideas, please refer to my previous post (#211) concerning my Sapphire HD2600 XT card and my issues after following the instructions at the beginning of this post to the letter.

---

### Post by boandmichele on 2008-01-17
should be xorg.confusing.  installed ati x600, now:

*everything is freezing up at random intervals, irrelevant of what i am doing at the time.  
*i cant run unreal 2004, except on very low settings (which is ridiculous, considering my system)
*compiz is running perfectly.  ??
*and my firefox is graying out for no reason.  
*oh, and also vlc and totem will close for no reason.  

running ubuntu amd64, core2 6550, 4 gb of ram.  installed fglrx with no luck, enabled restricted ati drivers with no luck.  had no 3d at all with those.  so i installed the ati driver from their site as per the OP in this thread.

any help is appreciated.  im baffled.  windows user since win3.0, and have had it with microsoft and proprietary things. (except, obviously for my video driver and various codecs)

heres my xorg (im sure its something stupid and obvious to you guys ;))

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV380 [Radeon X600 (PCIE)]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV380 [Radeon X600 (PCIE)]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

---

### Post by Yellow Pasque on 2008-01-17
Do theses problems still occur if you disable Compiz? The x600 is on the compiz blacklist.

---

### Post by boandmichele on 2008-01-17
> **Temüjin said:**
> Do theses problems still occur if you disable Compiz? The x600 is on the compiz blacklist.

well, i havent tried that, nor did i even know there was a blacklist!  :)  i will disable it, doesnt hinder productivity, its just fun to have.  ill post back sometime tomorrow to update.  thanks for the suggestion.

---

### Post by unshareef on 2008-01-18
Dear Ubuntu Scholars,

I hope you can help. I believe it is an easy problem but I am new.

I have a Dell Inpiron 6400 laptop with Intel Core Duo 1.73GHz, 1GB RAM, and X1300 ATI Graphics card.

I had problems installing the ATI driver but I believe I have succeeded (I presume) now that my resolution is correct and ATI Catalyst Control Centre has appeared.

THE PROBLEM: I can't enable desktop effects in the Appearance window. When I switch it onto medium or full it says "Composite Extension not available".

Here is my compiz file:

> ```
#!/bin/sh

# Compiz Manager wrapper script

# 

# Copyright (c) 2007 Kristian Lyngstøl <kristian@bohemians.org>

#

# This program is free software; you can redistribute it and/or modify

# it under the terms of the GNU General Public License as published by

# the Free Software Foundation; either version 2 of the License, or

# (at your option) any later version.

#

# This program is distributed in the hope that it will be useful,

# but WITHOUT ANY WARRANTY; without even the implied warranty of

# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the

# GNU General Public License for more details.

#

#

# You should have received a copy of the GNU General Public License

# along with this program; if not, write to the Free Software

# Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA  02110-1301  USA

#

#

# Contributions by: Treviño (3v1n0) <trevi55@gmail.com>, Ubuntu Packages

#

# Much of this code is based on Beryl code, also licensed under the GPL.

# This script will detect what options we need to pass to compiz to get it

# started, and start a default plugin and possibly window decorator.

# 





COMPIZ_BIN_PATH="/usr/local/bin/" # For window decorators and compiz

PLUGIN_PATH="/usr/local/lib/compiz/" 

GLXINFO="/usr/bin/glxinfo"

KWIN="/usr/bin/kwin"

METACITY="/usr/bin/metacity"

COMPIZ_NAME="compiz" # Final name for compiz (compiz.real) 



# For Xgl LD_PRELOAD

LIBGL_NVIDIA="/usr/lib/nvidia/libGL.so.1.2.xlibmesa"

LIBGL_FGLRX="/usr/lib/fglrx/libGL.so.1.2.xlibmesa"



# Minimum amount of memory (in kilo bytes) that nVidia cards need

# to be allowed to start

# Set to 262144 to require 256MB

NVIDIA_MEMORY="65536" # 64MB

NVIDIA_SETTINGS="nvidia-settings" # Assume it's in the path by default



# For detecting what driver is in use, the + is for one or more /'s

XORG_DRIVER_PATH="/usr/lib/xorg/modules/drivers/+"



FALLBACKWM="${METACITY}"

FALLBACKWM_OPTIONS="--replace $@"



# Driver whitelist

WHITELIST="nvidia fglrx intel ati radeon i810"



# blacklist based on the pci ids 

# See http://wiki.compiz-fusion.org/Hardware/Blacklist for details

T="   1002:5954 1002:5854 1002:5955" # ati rs480

T="$T 1002:4153" # ATI Rv350

T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965

T="$T 8086:2972" # i965 (x3000)

T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700 

BLACKLIST_PCIIDS="$T"

unset T



COMPIZ_OPTIONS="--ignore-desktop-hints --replace"

COMPIZ_PLUGINS=""

ENV=""



# Use emerald by default if it exist

USE_EMERALD="yes"



# No indirect by default

INDIRECT="no"



# Set to yes to enable verbose

VERBOSE="yes"



# Echos the arguments if verbose

verbose()

{

	if [ "x$VERBOSE" = "xyes" ]; then

		printf "$*"

	fi

}



# abort script and run fallback windowmanager

abort_with_fallback_wm()

{

	if [ "x$SKIP_CHECKS" = "xyes" ]; then

		verbose "SKIP_CHECKS is yes, so continuing despite problems.\n"

		return 0;

	fi



	verbose "aborting and using fallback: $FALLBACKWM \n"



	if [ -x $FALLBACKWM ]; then

		exec $FALLBACKWM $FALLBACKWM_OPTIONS

	else

		printf "no $FALLBACKWM found, exiting\n"

		exit 1

	fi

}



# Check for non power of two texture support

check_npot_texture()

{

	verbose "Checking for non power of two support: "

	if glxinfo 2> /dev/null | egrep -q '(GL_ARB_texture_non_power_of_two|GL_NV_texture_rectangle|GL_EXT_texture_rectangle|GL_ARB_texture_rectangle)' ; then

		verbose "present. \n";

		return 0;

	else

		verbose "Not present. \n"

		return 1;

	fi



}



# Check for presence of FBConfig

check_fbconfig()

{

	verbose "Checking for FBConfig: "

	if [ "$INDIRECT" = "yes" ]; then

		$GLXINFO -i | grep -q GLX.*fbconfig 

		FB=$?

	else

		$GLXINFO | grep -q GLX.*fbconfig 

		FB=$?

	fi



	if [ $FB = "0" ]; then

		unset FB

		verbose "present. \n"

		return 0;

	else

		unset FB

		verbose "not present. \n"

		return 1;

	fi

}





# Check for TFP

check_tfp()

{

	verbose "Checking for texture_from_pixmap: "

	if [ $($GLXINFO 2>/dev/null | grep GLX_EXT_texture_from_pixmap -c) -gt 2 ] ; then

		verbose "present. \n"

		return 0;

	else

		verbose "not present. \n"

		if [ "$INDIRECT" = "yes" ]; then

			unset LIBGL_ALWAYS_INDIRECT

			INDIRECT="no"

			return 1;

		else

			verbose "Trying again with indirect rendering:\n";

			INDIRECT="yes"

			export LIBGL_ALWAYS_INDIRECT=1

			check_tfp;

			return $?

		fi

	fi

}



# Check wether the composite extension is present

check_composite()

{

	verbose "Checking for Composite extension: "

	if xdpyinfo -queryExtensions | grep -q Composite ; then

		verbose "present. \n";

		return 0;

	else

		verbose "not present. \n";

		return 1;

	fi

}



# Detects if Xgl is running

check_xgl()

{

	verbose "Checking for Xgl: "

	if xvinfo | grep -q Xgl ; then

		verbose "present. \n"

		return 0;

	else

		verbose "not present. \n"

		return 1;

	fi

}



# Check if the nVidia card has enough video ram to make sense

check_nvidia_memory()

{

	MEM=$(${NVIDIA_SETTINGS} -q VideoRam | egrep Attribute\ \'VideoRam\'\ .*: | cut -d: -f3 | sed 's/[^0-9]//g')

	if [ $MEM -lt $NVIDIA_MEMORY ]; then

		verbose "Less than ${NVIDIA_MEMORY}kb of memory and nVidia";

		return 1;

	fi

	return 0;

}



# Check for existence if NV-GLX

check_nvidia()

{

	if [ ! -z $NVIDIA_INTERNAL_TEST ]; then

		return $NVIDIA_INTERNAL_TEST;

	fi

	verbose "Checking for nVidia: "

	if xdpyinfo | grep -q NV-GLX ; then

		verbose "present. \n"

		NVIDIA_INTERNAL_TEST=0

		return 0;

	else

		verbose "not present. \n"

		NVIDIA_INTERNAL_TEST=1

		return 1;

	fi

}



# Check if the max texture size is large enough compared to the resolution

check_texture_size()

{

	TEXTURE_LIMIT=$(glxinfo -l | grep GL_MAX_TEXTURE_SIZE | sed 's/.*=[^0-9]//g')

	RESOLUTION=$(xdpyinfo  | grep -i dimensions: | sed 's/[^0-9]*pixels.*(.*).*//' | sed 's/[^0-9x]*//')

	VRES=$(echo $RESOLUTION | sed 's/.*x//')

	HRES=$(echo $RESOLUTION | sed 's/x.*//')

	verbose "Comparing resolution ($RESOLUTION) to maximum 3D texture size ($TEXTURE_LIMIT): ";

	if [ $VRES -gt $TEXTURE_LIMIT ] || [ $HRES -gt $TEXTURE_LIMIT ]; then

		verbose "Failed.\n"

		return 1;

	fi

	verbose "Passed.\n"

	return 0

}



# check driver whitelist

running_under_whitelisted_driver()

{

	LOG=$(xset q|grep "Log file"|awk '{print $3}')

	if [ -z "$LOG" ];then

		verbose "AIEEEEH, no Log file found \n"

		verbose "$(xset q) \n"

	return 0

	fi

	for DRV in ${WHITELIST}; do

		if egrep -q "Loading ${XORG_DRIVER_PATH}${DRV}_drv\.so" $LOG &&

		   ! egrep -q "Unloading ${XORG_DRIVER_PATH}${DRV}_drv\.so" $LOG; 

		then

			return 0

		fi

	done

	verbose "No whitelisted driver found\n"

	return 1

}



# check pciid blacklist

have_blacklisted_pciid()

{

	OUTPUT=$(lspci -n)

	for ID in ${BLACKLIST_PCIIDS}; do

		if echo "$OUTPUT" | egrep -q "$ID"; then

			verbose "Blacklisted PCIID '$ID' found \n"

			return 0

		fi

	done

	OUTPUT=$(lspci -vn | grep -i VGA)

	verbose "Detected PCI ID for VGA: $OUTPUT\n"

	return 1

}



build_env()

{

	if check_nvidia; then

		ENV="__GL_YIELD=NOTHING "

	fi

	if [ "$INDIRECT" = "yes" ]; then

		ENV="$ENV LIBGL_ALWAYS_INDIRECT=1 "

	fi

	if check_xgl; then

		if [ -f ${LIBGL_NVIDIA} ]; then

			ENV="$ENV LD_PRELOAD=${LIBGL_NVIDIA}"

			verbose "Enabling Xgl with nVidia drivers...\n"

		fi

		if [ -f ${LIBGL_FGLRX} ]; then

			ENV="$ENV LD_PRELOAD=${LIBGL_FGLRX}"

			verbose "Enabling Xgl with fglrx ATi drivers...\n"

		fi

	fi



	ENV="$ENV FROM_WRAPPER=yes"



	if [ -n "$ENV" ]; then

		export $ENV

	fi

}



build_args()

{

	if [ $INDIRECT = "yes" ]; then

		COMPIZ_OPTIONS="$COMPIZ_OPTIONS --indirect-rendering "

	fi

	if check_nvidia; then

		COMPIZ_OPTIONS="$COMPIZ_OPTIONS --loose-binding"

	fi

}



####################

# Execution begins here.



# Read configuration from XDG paths

if [ -z "$XDG_CONFIG_DIRS" ]; then

	test -f /etc/xdg/compiz/compiz-manager && . /etc/xdg/compiz/compiz-manager

else

	test -f $XDG_CONFIG_DIRS/compiz/compiz-manager && . $XDG_CONFIG_DIRS/compiz/compiz-manager

fi



if [ -z "$XDG_CONFIG_HOME" ]; then

	test -f $HOME/.config/compiz/compiz-manager && . $HOME/.config/compiz/compiz-manager

else

	test -f $XDG_CONFIG_HOME/compiz/compiz-manager && .  $XDG_CONFIG_HOME/compiz/compiz-manager

fi



# Don't use compiz when running the failsafe session

if [ "x$GNOME_DESKTOP_SESSION_ID" = "xFailsafe" ]; then

	abort_with_fallback_wm

fi



if [ "x$LIBGL_ALWAYS_INDIRECT" = "x1" ]; then

	INDIRECT="yes";

fi



# if we run under Xgl, we can skip some tests here

if ! check_xgl; then

	# if vesa or vga are in use, do not even try glxinfo (LP#119341)

	if ! running_under_whitelisted_driver || have_blacklisted_pciid; then

		abort_with_fallback_wm

	fi

	# check if we have the required bits to run compiz and if not, 

	# fallback

	if ! check_tfp || ! check_npot_texture || ! check_composite || ! check_texture_size; then

		abort_with_fallback_wm

	fi



	if check_nvidia && ! check_nvidia_memory; then

		abort_with_fallback_wm

	fi



	if ! check_fbconfig; then

		abort_with_fallback_wm

	fi

fi



# load the ccp plugin if present and fallback to plain gconf if not

if [ -f ${PLUGIN_PATH}libccp.so ]; then

	COMPIZ_PLUGINS="$COMPIZ_PLUGINS ccp"

elif [ -f ${PLUGIN_PATH}libgconf.so ]; then

	COMPIZ_PLUGINS="$COMPIZ_PLUGINS glib gconf"

fi



# get environment

build_env

build_args



# start the gtk-window-decorator if present

if [ -x ${COMPIZ_BIN_PATH}emerald ] && [ "$USE_EMERALD" = "yes" ]; then

	verbose "Starting emerald\n"

	${COMPIZ_BIN_PATH}emerald --replace &

elif [ -x ${COMPIZ_BIN_PATH}gtk-window-decorator ] && [ -n "$GNOME_DESKTOP_SESSION_ID" ]; then

	verbose "Starting gtk-window-decorator\n"

	${COMPIZ_BIN_PATH}gtk-window-decorator --replace &

elif [ -x ${COMPIZ_BIN_PATH}kde-window-decorator ] && [ -n "$KDE_FULL_SESSION" ]; then

	verbose "Starting kde-window-decorator\n"

	${COMPIZ_BIN_PATH}kde-window-decorator --replace &

	FALLBACKWM="${KWIN}"

fi



${COMPIZ_BIN_PATH}${COMPIZ_NAME} $COMPIZ_OPTIONS "$@" $COMPIZ_PLUGINS || exec $FALLBACKWM $FALLBACKWM_OPTIONS


```

And here is my xorg file:

> ```


# xorg.conf (xorg X Window System server configuration file)

#

# This file was generated by dexconf, the Debian X Configuration tool, using

# values from the debconf database.

#

# Edit this file with caution, and see the xorg.conf manual page.

# (Type "man xorg.conf" at the shell prompt.)

#

# This file is automatically updated on xserver-xorg package upgrades *only*

# if it has not been modified since the last upgrade of the xserver-xorg

# package.

#

# If you have edited this file but would like it to be automatically updated

# again, run the following command:

#   sudo dpkg-reconfigure -phigh xserver-xorg



Section "ServerLayout"

	

	# Uncomment if you have a wacom tablet

	#	InputDevice     "stylus"	"SendCoreEvents"

	#	InputDevice     "cursor"	"SendCoreEvents"

	#	InputDevice     "eraser"	"SendCoreEvents"

	Identifier	"Default Layout"

  screen 0 "aticonfig-Screen[0]" 0 0

	Inputdevice	"Generic Keyboard"

	Inputdevice	"Configured Mouse"

	Inputdevice	"Synaptics Touchpad"

EndSection



Section "Files"

EndSection



Section "Module"

	Load		"glx"

EndSection



Section "ServerFlags"

	Option		"AIGLX"	"off"

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

	Option		"Device"	"/dev/input/mice"

	Option		"Protocol"	"ImPS/2"

	Option		"ZAxisMapping"	"4 5"

	Option		"Emulate3Buttons"	"true"

EndSection



Section "InputDevice"

	Identifier	"Synaptics Touchpad"

	Driver		"synaptics"

	Option		"SendCoreEvents"	"true"

	Option		"Device"	"/dev/psaux"

	Option		"Protocol"	"auto-dev"

	Option		"HorizEdgeScroll"	"0"

EndSection



Section "InputDevice"

	Identifier	"stylus"

	Driver		"wacom"

	Option		"Device"	"/dev/input/wacom"

	Option		"Type"	"stylus"

	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY

EndSection



Section "InputDevice"

	Identifier	"eraser"

	Driver		"wacom"

	Option		"Device"	"/dev/input/wacom"

	Option		"Type"	"eraser"

	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY

EndSection



Section "InputDevice"

	Identifier	"cursor"

	Driver		"wacom"

	Option		"Device"	"/dev/input/wacom"

	Option		"Type"	"cursor"

	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY

EndSection



Section "Monitor"

	Identifier	"aticonfig-Monitor[0]"

	Option		"VendorName"	"ATI Proprietary Driver"

	Option		"ModelName"	"Generic Autodetecting Monitor"

	Option		"DPMS"	"true"

EndSection



Section "Device"

	Identifier	"aticonfig-Device[0]"

	Driver		"fglrx"

EndSection



Section "Screen"

	Identifier	"aticonfig-Screen[0]"

	Device		"aticonfig-Device[0]"

	Monitor		"aticonfig-Monitor[0]"

	Defaultdepth	24

	SubSection "Display"

		Viewport	0	0

		Depth	24

	EndSubSection

EndSection



Section "Extensions"

	Option		"Composite"	"Disable"

	Option		"Composite"	"0"

EndSection


```

Please note: At the end of the Xorg file, it says "Composite" "Disable". When I changed this to enable, I then tried to switch on desktop effects. It almost seemed to work but then an error said "Could not enable desktop effects". I restarted the computer to see if it would work then but what I found was that my desktop arrangement had been ruined. My bottom panel had gone to the top and my top panel had gone to the bottom and all the buttons in the panels swapped places with each other . . . . WEIRD!

I very much hope somebody out there can help me. Very much appreciated.

Thanks

---

### Post by boandmichele on 2008-01-18
> **boandmichele said:**
> well, i havent tried that, nor did i even know there was a blacklist!  :)  i will disable it, doesnt hinder productivity, its just fun to have.  ill post back sometime tomorrow to update.  thanks for the suggestion.okay, i tried that.  unreal tournament 2004 is still choppy as can be, and that is only IF it runs long enough to enter a match.  it, along with totem and vlc still close.  if figure that they (totem/vlc) close if i am tracking through a video file.  (dragging the little square to jump ahead).  

so far firefox is okay, hasnt grayed out, and compiz is completely disabled.

---

### Post by angels on 2008-01-18
Hi unshareef,
> **unshareef said:**
> 

THE PROBLEM: I can't enable desktop effects in the Appearance window. When I switch it onto medium or full it says "Composite Extension not available".



I have some problems with the new driver, too, but...for the desktop effects, you have to comment out  the line "composite...", as I read in the guide here: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

It should look like this:
> Section "Extensions"
	Option	    "Composite" "0" #if commented-->the AIGLX enabled by default, i.e. Desktop effect are enabled by default
EndSection

maybe you may read once again the instructions...it works for me, but if I comment-out this line, I can really enable the extra effects, but the video doesn't play :(

I don't know if I can fix that...so when I like to see a fency desktop, I comment this line out, and if I want to watch the video, I uncomment it, and disable the composite ... maybe someone knows how to fix that?

I hope that is helpful for you.
Cheers, Angels

---

### Post by angels on 2008-01-18
**Monitor detection**...I tried to configure xorg.conf - add modeline specific for my LCD monitor (as suggested in [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.12_Driver_Manually guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.12_Driver_Manually"), but whatever I tried to add, the X window ran in low-graphic mode;
thus, I cannot add modeline for my monitor, not even vertical or horizontal refresh. I checked at the ATI Catalyst Control Center and everything is fine, but .. I would like to connect my computer with the TV, and I have no idea, how to do that, as I cannot add the mode for each of the monitors  (just for the record, I'm a newby in Linux). I saw in this thread that I can configure DualMonitor from the terminal with **sudo aticonfig --initial=dual-head --screen-layout=left**
(**thanks to [SIZE="1"]jdmelton[/SIZE]** :)). I did this, and now I have a new xorg.conf file, with two monitors and all other stuff, but as the second monitor is a TV, how can I configure that?
Anyhow, my graphic card is ATI Radeon X300, and I run Ubuntu 7.10.

I hope some can help me ...

**My new xorg.conf file:**

> ```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	Screen         "aticonfig-Screen[1]" LeftOf "aticonfig-Screen[0]"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "si"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "TexturedVideoSync" "on"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

**Part of my old, still working xorg.conf**

> ```

Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "si"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"

EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "0" 
EndSection
```

---

### Post by bwtranch on 2008-01-20
This doesn't work. I don't care what you say. I have tried it on all my machines and it just doesn't work.

---

### Post by diPSy on 2008-01-20
Hi. i install ATI drivers by Restricted drivers manager for my Radeon 9600. Now, 3d works fine, but i have really problems with playing videos in tottem. it's really slow down when i make right click and it's have very slow playback speed in fullscreen. With basic drivers it's works fine, but 3d was very slow. How i can fix it?

Here is my xorg.conf

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
	Load		"dri"
	Load		"v4l"
	Load		"glx"
EndSection
Section "device" #  
	Identifier	"device1"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection
Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" #  
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "device" #  
	Identifier	"device2"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:0:1"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection
Section "screen" #  
	Identifier	"screen2"
	Device		"device2"
	Defaultdepth	24
	Monitor		"monitor2"
EndSection
Section "monitor" #  
	Identifier	"monitor2"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection
```

---

### Post by angels on 2008-01-20
as I stated before, you have to comment out the section **Option "Composite" "0"**, because the driver already use AIGLX:

# Section "Extensions"
#        Option  "Composite" "0"
# EndSection


you can check also here [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually)

I hope this will help,
Angels

---

### Post by diPSy on 2008-01-21
I try this, but nothing happens. Also, i cant enable normal desktop effects. Remember, i install driver by drivers manager, not by downloading it's from ati website.

---

### Post by ykpaiha on 2008-01-21
For info
on a fresh install the new drivers didn't work at all
ati radeon 3850 512 mo + 22 inch 
as I tried all the trick here and there I insulted my choice of ati card
Then back to the envy driver (previous version with the screen size bug) then reinstall over it the new 8.1 and here it worked ?!!!!!
1680x1050 with compiz great I still have a bug when I restart or user change but at least it is usable for me.
try out it worth!
And if someone have an explanation.....

---

### Post by angels on 2008-01-21
> **diPSy said:**
> I try this, but nothing happens. Also, i cant enable normal desktop effects. Remember, i install driver by drivers manager, not by downloading it's from ati website.

Sorry... so as I understand, you have proprietary drivers installed, and restricted driver in use and enabled? try to make composite true:
Option "Composite" "true" 

that's worked for me
I followed this thread [http://ubuntuforums.org/showthread.php?t=569654](http://ubuntuforums.org/showthread.php?t=569654)
I hope now I understood better and this will help you

---

### Post by diPSy on 2008-01-21
Big thx for useful link. But i dont understand, why vlc play my movies perfectly even with enabled compiz, but totem play it with some slowdown and in avidemux i have some intresting and not understanded vertical artifacts? Avidemux very important for me bcs i professional VJ and install linux to find new ways to create content for my live shows. Can u help me fix it?

---

### Post by angels on 2008-01-21
> **diPSy said:**
> Big thx for useful link. But i dont understand, why vlc play my movies perfectly even with enabled compiz, but totem play it with some slowdown and in avidemux i have some intresting and not understanded vertical artifacts? Avidemux very important for me bcs i professional VJ and install linux to find new ways to create content for my live shows. Can u help me fix it?
Happy to help you with ATI, but I cannot help you with players..
Weeks ago I installed VLC because with Totem I couldn't play some .avi videos...and I don't know what happened, but now can I play them also with Totem :confused:
maybe because of the driver update ...
maybe someone else can help you with this as I'm a perfect beginner :):)

---

### Post by unshareef on 2008-01-21
Dear People,

I have just recently had a great deal of my problems solved to do with the ATI driver and compiz.

See it all here: [http://ubuntuforums.org/showthread.php?t=672182](http://ubuntuforums.org/showthread.php?t=672182)

Hope you find it useful.

---

### Post by shonisan on 2008-01-27
@tselliot ...

Are you aware that the site  [http://albertomilone.com/](http://albertomilone.com/) aka |208.109.14.20 is blocked by the great firewall of China.

I have been trying to find out about Envy lately and I have been unable to reach the site.

It may be that another user on the servers where you are located has pissed of the Chinese 'powers that be' with either a porn site or a political site and that has resulted in the whole server being blocked. :rolleyes:

Is there a place to find an alternate download???

Thanks in advance.

S

---

### Post by Noiano on 2008-01-27
> **shonisan said:**
> @tselliot ...

Are you aware that the site  [http://albertomilone.com/](http://albertomilone.com/) aka |208.109.14.20 is blocked by the great firewall of China.

I have been trying to find out about Envy lately and I have been unable to reach the site.

It may be that another user on the servers where you are located has pissed of the Chinese 'powers that be' with either a porn site or a political site and that has resulted in the whole server being blocked. :rolleyes:

Is there a place to find an alternate download???

Thanks in advance.

S

Try using [tor]("https://www.torproject.org/")

---

### Post by shonisan on 2008-01-27
Wow ... tanks for that. This may solve several problems that I have.

I appreciate you putting me on track.

---

### Post by nohammer on 2008-01-27
I've followed the guide both 
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
and
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_8.42.3_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_8.42.3_Driver_Manually)

and the driver appears to be installed correctly. 
 fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1650 Series
OpenGL version string: 2.1.7276 Release

but the screen is VERY choppy. Even as I am typing this it takes a second or two for the letters to appear. I have an intel core2duo 2.66 with 2 gigs of ram and my vid card is the ATI X1650 SE Pro.

Here is my xorg.conf

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg
#Section "Extensions"
#	Option		"Composite"	"0"
#EndSection

Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerFlags"
	Option	    "blank time" "0"
	Option	    "standby time" "0"
	Option	    "suspend time" "0"
	Option	    "off time" "0"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection

---

### Post by Noiano on 2008-01-27
> **shonisan said:**
> Wow ... tanks for that. This may solve several problems that I have.

I appreciate you putting me on track.

Just my duty sir :)

---

### Post by einherier on 2008-01-28
envy kept giving me something about another synaptic something or other error,  I thought about rebooting it but i just decided to use the supported method....works fine.

---

### Post by jack handy on 2008-02-01
updating to the most recent version of Envy worked perfectly for me.  thanks!

---

### Post by Serieneity on 2008-02-04
This is for everyone with E1505 or the 6400 Inspiron Ati X1400 Mobile 128 mb cards.

What I did was when you do your first reboot after everything is installed make sure to install the "ATI accelerated graphics driver". (I also install all of the updates for everything.)

Then you reboot.

You will notice when you log back in after the reboot that you get an error when you try to use the effects thats says something to do with "Composite extension".

The fix to this is to cut and paste this:

sudo apt-get install xserver-xgl

Into a terminal.  It will ask you yes or no.  Hit Y then enter.  It will finish up then give you a message about your XGL server setup has been changed.  Reboot and wala.  The special effects work. 

I don't really know the details on why this works someone explain it please?  

Seriene

PS:  Here is where i got the info from [http://forum.compiz-fusion.org/showthread.php?t=6101]("http://forum.compiz-fusion.org/showthread.php?t=6101")

---

### Post by NFITC1 on 2008-02-05
I have the lastest (8.443.1) ATI drivers and the latest gutsy kernel (2.6.22-14). I'm getting this output from the console:

```
foobar@HLaptop:~$ glxinfo |grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa project: www.mesa3d.org
foobar@HLaptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON 9600/9700 Series
OpenGL version string: 2.1.7170 Release

```

glxinfo is reporting:
```
name of display: :1.0
display: :1  screen: 0

```

My xorg.conf says this:
```
Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

```

and has no other listing for screens, monitors, or video devices.
Compiz works fine, but SDL and apps that depend upon it don't install correctly.
How do I change the display for glxinfo or stop it from being made?

---

### Post by Earl_Maroon on 2008-02-05
This is another guide to installing the drivers.  It worked flawlessly for me.

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

---

### Post by knmstrflx on 2008-02-07
Well, I am throwing in the towel and posting a plea for help.

I've searched high and low, googled, froogled,and bamboozled.

Read countless posts here, there and everywhere.

I've gotten myself so entirely twisted around, I don't even know where I stand anymore.

I'm sorry I was unable to solve this problem myself, but as should be implied, I AM A NOOB.

I've gone everywhere from having a decent setup and compiz-fusion running fairly well (although eating tons of CPU) to  barely chugging at 800x600.

Presently I'm at what looks like 1024x768 and scrolling through these posts feels like im' running Windows XP on a system with 32mb RAM (REALLY CHOPPY)

I'm about to post relevant info like xorg.conf, and I'm embarrassed to say when I read the man page for xorg.conf I think its writent in Greek.  I have very little comprehension of whats going on there, so when I post this and you see something even your grandmother could figure out, please don't laugh :)

My hardware: 32 bit system, FireGL v3100.

my xorg.conf

```

Section "Files"
EndSection

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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV370 5B64 [FireGL V3100 (PCIE)]"
	Driver		"ati"
	BusID		"PCI:5:0:0"
EndSection

Section "Monitor"
	Identifier	"PS790-2"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV370 5B64 [FireGL V3100 (PCIE)]"
	Monitor		"PS790-2"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "Extensions"
        Option      "Composite" "disable"
EndSection

```

the output of glxinfo -relevant? no idea but I saw someone else do it.

```

name of display: :1.0
display: :1  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX/SSE2 TCL
OpenGL version string: 1.2 (1.3 Mesa 7.0.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

My "must have goal" is to obtain help in getitng one display at a decent resolution running atleast weak 3D games on a ViewSonic PS790.

My wish list is to obtain help in getting this machine capable of running WoW or the like.  With dual monitor setup, (two of the previously mentioned ViewSonics)

---

### Post by NFITC1 on 2008-02-07
@knmstrflx:

What does "glxinfo -display :0.0" report?
I'm willing to bet that it looks fine.

---

### Post by knmstrflx on 2008-02-08
> **NFITC1 said:**
> @knmstrflx:

What does "glxinfo -display :0.0" report?
I'm willing to bet that it looks fine.

```

name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow

```

---

### Post by portach king on 2008-02-09
Has anyone got fglx to install on kernel 2.6.24? install via restricted packages isn't working (I assume as they are dowloading files made for 2.6.22). I'm very lost and would appreciate any help.

---

### Post by tseliot on 2008-02-12
> **portach king said:**
> Has anyone got fglx to install on kernel 2.6.24? install via restricted packages isn't working (I assume as they are dowloading files made for 2.6.22). I'm very lost and would appreciate any help.

Restricted manager works only with Ubuntu's default kernels (e.g. 2.6.22 on gutsy). If you either recompiled your kernel or installed Hardy's you can either use module-assistant or try Envy.

---

### Post by portach king on 2008-02-12
Thank you for the information. I've install the 8.1 drivers using Envy, and unfortunately while they work the performance is pretty terrible in comparison to the old drivers.
Is there any solution to install the previous drivers (I tried selecting the 8.40 and 8.28 through envy but 8.40 didn't seem to work at all (the installation seemed riddled with errors) and 8.28 simply installed 8.1 again)?

---

### Post by Ikith on 2008-02-12
No matter what I do I keep getting the Mesa Drivers :-(! I'm running an ATI HD2900... I've tryed 3 guides and no luck. I even rebuilt my xorg.conf 3 times... :-(! What am I doing wrong?

---

### Post by Uchikoma on 2008-02-13
> **knmstrflx said:**
> ```

name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow

```

I'm seeing Direct Rendering: No
Run fglrxinfo (NOT glxinfo) and give us the output of that.

You might also want to tack on LIBGL_DEBUG=verbose to it as well.
```
LIBGL_DEBUG=verbose fglrxinfo
```

Essentially if direct rendering is "no", then you can't do 3D (most likely due to an install problem...or the other possibility is your running XGL.)

---

### Post by kara.lockard on 2008-02-14
Thanx for the information. Your idea worked.

---

### Post by qurgh on 2008-02-15
> **NFITC1 said:**
> @knmstrflx:

What does "glxinfo -display :0.0" report?
I'm willing to bet that it looks fine.

I'm having the same problem as you are.

fglrxinfo reports that the fglrx driver is being used on display :0.0 while glxinfo displays data for display :1.0. When I run the above command it tells me that the ATI driver is doing gl on display :0.0.

Edit: I fixed this problem. I forgot to remove the xgl server. If your having this issue try issuing "sudo apt-get remove xserver-xgl" at a terminal, then restart X (ctrl-alt-backspace worked fine for me). 

Now fglrxinfo reports display :0.0 using the ATI drivers and glxinfo reports I'm using display :0.0 and it's using the ATI drivers to do openGL.

---

### Post by Siggma on 2008-02-16
The driver is not an executable until you add the x capability.

#sudo chmod +x ati-driver-installer-8.....
#sudo ./ati-driver-installer-8........

And it will run :)
A minor detail often overlooked.
-Tom

---

### Post by ts-hhh on 2008-02-16
Hi,

I'm new to Linux/Ubuntu. I finally managed to install the ATI driver, but I got this problem:

fgrlx is only loaded if I execute 'sudo aticonfig --initial -f' in the session before. (Xorg.0.log: (==) Using config file: "/etc/X11/xorg.conf")

Otherwise after the ubuntu-loading-screen the monitor is flickering (resolution tests?) and I get an error message and low-graphics-mode gets started. (Xorg.0.log: (= =)  Using config file: "/etc/X11/xorg.conf.failsafe")

System: Ubuntu 7.10 X64, HD 2600 XT

I need help, please. ;)

---

### Post by JoePits on 2008-02-17
the way i got it to install was to just use the amdccle package in the package manager.  not sure what version it is but i think its pretty new.  this is on hardy heron.

---

### Post by balsamo on 2008-02-17
After a lot of try with different methods, i'm still unable to have a working ati driver at all.

- The restricted driver manager does not detect my  HD2600 AGP card
- So i tried installing the ubuntu provided driver fglrx : X fail to start with no devices detected error.
- So i tried installing the amd/ati driver (fglrx) : when X starts, black screen and computer freeze
- So i tried envy : same result...

All the different how to and procedure leads to the same result. I'm lost !

Don't know what to try now. I really need to have a working ATI driver because the default vesa driver does not support 1440x900 resolutions wich is the one i need for my monitor.

Someone has succedded in configuring the ATI HD 2600 AGP on Gutsy 7.10 ??

---

### Post by Melcar on 2008-02-18
> **balsamo said:**
> After a lot of try with different methods, i'm still unable to have a working ati driver at all.

- The restricted driver manager does not detect my  HD2600 AGP card
- So i tried installing the ubuntu provided driver fglrx : X fail to start with no devices detected error.
- So i tried installing the amd/ati driver (fglrx) : when X starts, black screen and computer freeze
- So i tried envy : same result...

All the different how to and procedure leads to the same result. I'm lost !

Don't know what to try now. I really need to have a working ATI driver because the default vesa driver does not support 1440x900 resolutions wich is the one i need for my monitor.

Someone has succedded in configuring the ATI HD 2600 AGP on Gutsy 7.10 ??

x1xxx and after AGP card have issues with the new fglrx.  The ATI guys have been promising a hot fix for it, but I doubt it will come any time soon (hopefully by the next release).

On another matter.  I just re-installed Gutsy and had a hell of a time trying to get the driver working.  I have always gotten the driver to install successfully by simply running the script (no package generation).  Weird thing was that this time it would always fail.  It's the same driver with the same vanilla Gutsy install as before, only difference was I think some extra updates got installed.  Really strange.  Has there been any updates to Gutsy in the past few days (I just re-installed today)?

---

### Post by Yellow Pasque on 2008-02-18
> **balsamo said:**
> Someone has succedded in configuring the ATI HD 2600 AGP on Gutsy 7.10 ??
The fglrx driver does not play nice with AGP cards. Use the radeonhd driver instead (link in my sig). It's an excellent driver, but unfortunately, it doesn't have 3D acceleration at the moment and the time-frame is "several months".

---

### Post by jdb1981 on 2008-02-19
I can tell you what worked for me, as far as the 2600 goes, but who knows if it'll work for you...
I had a problem (still do, if I use parted magic or other live cd's) with the screen and window resolutions being all screwed up on the live cd during installation, if I had the 2600 card hooked up. The windows for the steps of the installation would display larger than the area of the screen, and there was no way to scroll down to click the various "Next" "Cancel" and "Accept" buttons to install Ubuntu. I also had no option in terms of resolution, 640X800 was it. So, I tried to install using onboard video, and then plug in the video card and try to install the drivers that way. And it was a fiasco. It never worked, even after trying every step outlined in every thread related to the 2600 in this forum, and appealing in this thread for help, without any response. 
I have gotten it working, finally, and I did it by doing a clean install, with the video card installed. I had to use trial and error to figure out how many times to hit the "Tab" button to highlight the correct option on the part of the screen I couldn't see, since I was still having that issue. Eventually, I got through it. (Then, a huge mess trying to get my monitor to display properly, but that's unrelated) Once it was installed, I used Envy to install the driver, which worked on the first try. Now I have advanced desktop effects enabled (never seen those before!) and I'm thinking about installing Beryl, though it was such a pain to get this working, I don't know if it's worth the risk of messing up the graphics settings. 
Anyhow, that's my story. I don't know why having the card in the system at install made the difference, or if that's even an option for you (re-installation, that is.) It doesn't make a whole lot of sense, but if you go back to my original posts (#211 & 217) and any of it sounds familiar, you might give it a shot. I can post a copy of my xorg.conf, or any other output that might be helpful, though I'm the last one to be able to interpret it for you, leave that to the smart ones!
Hope this helps, and I really think the 2600 cards ought to have their own thread, at least a small one, because every reference to them in these forums is just unsolved, unanswered frustration, at least the ones I found... Glad I got it working, I love Ubuntu, and I'm glad to be back!

/edit - After reading your post again, I realized you are actually having almost the same monitor problem I was as well (at least I think you are.) I had to manually edit my xorg.conf to get my monitor to display in its native resolution. I can't get to the file to post it right now, but try a general search in the forums with the model of your monitor, and look for a xorg.conf section you can copy from someone; it was a long list of resolutions and some other configuration info, and I just happened to find one someone with the same monitor had posted that I could copy-and-paste that section. 
Do this at your own risk, of course, and always back up your xorg.conf first. If someone could explain what I just wrote a little more clearly, that would probably help him out, I just happened to find a monitor config section that worked, but I don't really understand how one would create one from scratch if necessary.

---

### Post by mattjames_7 on 2008-02-19
hi im fairly new to using ubuntu, ive messed about with it a lot to try and get it working properly but i always have a problem with my graphics, i use an ATI x1950 Pro. Originally i was trying to get fglrx to work when i had an Asus m2r32 mvp motherboard and it worked really well until about a couple of rebots later and the screen would go blank a few minutes after i logged in and nothing would work. Now i use a MSI k9a2 platinum mobo and the screen just goes blank before the login screen starts up :s. I had the same problem with Fedora core 8 where the screen goes blank a minute or two after i log in with both motherboards. Any ideas how i can fix this?

---

### Post by brandon2009 on 2008-02-28
I just buy an iPod, how to put DVD on my iPod.

---

### Post by Derviansoul on 2008-03-02
Hello

I've spent the last few days with this i'm just a newbie in linux so i installed the latest ati drivers

using the:
```

 sudo sh ati-driver-installer-8-02-x86.x86_64.run

```
then
```

aticonfig --install ati-driver-installer-8-02-x86.x86_64.run
sudo aticonfig --overlay-type=Xv

```
 
then I restarted

i runned the fgrlxinfo and the output was 
```

display :0.0 screen: 0
OpenGL vendor string:Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string:1.4 (2.1 Mesa 7.0.1)

```

if i run the command glxinfo lgrep rendering i get the output direc rendering:No

This is my xorg.conf i've got two screens and i really want the xinerama ON but i tried with the same results with xinerama off
```

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	Screen         "aticonfig-Screen[1]" RightOf "Default Screen"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	Option	       "Xinerama"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "gb"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 72.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Generic Video Card"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Generic Video Card"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Modes    "1440x900" ""
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	
	EndSubSection
EndSection

```


my X11 log file gives me this errors:
```

(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 

(WW) fglrx(1): DRI initialization on primary screen failed.
(WW) fglrx(1): ***********************************************
(WW) fglrx(1): * DRI initialization failed!                  *
(WW) fglrx(1): * (maybe driver kernel module missing or bad) *
(WW) fglrx(1): * 2D acceleraton available (MMIO)             *
(WW) fglrx(1): * no 3D acceleration available                *
(WW) fglrx(1): ********************************************* *
(EE) fglrx(1): DRI initialization for 2nd screen failed - aborting!

(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(EE) AIGLX: Screen 1 is not DRI capable
(II) GLX: Initialized MESA-PROXY GL provider for screen 1

```

I looked at more than 5tutorials on in this forum and i always get the same result!!
i removed all packages that had xserver-xorg-video to force the fglrx to run but i got the same result.
i created links to the volatile folder like someone else said here but the file fglrx.ko
sudo ln -sf /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko
was there already and i still get the same result.
The first time that i tried to install it using 
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)
it actually worked but the e17 was really slow taking about 10min to l
og in or 5 to open   the ff!!
Can anyone help me , please i'm getting really frustrated with this!!


EDIT:I got fglrx working, i made a clean install of gutsy and i follow all the steps!and it's working now,but still no direct rendering!!

---

### Post by Yellow Pasque on 2008-03-02
nvm

---

### Post by incevolebus on 2008-03-04
Here's how you install ATi graphics card driver on Ubuntu 7.10, [http://ubuntuforums.org/showthread.php?t=580748&highlight=ati+9550](http://ubuntuforums.org/showthread.php?t=580748&highlight=ati+9550).

Once installed, enable your restricted ATi graphics card driver on Administration->Restricted Drivers (or something relative to the option).  Your 3D acceleration will work and all Ubuntu effects as well.

Avoid clicking the Synaptic Package Manaager, though, it will crash your Ubuntu!  That's what happened to my machine once I've installed the ATi graphics card driver.  It was all working fine until I click this darn option in the Administration menu.

---

### Post by Resonance378 on 2008-03-05
> **Derviansoul said:**
> 
*snip*
i runned the fgrlxinfo and the output was 
```

display :0.0 screen: 0
OpenGL vendor string:Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string:1.4 (2.1 Mesa 7.0.1)

```
*snip*

EDIT:I got fglrx working, i made a clean install of gutsy and i follow all the steps!and it's working now,but still no direct rendering!!

Here: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Post-Installation_Checks_and_Tweaks](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Post-Installation_Checks_and_Tweaks)

In bold... it loosely states that if you get this message to RE-Enable the Driver from the Restricted Hardware Manager.

I missed this a half dozen times myself one time.

Have you ensured that you have the restricted driver enabled??

---

### Post by Derviansoul on 2008-03-05
> **Resonance378 said:**
> Here: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Post-Installation_Checks_and_Tweaks](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Post-Installation_Checks_and_Tweaks)

In bold... it loosely states that if you get this message to RE-Enable the Driver from the Restricted Hardware Manager.

I missed this a half dozen times myself one time.

Have you ensured that you have the restricted driver enabled??


Hello 
after that i made a clean install and i managed to have the flgrx working with ati drivers but i'm getting segmentation fault when i make fglrxinfo, the problem now is that i get segmentation fault if i use e17 but if 
use failsafe it works properly without segmentation fault and with direct rendering!!
here i explain everything in detail in this post: [here]("http://ubuntuforums.org/showthread.php?t=716331")
thanks allot for all your help people!! without everyone here i would have to go back to vista:S ou xp x64 and i really don't want that!!
all the best!!

---

### Post by Marcusdegrote on 2008-03-11
Does anyone knows if mij Ati redeon HD 3650 has support in Ubuntu 7.10? I can't find anything.

---

### Post by Silent Warrior on 2008-03-13
I had something like the same issue Derviansoul has/had, and I've now apparently gotten over that. VICTORY! Got Compiz going and all that. Partied a bit by playing Warzone 2100 - worked just fine as well. Here's what I did:

(A rather optional step: Uninstalling previous drivers per ATI's instruction - /usr/share/ati/fglrx-uninstall.sh and reboot.)
1. Install Catalyst LE 8.3 using the GUI (I have, for reasons unknown, been unable to generate Ubuntu-packages from ATI's releases lately). Consider rebooting. I usually don't, and it's now taken me a good two years to get this driver installed. You with me?
2. ```
sudo aticonfig --initial --overlay-type=Xv
```
3. Open /etc/X11/xorg.conf in your favorite editor, and make sure it actually points to a display using the fglrx-driver... :) Here's a few relevant sections from my own:
```

<snip>
Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
	Load  "dri"
	Load  "ddc"
	Load  "bmp"
	Load  "fglrx"
	Load  "vesa"
	Load  "dbe"
EndSection

<snip>

Section "Monitor"
	Identifier   "SyncMaster 931c"
	HorizSync    30.0 - 100.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Syncmaster 931c"
	Option	    "DPMS" "true"
EndSection

#Section "Device"
#	Identifier  "ATI Radeon X1900XT"
#	Driver      "vesa"
#	BusID       "PCI:2:0:0"
#EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

#Section "Screen"
#	Identifier "Default Screen"
#	Device     "ATI Radeon X1900XT"
#	Monitor    "SyncMaster 931c"
#	DefaultDepth     24
#	SubSection "Display"
#		Modes    "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
#	EndSubSection
#EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

```
Not that I'm The Man(tm) or anything, but pay special attention to the commented entries and the other entry of the same category. Such as commenting out "Default screen" in favour of "aticonfig-Screen[0]". That seems to have done the trick for me. glxinfo reports I have direct rendering. No more trying to get Compiz running on VESA! I should also mention that the "Module"-section is entirely improvised. fglrx doesn't seem to normally be listed there, but I got a message about DRI missing, and thought to... take care of it. And, you know, better safe than sorry.

---

### Post by muddletupper on 2008-03-14
I've been trying to get my graphics card running 3d mode for a while now (spent all day yesterday trying and this morning).  I've tried multiple install guides from these boards.  I'm rather stuck and wondering if anyone else has some feedback that might help.

64-bit AMD system, 1G or RAM
ATI Radeon HD 2600 XT graphics card with 512M

Using this install guide, method 2, I initially thought I had a nice clean install but noticed it was failing on the libGL.so.1 install.  I can't even seem to find libGL.so.1 anywhere either through apt-get or synaptic.  I went with a libGL mesa driver I saw someone else suggest and it didn't come up with the fail message when I used that, seems to have worked.  But every time I try to start up I get the Ubuntu is running in low-graphics mode message.

Other points.

I'm using the most recent version of drivers from ATI.  I'm not sure if this guide expects I'm using older, recent versions and the newest one breaks something.

Under the current 7.10 build of Ubuntu for 64- bit I don't seem to have ANY restricted drivers under driver manager.

When I go through the low-graphics mode message to update it, the cards indicated don't seem to have one that actually applies to the HD 2600 XT series.  There's an option for rage cards and for standard radeon cards.  Most of the write ups don't seem to include the HD 2x00 cards really particularly not for 64-bit systems.


Any thoughts on how to get it running or anything I'm obviously overlooking?

---

### Post by BlueKoala on 2008-03-18
muddletupper:

I had a similar issue with 7.10
I just bought a phenom quad core which ran really well under 7.10 but my HD3650 was a pain.
I tried almost everything to get it working and it just wouldn't.

I upgraded my distribution to 8.04 alpha build and the restricted drivers manager picked up my card right away.

Although I don't suggest to an alpha build if you need your systems working 100% great 100% of the time.

---

### Post by muddletupper on 2008-03-23
I tried the latest alpha build and let it load up the restricted drivers and still have the same issue.  For whatever reason I just can't seem to get it to see my graphic card.  Whenever it reloads it either wants to use the vesa drivers or doesn't work.  Tried a few other walk throughs without any luck.

---

### Post by americano70e10 on 2008-03-25
Hi guys, I just installed my ATI driver using envy but when I try to log in normaly, I get kicked me back to the GDM screen, but I am able to login through the failsafe option. Anyone know what to do?
I have a x1200 card

---

### Post by tobyw01 on 2008-03-25
:(I have read through the forum and tried many ways to install the ATI driver but I' still having the MESA issue. I have an X200M ATI graphics card. I noticed that when I log into a failsafe gnome session everything works and I get direct rendering. But, when I log into regular Gnome session I get No direct rendering and Mesa for renderer.  Any Help would be appreciated. :(


This is one of my last issues with Linux on this Laptop.

Thanks

---

### Post by jameschapman on 2008-03-27
I have the same card, which I use at 1280x1024 with a LCD monitor.  I just tried the 7.10 live CD (actually DVD) today, and (somewhat to my surprise) it came up by default in the 1280x1024 setting.  Performance seemed to be fine.

---

### Post by alsdkjhf23465 on 2008-03-27
hello everyone, i'm rather new to ubuntu so forgiveme for being a little out of place as of yet.

i started of with a fresh install and have a rather stable system at the moment.
there are a few bits and pieces though:

i take it that ubuntu installed the open source at drivers... but it allows me from the gnome menu the ability to enable restricted drivers (from administration menu)...
trying to use pre installed drivers with google earth, makes the earth rotation look like a slide show... so its pretty bad.. however i could enable compiz and it was working quite alright...

meanwhile if i switch to the ati restricted driver (from within the gnome menu - NOT following the way that is suggested here) i get google earth to work nicely... but compiz does not start...

meaning that whenever i go to system->preferences->GL Desktop, the 'enable GL Desktop' checkbox is never checked.

glxinfo returns:

> nass@starlight:/etc/X11$ glxinfo 
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X300
OpenGL version string: 2.0.6473 (8.37.6)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array, 
    GL_S3_s3tc, GL_ARB_depth_texture, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_multisample, GL_ARB_occlusion_query, GL_ARB_point_parameters, 
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_blend, 
    GL_ARB_vertex_buffer_object, GL_ARB_pixel_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_ARB_draw_buffers, GL_ATI_draw_buffers, GL_ATI_element_array, 
    GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, GL_ATI_map_object_buffer, 
    GL_ATI_separate_stencil, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_float, GL_ATI_texture_mirror_once, 
    GL_ATI_vertex_array_object, GL_ATI_vertex_attrib_array_object, 
    GL_ATI_vertex_streams, GL_ATIX_texture_env_combine3, 
    GL_ATIX_texture_env_route, GL_ATIX_vertex_shader_output_point_size, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_EXT_vertex_shader, GL_HP_occlusion_test, GL_NV_blend_square, 
    GL_NV_occlusion_query, GL_NV_texgen_reflection, GL_SGI_color_matrix, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays



any ideas why compiz doesn't work?

---

### Post by Yellow Pasque on 2008-03-27
alsdkjhf23465 ,
See this: [http://ubuntuforums.org/showpost.php?p=4202892&postcount=6](http://ubuntuforums.org/showpost.php?p=4202892&postcount=6)

---

### Post by peakshysteria on 2008-03-28
My xorg seems to be messed up. At least that's what i think. After restart or reboot i'm given the low graphic manager. And i can't log in with anything else than 960 X 720. The correct resolution is 1280 X 1024. Witch for now seems unreachable. Can someone verify this and maybe point me in the right direction?

My xorg output:

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "no"
Option "XkbVariant" "no"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "vmmouse"
Option "Emulate3Buttons" "true"
EndSection

Section "Device"
Identifier "Configured Video Device"
Boardname "ATI Radeon (fglrx)"
Busid "PCI:1:0:0"
Driver "fglrx"
Screen 0
Vendorname "ATI"
Option "MergedFB" "off"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
Vendorname "Generic LCD Display"
Modelname "LCD Panel 1280x1024"
Horizsync 31.5-64.0
Vertrefresh 56.0 - 65.0
modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
modeline "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
modeline "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
modeline "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
modeline "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
Gamma 1.0
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
Defaultdepth 24
SubSection "Display"
Depth 24
Virtual 1280 1024
Modes "1280x1024@60" "1280x960@60" "1024x768@60" "800x600@60" "800x600@56" "640x480@60"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
screen 0 "Default Screen" 0 0
EndSection
Section "Module"
Load "glx"
Load "GLcore"
Load "dri"
Load "v4l"
EndSection
Section "device" #
Identifier "device1"
Boardname "ATI Radeon (fglrx)"
Busid "PCI:1:0:0"
Driver "fglrx"
Screen 1
Vendorname "ATI"
Option "MergedFB" "off"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
EndSection
Section "screen" #
Identifier "screen1"
Device "device1"
Defaultdepth 24
Monitor "monitor1"
EndSection
Section "monitor" #
Identifier "monitor1"
Gamma 1.0
EndSection
Section "ServerFlags"
EndSection
Section "Extensions"
Option "Composite" "Enable"
EndSection

Running 8.04 Hardy Heron Alpha 6. Kernel 2.6.24-12-Generic. Gnome 2.22.0
Amd Athlon 64 3000+
Mem: 3,0GB
ATI Radeon x700 Excalibur Pro

Driver is checked, green and in use in the restricted drivers manager. Installed it via Envy.

(and yeah i now Hardy isn't stable yet. But this seems to be the only really dedicated ongoing ATI thread).

---

### Post by Yellow Pasque on 2008-03-28
@peakshysteria:

Try commenting out (adding a '#' in front of) the vendor and model lines in the monitor section. Also make sure the modeline for 1280x1024 is correct by running this command (and changing the output's '_' to a '@'):
```
cvt -v 1280 1024 60.0Hz
```

---

### Post by Tolak68 on 2008-03-28
Hi there from Tolak 'the linux newbie'.

I am still coming to grips with Linux and the Shell commands, so please humour me?

I have my ATI driver exe package in-  home\tony\documents\ati driver folder, that's where I downloaded it to.

I copied and pasted the commands into shell as I saw them, I get this reply-

> tony@tony-desktop:~$ ./ati-driver-installer-8-01-x86.x86_64.run --buildpkg Ubuntu/gutsy
bash: ./ati-driver-installer-8-01-x86.x86_64.run: No such file or directory
tony@tony-desktop:~$                                                         

I can only presume I have the file in the wrong folder and shell can not find it?

Which folder should I use in order to load them with a shell command?

I appreciate your help. :-)

Tolak

---

### Post by markcgriffiths on 2008-04-06
Hi,

I have a Radeon x300 on my laptop.  I have two monitors, the laptop's and an external one.  I am using the external one to do everything.  The only thing is that I don't seem to be able to play movies on the external monitor.  Does anyone know why?  I only need to use one monitor at a time.

[http://ubuntuforums.org/showthread.php?t=745420](http://ubuntuforums.org/showthread.php?t=745420)

---

### Post by NCLI on 2008-04-06
My friend is running gutsy, with the drivers from the repo. The GPU is Radeon 9600.

When I restart the PC with the proprietary driver enabled, the screen blink a few times and I'm forced to use vesa. Runs just fine with the radeon open-source driver, but not good enough for Compiz and WoW, obviously. 

Tried a lot of guides, and used envy as well, but no luck.

Any help is appreciated. :confused:

---

### Post by Trollslayer on 2008-04-11
> **digital_exhaust said:**
> Gave it a try and I get...

```
digital@digital-desktop:~$ sudo sh ./ati-driver-installer-8.40.4-x86.x86_64.run
sh: Can't open ./ati-driver-installer-8.40.4-x86.x86_64.run
digital@digital-desktop:~$ 
```

Downloaded the drivers three separate times and got the same results each time... on a clean updated install... 

Any ideas?

Did you use [COLOR="Red"]**chmod**[/COLOR] to make it executable?

---

### Post by Trollslayer on 2008-04-13
> **digital_exhaust said:**
> Gave it a try and I get...

```
digital@digital-desktop:~$ sudo sh ./ati-driver-installer-8.40.4-x86.x86_64.run
sh: Can't open ./ati-driver-installer-8.40.4-x86.x86_64.run
digital@digital-desktop:~$ 
```

Downloaded the drivers three separate times and got the same results each time... on a clean updated install... 

Any ideas?

Use [COLOR="Red"]chmod 777[/COLOR] to make the file executable, ite is not exectuable when downloaded.

---

### Post by bobbiescap on 2008-04-14
Hi,

Just wanted to say that as a newcomer to this operating system I had been struggling with ATI driver installation and found the link to Envy on this post. The instructions were great and the package works a treat and has saved me much grief as I reinstalled Ubuntu twice because I couldn't find answers to these issues. All praise to Alberto and I think his solution should be included in an official repository.
Roger Barnes

---

### Post by munky99999 on 2008-04-18
```
glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300/X1550 Series
OpenGL version string: 2.0.6473 (8.37.6)
OpenGL extensions:

```

and

```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300/X1550 Series
OpenGL version string: 2.0.6473 (8.37.6)
```

and

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier	"Default Layout"
  screen "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"glx"
EndSection

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

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"Acer X193W"
	Option		"DPMS"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Acer X193W"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1440x1440"	"1440x900"	"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection

Section "ServerFlags"
	Option		"AIGLX"	"off"
EndSection
```

The problem is that it does say I'm direct rendered. BUT i dont have 3d acceleration.

[IMG]http://img440.imageshack.us/img440/4800/screenshotsq2.gif[/IMG]

What in the world am I doing wrong?

---

### Post by alewithjam on 2008-04-20
Hi im very new to ubuntu and this is my first post here.

after some time trying to get my ati radeon hd2400PRO to work im getting very confused

i followed the steps at the begginig of this thread and all seemed to be going fine i then

try to overly-type=Xv

and i get a message telling me that the configuration file is not found and i have to copy it /etc/X11/

another thing is i have multiple xorg.conf (xorg.conf1 xorg.conf2 all the way to 4)in this same directory is this normal.

Any help would be much appreciated

Thanks very much 

Ben

---

### Post by Yellow Pasque on 2008-04-21
Ben,
Use the force option to setup your xorg.conf file
```
sudo aticonfig --initial -f --overlay-type=Xv
```

---

### Post by alewithjam on 2008-04-21
Thanks for the reply Temujin sorry i didnt reply sooner

I did as you suggested and i think i made some process

Now when i do fglrxinfo i recieve this 

```

xlib extension "GLX" missing on dispaly:"0.0".
xlib extension "GLX" missing on dispaly:"0.0".
Error: couldn't find RGB GLX visual!

```

Any ideas what this means?

thanks again

Ben

---

### Post by CoolKat on 2008-04-21
Hello,

Hello,

Running Ubuntu 8.04 on above machine.

When running EnvyNG from Application/Systems Tools

I get the following error message:

EnvyNG - Version 1.1.1
Ubuntu Hardy 32bit
Your graphic card has been detected as a ATI Mobility / Radeon 9000
Your graphic card is supported by the legacy Driver
EnvyNG ERROR: ATI's legacy driver does not support your operating system

Please help...

Thanks

---

### Post by Yellow Pasque on 2008-04-21
Ben, is Load "glx" in the Modules section?

CoolKat, your card is not supported by the Catalyst driver. You're stuck with the open-source ati/radeon driver.

---

### Post by alewithjam on 2008-04-21
ok i think this is a big problem i sudo gedit xorg.conf and its empty aaaahhhh.
im writing this from ubuntu and the screen res is so bad, in fact the word bad is the size of my hand, lol.

---

### Post by munky99999 on 2008-04-21
> **alewithjam said:**
> ok i think this is a big problem i sudo gedit xorg.conf and its empty aaaahhhh.
im writing this from ubuntu and the screen res is so bad, in fact the word bad is the size of my hand, lol.


the code is

```
sudo gedit /etc/X11/xorg.conf
```

Make sure to capitalize the X in X11

---

### Post by alewithjam on 2008-04-21
aaahhhhh i see kinda embaresed now, ok got it i have disabled "glx" inside modules should i change this to load then.

Thanks for the help really really appreciated.

Also looking through my xorg the configurations i made in the xserver reconfigure are not there is this strange?

---

### Post by CoolKat on 2008-04-21
> **CoolKat said:**
> Hello,

Hello,

Running Ubuntu 8.04 on above machine.

When running EnvyNG from Application/Systems Tools

I get the following error message:

EnvyNG - Version 1.1.1
Ubuntu Hardy 32bit
Your graphic card has been detected as a ATI Mobility / Radeon 9000
Your graphic card is supported by the legacy Driver
EnvyNG ERROR: ATI's legacy driver does not support your operating system

Please help...

Thanks

Moving toward a solution... when installing ATIpropriotary driver I get the following error message:
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: unable to detect
Removing temporary directory: fglrx-install
gilbert@gilbert-laptop:~$ 

What am I missing... a Ubuntu-Linux newbe.. 4 days old 

Thanks

---

### Post by Yellow Pasque on 2008-04-22
**CoolKat, your card is not supported by the Catalyst driver. Use the ati/radeon driver (included with Ubuntu)**

(Sorry for the bold, but I'm guessing you didn't see my post above.)

---

### Post by Yellow Pasque on 2008-04-22
Double post.

---

### Post by CoolKat on 2008-04-22
> **Temüjin said:**
> **CoolKat, your card is not supported by the Catalyst driver. Use the ati/radeon driver (included with Ubuntu)**

(Sorry for the bold, but I'm guessing you didn't see my post above.)

ok.. ok.. got the point.. it was late last night.. 

Thank you

sniff..

---

### Post by alewithjam on 2008-04-23
Hi there i have load glx inside of modules and i feel i have configured xserver corrctly now but im still reciving the same problem as before load glx rgb thing.

My graphics are well different now.... anything that requires the graphics has a green ting to it ...... very alien...

Please help! really looking forward to having ubuntu as primary OS

---

### Post by Jyves on 2008-04-24
Hi  There!!!!!

Another newbie..here!!

I read most part of that thread, but nobody seems to have my problem.:(
I put a ATI Radeon 7000 PCI  Card in my dell gx270, it starts booting up and hangs there , I have noticed the floppy drive led stays constantly on. I removed the card , everything is back to normal . My bios is set to auto.My question is how do i get to do all the beautiful things you guys are saying if i don't even boot up ??????
I think Ubuntu doesn't know which one has the monitor plug in and just hangs.
I was thinking disable the onboard monitor on Ubuntu ( i don't know how ) (newbie remember ). I was wondering if anyone has any suggestion if yes, please post the complete A to Z on how to configure it completely.

Thank You.

---

### Post by imaca on 2008-04-25
Hi,
   I have 2 PCs to maintain with ATI video, my mothers (integrated x1250) and kids (R9800 pro).
The radeon hasn't worked with fglrx since 6.10, I only got the X1250 going with fglrx after stumbling on a post with a xorg.conf which enabled the card to run at the correct 1680x1050 resolution.
People keep saying to use ati driver but this is not an option because it is so slow.
The guide provided simply does not work for many ATI cards.
There seems to be several key problems.
1. there needs to be a guide as to what to put in xorg.conf.
Neither of these PCs has ever worked on any version of ubuntu (back to breezy for the R9800) without manual configuration of xorg.conf, both for the monitors and the video card. If there was a data base of what to use with which card it would be a HUGE help. 

2. There also seems to be mass confusion about what features will work with which cards. Again a database would be a big help here. The x1250 simply doesn't work with compiz, it does however work with a resolution of 1680x1050 provided the correct magic incantations are entered into xorg.conf. It would seem AGP ATI video cards like the R9800 don't work anymore with fglrx (is this true-perhaps it is a via motherboard problem?)
It seems to me if someone with enough knowledge to do this could get input from owners of particular video cards of what does and doesn't work, and from this set up a database.
A lot of work I guess but perhaps less so than endlessly answering the same questions over and over in the forum.
Is this possible or are ATI video cards an unknown unsolvable mystery to even the most knowledgable Ubuntu users?

---

### Post by Rocket2DMn on 2008-04-26
Just as an FYI for people who find this, older ATI cards (older than 9500 I believe) do not work with the restricted drivers, you need to use the open source "ati" drivers.
Because of a bug in these drivers, Compiz Fusion blacklisted cards running these drivers in Hardy Heron, but there is a simple workaround as I explained in this thread - [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)
Good luck.

---

### Post by gerben1 on 2008-04-27
I just don't seem able to get the ATI proprietary drivers installed. I have tried this tutorial: [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

I followed it closely, and have tried multiple times, but it just won't work I keep getting this:

gerben@CC1184274-A:~$ fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

I also tried using envyNG but it gave me exactly the same result,
even though it did recognize my card and said it was supported by the driver, it is a ATI Mobility Radeon X700 card.

Anyways I had this working perfectly fine in Gutsy, so it must be possible to get it working again. Does anybody have some suggestions for things to check?

---

### Post by munky99999 on 2008-04-27
Have you tried the simple method of going to 

System->Admin->Hardware Drivers-> and see if it's enabled.

---

### Post by gerben1 on 2008-04-27
It is not in there, there's only:

- Broadcom B43 wireless driver
- Software modem

that is it, no video driver there

---

### Post by munky99999 on 2008-04-27
> **gerben1 said:**
> It is not in there, there's only:

- Broadcom B43 wireless driver
- Software modem

that is it, no video driver there
Try hardware testing and make sure it is even detected.

or alternatively in the terminal you can use 

lspci

Which ought to list the card near the bottom.

---

### Post by gerben1 on 2008-04-27
> **munky99999 said:**
> Try hardware testing and make sure it is even detected.

or alternatively in the terminal you can use 

lspci

Which ought to list the card near the bottom.


gerben@CC1184274-A:~$ lspci | grep X700
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)

---

### Post by NOLU on 2008-04-27
I'm having slow issues all around on Heron.

01:00.0 VGA compatible controller: ATI Technologies Inc RV516 XT Radeon X1600 Series (Primary)
01:00.1 Display controller: ATI Technologies Inc RV516 XT Radeon X1600 Series (Secondary)

This is my card and in Hardware drivers, there is nothing there. Would this be why I'm having slow issues and what can I do to fix it please?

---

### Post by gerben1 on 2008-04-27
is it possible that my problems have to do with the problem described here?
[http://caulfield.info/emmet/2008/04/fix-ati-catalyst-84-driver-pac.html](http://caulfield.info/emmet/2008/04/fix-ati-catalyst-84-driver-pac.html)

and if so can I juts change the *_amd64.deb to *_i386.deb in his script and use it?

---

### Post by Ferux on 2008-04-27
Hi

this message can be found in page 5 of this thread:

[quote=Lolo Uila]So basically it looks like whenever fglrx loads without errors (well, without logged errors) I get hard locked when X is started.

I get all the boot messages and the loading stuff, but it hangs right when I'd expect the Gnome login screen to appear. At that point my screen is black, but my monitor detects a signal on whatever port I have it plugged into and it doesn't go into power save mode. It seems like the card is actually sending a black screen to the display. I have tried both ports with both DVI and Analog connections and the results are the same.

The system is hard locked as far as I can tell. Typing in my login info gets me nowhere (no login sounds or change to the black screen). Trying to exit to the shell with ctrl+alt+f1 does nothing. Hitting ctrl+alt+delete does make the hard drive busy light flash a few times, but nothing happens. No shutdown or reboot.[/quote]

I have exactly the same after installing the proprietary ATI driver. I have the problem by the automated Hardy installation (enable restricted driver), the same problem with Envy and when I install the driver I downloaded from ati.com.
The weird thing is that the proprietary driver worked perfect for me with my Radeon 9800 Pro. That card broke, so I replaced it with a 2600XT (both on AGP). Since then, I experience this bug.


As far as I know, this problem still isn't solved. I think a lot of people don't use Ubuntu just because of this bug.


Ubuntu Hardy Heron x64 desktop
MOBO: MSI K8N Neo2 Platinum
PROC: Athlon 64 3500+
MEM: 1GB
GRAPH: ATI 2600XT on AGP
SCREEN: Samsung 2232BW (22"), D-sub nor DVI works


If someone knows the answer to this problem, .. you get much respect from me :) (and probably many others)

---

### Post by zemoffm on 2008-04-27
^ I am having the same exact problem!  Also waiting for the fix.  Worked like a charm in 7.10.  Honestly, this release is amazing except for this one problem.  Fixed my sound perfectly, and it incredibly fast.  Just want compiz!

Laptop:  Gateway ML3109
Graphics:  ATI Radeon Xpress 200


Waiting for the fix.
:popcorn:

---

### Post by Melcar on 2008-04-28
Is it me, or do the fonts in Hardy look smaller and blurry?  As soon as I install fglrx the fonts look smaller than what they were.  This is in sharp contrast to the effect fglrx had on Hardy (bigger fonts).  Even the fonts inside the AMDCCCLE look smaller than usual.

---

### Post by rmcder on 2008-04-28
I have a 15.4" t60 laptop, ati X1400 video, 1680x1050 resolution.
I currently have everything working under 7.10; proper resolution, etc, using the restricted drivers and loading xgl (except for the suspend/hibernation issue). I'd like to be able to eliminate xgl, and resolve that last issue. Do the new ati drivers work ok? Anyone having the same combination of video card/resolution able to get it all working? If so, what's the best way to proceed? Or, if someone knows it DOESN'T yet work, please tell me THAT, and I'll leave well-enough alone for the present. 

Would an upgrade to Heron help?  Thanks!

---

### Post by chaime on 2008-05-04
Okay ...

Working in Hardy, none of the options, including EnvyNG, seem to work. The driver that Hardy is using does not enable me to use the more advanced graphics functions. There was no problem with this in 7.10. Also, now not only does my S3 suspend not work, as it did not in 7.10, but now whenever it shuts off my monitor it won't resume either.

This is the opposite of progress. I've been building Micrapsoft systems for like 20 years, and I can't find anything with Ubuntu that will work with my hardware.

Any solutions for Hardy?

Chaim

---

### Post by trickyarcher on 2008-05-05
Saint Angeles,

I want to thank you for all your efforts. However, I am still unable to get anywhere with my ATI card and DRI. I am attaching my xorg.conf. Maybe you can point me in the right direction.

I have tried everything from ubuntu Binary ATI install, ATI Linux wiki, EnvyNG, and Ed Hewitt's fix at [http://edhewitt.co.uk/2008/03/24/fix...deon-on-linux/](http://edhewitt.co.uk/2008/03/24/fix...deon-on-linux/) but nothing seems to be able to help me resolve the following:


```
:~$ less /var/log/Xorg.0.log |grep WW
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(WW) fglrx(0): Failed to open DRM connection
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(WW) fglrx(0): No DRM connection for driver fglrx.
(WW) fglrx(0): could not detect X server version (query_status=-3)
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(WW) fglrx(0): Textured Video not supported without DRI enabled.
(WW) fglrx(0): Option "AddARGBGLXVisuals" is not used
(WW) fglrx(0): Option "AllowGLXWithComposite" is not used
(WW) fglrx(0): Option "EnablePageFlip" is not used
(WW) fglrx(0): Option "AccelMethod" is not used
(WW) fglrx(0): Option "MigrationHeuristic" is not used
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(WW) Configured Mouse: No Device specified, looking for one...or. . .
```


```
:~$ less /var/log/Xorg.0.log |grep EE
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized.
```

If I can provide any more information to help people solve this, let me know and I will give it to you.

Thanks,
Tricky

**Update:** when I add the /etc/X11/lib/modules directory to the files section and reboot, my GNOME screen looks squiggly like pay-per-view back in the day.

---

### Post by ThinkDave on 2008-05-06
This solved my problem with the Ati Xpress 200M always loading mesa for OpenGl even when fglrx was installed.
e.g. **White screen of death problem. **
Note: You will only get this problem if you upgraded to Hardy you should not have this error if it is a fresh install.

It was a problem with the kernel not updating in grub bootloader.
At the terminal type
uname -r

If it doesn't start with 2.6.24.
Then your using the older kernel (the ati drivers will not install properly) and thats your problem... for once its not actually ati's fault.

I changed /boot/grub/menu.lst i don't know if thats the smartest way to do it so i wont write what i did. 
Can anyone suggest a way of automatically updating the grub menu.lst?

---

### Post by Silent Warrior on 2008-05-07
ThinkDave: There is a little application called Startupmanager (might be 'sum' in the repositories) which, among other things, seems to let you select which kernel is the default option to boot. I've never needed to do that myself, since I'm dual-booting and the GRUB-menu pops up by default on every boot. You can also remove the older kernels through Synaptic. (Just be VERY sure about what you're doing.)
Hm, well, I suppose this might fiddle with grub.lst as well, only it won't be directly by your hand. :)

---

### Post by Ren Höek on 2008-05-08
> **trickyarcher said:**
> Saint Angeles,

I want to thank you for all your efforts. However, I am still unable to get anywhere with my ATI card and DRI. I am attaching my xorg.conf. Maybe you can point me in the right direction.

I have tried everything from ubuntu Binary ATI install, ATI Linux wiki, EnvyNG, and Ed Hewitt's fix at [http://edhewitt.co.uk/2008/03/24/fix...deon-on-linux/](http://edhewitt.co.uk/2008/03/24/fix...deon-on-linux/) but nothing seems to be able to help me resolve the following:


```
:~$ less /var/log/Xorg.0.log |grep WW
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(WW) fglrx(0): Failed to open DRM connection
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(WW) fglrx(0): No DRM connection for driver fglrx.
(WW) fglrx(0): could not detect X server version (query_status=-3)
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(WW) fglrx(0): Textured Video not supported without DRI enabled.
(WW) fglrx(0): Option "AddARGBGLXVisuals" is not used
(WW) fglrx(0): Option "AllowGLXWithComposite" is not used
(WW) fglrx(0): Option "EnablePageFlip" is not used
(WW) fglrx(0): Option "AccelMethod" is not used
(WW) fglrx(0): Option "MigrationHeuristic" is not used
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(WW) Configured Mouse: No Device specified, looking for one...or. . .
```


```
:~$ less /var/log/Xorg.0.log |grep EE
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized.
```

If I can provide any more information to help people solve this, let me know and I will give it to you.

Thanks,
Tricky

**Update:** when I add the /etc/X11/lib/modules directory to the files section and reboot, my GNOME screen looks squiggly like pay-per-view back in the day.


I had the same messages in my log...
If you try
```
$ modprobe -vf fglrx
```
and get something like
```
install /sbin/lrm-video fglrx
```
the solution is to modify the file "/etc/modprobe.d/lrm-video". Comment out the line with fglrx so it looks like
```
#install fglrx /sbin/lrm-video fglrx $CMDLINE_OPTS
```
and reboot.

I hope it works for you too
   Ren

---

### Post by ladysun1 on 2008-05-08
Has anyone got their ATI 1600/1650 to work properly in Ubuntu?

I have the driver installed but all I get is a white screen and 

I cannot reconfigure xorg or xserver.  I'm not given an option of

what driver to use like ATI or NVIDIA only how to configure the 

keyboard and mouse.   Please help!:confused:

---

### Post by ThinkDave on 2008-05-09
> **ladysun1 said:**
> Has anyone got their ATI 1600/1650 to work properly in Ubuntu?

I have the driver installed but all I get is a white screen and 

I cannot reconfigure xorg or xserver.  I'm not given an option of

what driver to use like ATI or NVIDIA only how to configure the 

keyboard and mouse.   Please help!:confused:
See my post a few lines up. That fixed my white screen problems.

---

### Post by Ren Höek on 2008-05-09
> **ladysun1 said:**
> Has anyone got their ATI 1600/1650 to work properly in Ubuntu?

I have the driver installed but all I get is a white screen and 

I cannot reconfigure xorg or xserver.  I'm not given an option of

what driver to use like ATI or NVIDIA only how to configure the 

keyboard and mouse.   Please help!:confused:

If the solution of ThinkDave doesn't fit in your case, try to log in in terminal mode (press [Crtl] + [Alt] + [F1] instead of logging in with gnome/kde);  and post the results of
```
$ cat /var/log/Xorg.0.log | grep "(EE)\|(WW)"
```.
If there should be something like
```
(WW) fglrx(0): * DRI initialization failed! *
``` probably my last post can help...

---

### Post by ladysun1 on 2008-05-09
I decided to re-install Ubuntu and discovered that if I install flgrx or xorg with all its dependencies I get a white screen.  If I uninstall it I'm fine but then there is no ATI driver and I'm still stuck with the default Mesa drivers.  Is there any way to just install the ATI driver without the flgrx configuration?

---

### Post by Ren Höek on 2008-05-09
> **ladysun1 said:**
> I decided to re-install Ubuntu and discovered that if I install flgrx or xorg with all its dependencies I get a white screen.  If I uninstall it I'm fine but then there is no ATI driver and I'm still stuck with the default Mesa drivers.  Is there any way to just install the ATI driver without the flgrx configuration?

There are two different ATI drivers
radeon/radeonhd (open source), and
fglrx (proprietary driver by ATI/AMD).
Xorg is the implementation of the x window system, and installed by default.
The names of the packeges with the different drivers are maybe a little bit confusing by containing the term xorg...

So now you have to decide wich of the two drivers you prefer. Actually I don't know if the radeon/radeonhd has already 3D support for your card.
fglrx has mostly a better performance in 3D (radeon in 2D), but leads often to problems (like probably your white screen) and needs therefore a little bit more configuration before running...

If you decide for one and it won't work immediatelly, please post some logs and describe the problem as detailed as possible. I'm sure the one or other reader in this forum will be able to help you...

---

### Post by ladysun1 on 2008-05-10
Thanks for the clarification of the x-window or Xorg screen.  Right now I have no fglrx driver packages installed but would like to configure the open source ATI driver because in Vista I am already using version 8.4. How would I start to do that?  If at all possible I would rather avoid having to edit the Xorg configuration file but if I have to so be it. I promise to post my logs. I am using my Vista OS to transmit this response so please bear with me.  Thanks!

---

### Post by timdog44 on 2008-05-10
i have a weird one. i have an ati hd3650 and the fglrx driver only works if i DONT have the mouse plugged in.....
i have tried a couple different mice (all USB) and when it goes to load the GUI the comp freezes. if i reboot and unplug the mouse, everything seems to load OK. this is only with this video card, if i use the onboard video everything works fine. any ideas?

---

### Post by ladysun1 on 2008-05-10
> **Ren Höek said:**
> If the solution of ThinkDave doesn't fit in your case, try to log in in terminal mode (press [Crtl] + [Alt] + [F1] instead of logging in with gnome/kde);  and post the results of
```
$ cat /var/log/Xorg.0.log | grep "(EE)\|(WW)"
```.
If there should be something like
```
(WW) fglrx(0): * DRI initialization failed! *
``` probably my last post can help...

Here is my log when I run $ cat /var/log/Xorg.0.log | grep "(EE)\|(WW)"

Shall I re-install the flgrx packages again?  Run aticonfig?  Re-post the logs? or any other alternative?

It would be difficult to try and do this without the proper graphic settings..........


(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1) found
(WW) RADEON(0): R500 support is under development. Please report any issues to [email]xorg-driver-ati@lists.x.org[/email]
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
(WW) RADEON(0): No crtc mode list for crtc 1,continuing with desired mode
(WW) RADEON(0): Direct rendering disabled
(WW) Configured Mouse: No Device specified, looking for one...

---

### Post by ladysun1 on 2008-05-10
> **ladysun1 said:**
> Here is my log when I run $ cat /var/log/Xorg.0.log | grep "(EE)\|(WW)"

Shall I re-install the flgrx packages again?  Run aticonfig?  Re-post the logs? or any other alternative?

It would be difficult to try and do this without the proper graphic settings..........


(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1) found
(WW) RADEON(0): R500 support is under development. Please report any issues to [email]xorg-driver-ati@lists.x.org[/email]
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
(WW) RADEON(0): No crtc mode list for crtc 1,continuing with desired mode
(WW) RADEON(0): Direct rendering disabled
(WW) Configured Mouse: No Device specified, looking for one...
OK, I ran aticonfig and got this after editing the xorg.conf file

Now the trouble starts if and when I reboot and the white screen appears.....
The proprietary driver module (ATI) is enabled in Ubuntu (Hardy) but not in use

$ sudo gedit /etc/X11/xorg.conf
$ sudo aticonfig --initial -f
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-0

---

### Post by ladysun1 on 2008-05-10
> **ladysun1 said:**
> OK, I ran aticonfig and got this after editing the xorg.conf file

Now the trouble starts if and when I reboot and the white screen appears.....
The proprietary driver module (ATI) is enabled in Ubuntu (Hardy) but not in use

$ sudo gedit /etc/X11/xorg.conf
$ sudo aticonfig --initial -f
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-0

Downloaded the ATI driver and this is what my new Xorg file looks like and I've blacklisted fglrx
If I reboot my machine now will I be able to configure the monitor settings?


# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"ati"
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
EndSection

---

### Post by Ren Höek on 2008-05-11
> **ladysun1 said:**
> Thanks for the clarification of the x-window or Xorg screen.  Right now I have no fglrx driver packages installed but would like to configure the open source ATI driver because in Vista I am already using version 8.4. How would I start to do that?  If at all possible I would rather avoid having to edit the Xorg configuration file but if I have to so be it. I promise to post my logs. I am using my Vista OS to transmit this response so please bear with me.  Thanks!

I'm a little bit unsure wich of the two possible drivers you want.
Your post #327 shows logs of the open source driver radeon.
In post #328 you mention
```
$ sudo aticonfig --initial -f
```
to initialize fglrx.
But in post #329 your xorg.conf contains
```
Section "Device"
Identifier "aticonfig-Device[0]"
Driver "ati"
EndSection
```
where should be fglrx instead of ati, if using fglrx...

Actually I don't know about an open source driver for ATI and Vista in Version 8.4. and I guess you mean the closed source Catalyst™ Drivers (fglrx in Linux).

This here is a really good guide for installing fglrx on Hardy:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

With method two you will get the latest version 8.4.
Please try to follow as close as possible.

If you are ready and after reboot you have again the problem with the white screen after login,  press [Ctrl] + [Alt] + [F1] before logging in in graphical mode and log in in terminal mode.

Now you can use
```
$ cat /var/log/Xorg.0.log | grep "(EE)\|(WW)"
```
again to see what the problem could be.
If there appears something like
```
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized.
```
my post #319 should solve the problem.
If not, please post the results and the symptoms. You can also try to copy the logfile to your vista partition, so you don't have to copy by hand...

Goog luck
   Ren

---

### Post by markbuntu on 2008-05-11
Ren, I tried your suggestion and for me, it only made things worse and better. My desktop visual effects were working but very slow and now I get the white screen of death when I set them to anything but off.

glxgears was showing around 60-150 and is now up to about 900 so I guess that is some improvement but it should be around 5000 with my video card.

I am thinking this has something to do with the Mesa drivers preventing direct rendering.

Luckily ctrl alt backspace is still working to get me out of it.

---

### Post by Ren Höek on 2008-05-11
> **markbuntu said:**
> Ren, I tried your suggestion and for me, it only made things worse and better. My desktop visual effects were working but very slow and now I get the white screen of death when I set them to anything but off.

glxgears was showing around 60-150 and is now up to about 900 so I guess that is some improvement but it should be around 5000 with my video card.

I am thinking this has something to do with the Mesa drivers preventing direct rendering.

Luckily ctrl alt backspace is still working to get me out of it.

If you get such low FPS, it really can be, that the fglrx modul isn't loaded properly.
Do you get direct rendering?
```
$ glxinfo | grep "direct rendering"
```
And what does
```
$ fglrxinfo
```
tell? ATI or Mesa?
Do you get any Errors with
```
$ cat /var/log/Xorg.0.log | grep "(EE)\|(WW)" 
```?

---

### Post by markbuntu on 2008-05-11
I reinstalled the ATI driver and did aticonfig and rebooted and now the ATI Catalyst Control Center is working and tells me I have the right driver. The Xorg log also properly identifies my card and the driver. Envy does not recognize my HD3650 so that is no help for me.

fglrxinfo tells me it is running mesa.

Oxorg.0.log had the following warnings etc:

(WW) fglrx(0): Failed to open DRM connection

(WW) fglrx(0): No DRM connection for driver fglrx.

(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

before doing the modprobe as you suggested my visual effects were working and are still broken.

direct rendering is no according to glxinfo which also lists a bunch of Mesa stuff.

---

### Post by Ren Höek on 2008-05-11
> **markbuntu said:**
> I reinstalled the ATI driver and did aticonfig and rebooted and now the ATI Catalyst Control Center is working and tells me I have the right driver. The Xorg log also properly identifies my card and the driver. Envy does not recognize my HD3650 so that is no help for me.

fglrxinfo tells me it is running mesa.

Oxorg.0.log had the following warnings etc:

(WW) fglrx(0): Failed to open DRM connection

(WW) fglrx(0): No DRM connection for driver fglrx.

(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

before doing the modprobe as you suggested my visual effects were working and are still broken.

direct rendering is no according to glxinfo which also lists a bunch of Mesa stuff.

If you try
```
$ modprobe -vf fglrx
```
you will probably get something like
```
install /sbin/lrm-video fglrx
```.
The solution is to modify the file "/etc/modprobe.d/lrm-video". Comment out the line with fglrx so it looks like
```
#install fglrx /sbin/lrm-video fglrx $CMDLINE_OPTS
```
and reboot.
I guess this should solve your problem...

---

### Post by markbuntu on 2008-05-11
no, that does not work

---

### Post by Ren Höek on 2008-05-11
> **markbuntu said:**
> no, that does not work

Hmmm... what does
```
$ modprobe -vf fglrx
```
tell you after a fresh reboot, before loading fglrx module by hand, or something...?

---

### Post by markbuntu on 2008-05-11
I reloaded xserver-xgl and got compiz back but it also put me back to about 130 fps.
It seems I can either run on Xv and go half-fast with no compiz or opengl with compiz and go molasses slow.

---

### Post by Ren Höek on 2008-05-12
> **markbuntu said:**
> no, that does not work

Acutally I'm really sure, that your Problem with fglrx can be solved by modifying "/etc/modprobe.d/lrm-video". The output of your log is explicit for this error.

Maybe you have forgotten to use sudo or to save the changes or reboot or some orther bagatelle...
...or maybe you solved the Problem of loading fglrx module and get another one (my card, for example started freezing system with 3D, so also compiz, but this also can be solved...), looking similar to it.

Your graphic card seems to be supported by radeon/radeonhd, but not 3D yet, so your only chance for a fast direct rendering is to get fglrx working, I guess...

...so if you have the patience to try it again, please report
```
$ modprobe -vf fglrx
``` before the change  and the logs after it.

good luck
   ren

---

### Post by ladysun1 on 2008-05-12
Ren, I have successfully installed my video driver blacklisting fglrx however I would have much preferred that the line "Identifier" would've said ATI Radeon 1600.  I have posted my /etc/X11/xorg.conf:

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"ATI Radeon"
	Busid		"PCI:1:0:1"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "screen1" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"dri"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"ATI Radeon (fbdev)"
	Busid		"PCI:1:0:0"
	Driver		"radeon"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1680x1050@60"	"1680x1050@75"	"1600x1024@60"	"1920x1200@60"	"1440x900@60"	"1440x900@75"	"1280x800@60"	"1280x768@75"	"1280x800@75"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"
	EndSubSection
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Vendorname	"Dell"
	Modelname	"DELL E207WFP"
	Horizsync	30.0-83.0
	Vertrefresh	56.0-75.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1680x1050@75" 188.07 1680 1800 1984 2288 1050 1051 1054 1096 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

---

### Post by ladysun1 on 2008-05-12
> **Ren Höek said:**
> I'm a little bit unsure wich of the two possible drivers you want.
Your post #327 shows logs of the open source driver radeon.
In post #328 you mention
```
$ sudo aticonfig --initial -f
```
to initialize fglrx.
But in post #329 your xorg.conf contains
```
Section "Device"
Identifier "aticonfig-Device[0]"
Driver "ati"
EndSection
```
where should be fglrx instead of ati, if using fglrx...

Actually I don't know about an open source driver for ATI and Vista in Version 8.4. and I guess you mean the closed source Catalyst™ Drivers (fglrx in Linux).

This here is a really good guide for installing fglrx on Hardy:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

With method two you will get the latest version 8.4.
Please try to follow as close as possible.

If you are ready and after reboot you have again the problem with the white screen after login,  press [Ctrl] + [Alt] + [F1] before logging in in graphical mode and log in in terminal mode.

Now you can use
```
$ cat /var/log/Xorg.0.log | grep "(EE)\|(WW)"
```
again to see what the problem could be.
If there appears something like
```
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized.
```
my post #319 should solve the problem.
If not, please post the results and the symptoms. You can also try to copy the logfile to your vista partition, so you don't have to copy by hand...

Goog luck
   Ren
Ren, I do have another question --- I am experiencing garbled "video noise" at every shutdown. I'm wondering if this has anything to do with not opting for the "fglrx" driver?

---

### Post by Humans_Are on 2008-05-12
I'm new to Ubuntu... and im wondering what the deal is with this ATI stuff. I have the symptoms, slow everything, I haven't used ubuntu for a while because of it. even without the ATI driver. I had first heard that something was going to be updated soon.(that something began with a d, and was an acronym i believe.. I'm new and brainless to this stuff). anyway, after hearing that I still saw a bunch of threads being posted, not really understanding much of any of them. So my question is this... is there going to be an easy fix for this? if there is, should there be a stickied post? I guessing this problem is affecting a lot of people. I think it's weird that I've heard nothing really official about it. Maybe I just need to search more?
Peace.

---

### Post by markbuntu on 2008-05-12
> **Ren Höek said:**
> If you try
```
$ modprobe -vf fglrx
```
you will probably get something like
```
install /sbin/lrm-video fglrx
```.
The solution is to modify the file "/etc/modprobe.d/lrm-video". Comment out the line with fglrx so it looks like
```
#install fglrx /sbin/lrm-video fglrx $CMDLINE_OPTS
```
and reboot.
I guess this should solve your problem...

OK Ren, this is what is currently going on:

result of modprobe -vf fglrx
FATAL: Module fglrx not found

contents of etc/modprobe.d/lrm-video:
# Make nvidia/nvidia_legacy and fglrx use /sbin/lrm-video to load
#install fglrx /sbin/lrm-video fglrx $CMDLINE_OPTS
install nvidia /sbin/lrm-video nvidia $CMDLINE_OPTS
install nvidia_legacy /sbin/lrm-video nvidia_legacy $CMDLINE_OPTS
install nvidia_new /sbin/lrm-video nvidia_new $CMDLINE_OPTS

Relevant sections of Xorg.0.log:

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux mark-desktop 2.6.24-16-rt #1 SMP PREEMPT RT Thu Apr 10 15:15:40 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM

,,,


(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.47.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.476                    
(II) ATI Proprietary Linux Driver Build Date: Mar 29 2008 00:05:22
(--) Assigning device section with no busID to primary device
(--) Chipset Supported AMD Graphics Processor (0x9598) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed

...

drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(WW) fglrx(0): Failed to open DRM connection

...

(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.47.3
	ABI class: X.Org Server Extension, version 0.3
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000001f
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 256 MB
(WW) fglrx(0): No DRM connection for driver fglrx.
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.

...

(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(WW) fglrx(0): could not detect X server version (query_status=-3)
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

(==) fglrx(0): Backing store disabled

(II) fglrx(0): Acceleration enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): Direct rendering disabled

[glesx] __glESXExtensionInit: No GL ES2.0 capable screen found!
(II) AIGLX: Screen 0 is not DRI capable

(II) GLX: Initialized MESA-PROXY GL provider for screen 0


What now?
It is pretty clear what is going on but why?
and how do I fix it?

Forget it, this card is going on the trash heap. Good thing i only paid $70 for it.

---

### Post by Ren Höek on 2008-05-13
> **markbuntu said:**
> OK Ren, this is what is currently going on:

[...]

What now?
It is pretty clear what is going on but why?
and how do I fix it?

[...]

Well it is really confusing...

Let's give it a last try :).
Can you load the module with
```

$ sudo insmod /lib/modules/$(uname -r)/updates/dkms/fglrx.ko
$ modprobe fglrx

```?
If so, you should have direct rendering after restarting X...
(...if there is no file in this folder, try searching for fglrx.ko and use that one).

What is the result of
```
$ LIBGL_DEBUG=verbose fglrxinfo
```?
Maybe there is just a link missing to some submodule fglrx is needing...

Can you please also post your whole Xorg.0.log and xorg.conf?

I'll keep my fingers crossed.
Ren

---

### Post by Ren Höek on 2008-05-13
> **ladysun1 said:**
> Ren, I have successfully installed my video driver blacklisting fglrx however I would have much preferred that the line "Identifier" would've said ATI Radeon 1600.  I have posted my /etc/X11/xorg.conf:
[..]


Nice to hear, you have installed successfully.
Your xorg.conf is a little bit messed up...
Wich one do you have chosen? Radeon/RadeonHD, right? (Actually you have to blacklist the old fglrx if installing the new one, so it's not clear...)
Well, if your sorrow is the "Identifier" in your configuration file, I can reassure you. It's just an exchangeable string. It's just important, that the Identifier in Section "Device" is the same as the Device in Section "Screen".

> Ren, I do have another question --- I am experiencing garbled "video noise" at every shutdown. I'm wondering if this has anything to do with not opting for the "fglrx" driver?
With Radeon, I also get some strange "video noise" while shutting down...
...but as long as there are no video artifacts in normal use, it's not dramatic.
Your card seems to be quite new, does the driver support direct rendering?

---

### Post by markbuntu on 2008-05-13
OK Ren, I have done some digging around and found this in the usr/share/ati/ fglrx-install.log :

initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
 Assuming default VMAP API
 Assuming default munmap API
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.24-16-rt/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-rt'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.o
  Building modules, stage 2.
  MODPOST 1 modules
FATAL: modpost: GPL-incompatible module fglrx.ko uses GPL-only symbol '__rcu_read_lock'
make[2]: *** [__modpost] Error 1
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-rt'
make: *** [kmod_build] Error 2
build failed with return value 2
[Error] Kernel Module : Failed to compile kernel module - please consult readme.

So, it seems something weird is going with fglrx.ko during the build.

...3 hours later

OK, so I gave up and completely reinstalled 8.04 so I have a clean clean clean install.
All my problems went away!!! Yay!!
Downloaded and installed the restricted drivers and everything works now at blistering speeds

glxgears is now reporting around 5000fps and seems very stable so far.

The only problem is that I have to rebuild my system from the ground up now. I will go very carefully and as soon as something screws this up I will post.

---

### Post by Ren Höek on 2008-05-14
> **markbuntu said:**
> OK Ren, I have done some digging around and found this in the usr/share/ati/ fglrx-install.log :

initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
 Assuming default VMAP API
 Assuming default munmap API
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.24-16-rt/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-rt'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.o
  Building modules, stage 2.
  MODPOST 1 modules
FATAL: modpost: GPL-incompatible module fglrx.ko uses GPL-only symbol '__rcu_read_lock'
make[2]: *** [__modpost] Error 1
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-rt'
make: *** [kmod_build] Error 2
build failed with return value 2
[Error] Kernel Module : Failed to compile kernel module - please consult readme.

So, it seems something weird is going with fglrx.ko during the build.

...3 hours later

OK, so I gave up and completely reinstalled 8.04 so I have a clean clean clean install.
All my problems went away!!! Yay!!
Downloaded and installed the restricted drivers and everything works now at blistering speeds

glxgears is now reporting around 5000fps and seems very stable so far.

The only problem is that I have to rebuild my system from the ground up now. I will go very carefully and as soon as something screws this up I will post.

Great, that you get it working :).
A google search for "FATAL: modpost: GPL-incompatible module fglrx.ko uses GPL-only symbol" gives some results...
...there seems to be a problem to build fglrx with the rt Kernel, so I guess you reinstalled with another one. You could have changed only kernel and there also seems to be some kind of fix; but a clean, fresh system is nothing to be scoffed at.
Too bad, that you find mostly the solution after you fixed it already ;)...
...took quite a while to figure it out.

---

### Post by markbuntu on 2008-05-14
> **Ren Höek said:**
> Great, that you get it working :).
A google search for "FATAL: modpost: GPL-incompatible module fglrx.ko uses GPL-only symbol" gives some results...
...there seems to be a problem to build fglrx with the rt Kernel, so I guess you reinstalled with another one. You could have changed only kernel and there also seems to be some kind of fix; but a clean, fresh system is nothing to be scoffed at.
Too bad, that you find mostly the solution after you fixed it already ;)...
...took quite a while to figure it out.

Well, it was a good learning experience. I now know quite a bit more about how drivers etc, and X work. But, the problem was never solved. The only thing I could figure was to get rid of MesaGL but it had so many debs to like gdm and X and gnome that removing it would have made it impossible to log in or pretty much anything else so a complete reinstall seemed my only option. 

This did bring me to a question though? How can I remove a package like MesaGL and leave its debs?
The ati fglrx docs suggested this as a fix for this problem in red hat but I could find no way to do it in Ubuntu.

Lucky for me I had the time and had no desperate need to use the machine.

Anyway, I would suggest to anyone experiencing problems similar to mine that when all else fails and you are about to toss your ati card onto the trash heap to try a complete new reinstall and then very first thing install the restricted driver.

If you are replacing your board based ati 200M with a plug in card like I did, I would strongly recommend this procedure. Back up your important stuff off the disk drive and completely reinstall Ubuntu.

Thank you Ren for taking the time and putting your attention to my particular problem.

:popcorn:

---

### Post by Teloid on 2008-05-15
Hello, I have problems with DRI module - when I'm disabling it at xorg.conf by ```
Option "NoDRI"
``` all works fine(no direct rendering ;) ) , but with DRI after X start I have black screen and nothing else, system stops, I can't get connection from ssh, or serial consoles. I install my ATI x1300 (512Mb) after I broke my GeForce 6600. With nvidia drivers I have no problems, but ATI. I think i finaly uninstall nvidia drivers(i removed all packages, and all symlinks to modules at /usr/lib/xorg/modules) but at glxinfo output I still have some strange strings: ```
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: **NVIDIA Corporation**
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB
GLX version: 1.2
GLX extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_SGIX_fbconfig, 
    GLX_ARB_get_proc_address
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

```
At Xorg log I haven't any errors, only one interesting string:
```
(II) AIGLX: Screen 0 is not DRI capable
```. I have two screens, but now I want only enable direct rendering, but think that only Nvidia chipset may resolve problem =)

I tried to install drivers from repos, by envy and latest(8.4) from ATI site. Previous owner of this card(he stoped fighting with ATI and bought NVIDIA card) had direct rendering at ubuntu on 7.11 driver version, but no at newest versions. I'm failed to install that old version due it's no way to install it on 8.04 =)

---

### Post by nagmine on 2008-05-15
Hello, I am new to Ubuntu and was wanting mostly to use it as a media center (mplayer). But like many people I seem to be having an issue getting it to work proper. Id like to be able to use the svideo out to display it on a tv.

Radeon x700

 Currently I am unable to do so. I have tryed installing fglrx and get a black screen of death when I restart (it also clearly says dont use it in the device section).

Is this something that will change or is their a work around? If I cant get the Svideo to work its pretty much no use to me :/.

---

### Post by Teloid on 2008-05-16
> **nagmine said:**
> Hello, I am new to Ubuntu and was wanting mostly to use it as a media center (mplayer). But like many people I seem to be having an issue getting it to work proper. Id like to be able to use the svideo out to display it on a tv.

Radeon x700

 Currently I am unable to do so. I have tryed installing fglrx and get a black screen of death when I restart (it also clearly says dont use it in the device section).

Is this something that will change or is their a work around? If I cant get the Svideo to work its pretty much no use to me :/.

First read last Xorg log - /var/log/Xorg.0.log, and search for error messages. Maybe you have bug that I described above - DRI couses crash, if so, add to "Monitor" section at your /etc/X11/xorg.conf that string:
```

Option          "NoDRI"

```
And try to start Xorg again.

---

### Post by Ren Höek on 2008-05-16
Disabling DRI will let X use Mesa, so it's not remarkable, that fglrx does not freeze...
A black screen can have different causes. Does it appear immediately after login? Or does it not as long as you don't do anything and just with opening a window or something?
Are the visual effect active? (Hardy seems to activate some of them after installing fglrx...)

If so the driver freezes System only in 3D (compiz) and the Options
```

	Option	"UseInternalAGPGART"	"0"
	Option	"KernelModuleParm"	"agplock=0"

```
can help.
If not, try disabling AIGLX
```

Section "Extensions"
	Option	"Composite"	"0"
EndSection

Section "ServerFlags"
	Option	"AIGLX"	"0"
EndSection

```.
If not, try to log in in terminal mode ([Ctrl] + [Alt] + [F1]) and post the results of
```

$ cat /var/log/Xorg.0.log | grep "(WW)\|(FF)"

```

---

### Post by Teloid on 2008-05-16
Black screen appears immidiatly after Xorg start(Xorg means /usr/bin/Xorg), I can get that black screen by staring gdm or by startx or xinit. And as I described above I can't access serial consoles (by Ctrl+Alt+FN or Alt+FN), system (not computer at all) stops, any network services(like ssh server) doesn't available from network. I try to get all warnings from Xorg log, and post here, but at previous logs reading I can't found any interesting. Shaman dancing with proprietary hardware realy boring and non-useful at future.

---

### Post by lukasorin on 2008-05-16
hi there. i start to say i'm new in linux...i just buy a new video card Ati Radeon Sapphire X1650 Pro with 512 MB DDR2 on AGP 8x. right now i have fresh Ubuntu 8.04 on my PC. i can't find the corect driver for this card. on web site Ati they have just for X1600 driver..i read a lot of but i can't install corect the driver. please if any one can help me..i don't know were to ask more...every time after i try to set active the driver from Resctricted Drivers, i take restart to my PC and my screen stay black..i think is the 8 time when i install Ubuntu.. i'm afraid to make another install who maybe will not work..thank you so much . cheers

---

### Post by jireland on 2008-05-17
Hi,  I'm just decided to give Linux another go since I no longer use a wireless usb pen drive so no need to set that up again.

I am trying to get my ati 1950pro to work on a fresh install.  - I am a Linux noob but experienced windows administrator.

I have tried searching the forums but one problems seems to lead to another so if you can spot where I am going wrong I would appreciate it.  First off, ATI Fire GL appears in Hardware drivers, is enabled but status is not in use.

I tried downloading drivers from the ati website, I can not install this as I need to run as SUDO which I can not log in as (for security as I have read) so I tried the terminal window with:

jim@jim-desktop:~$ bash ./ati-driver-installer-8.40.4-x86.x86_64.run
bash: ./ati-driver-installer-8.40.4-x86.x86_64.run: No such file or directory

 sudo sh ./ati-driver-installer-8.40.4-x86.x86_64.runsh: Can't open ./ati-driver-installer-8.40.4-x86.x86_64.run

As you can see these did not work, the ati-driver-installer-8.40.4-x86.x86_64.run file is definitely on the desktop.

then I found this website: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

jim@jim-desktop:~$ sudo apt-get install linux-restricted-modules-generic restricted-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-restricted-modules-generic is already the newest version.
Note, selecting jockey-gtk for regex ‘restricted-manager’
jockey-gtk is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jim@jim-desktop:~$ sudo apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xorg-driver-fglrx
jim@jim-desktop:~$ 

So that did not work either.  As I said, I am a complete noob so probably doing something incredibly stupid.  Please help me, I was up till 3am trying to sort it out.

Thanks in advance

Jim

---

### Post by neuthral on 2008-05-17
Hi, another linux noob here, ive got an unusual problem with the fglrx driver. 

I just did a fresh Hardy installation (Ubuntu studio-32bit) installed the restricted driver->re booted-> fglrx works-> second boot-> can't start Xserver.-> Installed catalyst drivers from Ati's site in Vesa mode-> 
reboot can't start Xserver "PreInitDAL failed". Then it freezes there without X, and i do this

ALT+F1 into terminal
```

bender@ubuntu:~$ sudo aticonfig --initial -f
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-1
bender@ubuntu:~$ startx

```

Xserver manages to start with the fglrx driver, however i need to do this every restart and it creates a backup xorg.conf file everytime.
Can it be that some files dont have permission for X to start or sumting, im on dark waters here.

My gfx-card is Sapphire Radeon HD 2600XT and heres my xorg.conf

```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "fi"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection


```

---

### Post by Ren Höek on 2008-05-17
> **jireland said:**
> 
[..]

I tried downloading drivers from the ati website, I can not install this as I need to run as SUDO which I can not log in as (for security as I have read) so I tried the terminal window with:
You don't have to log in as sudo, you just type sudo in front of the command that you want to run with su rights.

> 
[..]
then I found this website: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

jim@jim-desktop:~$ sudo apt-get install linux-restricted-modules-generic restricted-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-restricted-modules-generic is already the newest version.
Note, selecting jockey-gtk for regex ‘restricted-manager’
jockey-gtk is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jim@jim-desktop:~$ sudo apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xorg-driver-fglrx
jim@jim-desktop:~$ 

Probably you just have not activated the source containing this package.
Go System &#8594; Administration &#8594; Software Sources and check if all sources are active.

---

### Post by markbuntu on 2008-05-17
The Ubuntu repository now has the latest ATI restricted driver 8. so there is no need to go anywhere else to get them. 

ATI Proprietary Linux Driver Version Identifier:8.47.3

---

### Post by sync_85 on 2008-05-18
i have tried installing my ati card on ubuntu 8.04 using envyng..but this is what i get...
cant understand what i'm doin wrong.
any help?

---

### Post by Teloid on 2008-05-18
You have Radeon 9000? Yesterday I have same problem with NVIDIA TNT2 Pro, legacy driver for this card, which worked at 6.06 failed to install at 8.04.

---

### Post by Ren Höek on 2008-05-18
> **sync_85 said:**
> i have tried installing my ati card on ubuntu 8.04 using envyng..but this is what i get...
cant understand what i'm doin wrong.
any help?

Your card is not supported by the newest fglrx 8.4.
[http://www2.ati.com/drivers/linux/catalyst_84_linux.html](http://www2.ati.com/drivers/linux/catalyst_84_linux.html)
The last proprietary ati driver supporting your card was 8.28.8
[http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html](http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html)

I don't know envyng (do you have the option between these two drivers?) but probably this is the reason...

---

### Post by markbuntu on 2008-05-18
The Radeon 9000 should work just fine with the open source drivers, That is why ATI no longer supports it in the restricted drivers.

---

### Post by markbuntu on 2008-05-18
If you have an AMD64 processor and an ATI video card I would highly reccomend using the x86_64 Kernel if you want to run compiz effects. CPU loading is far lower, at least on my machine.

---

### Post by krash182 on 2008-05-28
same thing with the radeon 7000 card on 8.04,  I am at witts end using a 800x600 graphics mode and poor video.

---

### Post by sim-value on 2008-05-28
When i did the last command (sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko) it told me operation not permitted then i tried as root - same. Then i loged out and in as it told me and had SERIOUSLY screwed graphics .... you could see totally nothing ...

Then i restarted and got a Black screen forcing me too press Reset (like all my Tries ended on Xubuntu/7.04/7.10/8.04/Kubuntu 8.04) 

I think i might try the manual method now though that also never worked. Are there only Noobs at ATI ?! Or am i seriously dump not able to read or anything ?
My card is Ati radeon X1550 By the way ...

---

### Post by tommytrying2linux on 2008-05-29
thankyou for this, finally able to get my drivers installed :)

---

### Post by sim-value on 2008-06-03
I installed the 8.5. Driver only via the GUI coming with it then rebooted then run aticonfig then restarted again. Now my resolution changed amdcccle is running correctly but i still get Mesa as OpenGL Provider .

That sucks !

---

### Post by Silent Warrior on 2008-06-04
Look at your xorg.conf and see if you're actually using a screen/device that's run on fglrx. I've had to manually sort that out on occasion.

---

### Post by primky on 2008-06-04
I am having problems with drivers for about one month now, from where i started using ubuntu.
I have Ubuntu Hardy 8.04. Kernel is 2.6.24-17-generic.

I found this program EnvyNG, which automatically finds drivers for your video card and installs it.

When i do it, everything is OK, my card is recognized and it says it is supported by the latest drivers. I have Ati Radeon X1650. 

But when i reboot and where it should show up login screen, the whole screen is black.

Any advice or any help would help me A LOT!

---

### Post by sim-value on 2008-06-04
> **Silent Warrior said:**
> Look at your xorg.conf and see if you're actually using a screen/device that's run on fglrx. I've had to manually sort that out on occasion.

Driver"fglrx" is set there .... or what do you mean ?

@primky You are having the same Chipset like me only drivers working for me are 8.42.3 and 8.5

---

### Post by Silent Warrior on 2008-06-05
sim-value: I mean that you not only need to have a proper device-entry with fglrx enabled, but you may need to check that your screen-entry points to the fglrx-powered device as well. Anyway, that's what I had to do way back when, to get rid of the 'fglrxinfo: vendorname MesaGL'-issue.

---

### Post by sim-value on 2008-06-05
```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "de"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection

```

My xorg.conf ... it seems right to me exept if screen would need to point to Aticonfig device .

---

### Post by primky on 2008-06-05
sim-value, i installed 8.42.3, but still it's black screen at the start. 

Could you give me the link which helped you to install them and to make them work? Please!

---

### Post by Silent Warrior on 2008-06-06
sim-value: That does look like it should work. Consider adding fglrx and dri in the list of modules to load. I don't know if that had much effect, but it just might. Then, your xorg.conf would morph into something like this:
```
Section "Module"
    Load    "dri"
    Load    "fglrx"
EndSection
```

Perhaps a bit overkill these days, but it hasn't caused any "incident" for me yet.

---

### Post by sim-value on 2008-06-06
> **primky said:**
> sim-value, i installed 8.42.3, but still it's black screen at the start. 

Could you give me the link which helped you to install them and to make them work? Please!
wiki.cchtml.com look there i got black screens with this driver multiple times too but this time it works
> **Silent Warrior said:**
> sim-value: That does look like it should work. Consider adding fglrx and dri in the list of modules to load. I don't know if that had much effect, but it just might. Then, your xorg.conf would morph into something like this:
```
Section "Module"
    Load    "dri"
    Load    "fglrx"
EndSection
```

Perhaps a bit overkill these days, but it hasn't caused any "incident" for me yet.
No change (didnt reboot just restarted X)

---

### Post by markbuntu on 2008-06-06
If you are using the ATI proprietary driver it will ignore any changes you make in xorg.conf unless you run this command:

sudo aticonfig --input=/etc/X11/xorg.conf --tls=1

this will write xorg.conf changes to the actual fglrx configuration file which cannot be edited by hand. You can find more info about that here:

[http://forum.compiz-fusion.org/forumdisplay.php?f=87](http://forum.compiz-fusion.org/forumdisplay.php?f=87)

be sure to thank djdoo.

---

### Post by Xinkill on 2008-06-06
Thanks for the info man, this drivers does his work way better than the propretairy driver from ubuntu and the driver which one can install with envy. Btw i noticed that Gutsy didn't recognized my HD3870 and that 8.04 installed it from the box.

Btw anyone knows if i would be able to activate compiz now with this drivers without inflicting any damage on the current x-server?

---

### Post by primky on 2008-06-08
> **sim-value said:**
> wiki.cchtml.com look there i got black screens with this driver multiple times too but this time it works

What have you done this time different that it works?

Is this that tutorial?
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

### Post by markbuntu on 2008-06-08
> **Xinkill said:**
> Thanks for the info man, this drivers does his work way better than the propretairy driver from ubuntu and the driver which one can install with envy. Btw i noticed that Gutsy didn't recognized my HD3870 and that 8.04 installed it from the box.

Btw anyone knows if i would be able to activate compiz now with this drivers without inflicting any damage on the current x-server?

Try it by changing you desktop visual effects. If it will do Extra without messing up your screen you should be good to go. Do it this way because it will default back to the old setting in 30 seconds if you don't accept the new settings or you screen is screwed up.

Anyway you should have no problems at all with your 3870 running compiz except for maybe some flickering playing videos which can be fixed by turning off the desktop visual effects. MY HD3650 runs great.

You can get to the desktop effects by right clicking anywhere on the desktop and choosing Change Desktop Background.

good luck!

---

### Post by sim-value on 2008-06-09
> **primky said:**
> What have you done this time different that it works?

Is this that tutorial?
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

I just installed it without anything before i was on Xubuntu that is long ago maybe it is just new kernel ...

---

### Post by mpscheidt on 2008-06-09
running fglrxinfo, glxgears, and many other programs result in a segmentation fault if not run as a superuser. Some examples:

```
$ fglrxinfo 
Segmentation fault

```

whereas sudo works:

```
$ sudo fglrxinfo 
Password or swipe finger: 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.1.7412 Release

```

```
$ glxgears 
Segmentation fault

$ sudo glxgears 
22307 frames in 5.0 seconds = 4461.345 FPS

```

```
$ amdcccle 
Segmentation fault

```

Also compiz cannot be started without superuser privileges:

```
$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:7145 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

```

...so desktop effects cannot be activated. running compiz as superuser works:
```
$ sudo compiz
Password or swipe finger: 
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:7145 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1400x1050) to maximum 3D texture size (4096): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (dbus) - Error: dbus_bus_get error: Failed to execute dbus-launch to autolaunch D-Bus session
/usr/bin/compiz.real (dbus) - Error: InitObject failed
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'dbus'
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

same for google earth, VMWare (when 3D effects turned on)..

So, what's the problem? Why do all these programs only work when started as superuser? I guess it should not be like that.

Refs: Thinkpad T60 with X1400, Ubuntu 8.04 using Ubuntu's ATI driver.

Markus

---

### Post by webbdawg on 2008-06-10
Is there a way Ubuntu can tell me what series ATI Radeonon I have? I know it is a 256mb ATI Radeon but I don't know which series.

I want to download ATI's correct driver. The one that Ubuntu supports locks my system at least twice a day.

---

### Post by Rocket2DMn on 2008-06-10
> **webbdawg said:**
> Is there a way Ubuntu can tell me what series ATI Radeonon I have? I know it is a 256mb ATI Radeon but I don't know which series.

I want to download ATI's correct driver. The one that Ubuntu supports locks my system at least twice a day.

run
```
lspci | grep VGA
```
or for more detailed info:
```
sudo lshw -C video
```

---

### Post by webbdawg on 2008-06-10
> **Rocket2DMn said:**
> run
```
lspci | grep VGA
```
or for more detailed info:
```
sudo lshw -C video
```

Thanks man it worked great. Though it seems that the System Monitor should have told me about all of my hardware.

Thanks
Dave

---

### Post by Mako Eyes on 2008-06-16
I've been reading this thread but I couldn't get anything working. I gave envy a whirl since I could do a simple *envyng --uninstall-all* if anything goes wrong.

Booting to the desktop gave nothing more than a white screen, but I could tell the drivers were at least a partial success as my ring application switcher worked under Compiz. Other than the ring switcher, I couldn't really do much else. So I rebooted and tried the *envyng --uninstall-all* command in recovery mode.

Well, I must have did something wrong, because I noticed that I was unable to enable Compiz when I got back. Whenever I try, it prompts me to install the proprietary (fglrx) drivers. Those run Compiz, but also bring their undesired effects with them.

I've tried messing with the Proprietary Drivers Manager, un/installing the drivers using Synaptec, and rebooting -- each in every order possible. Nothing worked.

What's very strange is that some of my global keyboard shortcuts do not work anymore. They worked fine before this ordeal (I use them quite often), but I cannot see how it would cause that to happen. Gecko embedded media player is also busted. This is very strange.

There's no way this is irreversible; there has to be some way to get the open source drivers up and running again. I'm just at a complete loss as to how. I'll keep looking for solutions, but so far I'm running into blanks. Are they actually gone, or are they just "broken?" Maybe this is Compiz' fault? I have no idea...

I should mention that I'm running a Sapphire Radeon X800 Pro PCIe. *compiz --replace* provides this output:

```
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
```

If there's any more information you need, just say so.

Thanks.

---

### Post by markbuntu on 2008-06-16
Which ATI card do you have?

If it is a newer one that is supported by the ati driver do this:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

Then do this:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

make sure you have removed any fglrx driver you already have installed.

This will make things much better and a lot is explained about the driver that is not explained elsewhere.

---

### Post by shahnn28 on 2008-06-16
I need help. I am new to Linux world and trying this our for corporate environment. I have 256MB ATI Radeon 2400 XT Video Card and trying to configure it for Extended Desktop. I have dual screens but are identical. Here is a copy of my xorg.conf. Can anyone please tell me where i am wrong.

 xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Main Screen"
    Screen        1  "Second Screen" Rightof "Main Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    Option        "Xinerama" "true"
EndSection

Section "Files"
EndSection

Section "Module"
    Load  "glx"
    Load  "GLcore"
    Load  "v4l"
EndSection

Section "InputDevice"
    Identifier  "Generic Keyboard"
    Driver      "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules" "xorg"
    Option        "XkbModel" "pc105"
    Option        "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier  "Configured Mouse"
    Driver      "mouse"
    Option        "CorePointer"
    Option        "Device" "/dev/input/mice"
    Option        "Protocol" "ImPS/2"
    Option        "ZAxisMapping" "4 5"
    Option        "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier   "Main Monitor"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    HorizSync    28-51
    VertRefresh  43-60
EndSection

Section "Monitor"
    Identifier   "Second Monitor"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    HorizSync    28-51
    VertRefresh  43-60
EndSection

Section "Device"
    Identifier  "0 ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
    Driver      "ati"
    BusID        "PCI:1:0:0"
    Screen         0
EndSection

Section "Device"
    Identifier  "1 ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
    Driver      "ati"
    BusID        "PCI:1:0:0"
    Screen         1
EndSection

Section "Screen"
    Identifier "Main Screen"
    Device     "0 ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
    Monitor    "Main Monitor"
    DefaultDepth     24
    SubSection "Display"
        Depth     1
        Modes      "1024x768"
Section "Screen"
    Identifier "Second Screen"
    Device     "1 ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
    Monitor    "Second Monitor"
    DefaultDepth     24
    SubSection "Display"
        Depth     1
        Modes      "1024x768"
    EndSubSection
EndSection

---

### Post by Mako Eyes on 2008-06-16
> **markbuntu said:**
> Which ATI card do you have?

If it is a newer one that is supported by the ati driver do this:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

Then do this:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

make sure you have removed any fglrx driver you already have installed.

This will make things much better and a lot is explained about the driver that is not explained elsewhere.

I have said that I'm using a Radeon X800 Pro. It's part of the R400 series and I'm pretty sure it is supported by the drivers. However, I do *not want* the fglrx drivers as they produce some undesired effects with the X800. All I want is the original open source driver functionality.

Despite this, I'll give the Catalyst 8.5 drivers a spin and get back to you. Maybe they have the problems fixed in that release.

EDIT: This is a no-go. They run better than the previous version, but my X800 [overheats](http://wiki.cchtml.com/index.php/Troubleshooting#Radeon_GPU_fan_is_very_loud_.2F_constantly_works), badly, to the point of causing visual artifacts on my desktop. That link explains it's a problem with the X800 architecture and there's no way to prevent it as long as I'm using these drives. Reverting back immediately.

Damn... I don't know what to do.

EDIT2: Well, I'll be. Disabling the proprietary drivers in the Hardware Drivers manager *after* installing them as you instructed brought everything back to normal; Compiz is up and running, global shortcuts work, and embedded media all systems go. I never even needed to move on to that second link of yours. I'm guessing the custom Catalyst 8.5 installation reinstalled/updated some stuff the open source drivers required, but were uninstalled using the Envy method? I don't know.

Who would have thought that the solution to the problem would be to update the drivers and then... not use them?

Regardless: Thanks!

---

### Post by mpscheidt on 2008-06-17
In order to solve the

$ fglrxinfo
Segmentation fault

issue after updating to Hardy, this possibly helps:

sudo gedit /etc/ati/ati-fglrx.sh
comment all lines (put # at the beginning of all lines in the file)

See also [http://ge.ubuntuforums.com/showthread.php?t=800650](http://ge.ubuntuforums.com/showthread.php?t=800650)
The bug also has been posted at [https://bugs.launchpad.net/ubuntu/+bug/224160](https://bugs.launchpad.net/ubuntu/+bug/224160)

Markus

---

### Post by Yellow Pasque on 2008-06-17
Mako Eyes,
```
gksudo gedit /usr/bin/compiz
```
Add fglrx to the WHITELIST="ati nvidia i810 .." line

---

### Post by Mako Eyes on 2008-06-17
> **Temüjin said:**
> Mako Eyes,
```
gksudo gedit /usr/bin/compiz
```
Add fglrx to the WHITELIST="ati nvidia i810 .." line

No worries, everything is fixed now. Thanks anyway though.

---

### Post by JKoder on 2008-06-18
Hello everyone.
I tryed to install the ati drivers from ati.com.
It installed fine, aticonfig worked but when i restarte the PC and after the login screen ( it was correctly displayed) my deskop was all white.

What i did wrong or what should i do to make it work.
P.P my ati card is : ATI Xpress 1100.

---

### Post by markbuntu on 2008-06-18
> **Mako Eyes said:**
> I have said that I'm using a Radeon X800 Pro. It's part of the R400 series and I'm pretty sure it is supported by the drivers. However, I do *not want* the fglrx drivers as they produce some undesired effects with the X800. All I want is the original open source driver functionality.

Despite this, I'll give the Catalyst 8.5 drivers a spin and get back to you. Maybe they have the problems fixed in that release.

EDIT: This is a no-go. They run better than the previous version, but my X800 [overheats](http://wiki.cchtml.com/index.php/Troubleshooting#Radeon_GPU_fan_is_very_loud_.2F_constantly_works), badly, to the point of causing visual artifacts on my desktop. That link explains it's a problem with the X800 architecture and there's no way to prevent it as long as I'm using these drives. Reverting back immediately.

Damn... I don't know what to do.

EDIT2: Well, I'll be. Disabling the proprietary drivers in the Hardware Drivers manager *after* installing them as you instructed brought everything back to normal; Compiz is up and running, global shortcuts work, and embedded media all systems go. I never even needed to move on to that second link of yours. I'm guessing the custom Catalyst 8.5 installation reinstalled/updated some stuff the open source drivers required, but were uninstalled using the Envy method? I don't know.

Who would have thought that the solution to the problem would be to update the drivers and then... not use them?

Regardless: Thanks!

Actually, you are most likely using the 8.5 driver. The hardware driver manager is saying that the restricted driver from the repos (8.47.3) is not enabled which is true. If you look in you Xorg.0.log you can find out exactly which driver is being used for fglrx. If you are using the 8.5 driver you should see a line like this:

(II) ATI Proprietary Linux Driver Version Identifier:8.49.7

which is the 8.5 driver.

---

### Post by Mako Eyes on 2008-06-18
> **markbuntu said:**
> Actually, you are most likely using the 8.5 driver. The hardware driver manager is saying that the restricted driver from the repos (8.47.3) is not enabled which is true. If you look in you Xorg.0.log you can find out exactly which driver is being used for fglrx. If you are using the 8.5 driver you should see a line like this:

(II) ATI Proprietary Linux Driver Version Identifier:8.49.7

which is the 8.5 driver.

Nope, I can assure you that I am not using them. The Catalyst driver caused my card's fan to go into overdrive and also caused video scaling issues. Trust me, they are not in use as I do not have these issues anymore and also am without 3D acceleration. The Catalyst control center uninstalled itself when I chose not to use them as well.

However, for the time being, this is the desired result. I don't plan to move to the official drivers until I get a new graphics card.

---

### Post by markbuntu on 2008-06-18
When you get to the login screen click on the little icon on the bottom left and change session to gnome safe mode. 

If that works, right click on the desktop and change your desktop viusal effects to none. Logout and login. If you get the desktop try enabling desktop visual effects again.

---

### Post by Mako Eyes on 2008-06-18
EDIT: Disregard this. markbuntu was talking to JKoder, not me.

---

### Post by cutOff on 2008-06-19
> **JKoder said:**
> Hello everyone.
I tryed to install the ati drivers from ati.com.
It installed fine, aticonfig worked but when i restarte the PC and after the login screen ( it was correctly displayed) my deskop was all white.

What i did wrong or what should i do to make it work.
P.P my ati card is : ATI Xpress 1100.

Boot-up in Recovery Mode and try following:

$ sudo aticonfig --initial --force

More info at [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

### Post by markbuntu on 2008-06-19
> **Mako Eyes said:**
> Nope, I can assure you that I am not using them. The Catalyst driver caused my card's fan to go into overdrive and also caused video scaling issues. Trust me, they are not in use as I do not have these issues anymore and also am without 3D acceleration. The Catalyst control center uninstalled itself when I chose not to use them as well.

However, for the time being, this is the desired result. I don't plan to move to the official drivers until I get a new graphics card.

OK, weird though. I recently got a HD3650 1GB for $60. The HD3870 was too much $$ considering the (for me) required p/s upgrade along with it. I would rather spend the ~$300 on a new mb and cpu.

btw, the new 8.6 driver is out and the install how to I mentioned above has been rewritten for it. No major changes, just some bug fixes etc.

---

### Post by chappers on 2008-06-19
HI all, i BET this HAS been answered but here goes! :(

I installed the latest 8.6 drivers on Ubuntu 8.04, all went fine - even the aticonfig went well via the ATI GUI way via running the .run file.

BUT

when i log in, the desktop/pc is SO SLOW its like running on 256MB of system ram or less!

I havent yet edited the xorg.conf file to set the resoultions ect <-- im a bit lost on that front Please could someone direct me to a basic file to use :)!

 - 
and when i type in fglrxinfo [i think] it still states MESA, and states that my card is running at 4X AGP. Its an 8X card!

and

the ATI CCC on the app's bit states there isn't a GFX card installed, therefore it states that ii have to quit that bit; even though it is!

I have re-installed 4 times in the last few days because of the WSOD and BSOD issues, but i *nearly* solved it last time with the drivers with the Hardware tab stating it was enabled and green., But then i had the WSOD and after much tweaking i was stumped and done a fresh install. Thats were i am now.

im on me dual boot xp at the moment and me system specs ect:

Ubuntu 8.04 Clean Install
ATI 8.6 Latest Drivers
X800XL 256MB AGP
Gigabyte Mobo
3Ghz P4 Prescott
1.5GB over 3 banks DDR PC3200
1 Monitor Samsung 22" 223BW @ 1680x1050@60Hz

I am not sure if Compiz [haven't got that far i seeing what it is  = Me N00bie to Linux] is installed, but from searching i have found this via the forum

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

BUT i haven't had a read through.

I did have a link to a wiki i believe that stated some code to enable the 3D acceleration properly, but i cant find it - but do i need it  - as i installed the drivers directly from the GUI of 8.6 drivers?

Many thanks for ANY help/pointers/links that you may post.

---

### Post by markbuntu on 2008-06-19
Using the ATI graphical installer does not work with Ubuntu. It is written for versions of linux with different structures than Debian/Ubuntu.

If you don't follow this guide:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

You WILL have problems with Ubuntu.

like no dri, no 2D acceleration, no 3D, revert to VESA, black screen, white screen, Mesa rendering, no compiz, slow screens.

So please, follow the cchtml guide.

If you have already done the wrong thing you may still be able to recover your system by following this guide.

---

### Post by chappers on 2008-06-20
well i tried and gues what. 

im at re-install #5 because of this issue.

going to follow things to do first guide and then install the drivers as suggested above :(

---

### Post by markbuntu on 2008-06-20
That guide works for both 386i and amd64. I have both on my machine and have tried it out. Still, it is important to follow this:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

To get it working at its best.

---

### Post by chappers on 2008-06-20
i have followed the guide[s] and troubleshooting bit and i still get mesa.

i have ati drivers installed as aticonfig and amdcccle work without problems.

HEres me xorg.conf

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
Option "AIGLX" "on"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
        Option "XAANoOffscreenPixmaps" "on"
        Option "TexturedVideo" "on"
        Option "VideoOverlay" "off"
        Option "OpenGLOverlay" "off"
        Option "Textured2D" "on" 
        Option "TexturedXrender" "off"
        Option "UseFastTLS" "1" 
        Option "BackingStore" "on" 
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
DefaultDepth 24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

I still need pointers on the correct settings ie Recognising my monitor for one!

my 

lspci -n | grep 0300

```
01:00.0 0300: 1002:554d
```

Card is Radeon X800XL 256DDR3 AGP ie:

my 

lspci | grep VGA

```
01:00.0 VGA compatible controller: ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)
```

my fglrxinfo

```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)
```

been round in circles today. Was considering another #6 re-install, but managed somehow - dont ask me how - to save this installation.

---

### Post by peterjanda on 2008-06-20
Hello all.

The rig I'm using to test and migrate to linux has an All-in-Wonder 8500 video card, based on the R200 chip set (I know, don't ask - it's a scavenged hand-me-down).  When I use the open source driver (i.e., xorg.conf contains Driver "ati"), my CPU gets 100% utilized as soon as I boot up.  When I corrupt the xorg.conf file to load up with an unconfigured, generic .conf, the rig is blazing fast - no issues, other than the maximum resolution being 800x600.

When using the open source driver, I dropped down to 800x600 resolution to assess whether being in 1280x1024 resolution was somehow the cause, but my CPU was still getting 100% utilized.

I believe I have eliminated all variables and pinned down the utilization problem to the driver.  I have 8.04 installed, 1 gig memory, 2.5 GHz CPU.  Does anyone have ideas about how to fix this issue?

Thanks,

Pete

---

### Post by rkrisher on 2008-06-20
Here is the script I use to install on my Debian Lenny.  You will need to mod one line for your Ubuntu version and edit the version of ati-driver-installer**.run that you downloaded from AMD.

#######################################################################

apt-get install module-assistant build-essential fakeroot dh-make debconf bzip2 wget
./ati-driver-installer-8-5-x86.x86_64.run --extract fglrx
cd fglrx
cd arch/x86_64/usr/X11R6
ln -s lib64 lib
ln -sf libfglrx_gamma.so.1.0 lib/libfglrx_gamma.so.1
cd -
./packages/Debian/ati-packager.sh --buildpkg lenny #replace with lenny or sid when appropriete
cd ..
dpkg -i fglrx*.deb
module-assistant prepare
module-assistant update
module-assistant a-i fglrx
aticonfig --initial

#####################################################################

I looked in my "fglrx" directory that was created.  The Ubuntu builds are listed inside the "ati-packager.sh" file and are for these versions:

DAPPER="dapper 6.06"
EDGY="edgy 6.10"
FEISTY="feisty 7.04"
GUTSY="gutsy 7.10"
HARDY="hardy 8.04"

For example, if you were installing on Ubuntu Feisty, you would change this line in the above script:

./packages/Debian/ati-packager.sh --buildpkg lenny

with this:


./packages/Ubuntu/ati-packager.sh --buildpkg feisty

reboot after the install.  

The command "fglrxinfo" should show something like:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7537 Release


It usually still says "MESA" if you didn't update your install with module-assistant.

You can get, through apt, a program called rovclock.  Lets you overclock your ATI card.  For my ATI Xpress 200M I issue, at the root prompt,:

rovclock -c490 -t tRFC:17 -t tWL:4

changes the clock from it's 300Mhz to 486.88Mhz

and get:

9472 frames in 5.0 seconds = 1894.231 FPS
9541 frames in 5.0 seconds = 1908.128 FPS
9655 frames in 5.0 seconds = 1930.843 FPS
9710 frames in 5.0 seconds = 1941.922 FPS
9711 frames in 5.0 seconds = 1942.163 FPS
when I run "glxgears" at the prompt.

I barely get 800 FPS out of the MESA drivers.

Hope this helps!!

---

### Post by rkrisher on 2008-06-20
Here is my lines from Xorg, tweeked for performance.

Section "Monitor"

  # created by KGamma
	Identifier   "aticonfig-Monitor[0]"
	Gamma        1.2 1.15 1.2
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "MaxGARTSize" "256"
	Option	    "NoTrapSignals" "on"
	Option	    "AIGLX" "On"
	Option	    "TexturedVideoSync" "on"
	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "off"
	Option	    "OverlayOnCRTC2" "0"
	Option	    "UseFastTLS" "on"
EndSection

Keep in mind I'm running on an external monitor instead of my laptops monitor.

---

### Post by erutufon on 2008-06-21
Hi
I have a radeon 9200se, running on ubuntu 7.10.  am a noob, so the discussion above a bit beyond me.  am trying to get correct drivers and then get TV output.  have tried the wiki, method one, and get stuck at aticonfig - I get

Warning: Could not find configuration file
Please copy configuration file template to /etc/X11

can anyone help? 

many thanks

---

### Post by sim-value on 2008-06-22
Running as Root ?

look if theres a file at /etc/X11/xorg.conf (nano /etc/X11/xorg.conf should display some text)

---

### Post by EarthMind on 2008-06-25
Hey,

I tried many things to get the latest ATI Radeon 9000 driver installed from the ATI website but whatever I do I always get an error so I hope someone here can help me.

I followed this tutorial but without success:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-43e2a0cc2efa10f6bc15751dde817d382728f516](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-43e2a0cc2efa10f6bc15751dde817d382728f516)

Here's what I did:
```
sudo apt-get install dpkg-dev debhelper libstdc++5 dkms
```
Error: none

```
sudo ./ati-driver-installer-8.28.8.run --buildpkg Ubuntu/gutsy
```
Error: Package not supported.
Second try with latest supported OS:
```
sudo ./ati-driver-installer-8.28.8.run --buildpkg Ubuntu/edgy
```
Result:
```
Generating package: Ubuntu/edgy
[: 182: ==: unexpected operator
./packages/Ubuntu/ati-packager.sh: 182: pushd: not found
Package build failed!
Package build utility output:
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
tail: cannot open `debian/changelog' for reading: No such file or directory
dpkg-buildpackage: failure: tail of debian/changelog gave error exit status 1
./packages/Ubuntu/ati-packager.sh: 182: popd: not found
Removing temporary directory: fglrx-install
```

Does anyone have any advice for me?


Thanks in advance

---

### Post by sim-value on 2008-06-25
That was the oldest version of the driver you could find ... was it ?

---

### Post by EarthMind on 2008-06-25
> **sim-value said:**
> That was the oldest version of the driver you could find ... was it ?

The driver is from Aug. 18, 2006 and seems to be the latest one for my graphic card, which is ATI Radeon 9000

---

### Post by markbuntu on 2008-06-25
> **EarthMind said:**
> The driver is from Aug. 18, 2006 and seems to be the latest one for my graphic card, which is ATI Radeon 9000

That is because the 9000 is supported by the open source driver, which is what you should be using.

---

### Post by Rocket2DMn on 2008-06-25
Yes, the Radeon 9000 is too old to be supported by the restricted fglrx drivers, so you should remove those if you actually installed them.
What version of Ubuntu are you using?

---

### Post by EarthMind on 2008-06-26
I am using the latest 8.04 Ubuntu and the reason I want the restricted ATI driver is because my xorg.conf looks like this:

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"be"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```

And I can't seem to set the resolution to 1024x768 for the loading and login screen...

Ive tried this:
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"be"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth 24

	SubSection "Display"
    		Depth 24
    		Modes "1024x768" "800x600"
  	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```

---

### Post by Rocket2DMn on 2008-06-26
EarthMind, your original xorg.conf is correct - assuming you are using Hardy, the new version of X relies more on autodetection and less on xorg.conf than it used to.  If you remove the fglrx driver and reset xorg.conf, you should be good to go.

---

### Post by Yellow Pasque on 2008-06-26
> **EarthMind said:**
> And I can't seem to set the resolution to 1024x768 for the loading and login screen..
Is /etc/usplash.conf set properly?

---

### Post by EarthMind on 2008-06-27
> **Rocket2DMn said:**
> EarthMind, your original xorg.conf is correct - assuming you are using Hardy, the new version of X relies more on autodetection and less on xorg.conf than it used to.  If you remove the fglrx driver and reset xorg.conf, you should be good to go.

I am using the included driver for my card and have tried to change the resolution of the login and loading screen in many ways without success.

Kind thanks

---

### Post by EarthMind on 2008-06-27
> **Temüjin said:**
> Is /etc/usplash.conf set properly?

This did the trick for the loading screen, do you by any chance also know how to change this for the login screen?

Many thanks

---

### Post by cotiK on 2008-06-27
ok, pleeeeeaaase heeelp!
 from "uname -r+ i get ```
2.6.24-19-generic
```
 so i do ```
sudo dpkg-reconfigure -phigh linux-restricted-modules-2.6.24-19-generic sudo insmod /lib/modules/2.6.24-19-generic/volatile/fglrx.ko
``` and i get ```
Package `insmod' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: insmod is not installed
```
so then i do separatley
```
sudo dpkg-reconfigure -phigh linux-restricted-modules-2.6.24-19-generic
```" and then
```
sudo insmod /lib/modules/2.6.24-19-generic/volatile/fglrx.ko
```
the first command returns nothing but the second ```
insmod: error inserting '/lib/modules/2.6.24-19-generic/volatile/fglrx.ko': -1 File exists
```

i have ubuntu hardy, and ati 9600
any suggestions please?

---

### Post by RobOrr on 2008-06-27
Don't know if anyone else has this problem, couldn't find it when i searched for it... but here goes:

Running 8.04, got the drivers working fine using the guide at the start of the thread. however, every time I restart my computer, I have to run the two terminal commands :

sudo dpkg-reconfigure -phigh linux-restricted-modules-2.6.24-19-generic
and
sudo insmod /lib/modules/2.6.24-19-generic/volatile/fglrx.ko

else the computer refuses to use the driver (says 'not in use' whilst the tickbox is ticked in 'Hardware Drivers')

can anyone help me get my computer to sort this out without me typing this in on every startup? would prefer to do it without just creating a cheap script to run each time my computer turns on.

---

### Post by zx5itouch on 2008-06-30
I currently run a Dell E1505 that has an ATI Mobility Radeon X1400 graphics card. I have tried to download the linux version from ATI with no success. Is there a way to install the driver that I use for my PC R128573.exe just like I can for my wireless card. I need to have S-video out to connect to my TV as it works in Windows but not Ubuntu. Please help. I'm a noob and I'm very frustrated that my Wireless card and my ATI graphics card is such a pain in the rear to get working correctly on Ubuntu Hardy heron.

---

### Post by FaizanKazi on 2008-07-02
glxgears does around 1900 fps with ATI binary drivers

fglrxinfo gives:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 1.4 (2.1.7659 Release)

glxinfo | grep direct       gives:
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)

BUT

fgl_glxgears         gives:
Using GLX_SGIX_pbuffer
Segmentation fault

AND

cat /proc/mtrr     gives:
reg00: base=0x00000000 (   0MB), size=2048MB: write-back, count=1
reg01: base=0x7ff00000 (2047MB), size=   1MB: uncachable, count=1

WHY is my video memory 1MB and what's this Segmentation fault thing?
The guide I used to install the binary Ati 8.6 drivers was the following:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Instructions%20for%20Ubuntu%208.04%20(Hardy)%20with%20ATi%208.443.1-1%20and%20above%20binary%20drivers](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Instructions%20for%20Ubuntu%208.04%20(Hardy)%20with%20ATi%208.443.1-1%20and%20above%20binary%20drivers)

---

### Post by realworld25 on 2008-07-02
> **kipman725 said:**
> Hello I installed the latest ATI drivers and they are working well but some of the information in the howto is not correct for all users:
control center works fine on my Pc
I didn't have to do any editing of linux-restricted-moduals-common file to have the latest driver

still don't have AGP DMA in any form working  so performance is still kind of neutered (this is a motherboard issue) but alot better than what I was getting with the apt-get drivers (I don't think they installed properly).  Thanks :D

i hav face same problem what should i do for that one ...

---

### Post by markbuntu on 2008-07-02
The directions linked to on the first page of this thread are outdated and mostly wrong.

If you need the newest driver from ATI you can download it from here:

[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

The directions for installing it are here (Use Method 2, Method 1 will get the latest one in the repos):

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

The directions for tweaking it are here:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

Please follow the directions for installing exactly. Many people have had problems by not doing so.

---

### Post by x351912 on 2008-07-09
Hi,

Thanks tseliot for the hard work and dedication you have to helping folks like me get their video cards working. Sadly, I ran into a problem that I hope can be resolved easily.  I ran these instructions:

> Instructions for Ubuntu 8.04 (Hardy)

Enable accelerated the accelerated ATI graphics driver in the restricted-manager, then do:

sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r`
sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko

Log out and log in. 

Here is the output from the command lines:
****@unrecognized:~$ sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r`
[sudo] password for ****: 
****@unrecognized:~$ sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko
insmod: error inserting '/lib/modules/2.6.24-19-generic/volatile/fglrx.ko': -1 Operation not permitted

Here is my chipset:
01:05.0 VGA compatible controller: ATI Technologies Inc RS690 [Radeon X1200 Series]

What happens when I reboot my system hangs after a ubuntu progress bar. No numlock, no ctlr-alt-backspace no ttys. All I can do is reboot and run recovery mode, and have it "fix" my xorg and I'm back to square one.

So here is my xorg.conf:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

Thanks in advance!

---

### Post by Alan Coleman on 2008-07-12
Hi there, having some probs getting this card to work. Any expirience of this card. Im useing an IBM thinkpad.
 
response to lspci is:
ATI Technologies Inc Radeon Mobility M6 LY

response to sudo gedit /etc/X11/xorg.conf is:
Section "Device"
	Identifier	"Configured Video Device"
EndSection


Im new but not that new and Ive had bad luck with graphics cards so far.

seems ive tried all the methods but it is possible human error or unknowing is responsible

thanks.ac

---

### Post by spike-soft on 2008-07-13
well the more i try all of you how to guides the worse my pc gets linux doesnt want you to play high-end classy games or let you use your ati x1550 pci-e or anything install line by line code that doesnt work is there lots of bad-minded jerks laughing at me n 10000s of other people who cant get linux working for them because its setup to cause you more headackes than windows does or SOMEONE PROVE ME WRONG CAUSE EVERY THING I DO DOESNT WORK CANT LOAD RUN OR INSTALL ATI DRIVERS IM FED UP ! AND I DONT THINK IT CAN BE DONE.
ALL I WANT IS TO PLAY NEED FOR SPEED PRO STREET , COPY THINGS N MAYBE DOWNLOAD STUFF BUT NO IT CANT B DONE CAN IT ?

---

### Post by Alan Coleman on 2008-07-13
Nope cant be done. <snip>

---

### Post by jenal2 on 2008-07-17
Hey
Welcome in this forum. Hope you will enjoy discussion and you will give good suggestions to other people also.

---

### Post by pfsquirrel on 2008-07-17
Having a similar issue with ATI 9700Pro AGP 128M.

System is:

Asus A7V880 mobo
512MB RAM (Kingston)
AMD Athlon 3200+

Everything runs blazing fast with a fresh install. However, I've tried installing the ATI proprietary drivers (latest 8.6) and once I reboot, the only thing I get is a blank screen. If I recover, I can get everything back fine.

Now I'm a relative Linux newbie, so I was a little throw off by the restricted-manager. What exactly is this? I'd like to try the open-source drivers or a change, too.

---

### Post by Melcar on 2008-07-17
> **pfsquirrel said:**
> Having a similar issue with ATI 9700Pro AGP 128M.

System is:

Asus A7V880 mobo
512MB RAM (Kingston)
AMD Athlon 3200+

Everything runs blazing fast with a fresh install. However, I've tried installing the ATI proprietary drivers (latest 8.6) and once I reboot, the only thing I get is a blank screen. If I recover, I can get everything back fine.

Now I'm a relative Linux newbie, so I was a little throw off by the restricted-manager. What exactly is this? I'd like to try the open-source drivers or a change, too.


The open source drivers should work on that card rather well.  Just make sure Ubuntu is loading "radeon" for the card.  In your xorg.conf, edit/add to the Device section:

Section  Device
...
Driver   "ati"
Option   "GARTSize"  "32"
EndSection

The driver won't give you spectacular 3D performance and it's only openGL1.3, but it should be enough to run things like Compiz and a few games.  Incidentally, I could never get fglrx working with any AGP card.

Edit: Just so you can get an idea of what kind of performance to expect, this is a PTS run I did on a spare machine I got in the office running similar specs as yours:

Athlon XP 1800+ (running @ 1.9GHz)
Abit NF7 V2
512MB RAM (DDR400)
Radeon 9800pro 128MB

[URL="http://global.phoronix-test-suite.com/index.php?k=profile&u=melcar-16054-32056-16144"]http://global.phoronix-test-suite.com/index.php?k=profile&u=melcar-
16054-32056-16144[/URL]

The gaming benchmarks are near the end.  Rather decent performance, except on Open Arena; some games do end up running incredibly poor with this driver for some reason, like Secret Maryo Chronicles (totally unplayable due to massive slowness).

---

### Post by sinaen on 2008-07-19
> **digital_exhaust said:**
> Gave it a try and I get...

```
digital@digital-desktop:~$ sudo sh ./ati-driver-installer-8.40.4-x86.x86_64.run
sh: Can't open ./ati-driver-installer-8.40.4-x86.x86_64.run
digital@digital-desktop:~$ 
```

Downloaded the drivers three separate times and got the same results each time... on a clean updated install... 

Any ideas?

Its wrong you should only write # sudo ./ati-driver-installer-8-6-x86.x86_64.run

---

### Post by ewh1533 on 2008-07-19
Greetings all. Unfortunately I'm a long time widows user with very little experience with linux. I've tried using a linux system once or twice before, but usualy when it came to drivers I found the situation to be rather frustrating. 

But after my last windows crash after an upgrade, I'd like to give it a try again. Things look hopeful with the massive amount of help availible here.

So, heres what I got. 

Running ubuntu 8.04 on the gigabyte ga-ma74gm-s2h motherboard. I'm using the on board ATI graphics addapter, which is supposedly ATI Radeon 2100 based. I looked for the linux drivers for this version of the radeon chipset, but I can't find the exact one for this version.

I'm currently running in low rez mode because the drivers that ubuntu is using aren't working properly. How do I get this up and running. I plan on trying to install Second Life on this thing, so I definitely need the proper drivers.

Edit: I went ahead and installed the restricted drivers. I'm still stuck in low rez mode however, only able to get up to 800X600.. There is some flicker with the 3d rendering of screen savers and such, so not everything is up to par.

---

### Post by markbuntu on 2008-07-19
ATI does not even list a 2100 graphics adapter. What does your X0rg.0.log tell you about what is going on?

Any (EE) or (WW) messages in there are important.

---

### Post by ewh1533 on 2008-07-19
Well, theres alot of II messages.. Some of them mentioning resolution availible in versa. 

other than that the only WW messages are as follows...

(WW) fglrx(0): board is an unknown third party board, chipset is supported

(WW) fglrx(0): Only one display is connnected,so single mode is enabled

(WW) fglrx(0): could not detect X server version (query_status=-3)

(WW) AIGLX: 3D driver claims to not support visual 0x23
(Though this error is repeated, 0x23 through 0x72)

(WW) Configured Mouse: No Device specified, looking for one...

Is there anything I should be tweeking, or maybe trying a different driver all together?

---

### Post by jimv on 2008-07-20
Do this real quick in a terminal.  It'll show what video card you have:

lspci | grep VGA

---

### Post by ewh1533 on 2008-07-20
> **jimv said:**
> Do this real quick in a terminal.  It'll show what video card you have:

lspci | grep VGA

Here's the output:

> 01:05.0 VGA compatible controller: ATI Technologies Inc Radeon 2100

ATI Doesn't seem to have a linux driver for this adapter.. In windows or linux. 

Heh, you never truly realize how much it takes to make an OS work until you have to actually do the work yourself.

---

### Post by jimv on 2008-07-20
Well crap, I didn't see a driver for that either.  Kinda odd ... but I have an idea.

Try using EnvyNG to install the driver.

```
sudo apt-get install envyng-gtk

envyng -t

```
Press 3 to install the ATI driver.

---

### Post by ewh1533 on 2008-07-20
Well tried that and this is what it gave me.. 

> EnvyNG ERROR: Envy does not recognise your card as compatible with any version of the driver.this might happen because either your card is not supported by the driver or Envy's hardwaredetection failed. You can try the manual installation at your risk.


Gigabyte mentions that the is some sort of hybrid, between ATI and AMD's chip sets. It's integrated into the north bridge. A real pain in the butt.

Is there a way I can increase my resolution past 800x600 at least?

---

### Post by markbuntu on 2008-07-20
You could try running this line in a terminal ;

sudo dpkg-reconfigure -phigh xserver-xorg

and try to set a higher resolution.

---

### Post by ewh1533 on 2008-07-20
I tried that, this was the output I got, however the highest resolution I can get is still 800x600. Was I supposed to add a modifier of some sort to set the highest resolution? 

> xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080720133704


---

### Post by ewh1533 on 2008-07-20
I don't know what I did to get it to work but now it's working fine. While there still seems to be a few bugs here and there (such as the screen saver window freezing on me) I have full resolution.

I had installed the restricted drivers for the ATI accelerated graphics card. Ubutu kept me in low rez mode. I had used Envy at one point, but I don't think I bothered to restart. I tried it again and installed the drivers, when restarted it worked just fine, crisp clear screen and full use of my resolution.

Edit:

Well, then again.. the drivers are working, but it seems not to the full capability of the graphics adapter. Tried running second life and the program advised me that the graphics card wasn't up to par. While this card isn't the top of the line, it should certainly be able to handle SL.

---

### Post by musiclover45 on 2008-07-21
hello ,

I'm having slow issues all around on Heron.

01:00.0 VGA compatible controller: ATI Technologies Inc RV516 XT Radeon X1600 Series (Primary)
01:00.1 Display controller: ATI Technologies Inc RV516 XT Radeon X1600 Series (Secondary)

This is my card and in Hardware drivers, there is nothing there. Would this be why I'm having slow issues and what can I do to fix it please? please help me out give me some suggestions.

---

### Post by DoomChisel on 2008-07-23
Hello all!
I have big trouble after fglrx installation and followed reboot: my xorg just hangs showing black screen. I cannot even switch desktops. My only way is to use Alt+SysRq+"Rising Elephants..." which works. 

So, windows on my configuration works without any problem, kUbuntu with vesa driver - too. Here's the configuration:
 - ATI Radeon Mobility 9700 video
 - notebook [_RoverBook Nautilus X500_]("http://www.roverbook.ru/site/roverbook/homen.nsf/techspecs/NB000133")
And kUbuntu is Hardy Heron 8.04. I installed this driver by various methods including wiki on ATI site; the last is Envy.

Examples of crash log:
 - after Envy:
> Jul 23 17:59:26 mobilis821 dhcdbd: Started up.
Jul 23 17:59:28 mobilis821 kernel: [   52.558856] [fglrx] Internal AGP support requested, but kernel AGP support active.
Jul 23 17:59:28 mobilis821 kernel: [   52.558863] [fglrx] Have to use kernel AGP support to avoid conflicts.
Jul 23 17:59:28 mobilis821 kernel: [   52.558867] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
Jul 23 17:59:28 mobilis821 kernel: [   52.559402] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Jul 23 17:59:28 mobilis821 kernel: [   52.559540] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Jul 23 17:59:28 mobilis821 kernel: [   52.559691] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Jul 23 17:59:28 mobilis821 kernel: [   52.559842] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
Jul 23 17:59:28 mobilis821 kernel: [   52.560004] [fglrx] Setup AGP aperture
Jul 23 17:59:28 mobilis821 kernel: [   52.560167] [fglrx] GART Table is not in FRAME_BUFFER range 
Jul 23 17:59:28 mobilis821 kernel: [   89.404940] Marking TSC unstable due to: cpufreq changes.
Jul 23 17:59:28 mobilis821 kernel: [   89.409013] [fglrx] Reserved FB block: Shared offset:0, size:40000 
Jul 23 17:59:28 mobilis821 kernel: [   89.409021] [fglrx] Reserved FB block: Unshared offset:7ff5000, size:b000 
Jul 23 18:05:39 mobilis821 syslogd 1.5.0#1ubuntu1: restart.


 - after method from wiki:
> Jul 23 10:45:49 mobilis821 kernel: [   56.690018] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
Jul 23 10:45:49 mobilis821 kernel: [   56.690303] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Jul 23 10:45:49 mobilis821 kernel: [   56.690447] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Jul 23 10:45:49 mobilis821 kernel: [   56.690603] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Jul 23 10:45:49 mobilis821 kernel: [   56.690782] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
Jul 23 10:45:49 mobilis821 kernel: [   56.690953] [fglrx] Setup AGP aperture
Jul 23 10:45:49 mobilis821 kernel: [   56.691116] [fglrx] GART Table is not in FRAME_BUFFER range 
Jul 23 10:45:49 mobilis821 kernel: [   56.693662] [fglrx] Reserved FB block: Shared offset:0, size:40000 
Jul 23 10:45:49 mobilis821 kernel: [   56.693667] [fglrx] Reserved FB block: Unshared offset:7ff5000, size:b000 
Jul 23 10:45:49 mobilis821 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 23 10:45:49 mobilis821 kernel: [   68.957843] Marking TSC unstable due to: cpufreq changes.


Maybe someone can save me from happy WiNDow$ world? :)

P.S.: "Marking TSC unstable due to: cpufreq changes." is normally for my system - it is also presented in logs of succesful boot.

---

### Post by NvidiaN on 2008-07-23
Hi, I'm very new to this but I'm going to try and give as much information as possible here with hopes that someone will be able to help me:

I'm relatively positive my graphics card (ATI IGP 320M) isn't being used by Ubuntu (Hardy Heron). Scrolling down a webpage lags the computer, which was never a problem in windows. I'm trying to install the drivers linked here: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) however I'm running into issues, regardless of which "path" I choose.

The problem I'm having explicitly with the "easy route" is

Enable accelerated the accelerated ATI graphics driver in the restricted-manager, then do:

```
sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r`
```

Initially I wasn't sure what the restricted manager was, but after googling it I found it was in system/administration/hardware drivers (I think). Well, there's no drivers listed here to enable, so I'm not really sure what to do.

```
 lspci -nn | grep VGA
```

Output looks like this:

01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility U1 [1002:4336]

```
sudo vim /etc/X11/xorg.conf
```
Output looks like this for the video device section:

Section "Device"
        Identifier      "Configured Video Device"
EndSection


Again as I said I'm very new to this stuff, I'm used to windows where I can just go to ati.com and download a driver for card X for operating system Y...so if I'm missing a simple/easy step here I apologize. But any help would be very appreciated!

---

### Post by Dreamerman on 2008-07-24
Hi. This really a stupid question. In the terminal, I keyed in the following $ lspci -nn | grep VGA to check graphic card name & shipset but nothing happened.

Can anyone help ?

Thanks

---

### Post by NvidiaN on 2008-07-24
> **Dreamerman said:**
> Hi. This really a stupid question. In the terminal, I keyed in the following $ lspci -nn | grep VGA to check graphic card name & shipset but nothing happened.

Can anyone help ?

Thanks

Take the $ out, 

```
lspci -nn | grep VGA
```

---

### Post by Dreamerman on 2008-07-25
Hi. I managed to check out my graphics card under terminal. Using lspci gave the following results:-

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 QW [Radeon 7500]

Then I used gedit on xorg.conf & got the following:-

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

I think so far so good. My VGA card is a 7500/RV200 based card & should have full 3D acceleration support using AIGLX. I hope I am right in this. I just did a fresh install of Ubuntu & have not used any proprietary drivers.

According to [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver), xorg.conf should read something like this:-

Section "Device"
        Identifier      "Radeon 9600"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
EndSection

Does it mean that I should manually edit my xorg.conf to reflect something like this?:-

Section "Device"
        Identifier      "Radeon 7500"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
EndSection

Sorry for the long post but I don't really know what to do next. Can anyone help please ?

Cheers

---

### Post by Rocket2DMn on 2008-07-25
Dreamerman, you shouldn't have to do anything extra to use the open source "ati" or "radeon" driver, this is enabled by default.  Problems would arise if you installed the fglrx drivers, which you should remove if you have them.  Your Radeon 7500 is only supported with the open source drivers.
The newer version of X (the backend GUI software) relies more on autodetection these days, so you don't need all that info in your xorg.conf file.  You can reset your xorg.conf file by running
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
Then restart X with CTRL+ALT+BACKSPACE.

---

### Post by Dreamerman on 2008-07-25
> **Rocket2DMn said:**
> Dreamerman, you shouldn't have to do anything extra to use the open source "ati" or "radeon" driver, this is enabled by default.  Problems would arise if you installed the fglrx drivers, which you should remove if you have them.  Your Radeon 7500 is only supported with the open source drivers.
The newer version of X (the backend GUI software) relies more on autodetection these days, so you don't need all that info in your xorg.conf file.  You can reset your xorg.conf file by running
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
Then restart X with CTRL+ALT+BACKSPACE.

Hi, thanks a bundle for your help. I reset the xorg.conf file per your instruction & CTRL+ALT+BACKSPACE. An error message appeared, something about cannot initialise HAL. I ignored the error & reboot. Rebooted ok. I went to terminal & glxinfo gave me the following. Did I manage to get it correct?. How do I know I have enabled my video card capabilities?

Many thanks.

master@ubuntu-server:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20061018 AGP 4x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.3-rc2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_logic_op, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_histogram, 
    GL_EXT_packed_pixels, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_MESA_ycbcr_texture, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x68 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

---

### Post by Rocket2DMn on 2008-07-25
If it's working OK, you should be good to go.  You can check that the radeon module is loaded by running
```
lsmod | grep radeon
```

Is everything working normally now?

---

### Post by Dreamerman on 2008-07-25
> **Rocket2DMn said:**
> If it's working OK, you should be good to go.  You can check that the radeon module is loaded by running
```
lsmod | grep radeon
```

Is everything working normally now?

Wow, thx for the super rapid reply. I got the following. Does it look correct ? Do I actually have 3D ?

master@ubuntu-server:~$ lsmod | grep radeon
radeon                124192  2 
drm                    82452  3 radeon

---

### Post by Rocket2DMn on 2008-07-25
> **Dreamerman said:**
> Wow, thx for the super rapid reply. I got the following. Does it look correct ? Do I actually have 3D ?

master@ubuntu-server:~$ lsmod | grep radeon
radeon                124192  2 
drm                    82452  3 radeon

Sexy.

You should have 3d available.  Now, since your card is so old, compiz may not work very well, but you can always try.  To see how to enable compiz on a card using these open source drivers, see this thread - [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633) (it has a brief explanation as to why this is needed)

---

### Post by Dreamerman on 2008-07-25
> **Rocket2DMn said:**
> Sexy.

You should have 3d available.  Now, since your card is so old, compiz may not work very well, but you can always try.  To see how to enable compiz on a card using these open source drivers, see this thread - [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633) (it has a brief explanation as to why this is needed)

GREATTTTTTTT :-)

I am not into eye candies so compiz isn't terribly important. In fact I am avoiding compiz due to past experience with SUSE 11 compiz. Wrecked my whole system ! Actually, I moved from SUSE 11 to Ubuntu. I can't believe the ease in which Ubuntu can be installed & get it working properly. I sold on Ubuntu forever !!

Yeah, my card is pretty old by today's standard but still going ok. Will stick to it until it's dead.

Once I am more comfortable with Ubuntu, I will say bye bye to XP !!

Thanks a million again.

---

### Post by Dreamerman on 2008-07-25
IMPORTANT : I think a special mention needs to me made to all who have older cards like mine ATI Radeon 7500LE. DO NOT INSTALL "ATI CATALYST CONTROL CENTER" from add/remove. When I installed it (don't ask why, stupid I guess), my settings went back to default ie no 3D or rendering. I had to totally remove it & re-set it again.

Suggestion : Perhaps there should be a mention under add/remove "ATI CATALYST CONTROL CENTER" description that this may not be suitable for all cards especially older ones.

Thanks.

---

### Post by Rocket2DMn on 2008-07-26
> **Dreamerman said:**
> IMPORTANT : I think a special mention needs to me made to all who have older cards like mine ATI Radeon 7500LE. DO NOT INSTALL "ATI CATALYST CONTROL CENTER" from add/remove. When I installed it (don't ask why, stupid I guess), my settings went back to default ie no 3D or rendering. I had to totally remove it & re-set it again.

Suggestion : Perhaps there should be a mention under add/remove "ATI CATALYST CONTROL CENTER" description that this may not be suitable for all cards especially older ones.

Thanks.

To be more specific, any card older than a Radeon 9500 should be using the open source drivers that come installed by default.

---

### Post by Adahn on 2008-07-27
Is envyNg installing the 8.6 or 8.7 cats?

---

### Post by markbuntu on 2008-07-27
I don't think so, I think envy is still at 8.5. If you want 8.7 you can follow this guide, use Method 2 and follow it very carefully:


[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

The directions for tweaking it are here:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

Release notes for 8.7

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_87_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_87_linux.html)

Release Notes for 8.6

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_86_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_86_linux.html)

Release notes for 8.5

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_85_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_85_linux.html)

Make sure that your card is listed in the release notes.

---

### Post by Melcar on 2008-07-27
> **markbuntu said:**
> 
...
The directions for tweaking it are here:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

...




Most of those "tweaks" are not really needed.  The driver loads whatever options the target card is capable of automatically once it's initialized (except in some occasions where you have to specify Xv), so using something else may have undesirable results.  Use these options with caution as they may  or may not work for all cards.

---

### Post by sim-value on 2008-07-28
W00t catalyst 8.7 works for me !

Only wine screws up and 3D is not working correctly with desktop effects on ...

---

### Post by Melcar on 2008-07-28
> **sim-value said:**
> W00t catalyst 8.7 works for me !

Only wine screws up and 3D is not working correctly with desktop effects on ...



You mean 3D games?  As long as you play them in fullscreen they should work fine.  Same thing applies to videos.

---

### Post by bondo101 on 2008-07-28
Thanks for the heads up and the info
                    bondo101

---

### Post by spandanj on 2008-07-31
I have a problem. I am using ati radeon mobility x1400 on dell 6400.

I am currently using ATI restricted driver provided by Ubuntu. But, I get pixelated video on full screen. I have compiz ON. No Xgl installed. I do NOT want to turn off Compiz to enjoy openGl to playback my fullscreen videos. Thus, WHAT SOLUTION is there to fix this. Naturally, regular updates has not solved the problem since I moved to 8.04 from 7.10.

Does this problem disappear if I install ATI's proprietary drivers - latest catalyst 8.7. Is that driver better than the Ubuntu's restricted driver. If yes, how shall I go about uninstalling the restricted driver and installing ATI's proprietary one?

thank you.

---

### Post by jonesa3 on 2008-07-31
Hi!

I've been using Ubuntu for a few months now on my laptop, which has an nvidia graphics card, and it has been working beautifully.  Couldn't be happier there.  

However, I just built myself a new machine (specs below) and am having trouble getting my ATI radeon hd 3650 to work fully.  Here is how the problem goes:

Everything installs fine, x loads just fine normally, and I'm up and running. However, whenever I go to enable the proprietary drivers for the ATI card, and I go to restart like it tells me to, I run into problems.  It shuts down fine, but when I go to start up, it gets past the Ubuntu loading bar screen, tries to start x and just freezes with a black screen.  My solution to this situation has been to restart, but in recovery mode, and tell it to try and fix the x server.  This proceeds, and then I can load up Ubuntu normally.  Same thing happens again and again when trying to use the proprietary drivers.  

When I tried loading from a command line at the outset, I got an error like "GTX warning, could not open display".  Just bizarre.

I have tried the instructions on Envy, but to no avail.  As it stands, my computer works like a dream, but I can't enable the desktop effects for some reason.  I guess what I'm wondering is if there is a way to get the 3d acceleration and desktop effects working on my computer.  

Sorry if this is a really simple question, but I didn't see an answer to my specific problem on the thread (albeit I only gave it a cursory glance).  I'm a new(er) user of Ubuntu, and I'm willing to take any advice you might be able to offer! :)

Thanks in advance!

Specs:

Intel Core 2 Duo (2.53ghz)
8 gb ddr2 
Saphire Radeon HD 3650 pcie2
Ubuntu 8.04 full updated.

Cheers,
Andrew

---

### Post by markbuntu on 2008-07-31
Try using these directions for installing the ati driver, use Method 2:


[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

I have a HD3650 and these directions have never failed me, since the 8.4 driver to the 8.7 driver now.

---

### Post by sim-value on 2008-07-31
> **Melcar said:**
> You mean 3D games?  As long as you play them in fullscreen they should work fine.  Same thing applies to videos.

Well wine screws up always also with desktop effects off ...

Videos run in fullscreen with Compiz more or less acceptable ...

but ill try to make it perfect later 3D games made for Linux are just cool !
(and i thought im a Programmer)

---

### Post by markbuntu on 2008-07-31
If you want to run wine, there are some suggestions here for setting up fglrx for that:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

These are not official and so may or may not work.

---

### Post by jonesa3 on 2008-08-01
> **markbuntu said:**
> Try using these directions for installing the ati driver, use Method 2:


[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

I have a HD3650 and these directions have never failed me, since the 8.4 driver to the 8.7 driver now.

markbuntu,  THANK YOU!  I'd been looking at different howto's, coming up empty, but this worked like a dream.  much appreciated!!

My computer is working perfectly now.  

Cheers!

Andrew

---

### Post by rogval on 2008-08-05
Ok...I have just put Ubuntu 8.04 on a system I have devised of some older parts in order to make a media server for the living room tv.  I am using a Radeon 9250 128mb video card which apparently support for this particular card is terrible.  Seems as though they danced all the way around this model.  But anyway...all I want to do is be able to use the S-video port, which apparently you have to either know how to write your own OS...or be able to use the ATI proprietary driver in order to activate/use the s-video port on this card, which apparently you can't with this version on linux.

To make a long story short...I have been googling and reading till I have gone into sensory overload and my eyeballs are bleeding, so I just want to know if there is ANY way to make the S-video work on this card!?!?!  I would even consider installing an older or different version of ubuntu.  But I would prefer that be an absolute last option!!

Thanks
Roger

---

### Post by peakshysteria on 2008-08-05
How can we find out which driver EnvyNG uses? For the past year Envy has let me down. Installing the ATI driver using Enyvy(NG) doesn't work in my end. Not sure why. A lot of other people seem to have had success with Envy. It would be nice if we could somehow find out which driver EnvyNG would install before we ran it. In addition it would be nice download the latest driver and tell EnvyNG to use it. For now I'm still a bit n00b when it comes to the terminal. The above mentioned method 2 is still to hard for me to come through. It always fails.

---

### Post by aussie_scisat on 2008-08-06
[FONT="Arial"][SIZE="2"]
Hi.

New to Ubuntu migrated from Mandriva.

Installed 8.04, and got most things going properly, but Google Earth won't run and the error message indicates a rending problem.
[SIZE="2"][FONT="Arial"][/FONT][/SIZE]
I have been following this "How To" without success. [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
The problem may be that I am using a wide screen monitor AOC 210V.

My system
MB Intel D975 XBX
1 GB RAM
SATA HD
Dual 3GHz processors
Video Card PCI-e ASUS AX550  lspci gives Radeon RV370 Sapphire

My modified xorg.conf.
=====================  Paste
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

Section "Device"
    Identifier    "Radeon RV370"
        Driver          "ati"
        BusID           "PCI:01:00:1"
        Option          "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    Option          "DPMS"
    HorizSync       28-72
    VertRefresh     43-60
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Radeon RV370"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection "Display"
                Depth           24
                Modes           "1680x1050" "1440x900" "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
    Option        "AIGLX"        "true"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice     "Generic Keyboard"
    InputDevice     "Configured Mouse"
EndSection

Section "DRI"
    Mode 0666
EndSection

Section "Extensions"
    Option "Composite" "Enable"
EndSection
================= End of paste

Yes, I know, it's an ATI !
I just thought I might ask before I go out and buy an nVidea card.
The card I am looking at is a budget priced card
ASUS EN8400GS     which uses the GeForce 8400GS chipset.
Any problems with this card seem to have been solved.

I might add that I have tried the "flgrx" driver. The result was that I finished up with the screen covered by a pale blue (opaque) curtain. When I used <cntrl> <alt> <backspace> the blue film disappeared and the default H.H. screen very briefly appeared. If anyone has thoughts on this as well - I would love to hear.

Thank you all for any help.

Regards

Philip

[/SIZE][/FONT]

---

### Post by elcid89 on 2008-08-09
> **markbuntu said:**
> Try using these directions for installing the ati driver, use Method 2:


[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

I have a HD3650 and these directions have never failed me, since the 8.4 driver to the 8.7 driver now.

I tried method 2, and found that I was consistently having the problem with MESA loading instead of the ATI driver.

When attempting to remove xserver-xgl, it was already not installed, so no joy there.

I ended up having to remove xserver-xorg-video-intel

The driver for the onboard Intel video was conflicting with the ATi driver, and Ubuntu was trying to load them both, ergo problems ...

Removed the intel driver and immediate joy. Everything works perfectly now. If you have onboard Intel video on your motherboard and are having the MESA loading instead of ATI problem, it might be worth it for you to give that a try.

---

### Post by BogdanV on 2008-08-10
I'm afraid I tried using all of the methods provided on : the BinaryDriverHowto [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI), the unofficial Linux ATi Drivers Wiki (both 1st and 2nd method), tried executing the .run package provided by AMD/ATi's official site and executing the setup. I also tried by enabling the Driver in Restricted Drivers Manager. I also tried using EnvyNG.
 All methods resulted in a blank screen after the load screen.

 I'm running a X1300 ATi card on Xubuntu (Hardy Heron version). Is there anything I can do ? 
 How should I alter the Xorg.conf file in order to make the driver run (and stop using the Mesa drivers), either proprietary or open-source ?

---

### Post by ummelum on 2008-08-10
hardware: an ATI Radeon Mobility 9600 with 64MB onboard, in a NEC I-Select 4610 laptop; laptop has 512MB of system memory which is fine according to memtest86+; laptop has a LCD creen, which runs at widescreen 1280x800

software: latest xubuntu (kernel 2.6.24-19-generic), run from harddrive

story: i'm trying to get ATI's proprietary driver to work

problem: ATI's driver installed fine through Synaptic, i have 'RADEON_LIGHT=true' in /etc/defaults/acpi-support (i need it); i disabled the Composite extension in xorg's configuration file (i don't need it), ran aticonfig on it, and rebooted. everything works except anything that does 3d (anything that uses OpenGL?); sometimes 3d-related stuff works for a very brief period (several seconds), but usually starts trashing the screen, locking up the box hard (i can't switch to a text console, i can't kill the x-server with crl-alt-backspace, i can't ssh in): eg., i can run glxgears or fgl_glxgears and it might work, might work shortly, or might start trashing the screen immediately. Blender doesn't work, GoogleEarth doesn't work, fancy screensavers or music visualization don't work; even if i start fglrxinfo or glxinfo from a terminal window, it sometimes trashes the screen and locks up the box...

note that i could only get Xubuntu to install in 'safe graphics mode'...
note that before using the proprietary ATI drivers, i used xorg's radeon, and these gave me more problems than just the 3d stuff...
note that i tried using Envy-ng, and it didn't work either

'sudo lspci|grep VGA'
```
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
```

partial output of 'sudo lspci -nnvvv'
```
00:01.0 PCI bridge [0604]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to AGP Controller [8086:3581] (rev 02) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000c000-0000dfff
	Memory behind bridge: e0000000-efffffff
	Prefetchable memory behind bridge: a0000000-afffffff
	Secondary status: 66MHz+ FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-

01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] [1002:4e50] (prog-if 00 [VGA controller])
	Subsystem: Unknown device [1631:c005]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 255 (2000ns min), Cache Line Size: 16 bytes
	Interrupt: pin A routed to IRQ 10
	Region 0: Memory at a8000000 (32-bit, prefetchable) [size=128M]
	Region 1: I/O ports at c100 [size=256]
	Region 2: Memory at e0010000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at a0000000 [disabled] [size=128K]
	Capabilities: [58] AGP version 2.0
		Status: RQ=80 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3- Rate=x1,x2,x4
		Command: RQ=32 ArqSz=0 Cal=0 SBA+ AGP+ GART64- 64bit- FW+ Rate=x4
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
```

'sudo lshw -C display'
```
  *-display
       description: VGA compatible controller
       product: RV350 [Mobility Radeon 9600 M10]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm vga_controller bus_master cap_list
       configuration: driver=fglrx_pci latency=255 mingnt=8 module=fglrx
```

partial output of'sudo lshw -C bridge'
```
     *-pci:0
          description: PCI bridge
          product: 82852/82855 GM/GME/PM/GMV Processor to AGP Controller
          vendor: Intel Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: 02
          width: 32 bits
          clock: 66MHz
          capabilities: pci normal_decode bus_master
```

'sudo fglrxinfo'
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON 9600/9700 Series
OpenGL version string: 2.1.7412 Release
```

'sudo cat /etc/X11/xorg.conf'
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"be"
EndSection
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection
Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option	"Composite"	"Disable"
EndSection
```

'sudo xdpyinfo'
```
name of display:    :0.0
version number:    11.0
vendor string:    The X.Org Foundation
vendor release number:    10400090
X.Org version: 1.4.0.90
maximum request size:  16777212 bytes
motion buffer size:  256
bitmap unit, bit order, padding:    32, LSBFirst, 32
image byte order:    LSBFirst
number of supported pixmap formats:    7
supported pixmap formats:
    depth 1, bits_per_pixel 1, scanline_pad 32
    depth 4, bits_per_pixel 8, scanline_pad 32
    depth 8, bits_per_pixel 8, scanline_pad 32
    depth 15, bits_per_pixel 16, scanline_pad 32
    depth 16, bits_per_pixel 16, scanline_pad 32
    depth 24, bits_per_pixel 32, scanline_pad 32
    depth 32, bits_per_pixel 32, scanline_pad 32
keycode range:    minimum 8, maximum 255
focus:  window 0x240001f, revert to Parent
number of extensions:    35
    ATIFGLEXTENSION
    ATIFGLRXDRI
    ATITVOUT
    BIG-REQUESTS
    DAMAGE
    DOUBLE-BUFFER
    DPMS
    Extended-Visual-Information
    GLX
    MIT-SCREEN-SAVER
    MIT-SHM
    MIT-SUNDRY-NONSTANDARD
    RANDR
    RECORD
    RENDER
    SECURITY
    SGI-GLX
    SHAPE
    SYNC
    TOG-CUP
    X-Resource
    XAccessControlExtension
    XC-APPGROUP
    XC-MISC
    XFIXES
    XFree86-Bigfont
    XFree86-DGA
    XFree86-DRI
    XFree86-Misc
    XFree86-VidModeExtension
    XINERAMA
    XInputExtension
    XKEYBOARD
    XTEST
    XVideo
default screen number:    0
number of screens:    1

screen #0:
  dimensions:    1280x800 pixels (339x212 millimeters)
  resolution:    96x96 dots per inch
  depths (7):    24, 1, 4, 8, 15, 16, 32
  root window id:    0x86
  depth of root window:    24 planes
  number of colormaps:    minimum 1, maximum 1
  default colormap:    0x20
  default number of colormap cells:    256
  preallocated pixels:    black 0, white 16777215
  options:    backing-store NO, save-unders NO
  largest cursor:    64x64
  current input event mask:    0x7a802c
    ButtonPressMask          ButtonReleaseMask        LeaveWindowMask          
    ExposureMask             StructureNotifyMask      SubstructureNotifyMask   
    SubstructureRedirectMask FocusChangeMask          PropertyChangeMask       
  number of visuals:    80
  default visual id:  0x23
  visual:
    visual id:    0x23
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x24
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x25
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x26
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x27
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x28
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x29
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2a
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2b
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2c
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2d
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2e
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2f
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x30
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x31
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x32
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x33
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x34
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x35
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x36
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x37
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x38
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x39
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x3a
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x3b
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x3c
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x3d
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x3e
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x3f
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x40
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x41
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x42
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x43
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x44
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x45
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x46
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x47
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x48
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x49
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x4a
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x4b
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x4c
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x4d
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x4e
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x4f
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x50
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x51
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x52
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x53
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x54
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x55
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x56
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x57
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x58
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x59
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x5a
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x5b
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x5c
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x5d
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x5e
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x5f
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x60
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x61
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x62
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x63
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x64
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x65
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x66
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x67
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x68
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x69
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x6a
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x6b
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x6c
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x6d
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x6e
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x6f
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x70
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x71
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x72
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
```

'cat ~/.xsession-errors'
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
** Message: Querying XF86Misc extension
** Message: XF86Misc extension found
** Message: Querying Xkb extension
** Message: Xkb extension found
** Message: Querying XINPUT extension
** Message: XINPUT extension found
** Message: Querying Xkb extension
** Message: Xkb extension found
** (xfwm4:5616): WARNING **: The display does not support the XComposite extension.
** (xfwm4:5616): WARNING **: Compositing manager disabled.
```

'sudo cat /var/log/Xorg.0.log'
```
This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux facio 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Aug 10 14:48:34 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(**) |-->Input Device "Synaptics Touchpad"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,

	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is disabled
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,3580 card 1631,c005 rev 02 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 8086,3584 card 1631,c005 rev 02 class 08,80,00 hdr 00
(II) PCI: 00:00:3: chip 8086,3585 card 1631,c005 rev 02 class 08,80,00 hdr 80
(II) PCI: 00:01:0: chip 8086,3581 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24c2 card 1631,c005 rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 1631,c005 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 1631,c005 rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev 83 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24cc card 0000,0000 rev 03 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24ca card 1631,c005 rev 03 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24c3 card 1631,c005 rev 03 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24c5 card 1631,c005 rev 03 class 04,01,00 hdr 00
(II) PCI: 00:1f:6: chip 8086,24c6 card 1631,c005 rev 03 class 07,03,00 hdr 00
(II) PCI: 01:00:0: chip 1002,4e50 card 1631,c005 rev 00 class 03,00,00 hdr 00
(II) PCI: 02:01:0: chip 8086,4220 card 8086,2701 rev 05 class 02,80,00 hdr 00
(II) PCI: 02:02:0: chip 10ec,8139 card 1631,c005 rev 10 class 02,00,00 hdr 00
(II) PCI: 02:04:0: chip 1524,1411 card a400,0000 rev 01 class 06,07,00 hdr 82
(II) PCI: 02:04:1: chip 1524,0510 card 1631,c005 rev 00 class 05,01,00 hdr 00
(II) PCI: 02:05:0: chip 1106,3044 card 1631,c005 rev 80 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000dfff (0x2000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xa0000000 - 0xafffffff (0x10000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,6), BCTRL: 0x0802 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000a000 - 0x0000bfff (0x2000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x90000000 - 0x9fffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 3: bridge is at (2:4:0), (2,3,6), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[1] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xd4000000 - 0xd7ffffff (0x4000000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0x90000000 - 0x93ffffff (0x4000000) MX[B]
(--) PCI:*(1:0:0) ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] rev 0, Mem @ 0xa8000000/27, 0xe0010000/16, I/O @ 0xc100/8
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xb0000000 from 0xbfffffff to 0xafffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xd0000000 - 0xd00007ff (0x800) MX[B]
	[1] -1	0	0xd0000800 - 0xd00008ff (0x100) MX[B]
	[2] -1	0	0xd0001000 - 0xd0001fff (0x1000) MX[B]
	[3] -1	0	0xf0000600 - 0xf00006ff (0x100) MX[B]
	[4] -1	0	0xf0000400 - 0xf00005ff (0x200) MX[B]
	[5] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[6] -1	0	0xfebff000 - 0xfebff3ff (0x400) MX[B]
	[7] -1	0	0xb0000000 - 0xafffffff (0x0) MX[B]O
	[8] -1	0	0xe0010000 - 0xe001ffff (0x10000) MX[B](B)
	[9] -1	0	0xa8000000 - 0xafffffff (0x8000000) MX[B](B)
	[10] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B]
	[11] -1	0	0x0000a080 - 0x0000a0ff (0x80) IX[B]
	[12] -1	0	0x0000a200 - 0x0000a2ff (0x100) IX[B]
	[13] -1	0	0x0000e300 - 0x0000e37f (0x80) IX[B]
	[14] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[15] -1	0	0x0000e100 - 0x0000e13f (0x40) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[17] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[18] -1	0	0x00001100 - 0x0000110f (0x10) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x00001600 - 0x0000161f (0x20) IX[B]
	[24] -1	0	0x00001200 - 0x0000121f (0x20) IX[B]
	[25] -1	0	0x0000c100 - 0x0000c1ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd0000000 - 0xd00007ff (0x800) MX[B]
	[1] -1	0	0xd0000800 - 0xd00008ff (0x100) MX[B]
	[2] -1	0	0xd0001000 - 0xd0001fff (0x1000) MX[B]
	[3] -1	0	0xf0000600 - 0xf00006ff (0x100) MX[B]
	[4] -1	0	0xf0000400 - 0xf00005ff (0x200) MX[B]
	[5] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[6] -1	0	0xfebff000 - 0xfebff3ff (0x400) MX[B]
	[7] -1	0	0xb0000000 - 0xafffffff (0x0) MX[B]O
	[8] -1	0	0xe0010000 - 0xe001ffff (0x10000) MX[B](B)
	[9] -1	0	0xa8000000 - 0xafffffff (0x8000000) MX[B](B)
	[10] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B]
	[11] -1	0	0x0000a080 - 0x0000a0ff (0x80) IX[B]
	[12] -1	0	0x0000a200 - 0x0000a2ff (0x100) IX[B]
	[13] -1	0	0x0000e300 - 0x0000e37f (0x80) IX[B]
	[14] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[15] -1	0	0x0000e100 - 0x0000e13f (0x40) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[17] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[18] -1	0	0x00001100 - 0x0000110f (0x10) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x00001600 - 0x0000161f (0x20) IX[B]
	[24] -1	0	0x00001200 - 0x0000121f (0x20) IX[B]
	[25] -1	0	0x0000c100 - 0x0000c1ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd0000000 - 0xd00007ff (0x800) MX[B]
	[5] -1	0	0xd0000800 - 0xd00008ff (0x100) MX[B]
	[6] -1	0	0xd0001000 - 0xd0001fff (0x1000) MX[B]
	[7] -1	0	0xf0000600 - 0xf00006ff (0x100) MX[B]
	[8] -1	0	0xf0000400 - 0xf00005ff (0x200) MX[B]
	[9] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[10] -1	0	0xfebff000 - 0xfebff3ff (0x400) MX[B]
	[11] -1	0	0xb0000000 - 0xafffffff (0x0) MX[B]O
	[12] -1	0	0xe0010000 - 0xe001ffff (0x10000) MX[B](B)
	[13] -1	0	0xa8000000 - 0xafffffff (0x8000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B]
	[17] -1	0	0x0000a080 - 0x0000a0ff (0x80) IX[B]
	[18] -1	0	0x0000a200 - 0x0000a2ff (0x100) IX[B]
	[19] -1	0	0x0000e300 - 0x0000e37f (0x80) IX[B]
	[20] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[21] -1	0	0x0000e100 - 0x0000e13f (0x40) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[23] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[24] -1	0	0x00001100 - 0x0000110f (0x10) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x00001600 - 0x0000161f (0x20) IX[B]
	[30] -1	0	0x00001200 - 0x0000121f (0x20) IX[B]
	[31] -1	0	0x0000c100 - 0x0000c1ff (0x100) IX[B](B)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.47.3
	Module class: X.Org Video Driver
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.47.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.471                    
(II) ATI Proprietary Linux Driver Build Date: Feb 25 2008 21:22:09
(--) Assigning device section with no busID to primary device
(--) Chipset Supported AMD Graphics Processor (0x4E50) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd0000000 - 0xd00007ff (0x800) MX[B]
	[5] -1	0	0xd0000800 - 0xd00008ff (0x100) MX[B]
	[6] -1	0	0xd0001000 - 0xd0001fff (0x1000) MX[B]
	[7] -1	0	0xf0000600 - 0xf00006ff (0x100) MX[B]
	[8] -1	0	0xf0000400 - 0xf00005ff (0x200) MX[B]
	[9] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[10] -1	0	0xfebff000 - 0xfebff3ff (0x400) MX[B]
	[11] -1	0	0xb0000000 - 0xafffffff (0x0) MX[B]O
	[12] -1	0	0xe0010000 - 0xe001ffff (0x10000) MX[B](B)
	[13] -1	0	0xa8000000 - 0xafffffff (0x8000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B]
	[17] -1	0	0x0000a080 - 0x0000a0ff (0x80) IX[B]
	[18] -1	0	0x0000a200 - 0x0000a2ff (0x100) IX[B]
	[19] -1	0	0x0000e300 - 0x0000e37f (0x80) IX[B]
	[20] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[21] -1	0	0x0000e100 - 0x0000e13f (0x40) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[23] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[24] -1	0	0x00001100 - 0x0000110f (0x10) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x00001600 - 0x0000161f (0x20) IX[B]
	[30] -1	0	0x00001200 - 0x0000121f (0x20) IX[B]
	[31] -1	0	0x0000c100 - 0x0000c1ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x820cbb8
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd0000000 - 0xd00007ff (0x800) MX[B]
	[5] -1	0	0xd0000800 - 0xd00008ff (0x100) MX[B]
	[6] -1	0	0xd0001000 - 0xd0001fff (0x1000) MX[B]
	[7] -1	0	0xf0000600 - 0xf00006ff (0x100) MX[B]
	[8] -1	0	0xf0000400 - 0xf00005ff (0x200) MX[B]
	[9] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[10] -1	0	0xfebff000 - 0xfebff3ff (0x400) MX[B]
	[11] -1	0	0xb0000000 - 0xafffffff (0x0) MX[B]O
	[12] -1	0	0xe0010000 - 0xe001ffff (0x10000) MX[B](B)
	[13] -1	0	0xa8000000 - 0xafffffff (0x8000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B]
	[20] -1	0	0x0000a080 - 0x0000a0ff (0x80) IX[B]
	[21] -1	0	0x0000a200 - 0x0000a2ff (0x100) IX[B]
	[22] -1	0	0x0000e300 - 0x0000e37f (0x80) IX[B]
	[23] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[24] -1	0	0x0000e100 - 0x0000e13f (0x40) IX[B]
	[25] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[26] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[27] -1	0	0x00001100 - 0x0000110f (0x10) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x00001600 - 0x0000161f (0x20) IX[B]
	[33] -1	0	0x00001200 - 0x0000121f (0x20) IX[B]
	[34] -1	0	0x0000c100 - 0x0000c1ff (0x100) IX[B](B)
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): PCI bus 1 card 0 func 0
(II) fglrx(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(II) fglrx(0): Loading PCS database from /etc/ati/amdpcsdb
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "ATI MOBILITY RADEON 9600/9700 Series" (Chipset = 0x4e50)
(--) fglrx(0): (PciSubVendor = 0x1631, PciSubDevice = 0xc005)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xa8000000
(--) fglrx(0): MMIO registers at 0xe0010000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 65536 kB
(II) fglrx(0): VESA VBE OEM: ATI MOBILITY RADEON 9600   
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: C10 
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.47.3
	ABI class: X.Org Server Extension, version 0.3
(II) fglrx(0): Using adapter: 1:0.0.
(--) fglrx(0): VideoRAM: 65536 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) fglrx(0): Connected Display1: LCD on internal LVDS [lvds]
(II) fglrx(0):  Display1: No EDID information from DDC.
(II) fglrx(0):  Display1: Failed to get EDID information. 
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay version 3.  2 power states available:
(II) fglrx(0):   1. 297/203MHz @ 60Hz [enable load balancing]
(II) fglrx(0):   2. 105/105MHz @ 60Hz [low voltage, enable sleep]
(==) fglrx(0): Qbs is not supported in this release. Disabled.
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 14 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x800 (pitch 0)
(**) fglrx(0): *Mode "1280x800": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"x60.0   68.90  1280 1288 1328 1408  800 800 803 816 (48.9 kHz)
(**) fglrx(0): *Mode "1280x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   68.90  1280 1288 1328 1408  768 784 787 816 (48.9 kHz)
(**) fglrx(0): *Mode "1024x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   68.90  1024 1160 1200 1408  768 784 787 816 (48.9 kHz)
(**) fglrx(0): *Mode "848x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"x60.0   68.90  848 1072 1112 1408  480 640 643 816 (48.9 kHz)
(**) fglrx(0): *Mode "800x600": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   68.90  800 1048 1088 1408  600 700 703 816 (48.9 kHz)
(**) fglrx(0): *Mode "720x576": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"x60.0   68.90  720 1008 1048 1408  576 688 691 816 (48.9 kHz)
(**) fglrx(0): *Mode "720x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   68.90  720 1008 1048 1408  480 640 643 816 (48.9 kHz)
(**) fglrx(0): *Mode "640x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   68.90  640 968 1008 1408  480 640 643 816 (48.9 kHz)
(**) fglrx(0):  Default mode "640x400": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   68.90  640 968 1008 1408  400 600 603 816 (48.9 kHz)
(**) fglrx(0):  Default mode "640x350": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x350"x60.0   68.90  640 968 1008 1408  350 575 578 816 (48.9 kHz)
(**) fglrx(0):  Default mode "512x384": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   68.90  512 904 944 1408  384 592 595 816 (48.9 kHz)
(**) fglrx(0):  Default mode "400x300": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0   68.90  400 848 888 1408  300 700 703 816 doublescan (48.9 kHz)
(**) fglrx(0):  Default mode "320x240": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0   68.90  320 808 848 1408  240 640 643 816 doublescan (48.9 kHz)
(**) fglrx(0):  Default mode "320x200": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0   68.90  320 808 848 1408  200 611 614 816 doublescan (48.9 kHz)
(==) fglrx(0): DPI set to (96, 96)
(--) fglrx(0): Virtual size is 1280x800 (pitch 1280)
(**) fglrx(0): *Mode "1280x800": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"x60.0   68.90  1280 1288 1328 1408  800 800 803 816 (48.9 kHz)
(**) fglrx(0): *Mode "1280x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   68.90  1280 1288 1328 1408  768 784 787 816 (48.9 kHz)
(**) fglrx(0): *Mode "1024x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   68.90  1024 1160 1200 1408  768 784 787 816 (48.9 kHz)
(**) fglrx(0): *Mode "848x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"x60.0   68.90  848 1072 1112 1408  480 640 643 816 (48.9 kHz)
(**) fglrx(0): *Mode "800x600": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   68.90  800 1048 1088 1408  600 700 703 816 (48.9 kHz)
(**) fglrx(0): *Mode "720x576": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"x60.0   68.90  720 1008 1048 1408  576 688 691 816 (48.9 kHz)
(**) fglrx(0): *Mode "720x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   68.90  720 1008 1048 1408  480 640 643 816 (48.9 kHz)
(**) fglrx(0): *Mode "640x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   68.90  640 968 1008 1408  480 640 643 816 (48.9 kHz)
(**) fglrx(0):  Default mode "640x400": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   68.90  640 968 1008 1408  400 600 603 816 (48.9 kHz)
(**) fglrx(0):  Default mode "640x350": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x350"x60.0   68.90  640 968 1008 1408  350 575 578 816 (48.9 kHz)
(**) fglrx(0):  Default mode "512x384": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   68.90  512 904 944 1408  384 592 595 816 (48.9 kHz)
(**) fglrx(0):  Default mode "400x300": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0   68.90  400 848 888 1408  300 700 703 816 doublescan (48.9 kHz)
(**) fglrx(0):  Default mode "320x240": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0   68.90  320 808 848 1408  240 640 643 816 doublescan (48.9 kHz)
(**) fglrx(0):  Default mode "320x200": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0   68.90  320 808 848 1408  200 611 614 816 doublescan (48.9 kHz)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 256 MB
(II) fglrx(0): [pci] find AGP GART
(II) fglrx(0): [agp] Mode=0x1f000217 bridge: 0x8086/0x3580
(II) fglrx(0): [agp] AGP v1/2 disable mask 0x00000000
(II) fglrx(0): [agp] AGP v3 disable mask   0x00000000
(II) fglrx(0): [agp] enabling AGP with mode=0x1f000314
(II) fglrx(0): [agp] Remapping MC AGP space (new MCAGPBase = 0xb0000000, MCAGPSize = 0x10000000)
(II) fglrx(0): [agp] AGP protocol is enabled for graphics board. (cmd=0x1f000314)
(II) fglrx(0): [agp] graphics chipset has AGP v2.0
(II) fglrx(0): [pcie] 0 kB allocated
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe0010000 - 0xe001ffff (0x10000) MX[B]
	[1] 0	0	0xa8000000 - 0xafffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xd0000000 - 0xd00007ff (0x800) MX[B]
	[7] -1	0	0xd0000800 - 0xd00008ff (0x100) MX[B]
	[8] -1	0	0xd0001000 - 0xd0001fff (0x1000) MX[B]
	[9] -1	0	0xf0000600 - 0xf00006ff (0x100) MX[B]
	[10] -1	0	0xf0000400 - 0xf00005ff (0x200) MX[B]
	[11] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[12] -1	0	0xfebff000 - 0xfebff3ff (0x400) MX[B]
	[13] -1	0	0xb0000000 - 0xafffffff (0x0) MX[B]O
	[14] -1	0	0xe0010000 - 0xe001ffff (0x10000) MX[B](B)
	[15] -1	0	0xa8000000 - 0xafffffff (0x8000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[19] 0	0	0x0000c100 - 0x0000c1ff (0x100) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B]
	[23] -1	0	0x0000a080 - 0x0000a0ff (0x80) IX[B]
	[24] -1	0	0x0000a200 - 0x0000a2ff (0x100) IX[B]
	[25] -1	0	0x0000e300 - 0x0000e37f (0x80) IX[B]
	[26] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[27] -1	0	0x0000e100 - 0x0000e13f (0x40) IX[B]
	[28] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[29] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[30] -1	0	0x00001100 - 0x0000110f (0x10) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[35] -1	0	0x00001600 - 0x0000161f (0x20) IX[B]
	[36] -1	0	0x00001200 - 0x0000121f (0x20) IX[B]
	[37] -1	0	0x0000c100 - 0x0000c1ff (0x100) IX[B](B)
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(WW) fglrx(0): could not detect X server version (query_status=-3)
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) [drm] DRM interface version 1.0
(II) [drm] DRM open master succeeded.
(II) fglrx(0): [drm] Using the DRM lock SAREA also for drawables.
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [drm] installed DRM signal handler
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.47.3
(II) fglrx(0):     Date: Feb 25 2008
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.24-19-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00005000
(II) fglrx(0): Interrupt handler installed at IRQ 10.
(II) fglrx(0): Exposed events to the /proc interface
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xa8140000 FBMappedSize: 0x005f0000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,1216)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,800) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 416
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(II) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Solid Lines
	Dashed Lines
	Setting up tile and stipple cache:
		30 128x128 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
[atiddx] ASYNCIO init succeed!
Receive enable interrupt ret message
...irqEnableMask: 20008000
...dwIRQEnableId: 00000004
Receive enable interrupt ret message
...irqEnableMask: 10000000
...dwIRQEnableId: 00000005
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(WW) AIGLX: 3D driver claims to not support visual 0x33
(WW) AIGLX: 3D driver claims to not support visual 0x34
(WW) AIGLX: 3D driver claims to not support visual 0x35
(WW) AIGLX: 3D driver claims to not support visual 0x36
(WW) AIGLX: 3D driver claims to not support visual 0x37
(WW) AIGLX: 3D driver claims to not support visual 0x38
(WW) AIGLX: 3D driver claims to not support visual 0x39
(WW) AIGLX: 3D driver claims to not support visual 0x3a
(WW) AIGLX: 3D driver claims to not support visual 0x3b
(WW) AIGLX: 3D driver claims to not support visual 0x3c
(WW) AIGLX: 3D driver claims to not support visual 0x3d
(WW) AIGLX: 3D driver claims to not support visual 0x3e
(WW) AIGLX: 3D driver claims to not support visual 0x3f
(WW) AIGLX: 3D driver claims to not support visual 0x40
(WW) AIGLX: 3D driver claims to not support visual 0x41
(WW) AIGLX: 3D driver claims to not support visual 0x42
(WW) AIGLX: 3D driver claims to not support visual 0x43
(WW) AIGLX: 3D driver claims to not support visual 0x44
(WW) AIGLX: 3D driver claims to not support visual 0x45
(WW) AIGLX: 3D driver claims to not support visual 0x46
(WW) AIGLX: 3D driver claims to not support visual 0x47
(WW) AIGLX: 3D driver claims to not support visual 0x48
(WW) AIGLX: 3D driver claims to not support visual 0x49
(WW) AIGLX: 3D driver claims to not support visual 0x4a
(WW) AIGLX: 3D driver claims to not support visual 0x4b
(WW) AIGLX: 3D driver claims to not support visual 0x4c
(WW) AIGLX: 3D driver claims to not support visual 0x4d
(WW) AIGLX: 3D driver claims to not support visual 0x4e
(WW) AIGLX: 3D driver claims to not support visual 0x4f
(WW) AIGLX: 3D driver claims to not support visual 0x50
(WW) AIGLX: 3D driver claims to not support visual 0x51
(WW) AIGLX: 3D driver claims to not support visual 0x52
(WW) AIGLX: 3D driver claims to not support visual 0x53
(WW) AIGLX: 3D driver claims to not support visual 0x54
(WW) AIGLX: 3D driver claims to not support visual 0x55
(WW) AIGLX: 3D driver claims to not support visual 0x56
(WW) AIGLX: 3D driver claims to not support visual 0x57
(WW) AIGLX: 3D driver claims to not support visual 0x58
(WW) AIGLX: 3D driver claims to not support visual 0x59
(WW) AIGLX: 3D driver claims to not support visual 0x5a
(WW) AIGLX: 3D driver claims to not support visual 0x5b
(WW) AIGLX: 3D driver claims to not support visual 0x5c
(WW) AIGLX: 3D driver claims to not support visual 0x5d
(WW) AIGLX: 3D driver claims to not support visual 0x5e
(WW) AIGLX: 3D driver claims to not support visual 0x5f
(WW) AIGLX: 3D driver claims to not support visual 0x60
(WW) AIGLX: 3D driver claims to not support visual 0x61
(WW) AIGLX: 3D driver claims to not support visual 0x62
(WW) AIGLX: 3D driver claims to not support visual 0x63
(WW) AIGLX: 3D driver claims to not support visual 0x64
(WW) AIGLX: 3D driver claims to not support visual 0x65
(WW) AIGLX: 3D driver claims to not support visual 0x66
(WW) AIGLX: 3D driver claims to not support visual 0x67
(WW) AIGLX: 3D driver claims to not support visual 0x68
(WW) AIGLX: 3D driver claims to not support visual 0x69
(WW) AIGLX: 3D driver claims to not support visual 0x6a
(WW) AIGLX: 3D driver claims to not support visual 0x6b
(WW) AIGLX: 3D driver claims to not support visual 0x6c
(WW) AIGLX: 3D driver claims to not support visual 0x6d
(WW) AIGLX: 3D driver claims to not support visual 0x6e
(WW) AIGLX: 3D driver claims to not support visual 0x6f
(WW) AIGLX: 3D driver claims to not support visual 0x70
(WW) AIGLX: 3D driver claims to not support visual 0x71
(WW) AIGLX: 3D driver claims to not support visual 0x72
(II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event7
(**) Option "Device" "/dev/input/event7"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "be"
(**) Generic Keyboard: XkbLayout: "be"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event7
(**) Option "Device" "/dev/input/event7"
(--) Synaptics Touchpad touchpad found
SetClientVersion: 0 9
SetKbdSettings - type: -1078868532 rate: 45 delay: 463 snumlk: 28
```

'sudo cat /etc/ati/amdpcsdb'
```
AMDPCSDBV1
[AMDPCSROOT/SYSTEM/MCIL]
PXACAutoSwitch=V0
PXDCAutoSwitch=V0
CVRULE_CUSTOMIZEDMODESENABLED=V1
DALLinuxSupport=V1
DALNonStandardModesBCD=R140010500000006017921344000000601800144000000060185613920000006016001200000000601280076800000060144009000000006012800960000000601680105000000060
DALRULE_ADDNATIVEMODESTOMODETABLE=V1
DALRULE_DYNAMICMODESUPPORT=V1
DALRULE_GetLCDFakeEDID=V1
DALRULE_GetTVFakeEDID=V1
DALRULE_NOFORCEBOOT=V1
DALRULE_POWERPLAYDISREGARDDISPLAY=V1
DALRULE_RESTRICTDISPLAYSBASEDONPANELRES=V0
GCORULE_FlickerWA=V1
GCORULE_LCDValidatePixelClkOnly=V1
GXOM5XDisableLaneSwitch=V1
R6LCD_RETURNALLBIOSMODES=V1
TVEnableOverscan=V1
DALPowerPlayOptions=V1
DALLastSelected=V2
DALLastConnected=V2
DALLastTypes=V7
DALObjectData0=R01010001010001010001010001020001020001030001030001040001040001050001050003020403020403030403030401010001010001010000000001020000000001020002000101040000000001010002000401020002000401030002000400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
DALObjectData1=R0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
DALSelectObjectData0=R01010001010001010001010001020001020001030001030001040001040001050001050003020403020403030403030401010001010001010000000001020000000001020002000101040000000001010002000401020002000401030002000400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
DALSelectObjectData1=R0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
DALCurrentObjectData=R010200000000
DALR6 LCD_MaxModeInfo=R000000000005000020030000000000003C000000
```

'sudo dmesg|grep fglrx'
```
[   22.881984] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   23.108086] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[   23.108128] [fglrx] ASYNCIO init succeed!
[   23.108718] [fglrx] PAT is enabled successfully!
[   23.115789] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   44.578646] [fglrx] Internal AGP support requested, but kernel AGP support active.
[   44.578653] [fglrx] Have to use kernel AGP support to avoid conflicts.
[   44.578657] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
[   44.579559] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
[   44.582454] [fglrx] GART Table is not in FRAME_BUFFER range 
[   44.582460] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[   44.582463] [fglrx] Reserve Block - 1 offset =  0X3ff5000 length = 0Xb000
[   44.738898] [fglrx] interrupt source 20008000 successfully enabled
[   44.738904] [fglrx] enable ID = 0x00000004
[   44.738913] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[   44.738952] [fglrx] interrupt source 10000000 successfully enabled
[   44.738955] [fglrx] enable ID = 0x00000005
[   44.738958] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
```

'sudo dmesg|grep agpgart'
```
[   21.769586] Linux agpgart interface v0.102
[   21.952054] agpgart: Detected an Intel 855GM Chipset.
[   21.972780] agpgart: AGP aperture is 256M @ 0xb0000000
[   44.579139] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   44.579270] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   44.579416] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
```

'sudo glxinfo'
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON 9600/9700 Series
OpenGL version string: 2.1.7412 Release
OpenGL extensions:
    GL_AMD_performance_monitor, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_shadow, GL_ARB_shadow_ambient, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, 
    GL_ATI_meminfo, GL_ATI_separate_stencil, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_float, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_EXT_vertex_array, 
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_texgen_reflection, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, 
    GL_WIN_swap_hint, WGL_EXT_swap_control

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x43 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x44 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x45 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x46 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x47 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x48 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x49 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x4a 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x63 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x64 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x65 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x66 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x67 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x68 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x69 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x6a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x6b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6f 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x70 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x71 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x72 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
```

'sudo dmesg'
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fffffc0 (ACPI data)
[    0.000000]  BIOS-e820: 000000001fffffc0 - 0000000020000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 131056) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131056
[    0.000000]   HighMem    131056 ->   131056
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131056
[    0.000000] On node 0 totalpages: 131056
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125969 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00E6010 checksum 0
[    0.000000] ACPI: RSDP 000E6010, 0014 (r0 OID_00)
[    0.000000] ACPI: RSDT 1FFFCC36, 0034 (r1 INSYDE RSDT_000        1 _CSI    10103)
[    0.000000] ACPI: FACP 1FFFFB00, 0074 (r1 INSYDE FACP_000      100 _CSI    10103)
[    0.000000] ACPI: DSDT 1FFFCED0, 2C2C (r1 INSYDE INTELIC4     1004 INTL  2002025)
[    0.000000] ACPI: FACS 1FFFFFC0, 0040
[    0.000000] ACPI: BOOT 1FFFFB90, 0028 (r1 INSYDE SYS_BOOT      100 _CSI    10103)
[    0.000000] ACPI: DBGP 1FFFFBC0, 0034 (r1 INSYDE DBGP_000      100 _CSI    10103)
[    0.000000] ACPI: SSDT 1FFFCC6A, 010C (r1 INSYDE   GV3Ref     1001 INTL  2012044)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfb80000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 130033
[    0.000000] Kernel command line: root=UUID=8f885e1c-68f6-4459-a087-798253e5e3bd ro quiet splash xforcevesa lapic
[    0.000000] Local APIC disabled by BIOS -- reenabling.
[    0.000000] Found and enabled local APIC!
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1695.815 MHz processor.
[    5.146241] Console: colour VGA+ 80x25
[    5.146246] console [tty0] enabled
[    5.146430] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    5.146654] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    5.159349] Memory: 507780k/524224k available (2177k kernel code, 15928k reserved, 1006k data, 368k init, 0k highmem)
[    5.159357] virtual kernel memory layout:
[    5.159358]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[    5.159360]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    5.159361]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[    5.159362]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
[    5.159364]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[    5.159365]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
[    5.159366]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
[    5.159370] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    5.159409] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    5.239321] Calibrating delay using timer specific routine.. 3393.83 BogoMIPS (lpj=6787667)
[    5.239348] Security Framework initialized
[    5.239355] SELinux:  Disabled at boot.
[    5.239373] AppArmor: AppArmor initialized
[    5.239377] Failure registering capabilities with primary security module.
[    5.239385] Mount-cache hash table entries: 512
[    5.239516] Initializing cgroup subsys ns
[    5.239521] Initializing cgroup subsys cpuacct
[    5.239531] CPU: After generic identify, caps: afe9fbbf 00000000 00000000 00000000 00000180 00000000 00000000 00000000
[    5.239543] CPU: L1 I cache: 32K, L1 D cache: 32K
[    5.239545] CPU: L2 cache: 2048K
[    5.239548] CPU: After all inits, caps: afe9fbbf 00000000 00000000 00002040 00000180 00000000 00000000 00000000
[    5.239557] Compat vDSO mapped to ffffe000.
[    5.239570] Checking 'hlt' instruction... OK.
[    5.255655] SMP alternatives: switching to UP code
[    5.257413] Freeing SMP alternatives: 11k freed
[    5.257519] Early unpacking initramfs... done
[    5.619723] ACPI: Core revision 20070126
[    5.619780] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    5.620979] ACPI: setting ELCR to 0200 (from 0ca8)
[    5.632866] CPU0: Intel(R) Pentium(R) M processor 1.70GHz stepping 06
[    5.632872] SMP motherboard not detected.
[    5.738692] Brought up 1 CPUs
[    5.738709] CPU0 attaching sched-domain:
[    5.738711]  domain 0: span 01
[    5.738713]   groups: 01
[    5.738883] net_namespace: 64 bytes
[    5.738895] Booting paravirtualized kernel on bare hardware
[    5.739341] Time: 13:40:50  Date: 08/10/08
[    5.739366] NET: Registered protocol family 16
[    5.739556] EISA bus registered
[    5.739578] ACPI: bus type pci registered
[    5.739706] PCI: PCI BIOS revision 2.10 entry at 0xe9864, last bus=2
[    5.739708] PCI: Using configuration type 1
[    5.739731] Setting up standard PCI resources
[    5.743659] ACPI: EC: Look up EC in DSDT
[    5.744875] ACPI: Interpreter enabled
[    5.744878] ACPI: (supports S0 S3 S4 S5)
[    5.744891] ACPI: Using PIC for interrupt routing
[    5.746451] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    5.753210] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    5.753213] ACPI: EC: driver started in interrupt mode
[    5.753249] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    5.753606] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    5.753610] PCI quirk: region 1300-133f claimed by ICH4 GPIO
[    5.754131] PCI: Transparent bridge - 0000:00:1e.0
[    5.754189] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    5.754247] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[    5.756684] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 *10 11)
[    5.756767] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 10 11)
[    5.756846] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 10 *11)
[    5.756926] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 10 *11)
[    5.757002] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 10 *11)
[    5.757068] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 10 11) *0, disabled.
[    5.757142] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 10 11)
[    5.757215] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 10 11) *7
[    5.757312] Linux Plug and Play Support v0.97 (c) Adam Belay
[    5.757341] pnp: PnP ACPI init
[    5.757348] ACPI: bus type pnp registered
[    5.761034] pnp: PnP ACPI: found 10 devices
[    5.761036] ACPI: ACPI bus type pnp unregistered
[    5.761041] PnPBIOS: Disabled by ACPI PNP
[    5.761242] PCI: Using ACPI for IRQ routing
[    5.761245] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    5.770626] NET: Registered protocol family 8
[    5.770628] NET: Registered protocol family 20
[    5.770683] AppArmor: AppArmor Filesystem Enabled
[    5.774598] Time: tsc clocksource has been installed.
[    5.782622] system 00:05: iomem range 0xfff80000-0xffffffff could not be reserved
[    5.782628] system 00:07: ioport range 0x680-0x6ff has been reserved
[    5.782631] system 00:07: ioport range 0x200-0x20f has been reserved
[    5.782634] system 00:07: ioport range 0x290-0x297 has been reserved
[    5.782637] system 00:07: ioport range 0x1000-0x107f has been reserved
[    5.782640] system 00:07: ioport range 0x1300-0x133f has been reserved
[    5.782643] system 00:07: ioport range 0x77c-0x77f has been reserved
[    5.812989] PCI: Bridge: 0000:00:01.0
[    5.812992]   IO window: c000-dfff
[    5.812995]   MEM window: e0000000-efffffff
[    5.812998]   PREFETCH window: a0000000-afffffff
[    5.813007] PCI: Bus 3, cardbus bridge: 0000:02:04.0
[    5.813009]   IO window: 0000a400-0000a4ff
[    5.813013]   IO window: 0000a800-0000a8ff
[    5.813016]   PREFETCH window: 90000000-93ffffff
[    5.813020]   MEM window: d4000000-d7ffffff
[    5.813024] PCI: Bridge: 0000:00:1e.0
[    5.813026]   IO window: a000-bfff
[    5.813031]   MEM window: d0000000-dfffffff
[    5.813035]   PREFETCH window: 90000000-9fffffff
[    5.813049] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    5.813188] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[    5.813191] PCI: setting IRQ 5 as level-triggered
[    5.813195] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[    5.813208] NET: Registered protocol family 2
[    5.850551] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    5.850740] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    5.850847] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    5.850951] TCP: Hash tables configured (established 16384 bind 16384)
[    5.850954] TCP reno registered
[    5.862583] checking if image is initramfs... it is
[    6.313850] Switched to high resolution mode on CPU 0
[    6.569357] Freeing initrd memory: 7289k freed
[    6.569609] Simple Boot Flag at 0x37 set to 0x1
[    6.569996] audit: initializing netlink socket (disabled)
[    6.570014] audit(1218375650.300:1): initialized
[    6.572073] VFS: Disk quotas dquot_6.5.1
[    6.572150] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    6.572293] io scheduler noop registered
[    6.572295] io scheduler anticipatory registered
[    6.572297] io scheduler deadline registered
[    6.572309] io scheduler cfq registered (default)
[    6.572368] Boot video device is 0000:01:00.0
[    6.572643] isapnp: Scanning for PnP cards...
[    6.925826] isapnp: No Plug & Play device found
[    6.952378] Real Time Clock Driver v1.12ac
[    6.952485] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    6.953100] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[    6.953110] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[    6.953722] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    6.953795] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    6.953889] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    6.963304] i8042.c: Detected active multiplexing controller, rev 1.1.
[    6.967925] serio: i8042 KBD port at 0x60,0x64 irq 1
[    6.967930] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    6.967933] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    6.967935] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    6.967938] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    6.976924] mice: PS/2 mouse device common for all mice
[    6.977033] EISA: Probing bus 0 at eisa.0
[    6.977040] Cannot allocate resource for EISA slot 1
[    6.977067] EISA: Detected 0 cards.
[    6.977070] cpuidle: using governor ladder
[    6.977072] cpuidle: using governor menu
[    6.977169] NET: Registered protocol family 1
[    6.977197] Using IPI No-Shortcut mode
[    6.977232] registered taskstats version 1
[    6.977335]   Magic number: 4:274:685
[    6.977422] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    6.977424] EDD information not available.
[    6.977643] Freeing unused kernel memory: 368k freed
[    6.996852] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    8.179887] fuse init (API version 7.9)
[    8.197449] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    8.197454] ACPI: Processor [CPU0] (supports 8 throttling states)
[    8.770315] usbcore: registered new interface driver usbfs
[    8.770341] usbcore: registered new interface driver hub
[    8.782265] usbcore: registered new device driver usb
[    8.798245] USB Universal Host Controller Interface driver v3.0
[    8.798497] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[    8.798500] PCI: setting IRQ 10 as level-triggered
[    8.798504] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[    8.798515] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    8.798519] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    8.798855] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    8.798881] uhci_hcd 0000:00:1d.0: irq 10, io base 0x00001200
[    8.799014] usb usb1: configuration #1 chosen from 1 choice
[    8.799038] hub 1-0:1.0: USB hub found
[    8.799043] hub 1-0:1.0: 2 ports detected
[    8.846368] SCSI subsystem initialized
[    8.914056] libata version 3.00 loaded.
[    8.921207] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    9.301658] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    9.301665] PCI: setting IRQ 11 as level-triggered
[    9.301669] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[    9.301684] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    9.301689] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    9.301740] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    9.301766] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001600
[    9.301898] usb usb2: configuration #1 chosen from 1 choice
[    9.301922] hub 2-0:1.0: USB hub found
[    9.301928] hub 2-0:1.0: 2 ports detected
[    9.605203] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    9.605208] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[    9.605227] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    9.605231] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    9.605270] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 3
[    9.609170] ehci_hcd 0000:00:1d.7: debug port 1
[    9.609176] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    9.609184] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xfebff000
[    9.625032] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    9.625132] usb usb3: configuration #1 chosen from 1 choice
[    9.625156] hub 3-0:1.0: USB hub found
[    9.625162] hub 3-0:1.0: 4 ports detected
[    9.729120] 8139cp 0000:02:02.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    9.729125] 8139cp 0000:02:02.0: Try the "8139too" driver instead.
[    9.731871] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 3
[    9.731875] PCI: setting IRQ 3 as level-triggered
[    9.731879] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNKG] -> GSI 3 (level, low) -> IRQ 3
[    9.731886] PCI: Setting latency timer of device 0000:02:05.0 to 64
[    9.784537] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[3]  MMIO=[d0000000-d00007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    9.790907] 8139too Fast Ethernet driver 0.9.28
[    9.810248] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[    9.810253] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[    9.810265] PCI: Setting latency timer of device 0000:02:02.0 to 64
[    9.810793] eth0: RealTek RTL8139 at 0xa200, 00:40:d0:6b:77:9f, IRQ 11
[    9.810796] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    9.810869] ata_piix 0000:00:1f.1: version 2.12
[    9.810881] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[    9.811021] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    9.811024] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[    9.811055] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    9.811617] scsi0 : ata_piix
[    9.812032] scsi1 : ata_piix
[    9.812724] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1100 irq 14
[    9.812728] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1108 irq 15
[    9.977019] ata1.00: ATA-6: IC25N060ATMR04-0, MO3OAD4A, max UDMA/100
[    9.977023] ata1.00: 117210240 sectors, multi 16: LBA48 
[    9.992927] ata1.00: configured for UDMA/100
[   10.328280] ata2.00: ATAPI: _NEC DVD+/-RW ND-6500A, 4.60, max UDMA/33
[   10.531925] ata2.00: configured for UDMA/33
[   10.532034] scsi 0:0:0:0: Direct-Access     ATA      IC25N060ATMR04-0 MO3O PQ: 0 ANSI: 5
[   10.567366] scsi 1:0:0:0: CD-ROM            _NEC     DVD+-RW ND-6500A 4.60 PQ: 0 ANSI: 5
[   10.579677] Driver 'sd' needs updating - please use bus_type methods
[   10.579750] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[   10.579763] sd 0:0:0:0: [sda] Write Protect is off
[   10.579765] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   10.579781] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   10.579825] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[   10.579835] sd 0:0:0:0: [sda] Write Protect is off
[   10.579837] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   10.579852] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   10.579857]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   10.606896]  sda1 sda2 sda3 sda4
[   10.647377] sd 0:0:0:0: [sda] Attached SCSI disk
[   10.653590] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   10.653610] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   10.839691] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   10.839696] Uniform CD-ROM driver Revision: 3.20
[   10.839747] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   11.079053] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0040d00100258af9]
[   11.124445] Attempting manual resume
[   11.124449] swsusp: Resume From Partition 8:2
[   11.124451] PM: Checking swsusp image.
[   11.124584] PM: Resume from disk failed.
[   11.132018] JFS: nTxBlock = 4027, nTxLock = 32223
[   11.302601] Clocksource tsc unstable (delta = -182571858 ns)
[   11.306581] Time: acpi_pm clocksource has been installed.
[   22.947564] Linux agpgart interface v0.102
[   23.023464] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   23.099554] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   23.195964] iTCO_vendor_support: vendor-support=0
[   23.251103] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   23.251179] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   23.251208] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   23.327054] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   23.402884] agpgart: Detected an Intel 855GM Chipset.
[   23.447191] agpgart: AGP aperture is 256M @ 0xb0000000
[   23.508114] intel_rng: Firmware space is locked read-only. If you can't or
[   23.508117] intel_rng: don't want to disable this in firmware setup, and if
[   23.508119] intel_rng: you are certain that your system has a functional
[   23.508120] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   23.698507] input: Power Button (FF) as /devices/virtual/input/input3
[   23.714392] ACPI: Power Button (FF) [PWRF]
[   23.714454] input: Sleep Button (CM) as /devices/virtual/input/input4
[   23.730364] ACPI: Sleep Button (CM) [SBTN]
[   23.730418] input: Lid Switch as /devices/virtual/input/input5
[   23.733268] ACPI: Lid Switch [LID]
[   23.779534] ACPI: Battery Slot [BAT0] (battery present)
[   23.922172] ACPI: AC Adapter [AC] (on-line)
[   24.774833] Synaptics Touchpad, model: 1, fw: 5.9, id: 0xf6eb3, caps: 0xa04713/0x0
[   24.824380] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio3/input/input6
[   24.909128] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input7
[   24.936621] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   25.430986] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   25.431011] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   25.763619] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   25.997874] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[   25.997915] [fglrx] ASYNCIO init succeed!
[   25.998375] [fglrx] PAT is enabled successfully!
[   26.029458] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   26.099044] ieee80211_crypt: registered algorithm 'NULL'
[   26.175343] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   26.175347] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   26.247973] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   26.247978] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   26.254620] intel8x0_measure_ac97_clock: measured 55479 usecs
[   26.254623] intel8x0: clocking to 48000
[   26.255529] Yenta: CardBus bridge found at 0000:02:04.0 [1631:c005]
[   26.255546] Yenta: Using CSCINT to route CSC interrupts to PCI
[   26.255548] Yenta: Routing CardBus interrupts to PCI
[   26.255552] Yenta TI: socket 0000:02:04.0, mfunc 0x010c1202, devctl 0x44
[   26.486619] Yenta: ISA IRQ mask 0x00c0, PCI irq 5
[   26.486624] Socket status: 30000006
[   26.486627] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   26.486633] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xbfff
[   26.486637] cs: IO port probe 0xa000-0xbfff: clean.
[   26.487084] pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xdfffffff
[   26.487086] pcmcia: parent PCI bridge Memory window: 0x90000000 - 0x9fffffff
[   26.494323] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   26.494332] PCI: Setting latency timer of device 0000:02:01.0 to 64
[   26.499073] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   27.295099] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   27.383734] cs: IO port probe 0x100-0x3af: clean.
[   27.385275] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   27.385970] cs: IO port probe 0x820-0x8ff: clean.
[   27.386530] cs: IO port probe 0xc00-0xcf7: clean.
[   27.387239] cs: IO port probe 0xa00-0xaff: clean.
[   27.591578] lp: driver loaded but no devices found
[   27.785104] Adding 996020k swap on /dev/sda2.  Priority:-1 extents:1 across:996020k
[   38.118553] ip_tables: (C) 2000-2006 Netfilter Core Team
[   38.779440] No dock devices found.
[   41.099000] NET: Registered protocol family 10
[   41.099397] lo: Disabled Privacy Extensions
[   41.816885] ppdev: user-space parallel port driver
[   42.354005] audit(1218375693.252:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4818 profile="/usr/sbin/cupsd" namespace="default"
[  120.498375] Marking TSC unstable due to: cpufreq changes.
[   43.310733] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   44.655413] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[  127.180684] NET: Registered protocol family 17
[   45.974213] [fglrx] Internal AGP support requested, but kernel AGP support active.
[   45.974220] [fglrx] Have to use kernel AGP support to avoid conflicts.
[   45.974225] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
[   45.974787] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   45.976586] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   45.976741] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   45.976886] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
[   45.980231] [fglrx] GART Table is not in FRAME_BUFFER range 
[   45.980238] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[   45.980241] [fglrx] Reserve Block - 1 offset =  0X3ff5000 length = 0Xb000
[   46.091115] [fglrx] interrupt source 20008000 successfully enabled
[   46.091121] [fglrx] enable ID = 0x00000004
[   46.091398] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[   46.091563] [fglrx] interrupt source 10000000 successfully enabled
[   46.091566] [fglrx] enable ID = 0x00000005
[   46.091752] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[  139.697969] eth0: no IPv6 routers present
```

---

### Post by EXCRANIUM on 2008-08-10
Thank you very very much.

---

### Post by king2rook1 on 2008-08-16
Hello,

I recently installed 8.04 and wanted to get my dual monitor setup working, so I installed the restricted driver for my ATI Radeon X300 video card (in a Dell Optiplex GX280 with one Dell and one Gateway 17 in. LCD monitor, both connected as analog).  Then I did this:

sudo aticonfig --initial=dual-head --screen-layout=left

(because my main monitor is to the right and the secondary monitor is to the left).  That worked great, UNTIL...

I should say I could use the two monitors as if I were running two separate sessions of Ubuntu, could move the mouse pointer between them but not move open windows between them.  I tried to set that up, but it just went back to mirroring the display of my primary monitor again.  Not a problem.  I can live with it.

However, eventually the primary monitor went into screen saver, and that was the end of it!  Everything GUIish froze completely (I was in Gnome).  I went into a text console and rebooted.  (Btw, I understand Ubuntu is considering doing away with the text consoles.  PLEASE DON'T.  I would have had to pull the plug without that recourse!)  Then I tried to turn off the screen saver to avert the problem happening again, but it won't let me.  Screen saver preferences no longer work.

How do I get the screen saver turned off to prevent my system from crashing again?  Do I have to start from scratch?

Btw, if you are installing the ATI drivers and aticonfig, turn off your screen saver first!

Thanks.

---

### Post by Nitrius on 2008-08-16
> **markbuntu said:**
> Try using these directions for installing the ati driver, use Method 2:


[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

I have a HD3650 and these directions have never failed me, since the 8.4 driver to the 8.7 driver now.

Thanks for the link. 
Got a question: > If you are using the x86_64 architecture (64 bit), be sure to inst "ia32-libs" before proceeding! 
This mean i should do a:
```
sudo apt-get install ia32-libs
```
Before proceeding?


Edit: Used the guide in the link, and so far it seems to work well, no problems yet on my ati 4870.

---

### Post by sinaen on 2008-08-17
Does anyone know a fix to make wine run direct3d games correctly??

i havent managed yet with my ati radeon 9800 pro.. :(

---

### Post by markbuntu on 2008-08-18
> **elcid89 said:**
> I tried method 2, and found that I was consistently having the problem with MESA loading instead of the ATI driver.

When attempting to remove xserver-xgl, it was already not installed, so no joy there.

I ended up having to remove xserver-xorg-video-intel

The driver for the onboard Intel video was conflicting with the ATi driver, and Ubuntu was trying to load them both, ergo problems ...

Removed the intel driver and immediate joy. Everything works perfectly now. If you have onboard Intel video on your motherboard and are having the MESA loading instead of ATI problem, it might be worth it for you to give that a try.

Did you disable the intel video in the bios. If you did then you should not have had that problem. But it is good you found a way to fix it, many people end up in mesa hell. 

Last time for me was getting the rt kernel to work in my amd64. The kernel worked but did not have the fglrx kernel modules loaded so the driver defaulted to Mesa and would not let me load the kernel modules by hand and it just became a hideous nightmare when trying to remove/reinstall the driver broke dpkg due to links fglrx made to Mesa to fix itself without any kernel modules. Every time I ran dpkg it failed with an error about fglrx links. I could get no pkgs from anywhere while this was going on. It was a scary nightmare from hell.

Eventually, I tried the force downgrade with Synaptic, dpkg removed that with no complaints and I was able to reinstall and everything worked. Whew!! I was about ready to do a complete new clean system reinstall.

---

### Post by peakshysteria on 2008-08-22
So once again I installed EnvyNG via synaptic. Then installed the ATI driver offered (It might be the latest one in hardy-proposed, which might be 8.8, not sure really). Anyaway, all went very well for the first time. Ubuntu booted with the right resolution. Yay! But:
fglrxinfo gives me the dreaded:
```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

```

Mesa hell once again.

The output of my Xorg:

```
Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

```

Can anyone point me in the right direction? I have tried several guides and forum threads. But with no luck yet. I'm not to good with the terminal so EnvyNG really offers something which is more my cup-o-tea. But it doesn't seem to work well with my ATI card for some strange reason.

lspci -nn | grep VGA gives me:
```
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)] [1002:5e4b]
```

And is there a way to found out the exact ATI driver EnvyNG has installed even though fglrxinfo says MESA?

---

### Post by Dreamerman on 2008-08-23
I have an old dual head ATI Radeon 7500LE AGP card. I could not get it to work properly under SUSE. Then I met Ubuntu. Correct drivers for my ATI came by default. No problems at all. BTW, I don't know about the dual head as I don't currently use it.

---

### Post by Rocket2DMn on 2008-08-23
The Radeon 7500 all the way up until (but not including) the 9500 can only use the open source ati drivers.  The restricted fglrx drivers should not be used on those cards.  However, AFAIK, the open source drivers do not support dual head well, or at all, except for cloning output.

---

### Post by Grone1985 on 2008-08-24
Hey!

So I have the restricted drivers enabled but never did this...

```
sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r`
sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko
```

...as suggested [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Instructions%20for%20Ubuntu%208.04%20(Hardy)"). I never knew about this guide so far and I don't know if that step is needed.

to the command lspci -nn | grep VGA I get this

```
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP] [1002:5975]
```

and on /etc/X11/xorg.conf I see this:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection
```

I get pixelated video on fullscreen and kinda choppy... and sometimes I get flickering when Compiz enabled (BTW I don't have Compiz enabled when watching videos)... So my question is if there's anything I can do to make my card work better?? or does it all look properly configured??

BTW all of this is under Ubuntu Hardy x64. Thanks in advance!

---

### Post by Dreamerman on 2008-08-24
> **Rocket2DMn said:**
> The Radeon 7500 all the way up until (but not including) the 9500 can only use the open source ati drivers.  The restricted fglrx drivers should not be used on those cards.  However, AFAIK, the open source drivers do not support dual head well, or at all, except for cloning output.

Thanks. I don't worry about dual head. I wonder if default open sourced ATI drivers supports DVI output. I am thinking of buying a 22" or 24" LCD monitor. According to tech specs ([http://www.technoyard.com/hardware/video_cards/ati-Excalibur/page_1.html](http://www.technoyard.com/hardware/video_cards/ati-Excalibur/page_1.html)) the card supports:-

- Features DVI interface with integrated TMDS for resolutions up to 1600 x 1200
- Supports 3D resolutions (32-bit color) up to 2048 x 1536

22" LCD supports upto 1680x1050 & 24" upto 1920x1200. I am not very techie but do you know if I can use either LCDs properly ?

Thanks

---

### Post by Rocket2DMn on 2008-08-25
That depends on your video card - you need to check that it is capable of the resolution that the monitor can do.  1680x1050 may be about the limit of your video card.

---

### Post by sim-value on 2008-08-27
I already have Catalist 8.7 Installed and working how do i upgrade to 8.8 without screwing up ?

---

### Post by markbuntu on 2008-08-28
> **sim-value said:**
> I already have Catalist 8.7 Installed and working how do i upgrade to 8.8 without screwing up ?


[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

Method 2.

---

### Post by lavinog on 2008-08-30
> **sim-value said:**
> I already have Catalist 8.7 Installed and working how do i upgrade to 8.8 without screwing up ?

I have been successful in using the built-in installer.
But 8-8 lowered my performance a little and has crashed my system a couple of times. I went back to 8-7 and will wait for 8-9.

---

### Post by Chris_Caves on 2008-08-31
I was messing around with the graphic controls trying to make the graphic interface pretty using my HD2900 Pro Ati graphics card and theeeeennnn I changed some xorg.config files and woops, I didn't know what i was doing. I uninstalled my linux partition by "deleting" it on my xp partition (woops, bigger hole) so the grub bootloader that im using fails. I made a bootloader from an .iso and made a new live cd. Here's the problem: Having already installed linux mint onto my computer i think that some of the settings concerning my graphics card were kept. This makes it impossible for me to install the new distro on my computer. I get the white screen of death. I can access the terminal but i do not have root password (i think) and i don't know what im doing! HELP PLEASE I just want my baby to work again! Thanks :)

---

### Post by lavinog on 2008-08-31
> **Chris_Caves said:**
> I was messing around with the graphic controls trying to make the graphic interface pretty using my HD2900 Pro Ati graphics card and theeeeennnn I changed some xorg.config files and woops, I didn't know what i was doing. I uninstalled my linux partition by "deleting" it on my xp partition (woops, bigger hole) so the grub bootloader that im using fails. I made a bootloader from an .iso and made a new live cd. Here's the problem: Having already installed linux mint onto my computer i think that some of the settings concerning my graphics card were kept. This makes it impossible for me to install the new distro on my computer. I get the white screen of death. I can access the terminal but i do not have root password (i think) and i don't know what im doing! HELP PLEASE I just want my baby to work again! Thanks :)

You need to start a new thread first. The people that can help you are not going to see this post because the title is irrelevant to your issue.

I am also confused on where you stand. Is linux installed or not, and how do you not have the root password?
Is the problem now just that you are getting the white screen of death? If so you probably need to disable compiz
try:
```
metacity --replace
```

---

### Post by Chris_Caves on 2008-08-31
Thanks for the reply. I'll try to start a new thread next time (I'm new to the community and just exploring the forums' workings). Linux is not installed (I am working within the terminal of the live cd), and I do have root. The output for the command that you suggested:
Window manager error: Unable to open X display

---

### Post by Chris_Caves on 2008-08-31
After the command startx:
Fatal server error:
Server is already active for display 0
     If this server is no longer running, remove /tmp/.X0-lock
     and start again.

---

### Post by lavinog on 2008-08-31
Which live cd are you using?
have you tried the Ubuntu 8.04.1 live cd?
Is the desktop showing up at all on the live cd, or is it going straight to the terminal?

---

### Post by Chris_Caves on 2008-09-01
I have tried installing 8.04 as well as Linux Mint -5 ( a distro off of ubuntu). I haven't made it to installing either. When trying to install, both cds(checked for errors) boot and bring me to a blank white screen and i can hear a start-up sound and that is all. I know the problem is my graphics card driver. I had deleted the file from my previous comment and started the x serv. The output listed my last display configuration (i had linux mint previously installed) with the ATI driver installed. I've tried to play with the partition from my vista partition and delete everything on it but somehow it still draws from my last linux mint settings. ARGH!

---

### Post by lavinog on 2008-09-01
You may want to try safe mode when you boot from cd. I think they made it less noticable, but i think you have to try one of the F4 key and choose safe graphics mode

---

### Post by Xobi on 2008-09-01
Thank you, would this work on ATI Radeon Xpress 200 M? I tried your HOWTO but no effect I am having probs with DVD:s only - the videos work OK.

---

### Post by Chris_Caves on 2008-09-01
Dear lavinog,

Thank you so much.
It's working. 
I love you.

-Chris

---

### Post by JakeK23 on 2008-09-05
Alright, my turn.  So, I have tried just about everything to stop using Mesa drivers.  My first question... if I wanted to just wipe all the drivers and start over, how would I do that short of completely reinstalling?

Second, here are my errors and warnings in Xorg.0.log

```
(EE) fglrx(0): [agp] unable to acquire AGP, error -1023
(EE) fglrx(0): cannot init AGP
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 

(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(WW) fglrx(0): could not detect X server version (query_status=-3)
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(WW) Configured Mouse: No Device specified, looking for one...
```

I have tried all of the things to fix this but nothing seems to work.

And just for reference here is my xorg.conf

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "dri"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "UseFastTLS" "1"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection
```

Any help would be abundantly appreciated!  Thanks!

Edit:  I guess I should say that I am running Hardy (Linux Mint 5) will a Radeon 9800 Pro.  I had Compiz working in Fedora 7 so I figure its at least possible in ubuntu.

---

### Post by BMWDriver on 2008-09-08
> **JakeK23 said:**
> Alright, my turn.  So, I have tried just about everything to stop using Mesa drivers.  My first question... if I wanted to just wipe all the drivers and start over, how would I do that short of completely reinstalling?


Check out the first few instructions [here]("https://help.ubuntu.com/community/RadeonDriver"), that's what I just did. So far, so good.

---

### Post by rgb1701 on 2008-09-11
[http://ubuntuforums.org/showthread.php?t=916840](http://ubuntuforums.org/showthread.php?t=916840)

An alternative no-terminal-needed, GUI-only ATI and Nvidia install procedure that should pick up the latest drivers in Ubuntu and Mint.

---

### Post by Pocket Universe on 2008-09-12
Hello there.

I tried following the steps for 8.04 to get my ATI Radeon X800 XT up and running yet somehow it wasn't working.

When I installed my 8.04 (AMD64) I had to go for the safe mode since Ubuntu refused to understand what my graphics card was. My first attempt to get the card up and running after a safe install was to use the popup-box which explained that "you may use proprietary drivers instead", that however only made the system crash while booting, leaving it in an endless cycle of reboots (without any errors being printed, mind you).

After trying your method, nothing happened, I still can't set my resolution above 640*480 and I doubt that I am using a full colour-spectrum. It's as if it wasn't actually installed at all.

I'd really appreciate some help.

---

### Post by pixel4e on 2008-09-13
I am sure this has been asked before, but I have no restricted drivers listed in the RDmanager. I am on a lappy with IGP9100 which is currently f-ed up, so I can't post xorg or lspci. The fact is though that I can't follow the rest of the guide before I enable the restricted drivers and I can't do that.

Any help would be appreciated.

---

### Post by RobOrr on 2008-09-21
I try to get the ati driver working using the aforementioned method and the insmod operation is apparently not permitted
> 
insmod: error inserting '/lib/modules/2.6.24-19-generic/volatile/fglrx.ko': -1 Operation not permitted

the result of this as far as i can tell, is that if i log out and log back in the driver is working fine, C&C3 looks all pretty and nice. however, if my computer is turned off and back on again, I white screen of death and I have to boot failsafe GNOME, run the dpkg reconfigure again and then log out log in again.

If anyone has had this problem and solved it, whether it be the refusal to insmod or the WSD after a powered restart, please reply!

---

### Post by 73ckn797 on 2008-09-21
My solution to the ATI issue is posted here:
[http://ubuntuforums.org/showthread.php?t=902913](http://ubuntuforums.org/showthread.php?t=902913)

---

### Post by BMWDriver on 2008-09-28
To install the ATI proprietary drivers manually (Catalyst 8.9), I went [**here**]("http://wiki.cchtml.com/index.php/Ubuntu") and followed the appropriate instructions. They specify all the tools you must install unlike in the Ubuntu help forums.

After much headaches with trying to install the driver with the restricted drivers check box - always getting Mesa drivers with fglrxinfo even after trying to uninstall the Mesa drivers, countless reboots and line inputs on the term - I was successful in installing the latest drivers and getting them to work properly instead.

I found the information there to be better organized.

---

### Post by mziskandar on 2008-09-29
I've tried many solutions, suggestions, advices.. eg: those agp conflict, xorg editing, and many others.. lengthy and tiring. After a week with few times of reformatting and re-installation.. I got the same beautiful white screen.

My solution..
1. Install Envy. Let Envy modify the kernel..
   -> result: doesn't work.
2. Uninstall Envy.
   -> result: broken ubuntu. go to text mode..
   -> some installation failed. accusing Mesa.
3. Install ati driver 8.9
   -> result: unknown
4. Reboot
   -> oppsss.. I got accelerated perfectly.
5. Compiz is running
   -> result: my wife screaming. delayed 1 hour for our vacation (hey, just got compiz to work! She should understand)

I've done a lot of changes everywhere.  This post might not be a solution. Give it a try.. share the result.

As soon I get back, I'll format my PC and try to reinstall ubuntu again. (I did reflash my bios few times with various version)

My Spec: ATI 9600XT, VIA P4V800-X, P4 3.0HT, ZTE HSDPA USB Modem (+Storage), 1G Ram, USB Mouse. 3 Harddisk, 1 DVD RW.

---

### Post by AsusFreak on 2008-10-06
> **BMWDriver said:**
> To install the ATI proprietary drivers manually (Catalyst 8.9), I went [**here**]("http://wiki.cchtml.com/index.php/Ubuntu") and followed the appropriate instructions. They specify all the tools you must install unlike in the Ubuntu help forums.

After much headaches with trying to install the driver with the restricted drivers check box - always getting Mesa drivers with fglrxinfo even after trying to uninstall the Mesa drivers, countless reboots and line inputs on the term - I was successful in installing the latest drivers and getting them to work properly instead.

I found the information there to be better organized.

I had two days of searching and trying, but with no results, only made X Serv not working, went to that site which Driver mentioned above did as it says and wuala:
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series
OpenGL version string: 2.1.7979 Release

all set up and running. Thanks Drive!:popcorn:

---

### Post by Dark_Jester on 2008-10-06
I enabled the ATI drivers for my Radeon 9600 in my fresh installation of Ubuntu 8.04, and the LCD display runs in 1440x900, which is fine apart from the fact that it's only running at 60Hz so I get flickering when I move windows around and such. My fumbling attempts at using aticonfig to force 75Hz, which I have seen my monitor do in Windows, only resulted in the display dropping to 1024x768@60hz and refusing to do anything different until I restored my xorg.conf. Can anybody help me up the refresh rate?

---

### Post by BMWDriver on 2008-10-09
> **Dark_Jester said:**
> I enabled the ATI drivers for my Radeon 9600 in my fresh installation of Ubuntu 8.04, and the LCD display runs in 1440x900, which is fine apart from the fact that it's only running at 60Hz so I get flickering when I move windows around and such. My fumbling attempts at using aticonfig to force 75Hz, which I have seen my monitor do in Windows, only resulted in the display dropping to 1024x768@60hz and refusing to do anything different until I restored my xorg.conf. Can anybody help me up the refresh rate?

I also had flickering problems with my Radeon 9600 with my LCD. I would suggest consulting the thread I point to a few posts above. It is very likely that your problem has nothing to do with the refresh rate of your screen. LCDs are quite different in that respect.

---

### Post by tamalatamala on 2008-10-10
I have a HP compaq 6735b running on AMD Turion X2 Ultra. I had a hard time getting ATI to work properly (ATI Radeon HD 3200 Graphics).

I finally did it following:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)
(btw, I had to replace gedit command by vi)

I had to apply method 2 and then also resolve special issues 2.1 and 2.2. I've rebooted several times now and it works.

---

### Post by JeeZiTsDave on 2008-10-15
Thanks, I was looking for something like this.  I need to install it on my desktop machine, but was not going to officially move to Ubuntu with out the proper proprietary drivers for ATI Graphics Chipsets.  I myself on my laptop machine prefer Intel Chipsets.  They are great and require no third party setup in my Ubuntu with KDE Desktop Environment and also GNOME.

---

### Post by Johny_123 on 2008-10-21
:lolflag::lolflag:

---

### Post by XxX_VLAD_XxX on 2008-11-15
I follow the directions from

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

but when I reboot it shows a window telling me I have to run in Low resolution Mode

I have a Radeon X1550 and Ubuntu 8.04, It's supposed to be supported by the open-source but it simply doesn't work

---

### Post by toallpointswest on 2008-11-17
> **XxX_VLAD_XxX said:**
> I follow the directions from

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

but when I reboot it shows a window telling me I have to run in Low resolution Mode

I have a Radeon X1550 and Ubuntu 8.04, It's supposed to be supported by the open-source but it simply doesn't work

I'm running into a similar problem in my case I discovered that the old fglrx driver was still running even though I'd removed the package (I'd forgotten to reboot). After rebooting I discovered that the radeon oss driver would load (and didn't create the /dev/dri/card0 device) 

I found that by running in recovery mode, then forcing the driver to load (modprobe radeon) , and then issuing an "init 2" I was able to get back to a GUI. My question is, how can I get the radeon driver to auto-load, even though it's called in my my xorg.conf (as "Driver" ati) it still doesn't load.

---

### Post by mrincubus88 on 2008-11-25
VERY similar problem I'm running into... I'm using the ati driver as well and every time i boot it requests for me to boot in low-graphics mode. I really have no clue on what to do.  I have a x1600 pro AGP card 512 mb

---

### Post by peakshysteria on 2008-11-25
> **mrincubus88 said:**
> VERY similar problem I'm running into... I'm using the ati driver as well and every time i boot it requests for me to boot in low-graphics mode. I really have no clue on what to do.  I have a x1600 pro AGP card 512 mb

My solution to exactly the same problem:

> **peakshysteria said:**
> After an irritating trouble with recurring problems with sound in Flash I decided to make the jump and upgrade to Intrepid. After the upgrade I also got the black screen of death. Rebooting gave me low graphics mode (strangely enough with perfect aspect ratio). Had some trouble with getting my ATI driver up and running. But after following: [Installing the restricted drivers "the Ubuntu way"]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_.22the_Ubuntu_way.22") After a restart everything booted fine and dandy. Smooth as ever. With working flash, java, ATI CCC, Compiz, SAMBA, NTFS, Google Earth, Mozilla Firefox, Mozilla Thunderbird, Deluge etc.

```
fglrxinfo
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X700 PRO
OpenGL version string: 2.1.8087 Release

Intrepid seem stable as a rock (but I guess it's still early coming from a fresh upgrade). Yay for now anyways :)



---

### Post by XxX_VLAD_XxX on 2008-11-25
The way I solved was to download the proprietary drivers and installed them using a tutorial I found.

---

### Post by mrincubus88 on 2008-11-25
I'm trying this again peak... but I believe ive done this before... not sure as i've been through this like 900000 times lol

---

### Post by mrincubus88 on 2008-11-25
Now it just gets past the splash screen and goes for me to login in terminal it wont load the gui system at all...

---

### Post by munky99999 on 2008-11-25
> **mrincubus88 said:**
> VERY similar problem I'm running into... I'm using the ati driver as well and every time i boot it requests for me to boot in low-graphics mode. I really have no clue on what to do.  I have a x1600 pro AGP card 512 mb
I tried to update from 8.9 catalyst to 8.11 being the latest and had the same issue. It couldnt be resolved. So I simply removed the drivers and installed 8.9 back and it is back to working properly.

Pretty sure there's a conflict between the latest drivers and xorg 7.4 but dont quote me on that.

Catalyst 8.10 most likely works properly also as there's no xorg 7.4 deal.

Best bet is to go with 8.9

You can get the older drivers from the same place.

[http://ati.amd.com/support/driver.HTML](http://ati.amd.com/support/driver.HTML)

Previous drivers listed under additional links once you get to the appropriate os driver.

---

### Post by Outlit on 2008-11-25
Are you interested in making absolutely free money?

Nothing better then Bux.to!

Click here and join today -----V

[[IMG]http://i423.photobucket.com/albums/pp318/Outlit/banner.png[/IMG]]("http://bux.to/?r=Outlit")

---

### Post by mrincubus88 on 2008-11-25
Hey thanks, I'll try this the other one 8.11 just ruins me lol...

---

### Post by markbuntu on 2008-11-25
I tried those directions in the how to, they just don't work for me. I always end up in VESA land. Instead, after I downloaded the driver to my desktop I just ran the installer:
```

cd Desktop

sudo ./ati-driver-installer-8-10-x86.x86_64.run

```
Choose automatic, etc...

Then run aticonfig
```

sudo aticonfig --initial -f

```

If you get an error then reboot before running aticonfig.

Restart x, Open the Catalyst Control Center and reconfigure my big desktop etc, restart x  and viola'.

---

### Post by munky99999 on 2008-11-25
markbuntu we more or less know how to do that.

The reason why it worked for you was the fact you werent using the latest version.

ati-driver-installer-[SIZE="5"]8-10[/SIZE]-x86.x86_64.run

I guess this affirms that 8.10 is working properly. It is simply 8.11 that's messed.

---

### Post by mrincubus88 on 2008-11-25
Well i just did a fresh install so ill be checking out nine if that doesn't work well... back to the drawing board.

---

### Post by mrincubus88 on 2008-11-25
It seems like it wont run... This is what I get after i try to run it... 

```
Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.27-7-generic; make sure that the version is being correctly set up by --iscurrentdistro
```

---

### Post by yuli_capone on 2008-11-26
i have a ATI radeon x1100.you think this will work with my video card?

---

### Post by mrincubus88 on 2008-11-26
Okay it seems that 8-9 only goes to X 7.3 so it wont install on my new x server that I have... Is there anyway in reinstalling x server to 7.3?

---

### Post by peakshysteria on 2008-11-26
> **mrincubus88 said:**
> Okay it seems that 8-9 only goes to X 7.3 so it wont install on my new x server that I have... Is there anyway in reinstalling x server to 7.3?

I'm running latest Ubuntu 8.10 Intrepid Ibex with the 8.10 version of the ATI driver on xorg 7.4. Smooth as ever (thanks to markbuntu actually). So you can choose between 8.10 and 8.11. Version 8.9 is not compatible.

---

### Post by markbuntu on 2008-11-26
I always stay at least one version behind for anything and keep an eye on the forums....
To those who stay on the bleeding edge....Thanks!

---

### Post by mrincubus88 on 2008-11-26
I just jumped back to 8.04 Ubuntu to see if it will work... if not then its a different problem ...

I tried what markbuntu said as well but it wont let me open 8.10 or 8.9... it gives me that error i posted up above.

---

### Post by NoVista on 2008-11-27
> I'm running latest Ubuntu 8.10 Intrepid Ibex with the 8.10 version of the ATI driver on xorg 7.4. Smooth as ever 

Smooth as ever?
You're kidding right?

Another month, another poor driver set from ATI.
Another month with herky-jerky full screen video.

Back to the great open source drivers for me.
Goodbye 3D :(

---

### Post by sim-value on 2008-12-11
> **mrincubus88 said:**
> It seems like it wont run... This is what I get after i try to run it... 

```
Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.27-7-generic; make sure that the version is being correctly set up by --iscurrentdistro
```

Same here ...

---

### Post by spandanj on 2008-12-11
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

just follow method 1 on this link.

I don't have time to figure out installing the driver on my own. I will hope that Ubuntu will update their default restricted driver to latest ATI driver on a regular basis. And, I hope I won't be put to a disadvantage because I have faith in Ubuntu team to provide me the best working solution and latest features of a driver.

What do you think? any reason not to use the restricted driver provided by Ubuntu itself?

---

### Post by sim-value on 2008-12-12
> **spandanj said:**
> [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

just follow method 1 on this link.

I don't have time to figure out installing the driver on my own. I will hope that Ubuntu will update their default restricted driver to latest ATI driver on a regular basis. And, I hope I won't be put to a disadvantage because I have faith in Ubuntu team to provide me the best working solution and latest features of a driver.

What do you think? any reason not to use the restricted driver provided by Ubuntu itself?
Dont know ... exept that its not working (atleast it never worked since 7.04 for me)

---

### Post by spandanj on 2008-12-12
> **sim-value said:**
> Dont know ... exept that its not working (atleast it never worked since 7.04 for me)

it worked for me for 7.11, 8.04, and 8.11. 

everything works except openGL + compiz which is not th driver's problem as far as i know. I use x11 in smplayer to play video files. I haven't tried external monitor

---

### Post by lavinog on 2008-12-13
> **sim-value said:**
> Dont know ... exept that its not working (atleast it never worked since 7.04 for me)

What version of ubuntu are you using now? Also is it 32 bit or 64 bit?
What video card do you have?

---

### Post by sim-value on 2008-12-15
> **lavinog said:**
> What version of ubuntu are you using now? Also is it 32 bit or 64 bit?
What video card do you have?

64 Bit 8.04 (was on 8.10 before also didnt work) ...

Its an HD 3650 .. it also didnt work before with my X1550 on 32 Bit Feisty Fawn - Hardy 

But atleast i now know that its not that ati cant make linux drivers but they generally cant make drivers ...

under vista it aint working to ...

---

### Post by lavinog on 2008-12-15
Have you tried the 8-12 driver. It was released a couple of days ago.
Are you sure the problem isn't your card?...does it work in xp
What exactly is it doing/not doing?

---

### Post by Angus77 on 2008-12-18
The 8-12 driver is the same old story for me as all the others have been.  After a certain amount of time, the screen suddenly starts going to garbage.

I use a Radeon x1300 Pro.

---

### Post by markbuntu on 2008-12-18
I just installed the 8.12 driver on hardy 386 and it works better than any previous driver with my HD3650. I removed the old driver, ran the installer and rebooted to get the new kernel modules working, voila!

I will be trying it soon on my amd64 hardy and amd64 intrepid installs and will report back.

---

### Post by lavinog on 2008-12-19
I just installed it, and I got my first performance gain since 8-4.
Every thing seems to be working fine on my 8.10 (64bit) machine (ATI 3200 IGP). 
I just ordered a Saphire 3600 card so I am hoping everything still works after the transplant.

---

### Post by markbuntu on 2008-12-19
> **lavinog said:**
> I just installed it, and I got my first performance gain since 8-4.
Every thing seems to be working fine on my 8.10 (64bit) machine (ATI 3200 IGP). 
I just ordered a Saphire 3600 card so I am hoping everything still works after the transplant.

With the new driver you can use them both with surroundview.

---

### Post by lavinog on 2008-12-20
> **markbuntu said:**
> With the new driver you can use them both with surroundview.

I have 4 monitors available...might come in handy when I have a project to work on...I will have to give it a try.

I got my new card today. I put it in and ubuntu fglrx complained that it couldn't find any video cards. I tried reinstalling 8-12 using the automated installer and it didn't work.
the installer said that everything went fine, but /usr/share/ati/fglrx-install.log says this:
```

[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Message] Kernel Module : Found kernel module build environment, generating kernel module now.
AMD kernel module generator version 2.1
doing Makefile based build for kernel 2.6.x and higher
rm -rf *.c *.h *.o *.ko *.GCC* .??* *.symvers
make -C /lib/modules/2.6.27-10-generic/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-10-generic'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function ‘KCL_MEM_VM_GetRegionPhysAddrStr’:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3221: warning: return makes pointer from integer without a cast
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3222: warning: return makes pointer from integer without a cast
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3223: warning: return makes pointer from integer without a cast
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3225: warning: return makes pointer from integer without a cast
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_acpi.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_debug.o
/lib/modules/fglrx/build_mod/2.6.x/kcl_debug.c: In function ‘KCL_DEBUG_Print’:
/lib/modules/fglrx/build_mod/2.6.x/kcl_debug.c:89: warning: format not a string literal and no format arguments
/lib/modules/fglrx/build_mod/2.6.x/kcl_debug.c: In function ‘__ke_printk’:
/lib/modules/fglrx/build_mod/2.6.x/kcl_debug.c:146: warning: format not a string literal and no format arguments
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_ioctl.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_io.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_pci.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_str.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_wait.o
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /lib/modules/fglrx/build_mod/2.6.x/fglrx.mod.o
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-10-generic'
build succeeded with return value 0
duplicating results into driver repository...
done.
You must change your working directory to /lib/modules/fglrx
and then call ./make_install.sh in order to install the built module.
- recreating module dependency list
- trying a sample load of the kernel modules
done.

```
I wound up re-installing it using the manual method of building the deb packages and installing them...I had a lot of dependancy issues...mainly dkms had to be installed. (but yet i already had a /var/lib/dkms/fglrx/8.552 folder)
long story short
Everything is working now and my fglrx gears went from 1200fps to 3150 fps
I can play UT2004 on 1280x1024 with highest details while I had to play 800x600 with lowest before.
I am a little thrown off by lspci though
```
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3600 Series

```
Why is it calling it a Mobility Radeon?
Either way the card is working great. It is a Sapphire HD3650 512M DDR2 PCI-E with Dual DVI. Got it on newegg for $50.

---

### Post by peakshysteria on 2008-12-21
> **markbuntu said:**
> I just installed the 8.12 driver on hardy 386 and it works better than any previous driver with my HD3650. I removed the old driver, ran the installer and rebooted to get the new kernel modules working, voila!

I will be trying it soon on my amd64 hardy and amd64 intrepid installs and will report back.

How did you remove the driver (what command or where)? Cant't you just run the new installer on top of the old one? I think I'm running the 8.9 version of the driver right now (how can I found out the version of my driver?). It's running very smooth on my Intrepid.

---

### Post by lavinog on 2008-12-21
> **peakshysteria said:**
> How did you remove the driver (what command or where)? Cant't you just run the new installer on top of the old one? I think I'm running the 8.9 version of the driver right now (how can I found out the version of my driver?). It's running very smooth on my Intrepid.

I thought 8.9 didn't support the Xorg version in intrepid.

---

### Post by markbuntu on 2008-12-21
> **peakshysteria said:**
> How did you remove the driver (what command or where)? Cant't you just run the new installer on top of the old one? I think I'm running the 8.9 version of the driver right now (how can I found out the version of my driver?). It's running very smooth on my Intrepid.

You need to remove old drivers to avoid dkms issues when you get kernel updates since multiple dkms will be available so the kernel will not use any of them. 

If you installed drivers from ati you can remove them like this (this is directly from the installer instructions);

Remove the previous driver

If the ATI Proprietary Linux Driver was installed using either the Automatic or
Custom options, then do the following:
1 Launch the Terminal Application/Window and navigate to the /usr/share/ati
     folder
2 With superuser permissions, enter the command "sh ./fglrx-uninstall.sh"
You have now successfully uninstalled the ATI Linux Proprietary Driver.

If you used envy, you need to use envy to completely uninstall the driver. If you got it from the repos you can use synaptic of apt-get purge to completely remove the old drivers and the kernel modules.

If you are using intrepid, you are using the 8.11 driver, previous drivers will not work with the 2.6.27-29  kernel in intrepid.

---

### Post by zika on 2008-12-27
now You got me worried. I've been using the drivers for HD 3650 that came with 8.11 Catalyst. once the new drivers were available I just got the file from ati.amd.com and done the whole action (sh... aticonfig  ...). I did not uninstall previous driver. everything worked OK and the log says:> Creating symlink /var/lib/dkms/fglrx/8.561/source ->
                 /usr/src/fglrx-8.561

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
pushd /var/lib/dkms/fglrx//build; sh make.sh --nohints; popd......
cleaning build area....

DKMS: build Completed.
Running module version sanity check.

fglrx.ko:
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.27-9-generic/updates/dkms/

depmod....

DKMS: install Completed.
I've checked and in aforementioned directories there are no remnants of old driver. just 8.561.

am I doing something wrong or it should be that simple?

what happens in the middle, ater unistalling old driver and installing new? in my case it all went with might one blank of screen, quicker that it was for the same driver in Vista.

to use this post to ask another question. I hear a lot about open-source driver for this card but I do not get how to get it and is it better than proprietary ATI driver?

---

### Post by markbuntu on 2008-12-28
It may be that the 8.12 driver removes the old modules, I know the previous drivers did not. The integration of those drivers with ubuntu is improving with every release and their documentation is sketchy so it is possible. Anyway, if you get a kerenl update that fails to load the fglrx kernel modules you will know what is going on and be able to fix it fairley easily.

---

### Post by lavinog on 2009-01-14
I found some computers (Both running hardy) where 3d wasn't working with fglrx.
It turned out that I needed to comment out everything in /etc/modprobe.d/lrm-video
I just happened to find this bug report on the issue:
[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/149934](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/149934)

---

### Post by jeff48 on 2010-12-27
I have ATI 7000/VRE AGP 32 mb (I know, old card). I am running it on a single core P4 at 2.66MHz. I tried to install ATI drivers on my Linux computer and it did not seem to work. I am unable to run many games, nor can I run any visual effects in appearance preferences. I would like to clean out any of the old drivers and start fresh either with the standard Linux drivers or try to install the ATI drivers again. Any suggestions?

---

### Post by handy on 2010-12-27
> **jeff48 said:**
> I have ATI 7000/VRE AGP 32 mb (I know, old card). I am running it on a single core P4 at 2.66MHz. I tried to install ATI drivers on my Linux computer and it did not seem to work. I am unable to run many games, nor can I run any visual effects in appearance preferences. I would like to clean out any of the old drivers and start fresh either with the standard Linux drivers or try to install the ATI drivers again. Any suggestions?

You can't install the AMD proprietary drivers as they don't support your card anymore.

For legacy cards you need to continue using the FOSS driver stack, which would have been installed by default by Ubuntu.

You can get performance improvements by using a later kernel & later versions of the files involved in the driver stack to do this (which is actually quite safe & easy) have a look at the first post in this thread, scroll down to the "Ubuntu Stuff" section for the how-to:

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

If you do go down this path let us know in the above linked to thread, as we benefit from user input.

I hope all goes well for you.

---

### Post by bbemmerful on 2012-05-19
This worked well for me thankyou:KS

---

### Post by ballfresno on 2012-05-27
I updated to 12.04 from 11.10 and found that I had lost acceleration in X11.  The log file for Xorg said that fglrx.ko could not be found.

The simplest solution was to

sudo dpkg-reconfigure fglrx-updates

Everything now works fine.

---

### Post by ktandal on 2012-07-07
This helped out a lot for me. After searching on google "How to..." and getting nowhere, 
I finally registered on ubuntu forums and got my answer and
 got both monitors up and working with no problems. I upgraded to 12.04 btw.

HAH!! Now I can monitor my kids on one screen and 
work on the other(sole purpose of getting dualheads on my pc). 
If I had only registered two weeks ago I wouldn't have lost 
so much sleep...


Thanks!!:p

---

### Post by arkanabar on 2012-07-11
I'm trying to follow the manual instructions for installing Catalyst 12.6beta (examples [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Manually_installing_Catalyst_12.6") and [here]("http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually")) in Lucid Lynx and I get to this step:```
sudo sh amd-driver-installer-12-6-x86.x86_64.run --buildpkg Ubuntu/lucid
```result:  ```
sh: Can't open amd-driver-installer-12-6-x86.x86_64.run
```So my question is:  what the hey?  I've done everything exactly as instructed (except that I had to grab & unzip a .zip version of the file in question).

---

