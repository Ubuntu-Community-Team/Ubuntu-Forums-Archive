---
title: "Resolution is 4:3 and not Widescreen"
date: 2012-09-23
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by teejay17 on 2012-09-23
Quantal does not seem to detect my monitor and as a result I have 1024x768 as the only option. Any suggestions as to how to fix?
More importantly, why is the monitor not detected? This is the first time I've had issues with Ubuntu not detecting the right display.

---

### Post by VinDSL on 2012-09-23
Do you have the "mesa-utils" package installed?

---

### Post by teejay17 on 2012-09-25
> **VinDSL said:**
> Do you have the "mesa-utils" package installed?
Yes, I went ahead and installed this package, but I still have limited resolution and everything seems "stretched." Perhaps I am missing a step?

---

### Post by jerrylamos on 2012-09-25
Widescreen TV here, 1366x768 not detected by Ubuntu when using VGA cable.

So I have in home directory:
.xprofile
#!/bin/bash
xrandr --newmode "1366x768_60.00"   85.25  1366 1440 1576 1784  768 771 781 798 -hsync +vsync
xrandr --addmode VGA1 "1366x768_60.00"
xrandr --output VGA1 --mode "1366x768_60.00"

must be marked executable sudo chmod +x .xprofile

and also
/etc/X11/xorg.conf
```
Section "Monitor"
    Identifier      "External DVI"
    Modeline        "1366x768_60.00"   85.25  1366 1440 1576 1784  768 771 781 798 -hsync +vsync
EndSection
Section "Device"
    Identifier      "Intel Corporation N10 Family Integrated Graphics Controller"
    Driver          "Intel"
    Option          "Monitor-DVI-0" "External DVI"
EndSection
Section "Screen"
    Identifier      "Primary Screen"
    Device          "Intel Corporation N10 Family Integrated Graphics Controller"
    DefaultDepth    24
    SubSection "Display"
        Depth           24
        Modes   "1366x768" "1024x768" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Primary Screen"
EndSection
```

also marked executable.

Then I go into system settings displays/monitor settings, turn the netbook screen off, and select 1366x768 on the external monitor

Now where all those funny numbers came from is a bit of a mystery from dredging around Ubuntu forums.  Some of them can be found by doing
xrandr
if you have a linux that does recognize the monitor.

On a new install I'll get 800x600 or so, then do   
./.xrandr
which might get a usable screen, then copy in the /etc/X11/xorg.conf which hopefully might help on the next boot.

Since .xprofile and xorg.conf plus system settings works I don't fix it until the next time I'm in trouble.

---

