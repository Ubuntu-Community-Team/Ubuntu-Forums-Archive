---
title: "End of Popular Games for Older hardware with newer Precise"
date: 2012-03-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ventrical on 2012-03-14
Older popular 3d games like Neverputt, Neverball GL Billiards, Brutal chess and the likes which worked on older Celeron boards with ATI Rage Pro 128's with the Precise alpha 3.2.0-12 kernel can no longer be excpected to work at all with beta1 +. The newer features of  Ubuntu Precise  and made it practically impossible for those older popular games to run at all. Although Unity 2d and other Unity features work really swell, the 3d games appear to be gone for good unless  a processor or video adapter upgrade is  part of the new hardware build.

 So anyone trying to restore older PCs  may find a very limited amount of success.

---

### Post by dino99 on 2012-03-14
hey, i'm still having a nice Jaunty around :)

---

### Post by JHCKX on 2012-03-14
Have you tried gnome-fallback? That will allow you to login using Gnome Classic (no effects). Video performance using Gnome classic is at least as good as in 10.04, I'd say it's even better.

---

### Post by ventrical on 2012-03-14
> **John2.Hendrickx@gmail.com said:**
> Have you tried gnome-fallback? That will allow you to login using Gnome Classic (no effects). Video performance using Gnome classic is at least as good as in 10.04, I'd say it's even better.


Tried and tired .... and .. I'll try again on this fresh install.. but GNOME-fallback , xubuntu-desktop or lubuntu-desktop  will not run those games on anything  Precise beta1 and up !

---

### Post by kostkon on 2012-03-14
The real reason is that [Mesa decided to drop support for older hardware]("http://www.phoronix.com/scan.php?page=news_item&px=OTg0Mg"); It's not Ubuntu's fault.

---

### Post by ventrical on 2012-03-14
> **John2.Hendrickx@gmail.com said:**
> Have you tried gnome-fallback? That will allow you to login using Gnome Classic (no effects). Video performance using Gnome classic is at least as good as in 10.04, I'd say it's even better.

 Just tired it ... no chance ... but worked great with Unity 2D 3.2.0-12 alpha 2. Definitely a regression for older PCs.

  I'm not scandalizing Precise. It is amazing that it even works at all on a machine such as I have described .. but those 3D games help sell the system overall to newer and older persons alike.  There is a set of hackers out there (sort of like those who restore classic cars) who like to bring back older PCs from the scrap heap to see what Ubuntu can do.  Perhaps others are having better luck.

btw  I'm not complaining.. I'm just reporting results of my experiments , the good, the bad and the ugly.

add-on

 Also if you drop to the previous kernel in GRUB (3.2.0-12) the graphicals will not work either.

---

### Post by ventrical on 2012-03-14
> **kostkon said:**
> The real reason is that [Mesa decided to drop support for older hardware]("http://www.phoronix.com/scan.php?page=news_item&px=OTg0Mg"); It's not Ubuntu's fault.

But that doesn't explain why it worked with a fresh beta1 Precise 3.2.0-12.

---

### Post by ventrical on 2012-03-14
> **dino99 said:**
> hey, i'm still having a nice Jaunty around :)

 I put up Lucid side by side .. works great !

---

### Post by teh603 on 2012-03-14
Waitaminute, SiS video was actually supported? I've got one of those crusty old video chipsets in my Winbook and was never able to get it to render anyway.

:lolflag:

---

### Post by ventrical on 2012-03-14
> **cariboo907 said:**
> @ventrical, your problems with games, have nothing to do with ccsm, it sounds more like a graphics driver problem.


 I see the light... I looked at a Lucid install and seen where the ATI Rage driver was installed and then looked at the Precise  :0.log and seen where it was dissed.

```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
Current Operating System: Linux ventrical-desktop 2.6.32-39-generic #86-Ubuntu SMP Mon Feb 13 21:47:32 UTC 2012 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-39-generic root=UUID=1c4eb7fb-7817-448a-8a88-1ea638c696b8 ro quiet splash
Build Date: 20 October 2011  03:05:54PM
xorg-server 2:1.7.6-2ubuntu7.10 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar 14 18:05:04 2012
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(++) using VT number 7

(--) PCI:*(0:1:0:0) 1002:5046:1002:0008 ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS rev 0, Mem @ 0xd4000000/67108864, 0xd9000000/16384, I/O @ 0x0000d000/256, BIOS @ 0x????????/131072
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
(==) AIGLX enabled
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
(==) Matched ati as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 6.13.0
(II) Loading /usr/lib/xorg/modules/drivers/r128_drv.so
(II) Module r128: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 6.8.1
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.0
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.4.1
(II) R128: Driver for ATI Rage 128 chipsets:
    ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
    ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
    ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
    ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
    ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
    ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
    ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
    ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
    ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
    ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
    ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
    ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
    ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
    ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
    ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
    ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
    ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
    ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
    ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
    ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
    ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
    ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
    ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
    ATI Rage 128 Pro ULTRA TU (AGP?)
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.0.2
(II) R128(0): PCI bus 1 card 0 func 0
(II) R128(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
(==) R128(0): Depth 24, (--) framebuffer bpp 32
(II) R128(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) R128(0): Default visual is TrueColor
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.1.0
(==) R128(0): RGB weight 888
(II) R128(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
(II) R128(0): initializing int10
(II) R128(0): Primary V_BIOS segment is: 0xc000
(--) R128(0): Chipset: "ATI Rage 128 Pro GL PF (AGP)" (ChipID = 0x5046)
(--) R128(0): Linear framebuffer at 0xd4000000
(--) R128(0): MMIO registers at 0xd9000000
(--) R128(0): VideoRAM: 32768 kByte (64-bit SDR SGRAM 1:1)
(**) R128(0): Using external CRT for display
(II) R128(0): Primary Display == Type 3
(WW) R128(0): Can't determine panel dimensions, and none specified.
    Disabling programming of FP registers.
(II) R128(0): PLL parameters: rf=2950 rd=65 min=12500 max=40000; xclk=12000
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
(II) R128(0): VESA BIOS detected
(II) R128(0): VESA VBE DDC supported
(II) R128(0): Manufacturer: VSC  Model: 220  Serial#: 16843009
(II) R128(0): Year: 2007  Week: 19
(II) R128(0): EDID Version: 1.3
(II) R128(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) R128(0): Sync:  Separate  Composite  SyncOnGreen
(II) R128(0): Max Image Size [cm]: horiz.: 41  vert.: 26
(II) R128(0): Gamma: 2.20
(II) R128(0): DPMS capabilities: Off; RGB/Color Display
(II) R128(0): Default color space is primary color space
(II) R128(0): First detailed timing is preferred mode
(II) R128(0): redX: 0.640 redY: 0.334   greenX: 0.286 greenY: 0.599
(II) R128(0): blueX: 0.154 blueY: 0.077   whiteX: 0.313 whiteY: 0.329
(II) R128(0): Supported established timings:
(II) R128(0): 720x400@70Hz
(II) R128(0): 640x480@60Hz
(II) R128(0): 640x480@67Hz
(II) R128(0): 640x480@72Hz
(II) R128(0): 640x480@75Hz
(II) R128(0): 800x600@56Hz
(II) R128(0): 800x600@60Hz
(II) R128(0): 800x600@72Hz
(II) R128(0): 800x600@75Hz
(II) R128(0): 832x624@75Hz
(II) R128(0): 1024x768@60Hz
(II) R128(0): 1024x768@70Hz
(II) R128(0): 1024x768@75Hz
(II) R128(0): 1280x1024@75Hz
(II) R128(0): 1152x864@75Hz
(II) R128(0): Manufacturer's mask: 0
(II) R128(0): Supported standard timings:
(II) R128(0): #0: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) R128(0): #1: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) R128(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) R128(0): #3: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) R128(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) R128(0): Supported detailed timing:
(II) R128(0): clock: 106.5 MHz   Image Size:  410 x 256 mm
(II) R128(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) R128(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) R128(0): Serial No: QN9071977913
(II) R128(0): Ranges: V min: 50 V max: 75 Hz, H min: 30 H max: 82 kHz, PixClock max 140 MHz
(II) R128(0): Monitor name: VA1930wm-3
(II) R128(0): EDID (in hex):
(II) R128(0):     00ffffffffffff005a63200201010101
(II) R128(0):     131101030e291a782ee5b5a355499927
(II) R128(0):     135054bfef809500950f81808140714f
(II) R128(0):     0101010101019a29a0d0518422305098
(II) R128(0):     36009a001100001c000000ff00514e39
(II) R128(0):     3037313937373931330a000000fd0032
(II) R128(0):     4b1e520e000a202020202020000000fc
(II) R128(0):     00564131393330776d2d330a20200017
(II) R128(0): EDID vendor "VSC", prod id 544
(II) R128(0): Using EDID range info for horizontal sync
(II) R128(0): Using EDID range info for vertical refresh
(II) R128(0): Printing DDC gathered Modelines:
(II) R128(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) R128(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) R128(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) R128(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) R128(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) R128(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) R128(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) R128(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) R128(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) R128(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) R128(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) R128(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) R128(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) R128(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) R128(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) R128(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) R128(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) R128(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) R128(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(==) R128(0): Using gamma correction (1.0, 1.0, 1.0)
error setting MTRR (base = 0xd4000000, size = 0x02000000, type = 1) Inappropriate ioctl for device (25)
(II) R128(0): I2C bus "DDC" initialized.
(II) R128(0): I2C device "DDC:ddc2" registered at address 0xA0.
(EE) R128(0): No DFP detected
error setting MTRR (base = 0xd4000000, size = 0x02000000, type = 1) Inappropriate ioctl for device (25)
(II) R128(0): <default monitor>: Using hsync range of 30.00-82.00 kHz
(II) R128(0): <default monitor>: Using vrefresh range of 50.00-75.00 Hz
(II) R128(0): <default monitor>: Using maximum pixel clock of 140.00 MHz
(II) R128(0): Estimated virtual size for aspect ratio 1.5769 is 1440x900
(II) R128(0): Clock range:  12.50 to 400.00 MHz
(II) R128(0): Not using default mode "640x350" (vrefresh out of range)
(II) R128(0): Not using default mode "320x175" (vrefresh out of range)
(II) R128(0): Not using default mode "640x400" (vrefresh out of range)
(II) R128(0): Not using default mode "320x200" (vrefresh out of range)
(II) R128(0): Not using default mode "720x400" (vrefresh out of range)
(II) R128(0): Not using default mode "360x200" (vrefresh out of range)
(II) R128(0): Not using default mode "640x480" (vrefresh out of range)
(II) R128(0): Not using default mode "320x240" (vrefresh out of range)
(II) R128(0): Not using default mode "800x600" (vrefresh out of range)
(II) R128(0): Not using default mode "400x300" (vrefresh out of range)
(II) R128(0): Not using default mode "1024x768" (vrefresh out of range)
(II) R128(0): Not using default mode "512x384" (vrefresh out of range)
(II) R128(0): Not using default mode "1024x768" (vrefresh out of range)
(II) R128(0): Not using default mode "512x384" (vrefresh out of range)
(II) R128(0): Not using default mode "1280x960" (height too large for virtual size)
(II) R128(0): Not using default mode "1280x960" (height too large for virtual size)
(II) R128(0): Not using default mode "640x480" (hsync out of range)
(II) R128(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) R128(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) R128(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) R128(0): Not using default mode "640x512" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) R128(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) R128(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) R128(0): Not using default mode "896x672" (hsync out of range)
(II) R128(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) R128(0): Not using default mode "896x672" (hsync out of range)
(II) R128(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) R128(0): Not using default mode "928x696" (hsync out of range)
(II) R128(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) R128(0): Not using default mode "928x696" (hsync out of range)
(II) R128(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) R128(0): Not using default mode "960x720" (hsync out of range)
(II) R128(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) R128(0): Not using default mode "960x720" (hsync out of range)
(II) R128(0): Not using default mode "1152x864" (vrefresh out of range)
(II) R128(0): Not using default mode "576x432" (vrefresh out of range)
(II) R128(0): Not using default mode "1152x864" (vrefresh out of range)
(II) R128(0): Not using default mode "576x432" (vrefresh out of range)
(II) R128(0): Not using default mode "1152x864" (hsync out of range)
(II) R128(0): Not using default mode "576x432" (hsync out of range)
(II) R128(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) R128(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) R128(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) R128(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) R128(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) R128(0): Not using default mode "700x525" (hsync out of range)
(II) R128(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) R128(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "840x525" (hsync out of range)
(II) R128(0): Not using default mode "1920x1080" (width too large for virtual size)
(II) R128(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) R128(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) R128(0): Not using default mode "960x720" (hsync out of range)
(II) R128(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using driver mode "1280x1024" (height too large for virtual size)
(II) R128(0): Not using driver mode "1280x1024" (height too large for virtual size)
(II) R128(0): Not using driver mode "1280x960" (height too large for virtual size)
(--) R128(0): Virtual size is 1440x900 (pitch 1440)
(**) R128(0): *Driver mode "1440x900": 106.5 MHz, 55.9 kHz, 59.9 Hz
(II) R128(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(**) R128(0): *Driver mode "1440x900": 136.8 MHz, 70.6 kHz, 75.0 Hz
(II) R128(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(**) R128(0): *Default mode "1440x900": 106.5 MHz, 55.9 kHz, 59.9 Hz
(II) R128(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(**) R128(0): *Default mode "1360x768": 84.8 MHz, 47.7 kHz, 59.8 Hz
(II) R128(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(**) R128(0): *Driver mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) R128(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) R128(0): *Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) R128(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) R128(0): *Default mode "1152x864": 105.0 MHz, 67.6 kHz, 75.0 Hz
(II) R128(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(**) R128(0): *Default mode "1152x864": 96.8 MHz, 63.0 kHz, 70.0 Hz
(II) R128(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(**) R128(0): *Default mode "1152x864": 81.6 MHz, 53.7 kHz, 60.0 Hz
(II) R128(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(**) R128(0): *Driver mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) R128(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) R128(0): *Driver mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) R128(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) R128(0): *Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) R128(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) R128(0): *Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) R128(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) R128(0): *Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) R128(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) R128(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) R128(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) R128(0): *Driver mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) R128(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) R128(0): *Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) R128(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) R128(0): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) R128(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) R128(0): *Driver mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) R128(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) R128(0): *Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) R128(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) R128(0): *Driver mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) R128(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) R128(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) R128(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) R128(0): *Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) R128(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) R128(0): *Default mode "800x600": 87.8 MHz, 81.2 kHz, 65.0 Hz (D)
(II) R128(0): Modeline "800x600"x65.0   87.75  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (81.2 kHz)
(**) R128(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) R128(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) R128(0): *Default mode "800x600": 81.0 MHz, 75.0 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "800x600"x60.0   81.00  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (75.0 kHz)
(**) R128(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) R128(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) R128(0): *Default mode "840x525": 93.5 MHz, 82.3 kHz, 75.0 Hz (D)
(II) R128(0): Modeline "840x525"x75.0   93.50  840 900 988 1136  525 526 529 549 doublescan -hsync +vsync (82.3 kHz)
(**) R128(0): *Default mode "840x525": 87.0 MHz, 76.6 kHz, 69.9 Hz (D)
(II) R128(0): Modeline "840x525"x69.9   87.00  840 900 988 1136  525 526 529 548 doublescan -hsync +vsync (76.6 kHz)
(**) R128(0): *Default mode "840x525": 73.1 MHz, 65.3 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "840x525"x60.0   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync (65.3 kHz)
(**) R128(0): *Default mode "700x525": 77.9 MHz, 81.5 kHz, 74.8 Hz (D)
(II) R128(0): Modeline "700x525"x74.8   77.90  700 732 892 956  525 526 532 545 doublescan +hsync +vsync (81.5 kHz)
(**) R128(0): *Default mode "700x525": 72.5 MHz, 76.5 kHz, 70.1 Hz (D)
(II) R128(0): Modeline "700x525"x70.1   72.53  700 748 824 948  525 525 527 546 doublescan -hsync +vsync (76.5 kHz)
(**) R128(0): *Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "700x525"x60.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz)
(**) R128(0): *Default mode "640x512": 67.5 MHz, 80.0 kHz, 75.0 Hz (D)
(II) R128(0): Modeline "640x512"x75.0   67.50  640 648 720 844  512 512 514 533 doublescan +hsync +vsync (80.0 kHz)
(**) R128(0): *Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "640x512"x60.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz)
(**) R128(0): *Default mode "720x450": 53.2 MHz, 55.9 kHz, 59.9 Hz (D)
(II) R128(0): Modeline "720x450"x59.9   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz)
(**) R128(0): *Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) R128(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) R128(0): *Driver mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) R128(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) R128(0): *Driver mode "640x480": 30.2 MHz, 35.0 kHz, 66.7 Hz
(II) R128(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(**) R128(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) R128(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) R128(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) R128(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) R128(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) R128(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) R128(0): *Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "640x480"x60.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz)
(**) R128(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) R128(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) R128(0): *Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
(II) R128(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(**) R128(0): *Default mode "680x384": 36.0 MHz, 47.4 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "680x384"x60.0   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz)
(**) R128(0): *Default mode "680x384": 42.4 MHz, 47.7 kHz, 59.8 Hz (D)
(II) R128(0): Modeline "680x384"x59.8   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz)
(**) R128(0): *Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(II) R128(0): Modeline "576x432"x75.0   54.00  576 608 672 800  432 432 434 450 doublescan +hsync +vsync (67.5 kHz)
(**) R128(0): *Default mode "576x432": 52.5 MHz, 67.6 kHz, 75.0 Hz (D)
(II) R128(0): Modeline "576x432"x75.0   52.49  576 612 676 776  432 432 434 451 doublescan -hsync +vsync (67.6 kHz)
(**) R128(0): *Default mode "576x432": 48.4 MHz, 63.0 kHz, 70.0 Hz (D)
(II) R128(0): Modeline "576x432"x70.0   48.38  576 612 672 768  432 432 434 450 doublescan -hsync +vsync (63.0 kHz)
(**) R128(0): *Default mode "576x432": 40.8 MHz, 53.7 kHz, 60.1 Hz (D)
(II) R128(0): Modeline "576x432"x60.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz)
(**) R128(0): *Default mode "512x384": 39.4 MHz, 60.0 kHz, 75.0 Hz (D)
(II) R128(0): Modeline "512x384"x75.0   39.38  512 520 568 656  384 384 386 400 doublescan +hsync +vsync (60.0 kHz)
(**) R128(0): *Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) R128(0): Modeline "512x384"x70.1   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync (56.5 kHz)
(**) R128(0): *Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz)
(**) R128(0): *Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) R128(0): Modeline "416x312"x74.7   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync (49.7 kHz)
(**) R128(0): *Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) R128(0): Modeline "400x300"x75.1   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync (46.9 kHz)
(**) R128(0): *Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) R128(0): Modeline "400x300"x72.2   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync (48.1 kHz)
(**) R128(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) R128(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) R128(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) R128(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) R128(0): *Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(II) R128(0): Modeline "320x240"x75.0   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync (37.5 kHz)
(**) R128(0): *Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(II) R128(0): Modeline "320x240"x72.8   15.75  320 332 352 416  240 244 246 260 doublescan -hsync -vsync (37.9 kHz)
(**) R128(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) R128(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(**) R128(0): Display dimensions: (410, 260) mm
(**) R128(0): DPI set to (89, 87)
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.2.1
(II) Loading /usr/lib/xorg/modules/libshadowfb.so
(II) Module shadowfb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
(II) R128(0): Page flipping disabled
(!!) R128(0): For information on using the multimedia capabilities
    of this adapter, please see http://gatos.sf.net.
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(--) Depth 24 pixmap format is 32 bpp
error setting MTRR (base = 0xd4000000, size = 0x02000000, type = 1) Inappropriate ioctl for device (25)
(II) [drm] loaded kernel module for "r128" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) R128(0): [drm] Using the DRM lock SAREA also for drawables.
(II) R128(0): [drm] framebuffer handle = 0xd4000000
(II) R128(0): [drm] added 1 reserved context for kernel
(II) R128(0): X context handle = 0x1
(II) R128(0): [drm] installed DRM signal handler
(II) R128(0): [agp] Mode 0x1f000201 [AGP 0x8086/0x7190; Card 0x1002/0x5046]
(II) R128(0): [agp] 8192 kB allocated with handle 0x00000001
(II) R128(0): [agp] ring handle = 0xd0000000
(II) R128(0): [agp] Ring mapped at 0xb750d000
(II) R128(0): [agp] ring read ptr handle = 0xd0101000
(II) R128(0): [agp] Ring read ptr mapped at 0xb776f000
(II) R128(0): [agp] vertex/indirect buffers handle = 0xd0102000
(II) R128(0): [agp] Vertex/indirect buffers mapped at 0xb730d000
(II) R128(0): [agp] AGP texture map handle = 0xd0302000
(II) R128(0): [agp] AGP Texture map mapped at 0xb6e2d000
(II) R128(0): [drm] register handle = 0xd9000000
(II) R128(0): [dri] Visual configs initialized
(II) R128(0): CCE in BM mode
(II) R128(0): Using 8 MB AGP aperture
(II) R128(0): Using 1 MB for the ring buffer
(II) R128(0): Using 2 MB for vertex/indirect buffers
(II) R128(0): Using 5 MB for AGP textures
(II) R128(0): Memory manager initialized to (0,0) (1440,3640)
(II) R128(0): Reserved area from (0,900) to (1440,902)
(II) R128(0): Largest offscreen area available: 1440 x 2738
(II) R128(0): Reserved back buffer from (0,902) to (1440,1802)
(II) R128(0): Reserved depth buffer from (0,1802) to (1440,2703)
(II) R128(0): Reserved depth span from (0,2702) offset 0xed7b00
(II) R128(0): Reserved 12288 kb for textures at offset 0x13fec00
(II) R128(0): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    8x8 mono pattern filled rectangles
    Indirect CPU to Screen color expansion
    Solid Lines
    Dashed Lines
    Setting up tile and stipple cache:
        32 128x128 slots
        11 256x256 slots
(II) R128(0): Acceleration enabled
(==) R128(0): Backing store disabled
(==) R128(0): Silken mouse enabled
(II) R128(0): Using hardware cursor (scanline 10812)
(II) R128(0): Largest offscreen area available: 1440 x 935
(==) R128(0): DPMS enabled
(II) R128(0): [DRI] installation complete
(II) R128(0): [drm] Added 128 16384 byte vertex/indirect buffers
(II) R128(0): [drm] Mapped 128 vertex/indirect buffers
(II) R128(0): [drm] dma control initialized, using IRQ 11
(II) R128(0): Direct rendering enabled
(==) RandR enabled
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: Loaded and initialized /usr/lib/dri/r128_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event4)
(**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
(**) ImPS/2 Generic Wheel Mouse: always reports core events
(**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event4"
(II) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
(II) ImPS/2 Generic Wheel Mouse: Found relative axes
(II) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
(**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
(II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
(II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)

```

diff

```

X.Org X Server 1.11.3
Release Date: 2011-12-16
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-31-server i686 Ubuntu
Current Operating System: Linux Precise-on-600MHzCeleron-with-parts-from-the-recycle-bin 3.2.0-18-generic-pae #29-Ubuntu SMP Mon Mar 12 00:42:23 UTC 2012 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-18-generic-pae root=UUID=f29cc10a-c309-4299-922e-3d3a48f4ed3d ro quiet splash vt.handoff=7
Build Date: 09 March 2012  11:30:14AM
xorg-server 2:1.11.4-0ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.24.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar 14 18:23:13 2012
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) Failed to load module "fglrx" (module does not exist, 0)
(EE) Failed to load module "fglrx" (module does not exist, 0)
(EE) open /dev/fb0: No such file or directory
(EE) R128(0): No DFP detected
(EE) AIGLX error: dlopen of /usr/lib/i386-linux-gnu/dri/r128_dri.so failed (/usr/lib/i386-linux-gnu/dri/r128_dri.so: cannot open shared object file: No such file or directory)
(EE) AIGLX: reverting to software rendering

```

---

### Post by cariboo on 2012-03-14
@ventrical, I moved your off-topic post to the correct thread.

---

### Post by ventrical on 2012-03-14
> **cariboo907 said:**
> @ventrical, I moved your off-topic post to the correct thread.


Thank you for your ever enduring patience.

---

### Post by dcstar on 2012-03-14
> **teh603 said:**
> Waitaminute, SiS video was actually supported? I've got one of those crusty old video chipsets in my Winbook and was never able to get it to render anyway.


It seems that only a tiny amount of the available SiS chipsets was "supported" in Linux, so low that hardly anyone bothered.

---

### Post by cariboo on 2012-03-15
> **dcstar said:**
> It seems that only a tiny amount of the available SiS chipsets was "supported" in Linux, so low that hardly anyone bothered.

I think is was back during the Maverick development cycle, there was a SIS engineer that was interested in updating the SIS driver, but nothing ever came of it.

---

