---
title: "XF86TouchpadToggle pressed, but not working (need for hardware issue)"
date: 2024-01-15
forum: Ubuntu/Debian BASED
---

### Post by ruwolf on 2024-01-15
Hello.

(I use beautiful Debian+Ubuntu chimera a.k.a. cute kind of [FrankenDebian monster]("https://wiki.debian.org/DontBreakDebian#Don.27t_make_a_FrankenDebian"), but I am 999.999_999‰ sure, that it is absolutely irrelevant here. BTW, it works smoothly everywhere, yet.)
```

$ inxi -Sxxxrz
System:
  Kernel: 6.5.0-0.deb12.4-amd64 arch: x86_64 bits: 64 compiler: gcc v: 12.2.0
    clocksource: tsc Desktop: Xfce v: 4.18.1 tk: Gtk v: 3.24.36
    info: xfce4-panel wm: xfwm v: 4.18.0 vt: 7 dm: LXDM Distro: Ubuntu 23.10
    (Mantic Minotaur)
Repos:
  Packages: pm: dpkg pkgs: 1740
  Active apt repos in: /etc/apt/sources.list.d/debian_stable-backports.sources
    1: deb http://deb.debian.org/debian stable-backports main contrib non-free non-free-firmware
  Active apt repos in: /etc/apt/sources.list.d/debian_stable.sources
    1: deb http://deb.debian.org/debian stable stable-updates stable-proposed-updates  main contrib non-free non-free-firmware
    2: deb http://deb.debian.org/debian-security/ stable-security main contrib non-free non-free-firmware
  Active apt repos in: /etc/apt/sources.list.d/ubuntu_22.04_jammy.sources
    1: deb http://ftp.energotel.sk/pub/linux/ubuntu/ jammy jammy-security jammy-updates jammy-backports main universe multiverse restricted
  Active apt repos in: /etc/apt/sources.list.d/ubuntu_23.04_lunar.sources
    1: deb http://ftp.energotel.sk/pub/linux/ubuntu/ lunar lunar-security lunar-updates lunar-backports main universe multiverse restricted
  Active apt repos in: /etc/apt/sources.list.d/ubuntu_23.10_mantic.sources
    1: deb http://ftp.energotel.sk/pub/linux/ubuntu/ mantic mantic-security mantic-updates mantic-backports main universe multiverse restricted

```

My touch-pad sometimes autonomously press and hold pseudo-mouse key, so I sometimes need to turn it off before I will give it to manufacturer service inspection. (I assume that Debian or Ubuntu has no tools to test or calibrate such behaviour.)
```

$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              id=4    [slave  pointer  (2)]
&#9116;   &#8627; ASUE1201:00 04F3:3148                   id=11   [slave  pointer  (2)]
&#9116;   &#8627; ASUE1201:00 04F3:3148                   id=12   [slave  pointer  (2)]
&#9116;   &#8627; ASUE1201:00 04F3:3148                   id=13   [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             id=5    [slave  keyboard (3)]
    &#8627; Video Bus                               id=6    [slave  keyboard (3)]
    &#8627; Power Button                            id=7    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                        id=14   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            id=15   [slave  keyboard (3)]

```
I hope this is the touch-pad, but I am not sure, because it has also sense-point. BTW, it has real buttons on top and virtual on bottom of it.
```

$ xinput --list --long 12
ASUE1201:00 04F3:3148                       id=12    [slave  pointer  (2)]
    Reporting 8 classes:
        Class originated from: 12. Type: XIButtonClass
        Buttons supported: 12
        Button labels: "Button Left" "Button Middle" "Button Right" "Button Wheel Up" "Button Wheel Down" "Button Horiz Wheel Left" "Button Horiz Wheel Right" None None None None None
        Button state:
        Class originated from: 12. Type: XIValuatorClass
        Detail for Valuator 0:
          Label: Rel X
          Range: 0.000000 - 3184.000000
          Resolution: 31000 units/m
          Mode: relative
        Class originated from: 12. Type: XIValuatorClass
        Detail for Valuator 1:
          Label: Rel Y
          Range: 0.000000 - 1850.000000
          Resolution: 32000 units/m
          Mode: relative
        Class originated from: 12. Type: XIValuatorClass
        Detail for Valuator 2:
          Label: Rel Horiz Scroll
          Range: 0.000000 - -1.000000
          Resolution: 0 units/m
          Mode: relative
        Class originated from: 12. Type: XIValuatorClass
        Detail for Valuator 3:
          Label: Rel Vert Scroll
          Range: 0.000000 - -1.000000
          Resolution: 0 units/m
          Mode: relative
        Class originated from: 12. Type: XIValuatorClass
        Detail for Valuator 4:
          Label: Abs MT Tool Type
          Range: -1.000000 - -1.000000
          Resolution: 0 units/m
          Mode: relative
        Class originated from: 12. Type: XIScrollClass
        Scroll info for Valuator 2
          type: 2 (horizontal)
          increment: 73.000000
          flags: 0x0
        Class originated from: 12. Type: XIScrollClass
        Scroll info for Valuator 3
          type: 1 (vertical)
          increment: 73.000000
          flags: 0x0

```

I have installed only **xserver-xorg-input-libinput**, before post I added **xserver-xorg-input-evdev**, **xserver-xorg-input-synaptics** and others **xorg-inpit-*** (not all) and ***Tap touchpad to click***  has stopped working in **xfce4-mouse-settings** and is always turned off. More precisely, it stopped working for a gentle touch, for a strong press of touch area, that causes a click, it still works even it is not checked in xfce4-mouse-settings (where setting  ***Enable horizontal scrolling*** does not work in the same way).
```

$ synclient
Parameter settings:
    LeftEdge                = 127
    RightEdge               = 3057
    TopEdge                 = 99
    BottomEdge              = 1751
    FingerLow               = 25
    FingerHigh              = 30
    MaxTapTime              = 180
    MaxTapMove              = 162
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    EmulateMidButtonTime    = 0
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 73
    HorizScrollDelta        = 73
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 0
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.0543183
    TouchpadOff             = 0
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 0
    RBCornerButton          = 0
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 0
    TapButton2              = 0
    TapButton3              = 0
    ClickFinger1            = 1
    ClickFinger2            = 3
    ClickFinger3            = 2
    CircularScrolling       = 0
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
    CircularPad             = 0
    PalmDetect              = 0
    PalmMinWidth            = 10
    PalmMinZ                = 200
    CoastingSpeed           = 20
    CoastingFriction        = 50
    PressureMotionMinZ      = 30
    PressureMotionMaxZ      = 160
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    GrabEventDevice         = 0
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    HorizHysteresis         = 18
    VertHysteresis          = 18
    ClickPad                = 1
    RightButtonAreaLeft     = 1592
    RightButtonAreaRight    = 0
    RightButtonAreaTop      = 1517
    RightButtonAreaBottom   = 0
    MiddleButtonAreaLeft    = 0
    MiddleButtonAreaRight   = 0
    MiddleButtonAreaTop     = 0
    MiddleButtonAreaBottom  = 0

```

I have found old thread [Touchpad enable/disable key not working]("https://forums.debian.net/viewtopic.php?p=334576"), but I cannot find mentioned boolean value like **/org/gnome/desktop/peripherals/touchpad/** by **dconf-editor**. This editor show me there multiple key: value pairs, not single value. I do not know, how to copy them here or how to run such list/dump in terminal.

I have tried:
```

$ dconf dump ~/.config/dconf/

```
```

$ dconf list ~/.config/dconf/

```
but they print nothing even if there is file **user** with 5390 B; the same with **/etc/dconf/** directory (there is only empty **db/**).

I have looked at **xev** and it seems to work:
```

$ xev

KeyPress event, serial 38, synthetic NO, window 0x1600001,
    root 0x6ab, subw 0x0, time 27142613, (163,-20), root:(1034,460),
    state 0x10, keycode 199 (keysym 0x1008ffa9, XF86TouchpadToggle), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 38, synthetic NO, window 0x1600001,
    root 0x6ab, subw 0x0, time 27142613, (163,-20), root:(1034,460),
    state 0x10, keycode 199 (keysym 0x1008ffa9, XF86TouchpadToggle), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

**Xdotool** does nothing with it, too:
```

$ xdotool key XF86TouchpadToggle

```
(I.e. it still works after this command.)

So, why do Xorg+Xfce ignore **XF86TouchpadToggle** event? And how to set them to acceptance?

(I have posted this in [Debian Forum]("https://forums.debian.net/viewtopic.php?t=158037"), too, but it was moved to section without support because chimerism, so I do not anticipate answer there.)

---

