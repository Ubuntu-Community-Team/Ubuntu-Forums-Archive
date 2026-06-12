---
title: "Maya 8 Display Garbage - Xorg Driver??"
date: 2009-06-20
forum: Ubuntu Studio
---

### Post by Kat of Zion on 2009-06-20
I have been using Maya 8 for a while on my Kubuntu Hardy Heron laptop.  While I am aware that an ATI Radeon 200M Xpress vid card is not a superior video card, I have not had any glitches with Maya...

...until now
[http://www.youtube.com/watch?v=BCFmEF0mPdw](http://www.youtube.com/watch?v=BCFmEF0mPdw)

I did try and roll back the Xorg flgrx driver to see if one of my newer driver upgrades is what started this but to no avail.  Any ideas?

---

### Post by Kat of Zion on 2009-06-20
Update: Running Maya in command line, I get this error upon crash:

X Error of failed request: BadMatch (invalid parameter attributes)
Major opcode of failed request: 1 (X_CreateWindow)
Serial number of failed request: 168173
Current serial number in output stream: 168175


Is this familiar to anyone?

---

### Post by Kat of Zion on 2009-07-03
Update (well, not really): Things are still giving me garbage on my screen with Maya 8 on my Kubuntu Hardy Heron install. On my partner's Hardy Heron (newer with a Radeon 8800G), mostly everything behaves as it should with no garbage. The only glitch he has is that sometimes if he opens a document anew and activates the Outliner, Xorg reboots, bringing him back into the computer logon.  Are these 2 things even related? o.O

---

### Post by Kat of Zion on 2009-07-04
Solution found.  Although my solution was not found here specifically, I figured for search purposes, that I post the solution below.  Thanks to everyone who made suggestions! :)

After following instructions here:
[https://help.ubuntu.com/community/RadeonXpress](https://help.ubuntu.com/community/RadeonXpress)

I went into the xorg.conf and made one change:

```
Section "Extensions"
# Changed Composite from Enable to Disable to allow Maya to work without screenglitches. 7-4-09
Option "Composite" "Disable"
Endsection

So, my total xorg file reads the following:

CODE
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "aticonfig-Screen[0]" 0 0
    InputDevice    "Synaptics Touchpad"
EndSection

# Video Device configuration

Section "Screen"
    Identifier       "aticonfig-Screen[0]"
    Device           "aticonfig-Device[0]"
    Monitor          "aticonfig-Monitor[0]"
    DefaultDepth     24
    SubSection "Display"
        Viewport  0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier  "Default Screen"
    Device      "Configured Video Device"
    Monitor     "Configured Monitor"
    DefaultDepth     24
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]"
    Driver      "fglrx"
    Option      "DRI" "True"
    Option      "GARTSize" "64"
EndSection

Section "Device"
    Identifier  "Configured Video Device"
    Driver      "radeon"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "Configured Monitor"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "DRI"
    Mode         0666
EndSection

Section "Extensions"
        # Changed Composite from Enable to Disable to allow Maya to work without screenglitches. 7-4-09
    Option         "Composite" "Disable"
Endsection

Section "Files"
EndSection

# Input Device Configuration

Section "InputDevice"
    Identifier  "Generic Keyboard"
    Driver      "kbd"
    Option        "XkbRules" "xorg"
    Option        "XkbModel" "pc105"
    Option        "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier  "Configured Mouse"
    Driver      "mouse"
    Option        "CorePointer"
EndSection

Section "InputDevice"
    Identifier  "Synaptics Touchpad"
    Driver      "synaptics"
    Option        "SendCoreEvents" "true"
    Option        "Device" "/dev/psaux"
    Option        "Protocol" "auto-dev"
    Option        "HorizEdgeScroll" "0"
EndSection
```

---

