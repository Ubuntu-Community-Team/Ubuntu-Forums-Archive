---
title: "Touchpad scroll in Windows 7"
date: 2009-10-13
forum: System76 Support
---

### Post by retrovertigo on 2009-10-13
I'm dual-booting with Windows 7 now on a Serval Pro, and while touchpad scrolling works in Linux, it does not in Windows.  In the Device Manager it shows up as a "PS/2 Compatible Mouse".

Any idea what the make/model number is so that I can search for an appropriate driver?

---

### Post by retrovertigo on 2009-10-13
Did a bit more googling and found that the Synaptics drivers for Vista work perfectly well.  Tried them and scrolling now works.

[http://www.synaptics.com/support/drivers](http://www.synaptics.com/support/drivers)

---

### Post by Lee_Machine on 2009-10-13
Installing the Synaptics driver is what I had to do on my Pangolin. I had no idea that there were so many things the touchpad could do. It has the same features in Linux, it just requires editing the xorg config file.

---

### Post by thomasaaron on 2009-10-14
Lee Machine. Have you gotten two-finger scrolling working on your Pangolin?

---

### Post by Lee_Machine on 2009-10-14
I have not. In Karmic under mice settings there is an option for two finger scrolling, but it does not work.

Even when **Option "VertTwoFingerScroll" "true"** is added in xorg for the mouse input device it does not work.

I even tried **Option "VertTwoFingerScroll" "1"**

I cannot remmember if under Windows in the Synaptics settings if there is a two finger scroll option. I'll have to look, and post that later.

I think it might just be this model. I have seen two finger scrolling work on other snaptics touchpads with ubuntu. 

For ease of use for extra synaptics touhpad fuctionality I found this cool UI called qSynaptics.

[http://qsynaptics.sourceforge.net/](http://qsynaptics.sourceforge.net/)

It looks like this is no longer in active devel as there have not been any updates for almost a year.

Also new in Karmic in the mice settings is the option to disable the trackpad while typing. I dont know what the default time is, but it's not long enough for me. So I set it to 3 seconds.

syndaemon -i 3 -d

Here is a good how to.

[http://ubuntuforums.org/showthread.php?t=271052&highlight=disable+touchpad+while+typing](http://ubuntuforums.org/showthread.php?t=271052&highlight=disable+touchpad+while+typing)




Has S76 gotten Two Finger Scrolling to work?

---

### Post by thomasaaron on 2009-10-15
No, we've not gotten it to work yet.

We used to use qsynaptics / gsynaptics for touchpad configuration on some older computers. Their functionality, however, was integrated into xserver, so they are no longer useful with current Ubuntu versions.

---

### Post by Lee_Machine on 2009-10-15
Yeah upon further tweaking I got circular scrolling to work, I find it to be more annoying, and it's evoked on accident too much. 

I was uber excited because I thought I got Two Finger Scrolling, but it turned out I just activated the left side to also be used for scrolling like the right side. :P

I kept on trying to tweek setting to see if it will work, but to no avail.

To see what each setting is, and what options are used I run

synclient -l

I don't know enough about this to say if its a hardware incompatible issue, or a software issue, maybe both?

I give up for now, :confused:

---

### Post by Lee_Machine on 2009-10-15
WAIT!!

I tried one last thing at it worked!!

Here is my xorg.conf

Section "InputDevice"
Driver "synaptics"
Identifier "touchpad"
Option "Device" "/dev/psaux"
Option "VertTwoFingerScroll" "1"
Option "Protocol" "auto-dev"
Option "LeftEdge" "1700"
Option "RightEdge" "5300"
Option "TopEdge" "1700"
Option "BottomEdge" "4200"
Option "FingerLow" "25"
Option "FingerHigh" "30"
Option "MaxTapTime" "180"
Option "MaxTapMove" "220"
Option "VertScrollDelta" "100"
Option "MinSpeed" "0.09"
Option "MaxSpeed" "0.18"
Option "AccelFactor" "0.015"
Option "SHMConfig" "on"
Option "Emulate3Buttons" "on"

EndSection
 

and here is my output of synclient -l

 LeftEdge                = 1752
    RightEdge               = 5192
    TopEdge                 = 1620
    BottomEdge              = 4236
    FingerLow               = 24
    FingerHigh              = 29
    FingerPress             = 255
    MaxTapTime              = 180
    MaxTapMove              = 221
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 1
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 280
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 5
    HorizScrollDelta        = 50
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 0
    MinSpeed                = 0.4
    MaxSpeed                = 0.7
    AccelFactor             = 0.132
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 29
    EdgeMotionMaxZ          = 159
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 401
    EdgeMotionUseAlways     = 1
    UpDownScrolling         = 1
    LeftRightScrolling      = 1
    UpDownScrollRepeat      = 1
    LeftRightScrollRepeat   = 1
    ScrollButtonRepeat      = 100
    TouchpadOff             = 1
    GuestMouseOff           = 0
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 0
    RBCornerButton          = 3
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 2
    ClickFinger1            = 1
    ClickFinger2            = 1
    ClickFinger3            = 1
    CircularScrolling       = 1
    CircScrollDelta         = 0.078
    CircScrollTrigger       = 1
    CircularPad             = 0
    PalmDetect              = 0
    PalmMinWidth            = 10
    PalmMinZ                = 199
    CoastingSpeed           = 0
    PressureMotionMinZ      = 29
    PressureMotionMaxZ      = 159
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    GrabEventDevice         = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    JumpyCursorThreshold    = 0

I also have two finger scrolling checked under Mouse settings in the Touchpad tab.

Two finger scrolling is not smooth like on a macbook, but it works. Right now it requires the curser to be still for 2 seconds, then use two fingers.
I know the xorg settings can be tweeked to make it smoother, but I'm just gonna leave it for now to make sure you guys can reproduce. 


Do I get a free computer for this? :P

---

