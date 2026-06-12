---
title: "Xorg.conf.d not picking up correct resolution"
date: 2017-04-12
forum: Ubuntu/Debian BASED
---

### Post by jlivin25 on 2017-04-12
System: HP N54 Microserver
OS: Kodibuntu (Description: Ubuntu 14.04.5 LTS)
Graphics Chip: NVIDIA
AMP: ONKYO TX-SR07

Hello Folks

I'm looking for some help to correctly configure my linux system to set up a preferred default screen resolution. I have an older Panasonic TV which has a native resolution 1360x768. Its at this resolution that all the colours look their best, there is no over/underscan and no adjustments needed to the picture.

My Linux system is hooked up with the rest of my AV media equipment to an Onkyo AMP.

If I turn my AMP and TV on and then boot the PC, the correct resolution is used in the KODI instance (1360x768) which is what I had hoped to achieve.

The issue i'm having is that if I turn the linux system on without having the amp or the TV on the system is defaulting to a 1280x1080p resolution. If I then turn the TV on I have overscan, weird colours (etc). I can manually correct this. As I say above i'm booting kodibuntu so the system logs straight into a fullscreen kodi instance. Using the settings->system settings->display I can change the resolution back manually but I want to avoid this.

Doing a fair bit of digging around on the internet and I came across and older post here

[https://sammart.in/2012/05/29/enabling-resolutions-in-ubuntu-12-04-lubuntu-12-04/](https://sammart.in/2012/05/29/enabling-resolutions-in-ubuntu-12-04-lubuntu-12-04/)

Essentially I used gtf to create a modeline for my resolution and popped this into file called [FONT=arial black]```
/usr/share/X11/xorg.conf.d/10-monitor.conf
```[/FONT]

full file looks like this
```

Section "Monitor"
  Identifier "Monitor0"
  Modeline "1360x768_60.00"  84.72  1360 1424 1568 1776  768 769 772 795  -HSync +Vsync
#  Modeline "1920x1080_60.00"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync
#  Modeline "1280x720_60.00"  74.48  1280 1336 1472 1664  720 721 724 746  -HSync +Vsync
EndSection
Section "Screen"
  Identifier "Screen0"
  Device "HDMI-0"
  Monitor "Monitor0"
  DefaultDepth 24
  SubSection "Display"
    Depth 24
    Modes "1360x768_60.00"
#   Modes "1920x1080_60.00"
#   Modes "1280x720_60.00"
  EndSubSection
EndSection

```

xrandr output for tv ON and AMP on then boot is:
```
Screen 0: minimum 8 x 8, current 1360 x 768, maximum 8192 x 8192DVI-I-0 disconnected primary (normal left inverted right x axis y axis)
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected 1360x768+0+0 (normal left inverted right x axis y axis) 160mm x 90mm
   1360x768       60.0*+
   1920x1080      59.9     50.0     30.0     25.0     24.0     60.1     60.0     50.0
   1280x720       60.0     59.9     50.0
   1024x768       75.0     70.1     60.0
   800x600        75.0     72.2     60.3
   720x576        50.0
   720x480        59.9
   640x480        75.0     72.8     59.9
   480x576        50.0
   480x480        59.9
   411x576        50.1
   411x480        60.0
```


xrandr output for boot then turn tv ON and amp ON is:

```
Screen 0: minimum 8 x 8, current 1280 x 720, maximum 8192 x 8192DVI-I-0 disconnected primary (normal left inverted right x axis y axis)
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected 1280x720+0+0 (normal left inverted right x axis y axis) 708mm x 398mm
   1920x1080      60.1 +   59.9     50.0     60.0     50.0
   1280x720       60.0*    59.9     50.0
   720x576        50.0     50.1
   720x480        59.9     60.1
   640x480        59.9
   480x576        50.0
   480x480        59.9
   411x576        50.1
   411x480        60.0
```

Can anyone advise me if I'm using the correct method, if not where should I look.......if I am is there a way of forcing/ensuring the same resolution is set however the linux system starts:confused:

I'm on a headless machine so trying to do everything via command line (figure its the best way to learn) :D

---

### Post by howefield on 2017-04-13
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

