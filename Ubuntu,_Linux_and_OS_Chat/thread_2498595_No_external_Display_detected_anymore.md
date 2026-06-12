---
title: "No external Display detected anymore"
date: 2024-06-21
forum: Ubuntu, Linux and OS Chat
---

### Post by dfrusone on 2024-06-21
Dear support, after 1 year of working with ubuntu 22.04 i got a terrible problem. The external Display stopped working suddently. I Startet my second partition whit Windows, and it's working without problems. No Hardware issue.

i tried different fixes in the communities, but in all the other situations, the hdmi/usb c port is visible, but not in mine:

Please Help

xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1920 x 1080, current 1920 x 1080, maximum 1920 x 1080
default connected primary 1920x1080+0+0 0mm x 0mm
   1920x1080     77.00* 

sudo get-edid | parse-edid  
Place your finger on the fingerprint reader
This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
No EDID on bus 0
No EDID on bus 1
No EDID on bus 2
Looks like no busses have an EDID. Sorry!
Attempting to use the classical VBE interface

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
    Function unsupported
    Call failed

    VBE version 0
    VBE string at 0x0 "O\&#65533;."

VBE/DDC service about to be called
    Report DDC capabilities

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
    Function unsupported
    Call failed

Reading next EDID block

VBE/DDC service about to be called
    Read EDID

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
    Function unsupported
    Call failed

The EDID data should not be trusted as the VBE call failed
Error: output block unchanged
I'm sorry nothing was successful. Maybe try some other arguments
if you played with them, or send an email to Matthew Kern <pyrophobicman@gmail.com>.
Partial Read... Try again

inxi -G
Graphics:
  Device-1: Intel WhiskeyLake-U GT2 [UHD Graphics 620] driver: N/A
  Device-2: Realtek Integrated_Webcam_HD type: USB driver: uvcvideo
  Display: x11 server: X.Org v: 1.21.1.4 driver: X: loaded: vesa
    unloaded: fbdev,modesetting gpu: N/A resolution: 1920x1080~77Hz
  OpenGL: renderer: llvmpipe (LLVM 15.0.7 256 bits)
    v: 4.5 Mesa 23.2.1-1ubuntu3.1~22.04.2

lspci -k | grep  VGA
00:02.0 VGA compatible controller: Intel Corporation WhiskeyLake-U GT2 [UHD Graphics 620] (rev 02)

glxinfo | grep "OpenGL version"
OpenGL version string: 4.5 (Compatibility Profile) Mesa 23.2.1-1ubuntu3.1~22.04.2

---

### Post by coffeecat on 2024-06-21
Duplicate of [https://ubuntuforums.org/showthread.php?t=2498596](https://ubuntuforums.org/showthread.php?t=2498596) . Thread closed.

---

