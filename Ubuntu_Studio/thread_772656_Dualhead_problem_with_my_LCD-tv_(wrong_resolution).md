---
title: "Dualhead problem with my LCD-tv (wrong resolution)"
date: 2008-04-28
forum: Ubuntu Studio
---

### Post by warelf on 2008-04-28
Hey, been trying for days now to get my resolution right on my LCD-tv, but it stops at 1280x768 and not 1360x768 as it should! think i have written 200 versions of the xorg.conf without luck. 

I'm posting my xorg.conf here, and hope someone can point me in the right direction :)

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" LeftOf "Screen1"
    Screen      1  "Screen1" 0 0
    Option      "Clone" "On"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
  #  Option         "Xinerama" "false"
  #  Option        "Clone" "true"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LPL"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Generic LCD Display"
    ModelName      "LCD Panel 1366x768"
    Option          "IgnoreEDID"
    Option          "ConnectedMonitor" "CRT-0"
    HorizSync       31.5 - 67.5
    VertRefresh     56.0 - 65.0
    Modeline "1366x768@54" 74.68 1360 1392 1672 1704 768 784 791 807
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600M GS"
    BusID       "PCI:1:0:0"
    Screen         1
EndSection


Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600M GS"
    BusID          "PCI:1:0:0"
    Option         "ConnectedMonitor" "CRT-0"
    Option         "NoLogo" "1"
  #  Option     "Metamodes" "CRT-0: 1360x768"
#    Screen          0
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection "Display"
        Depth   24
        Modes   "1280x800"
    EndSubsection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    SubSection "Display"
        Viewport        0 0
        Depth 24
        Modes   "720p" "1368x768" "1360x768" "1280x768"
    EndSubsection
EndSection
   

Can anyone see why this is not working? In my xorg log it just says that it removes the modes 1368 and 1360 etz.

---

### Post by r76 on 2008-05-18
Just a thought until someone cleverer comes along as I don't know anything about xorg, but I see you have an nvidia card - have you tried the GUI package nvidia-settings from the repos?  I always use that app to set up my TV-out.

---

### Post by warelf on 2008-05-18
Yeah have tried using the nvidia-settings GUI, but that just finds my tv to be 640x480 or something :(

---

### Post by thorgal on 2008-05-18
where did you get the LCD modeline from ?

if I run gtf, it gives me

Modeline "1368x768@54"  76.39  1368 1432 1576 1784  768 769 772 793  -HSync +Vsync

---

