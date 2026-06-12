---
title: "2D animation and Wacom"
date: 2009-03-28
forum: System76 Support
---

### Post by NerdcoreSteve on 2009-03-28
I am using a cool 2D animation program called [Pencil]("http://www.pencil-animation.org/") with my Wacom tablet. The pencil tool is pressure sensitive but the eraser tool is not. I've not got much luck with their forums so I thought I might ask here. Is there anything wrong with this xorg file? It works just fine with GIMP.

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom" # USB ONLY?
  Option        "Type"          "stylus"
  Option        "USB"           "on"               # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom" # USB ONLY?
  Option        "Type"          "eraser"
  Option        "USB"           "on"               # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom" # USB ONLY?
  Option        "Type"          "cursor"
  Option        "USB"           "on"               # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"
  Option        "Device"        "/dev/input/wacom"    # USB ONLY
  Option        "Type"          "pad"
  Option        "USB"           "on"                  # USB ONLY
EndSection

Section "ServerLayout"
  Identifier    "Default Layout"
  Screen        "Default Screen"
  InputDevice   "stylus"  "SendCoreEvents"
  InputDevice   "eraser"  "SendCoreEvents"
  InputDevice   "cursor"  "SendCoreEvents" # For non-LCD tablets only
EndSection

---

### Post by NerdcoreSteve on 2009-03-28
I forgot to mention I am using an intuous.

---

### Post by thomasaaron on 2009-03-28
Have a look here...
[https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

...and here...
[http://ubuntuforums.org/showthread.php?t=25151](http://ubuntuforums.org/showthread.php?t=25151)

---

### Post by muhkayoh on 2009-07-09
Hello,

I'm cross-posting this from the Pencil forum on the off-chance that anybody here has a solution.  Thanks in advance.

Matt

> I've lost pressure sensitivity somehow in Pencil under recent versions of Ubuntu.  I run Ubuntu 8.10 (32bit) on my laptop and 9.04 (also 32bit) on my desktop.  Pressure sensitivity is missing in both.  I've verified that the pressure box is checked.  Pressure also works as expected in every other program (Gimp, Inkscape, etc.).  It used to work for me in Pencil back when I had Ubuntu 8.04, but now it doesn't.  I've tried both the more recent 0.4.4b and the older 0.4.3b packages.  Neither one works with pressure.

I'm hesitant to fiddle with my xorg.conf file since my Wacom (Graphire 3) works beautifully under all other packages but Pencil, but if anybody has a specific fix, I'd love to hear it.

Thanks,

Matt

---

