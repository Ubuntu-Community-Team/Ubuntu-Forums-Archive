---
title: "Green Screen"
date: 2022-10-12
forum: Ubuntu, Linux and OS Chat
---

### Post by DuckHook on 2022-10-12
A curiosity question and though it is a technical one, this is not an Ubuntu problem, hence I'm posting it on this forum:

On my first boot in the morning from a cold poweroff state, I get the expected POST screen—nothing out of the ordinary.
 
However, if I reboot, my post screen turns into a bright shade of green background. This green screen carries over into the GRUB screen too. Thankfully, I can still read the output without problems but my nice custom GRUB background is corrupted/washed out. The green screen disappears halfway through the boot process, probably when the framebuffer kicks in, so it always rights itself and is therefore not an operational concern.

I've lived with it for months, but I am curious why my computer behaves this way.

I use a somewhat offbeat setup:
My monitor is a TCL Smart TV model 43S425-CA. It gives me 4K resolution at a small fraction of the cost of a 43" monitor. I'm very happy with it. I run Wayland, but xrandr shows the following:```
duckhook@Zeus:~$  xrandr
Screen 0: minimum 16 x 16, current 3840 x 2160, maximum 32767 x 32767
XWAYLAND0 connected primary 3840x2160+0+0 (normal left inverted right x axis y axis) 950mm x 540mm
   3840x2160     59.98*+
   2048x1536     59.95  
   1920x1440     59.97  
   1600x1200     59.87  
   1440x1080     59.99  
   1400x1050     59.98  
   1280x1024     59.89  
   1280x960      59.94  
   1152x864      59.96  
   1024x768      59.92  
   800x600       59.86  
   640x480       59.38  
   320x240       59.52  
   2560x1600     59.99  
   1920x1200     59.88  
   1680x1050     59.95  
   1440x900      59.89  
   1280x800      59.81  
   720x480       59.71  
   640x400       59.95  
   320x200       58.96  
   3200x1800     59.96  
   2880x1620     59.96  
   2560x1440     59.96  
   2048x1152     59.90  
   1920x1080     59.96  
   1600x900      59.95  
   1368x768      59.88  
   1280x720      59.86  
   1024x576      59.90  
   864x486       59.92  
   720x400       59.55  
   640x350       59.77
```
EDID info is:```
duckhook@Zeus:~$ sudo get-edid | parse-edid
This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
No EDID on bus 0
No EDID on bus 1
No EDID on bus 2
No EDID on bus 3
No EDID on bus 4
No EDID on bus 6
No EDID on bus 7
No EDID on bus 8
1 potential busses found: 5
256-byte EDID successfully retrieved from i2c bus 5
Looks like i2c was successful. Have a good day.
Checksum Correct

Section "Monitor"
	Identifier "43S425CA"
	ModelName "43S425CA"
	VendorName "TCL"
	# Monitor Manufactured week 1 of 2019
	# EDID version 1.3
	# Digital Display
	DisplaySize 950 540
	Gamma 2.20
	Option "DPMS" "false"
	Horizsync 15-81
	VertRefresh 23-76
	# Maximum pixel clock is 340MHz
	#Not giving standard mode: 1152x864, 75Hz
	#Not giving standard mode: 1280x960, 60Hz
	#Not giving standard mode: 1280x1024, 60Hz
	#Not giving standard mode: 1280x800, 60Hz
	#Not giving standard mode: 1440x900, 60Hz
	#Not giving standard mode: 1680x1050, 60Hz
	#Not giving standard mode: 1920x1080, 60Hz
	#Not giving standard mode: 1280x720, 60Hz

	#Extension block found. Parsing...
#WARNING: I may have missed a mode (CEA mode 95)
#DOUBLE WARNING: It's your first mode, too, so this may actually be important.
#WARNING: I may have missed a mode (CEA mode 93)
#DOUBLE WARNING: It's your first mode, too, so this may actually be important.
#WARNING: I may have missed a mode (CEA mode 100)
#DOUBLE WARNING: It's your first mode, too, so this may actually be important.
#WARNING: I may have missed a mode (CEA mode 98)
#DOUBLE WARNING: It's your first mode, too, so this may actually be important.
#WARNING: I may have missed a mode (CEA mode 62)
#WARNING: I may have missed a mode (CEA mode 60)
	Modeline 	"Mode 10" 297.00 3840 4016 4104 4400 2160 2168 2178 2250 +hsync +vsync 
	Modeline 	"Mode 0" 297.00 3840 4016 4104 4400 2160 2168 2178 2250 +hsync +vsync 
	Modeline 	"Mode 1" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync 
	Modeline 	"Mode 2" 148.500 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
	Modeline 	"Mode 3" 74.250 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
	Modeline 	"Mode 4" 74.250 1920 2558 2602 2750 1080 1084 1089 1125 +hsync +vsync
	Modeline 	"Mode 5" 74.250 1920 2008 2052 2200 1080 1082 1087 1125 +hsync +vsync interlace
	Modeline 	"Mode 6" 74.250 1280 1390 1420 1650 720 725 730 750 +hsync +vsync
	Modeline 	"Mode 7" 27.027 720 736 798 858 480 489 495 525 -hsync -vsync
	Modeline 	"Mode 8" 25.200 640 656 752 800 480 490 492 525 -hsync -vsync
	Modeline 	"Mode 9" 27.027 1440 1478 1602 1716 480 484 487 525 -hsync -vsync interlace
	Modeline 	"Mode 11" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync 
	Modeline 	"Mode 12" 74.25 1280 1390 1430 1650 720 725 730 750 +hsync +vsync 
	Modeline 	"Mode 13" 85.50 1360 1424 1536 1792 768 771 777 795 -hsync -vsync 
	Option "PreferredMode" "Mode 10"
EndSection

```
I replaced my old video card about a year ago. At first, I didn't get this green effect, but a few months into operating, it began to behave this way. Video card is:```
duckhook@Zeus:~$ sudo lshw -c display
[sudo] password for duckhook: 
  *-display                 
       description: VGA compatible controller
       product: Navi 22 [Radeon RX 6700/6700 XT / 6800M]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: /dev/fb0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=amdgpu latency=0 resolution=3840,2160
```
Since this effect starts at the initial UEFI POST screen, I've thought that it isn't an OS issue, but I may be wrong. Perhaps there is a property that the video card inherits from the OS which persists on reboot, but not from a cold start.

I've been scratching my head about this for months. It's a low priority concern, but it does pique my tinkerer's curiosity and it would be nice to get my GRUB background image back.

---

