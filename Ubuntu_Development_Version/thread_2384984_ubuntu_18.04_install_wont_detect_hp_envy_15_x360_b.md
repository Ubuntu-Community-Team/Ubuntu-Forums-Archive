---
title: "ubuntu 18.04 install wont detect hp envy 15 x360 built in monitor"
date: 2018-02-14
forum: Ubuntu Development Version
---

### Post by rokklimber on 2018-02-14
Installer works with reduced resolution (800X600). After reboot resolution still stuck at the same level even though monitor is 1920X1080 on windows 10.  Displays applet shows unknown display, is it possible I need a driver that I don't have, or need to load one?  lshw does not show monitor in the list so I am not sure where to go.  xrandr shows primary monitor 800x600+0+0 0mm x 0mm.  Seems like its loading the default config for vga and not detecting the monitor.  following steps to set xconfig also not successful as indicated on other blogs.  Can anyone tell me how to figure out where to go from here?

---

### Post by rokklimber on 2018-02-14
additionally, tried 16.04 and 17 with similar success.  seems like an autodetect issue with the edid if I had to guess..

---

### Post by benjimenez805 on 2018-02-14
I've noticed this too, when i check my graphic info it says unknown, so it might be an issue with driver support in these new releases of ubuntu.

---

### Post by ajgreeny on 2018-02-15
What graphics hardware do you have?
Let's see the output of terminal command **lspci** which will give us a start.

Note, however, that 18.04 is still very much in development and there are likely to be problems with it at this stage.

---

### Post by ajgreeny on 2018-02-15
*Thread moved to **Ubuntu Development Version**.* which is more appropriate and a better fit for this problem.

---

### Post by rokklimber on 2018-03-01
so installed the 4.16 rc2 and rc3, the framebuffer grabs the dsiplay and resizes, the screen dims looks like it found the backlighting driver as well, unf crashes trying to start the login just after the ubuntu splash with the dots shows...

---

### Post by rokklimber on 2018-03-01
fyi, this happend with 16,17, and 18 so its an issue with the lack of amd drivers in the kernel.  I am not sure you should write this off as a development issue.

---

### Post by rokklimber on 2018-03-01
also still an issue with the 4.15 kernel from the last update of 18.04 this week..

lspci output:
```

00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15d0
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Device 15d1
00:01.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
00:01.6 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 15d3
00:01.7 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 15d3
00:08.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
00:08.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 15db
00:08.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 15dc
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 61)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 51)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15e8
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15e9
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15ea
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15eb
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15ec
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15ed
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15ee
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15ef
01:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS522A PCI Express Card Reader (rev 01)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device b822
03:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Vega [Radeon Vega 8 Mobile] (rev c4)
03:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 15de
03:00.2 Encryption controller: Advanced Micro Devices, Inc. [AMD] Device 15df
03:00.3 USB controller: Advanced Micro Devices, Inc. [AMD] Device 15e0
03:00.4 USB controller: Advanced Micro Devices, Inc. [AMD] Device 15e1
03:00.6 Audio device: Advanced Micro Devices, Inc. [AMD] Device 15e3
04:00.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 51)
```

uname:
```

Linux XXXX 4.14.0-041400-generic #201711122031 SMP Sun Nov 12 20:32:29 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by QIII on 2018-03-01
Hello!

Please use code tags to enclose all terminal commands and their results.  It preserves terminal formatting and makes your post easier to read.

To use code tags:

Either click the # button above the text entry box and type or paste your text between the code tags that appear; or type or paste your text, highlight it and then click the # button.

You may also type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] after your text.  The square brackets are required.

Cheers!

---

### Post by rokklimber on 2018-03-05
more information, booted in text login and ran startx... seems like the amdgpu driver is having an issue

```

[   565.989] (II) AMDGPU(0): EDID for output HDMI-A-0
[   565.989] (II) AMDGPU(0): EDID for output DisplayPort-0
[   565.989] (II) AMDGPU(0): Output eDP connected
[   565.989] (II) AMDGPU(0): Output HDMI-A-0 disconnected
[   565.989] (II) AMDGPU(0): Output DisplayPort-0 disconnected
[   565.989] (II) AMDGPU(0): Using exact sizes for initial modes
[   565.989] (II) AMDGPU(0): Output eDP using initial mode 1920x1080 +0+0
[   565.989] (II) AMDGPU(0): mem size init: gart size :bfbfc000 vram size: s:e842000 visible:e842000
[   565.989] (==) AMDGPU(0): DPI set to (96, 96)
[   565.989] (==) AMDGPU(0): Using gamma correction (1.0, 1.0, 1.0)
[   565.989] (II) Loading sub module "ramdac"
[   565.989] (II) LoadModule: "ramdac"
[   565.989] (II) Module "ramdac" already built-in
[   565.989] (II) UnloadModule: "radeon"
[   565.989] (II) Unloading radeon
[   565.989] (II) UnloadModule: "modesetting"
[   565.989] (II) Unloading modesetting
[   565.989] (II) UnloadModule: "fbdev"
[   565.989] (II) Unloading fbdev
[   565.989] (II) UnloadSubModule: "fbdevhw"
[   565.989] (II) Unloading fbdevhw
[   565.989] (II) UnloadModule: "vesa"
[   565.989] (II) Unloading vesa
[   565.989] (--) Depth 24 pixmap format is 32 bpp
[   565.989] Failed to allocate front buffer memory
[   565.989] (EE) AMDGPU(0): amdgpu_setup_kernel_mem failed
[   565.989] (EE) 
Fatal server error:
[   565.989] (EE) AddScreen/ScreenInit failed for driver 0
[   565.989] (EE) 
[   565.989] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[   565.989] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   565.989] (EE) 
[   566.003] (EE) Server terminated with error (1). Closing log file.

```

---

### Post by rokklimber on 2018-03-12
so finally managed to get it to work... not sure how...  did disable the radeon config for X and now works most of the time, with the 4.15 kernel...

---

