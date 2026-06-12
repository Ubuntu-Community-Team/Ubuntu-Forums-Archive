---
title: "Two-finger scroll w/Synaptics touchpad"
date: 2012-01-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by xyzzyman on 2012-01-17
This problem exists for me on all distro's I've tried (Ubuntu 11.04->12.04), Arch, Fedora 15 & 16, OpenSuse, Backtrack 5R1. 

Switching to two-finger scrolling in touchpad settings only disables side-scroll but doesn't enable two-finger scroll even after reboot. On all distro's this is fixed by using this 50-synaptics.conf file placed in the appropriate directory for that distro:
```
Section "InputClass"
  Identifier "touchpad catchall"
  Driver "synaptics"
  MatchIsTouchpad "on"
    # Enable touchpad
    Option "TouchpadOff"        "0"
    # Edge Limits
    Option "LeftEdge" "1752"
    Option "RightEdge" "5192"
    Option "TopEdge" "1620"
    Option "BottomEdge" "4236"
    # Speed
    Option "MinSpeed" "01"
    Option "MaxSpeed" "1.75"
    Option "AccelFactor" "0.0398089"
    # Pressure
    Option "FingerLow" "25"
    Option "FingerHigh" "30"
    Option "FingerPress" "256"
    # Tapping Detection
    Option "MaxTapTime" "180"             # 0 disables tap
    Option "MaxTapMove" "221"
    Option "MaxDoubleTapTime" "180"
    Option "SingleTapTimeout" "180"
    Option "ClickTime" "100"
    Option "FastTaps" "0"
    # Tapping as Buttons (number of fingers)
    Option "TapButton1" "1"
    Option "TapButton2" "2"
    Option "TapButton3" "3"
    # Tap Dragging
    Option "LockedDrags" "0"
    Option "LockedDragTimeout" "5000"
    # Tap Gesture Dragging
    Option "TapAndDragGesture" "1"
    # Corner Tap Buttons
    Option "RTCornerButton" "0"
    Option "RBCornerButton" "0"
    Option "LTCornerButton" "0"
    Option "LBCornerButton" "0"
    # Scrolling Edges
    Option "VertEdgeScroll" "on"
    Option "VertScrollDelta" "100"
    Option "HorizEdgeScroll" "0"
    Option "HorizScrollDelta" "100"
    # Circular Scrolling
    Option "CircularScrolling" "0"
    Option "CircScrollDelta" "0.1"
    Option "CircScrollTrigger" "0"
    # Two Finger Scrolling
    Option "VertTwoFingerScroll" "on"
    Option "HorizTwoFingerScroll" "on"
    # Corner Coasting
    Option "CornerCoasting" "0"
    Option "CoastingSpeed" "20"
    Option "CoastingFriction" "50"
    # Kernel Event Protocol
    Option "GrabEventDevice" "1"
    # Edge Ignore Boundaries
    Option "AreaLeftEdge" "0"
    Option "AreaRightEdge" "0"
    Option "AreaTopEdge" "0"
    Option "AreaBottomEdge" "0"
    # Trackstick
    Option "TrackstickSpeed" "40"
    # Circular Trackpad
    Option "CircularPad" "0"
    # Multi-function Buttons
    Option "ClickFinger1" "1"
    Option "ClickFinger2" "1"
    Option "ClickFinger3" "1"
    # Edge Movements
    Option "EdgeMotionMinZ" "29"
    Option "EdgeMotionMaxZ" "159"
    Option "EdgeMotionMinSpeed" "1"
    Option "EdgeMotionMaxSpeed" "401"
    Option "EdgeMotionUseAlways" "0"
    # Pressure Motion
    Option "PressureMotionMinZ" "29"
    Option "PressureMotionMaxZ" "159"
    Option "PressureMotionMinFactor" "1"
    Option "PressureMotionMaxFactor" "1"
    # Emulations
    Option "EmulateMidButtonTime" "75"
    Option "EmulateTwoFingerMinZ" "40"
    Option "EmulateTwoFingerMinW" "8"
    # Palm Detection
    Option "PalmDetect" "1"
    Option "PalmMinWidth" "10"
    Option "PalmMinZ" "199"
EndSection
```

The two necessary lines are:

```

    # Two Finger Scrolling
    Option "VertTwoFingerScroll" "on"
    Option "HorizTwoFingerScroll" "on"

```

This is with a pretty generic synaptic touchpad in an Acer Aspire 6930G, but I've had to do it on every other synaptic touchpad I've encountered in the last few years.

Is this something that other people have to do? If so I'd open up a bug as it would be nice as two finger scroll I've found to be much more convenient. Ubuntu already turns on mouse clicksw/touchpad while everyone else defaults to it off, so it's def something Ubuntu takes into consideration. At the very least it'd be nice for it to work when you change the button as opposed to having to edit a file even though synaptic touchpads seem more common than alps.

---

### Post by ronacc on 2012-01-17
good info , thanks .

---

### Post by xyzzyman on 2012-01-17
So I should take it that two-finger scroll doesn't work from the touchpad settings for you also?

---

### Post by ronacc on 2012-01-18
the only installs I've got on something with a touch pad is 10.04 on a notebook and Lubuntu 11.10 on a netbook ( eeepc 4g ) . I'll give it a try with the eee .

---

### Post by Ibidem on 2012-01-20
No real tweaks needed, Ubuntu 10.10 MM/12.04 PP/ Debian 6.0 Squeeze.
Thinkpad X100e, evdev driver; here's how I switch it on:
```
#!/bin/sh
xinput set-int-prop 'TPPS/2 IBM TrackPoint' 'Evdev Wheel Emulation' 8 1
xinput set-int-prop 'TPPS/2 IBM TrackPoint' 'Evdev Wheel Emulation Button' 8 2
xinput set-int-prop 'TPPS/2 IBM TrackPoint' 'Evdev Wheel Emulation Timeout' 8 200

xinput set-int-prop 'TPPS/2 IBM TrackPoint' 'Evdev Wheel Emulation Axes' 8 6 7 4 5
```

---

### Post by xyzzyman on 2012-01-20
> **Ibidem said:**
> No real tweaks needed, Ubuntu 10.10 MM/12.04 PP/ Debian 6.0 Squeeze.
Thinkpad X100e, evdev driver; here's how I switch it on:
```
#!/bin/sh
xinput set-int-prop 'TPPS/2 IBM TrackPoint' 'Evdev Wheel Emulation' 8 1
xinput set-int-prop 'TPPS/2 IBM TrackPoint' 'Evdev Wheel Emulation Button' 8 2
xinput set-int-prop 'TPPS/2 IBM TrackPoint' 'Evdev Wheel Emulation Timeout' 8 200

xinput set-int-prop 'TPPS/2 IBM TrackPoint' 'Evdev Wheel Emulation Axes' 8 6 7 4 5
```

??? This is regarding synaptics touchpads.

But even with a non synaptics touchpad, you still aren't able to use two-finger scroll without running those commands? The option in mouse settings in 11.10/12.04 may be broken for more than just synaptic then. I don't have much thinkpad experience, so I wasn't aware they were using a non synaptics or alps solution. If the option in mouse settings doesn't work for you on 12.04 without those commands let me know and I'll definitely be opening a bug report.

EDIT: I asked on launchpad under the gnome-control-center package about this, and if they would like me to open a bug report with them or possibly with X11 instead as putting just

```

 MatchIsTouchpad "on"
    # Enable touchpad
    Option "TouchpadOff"        "0"
    # Scrolling Edges
    Option "VertEdgeScroll" "on"
    Option "VertScrollDelta" "100"
    Option "HorizEdgeScroll" "0"
    Option "HorizScrollDelta" "100"
    # Two Finger Scrolling
    Option "VertTwoFingerScroll" "on"
    Option "HorizTwoFingerScroll" "on"
EndSection
```

Or some variation of that in 51-synaptics-quirks.conf allows synaptics pads to be switched between edge/two-finger in gnome-control-center.

---

### Post by Ibidem on 2012-01-20
This was the standard approach from some time back.
It's probably the console equivalent of selecting two-finger scroll. 
I have not bothered testing the GUI, since this works well (I have it in my X startup scripts) and doesn't take a GUI.
Also, my other computer never had two-finger scroll working with any GUI, using either driver (AOA150, Synaptics touchpad but claimed by evdev; Lucid Lynx/Lucid Puppy/Kuki = Jaunty)

The device I previously referred to is an "UltraNav", which is an IBM/Lenovo branded combo of a trackpoint & a Synaptics touchpad.
I've gotten the impression that evdev grabs most touchpads.

---

### Post by xyzzyman on 2012-01-20
It should work out of the box, especially when the option is included in the GUI. I understand side-scroll being default if X11 doesn't support both being on at the same time though. evdev was how I first made it work, so setting it in a .conf for X11 is probably doing the same thing. It may wind up being upstream though, idk. I'll just wait until gnome-control-center on launchpad gets back to me.

UPDATE: It's been known for a long time. [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/554980](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/554980) There's multiple bug reports as far back as 2010 on launchpad. gnome themselves back in july 2010 made the decision for it to enable it in a certain for a newer style of multitouch synaptic pads, but all older ones previous that use what xorg calls an 'emulated' two finger scroll, the option just fails gracefully and it's up to the end user to enable manually... It's already known on ubuntu's launchpad going back awhile so even though it's a big feature to be broken for new users hopefully they'll find the answer here on the forums. :)

---

