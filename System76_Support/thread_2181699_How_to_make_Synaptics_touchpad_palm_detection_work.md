---
title: "How to make Synaptics touchpad palm detection work?"
date: 2013-10-18
forum: System76 Support
---

### Post by moschops on 2013-10-18
I'm trying to make palm detection work for the touchpad of my Galago UltraPro - since I have to pound away at the keyboard (see my other posts) I seem especially prone to moving the mouse around with my palms between typing. 

I've already set the standard Ubuntu "Disable while typing" for the touchpad.  But once I stop typing it is still easy to move the mouse around with a stray palm press.

So far I've been playing with the Synaptics 'synclient' command line tool - I know this has some effect, I can enable and disable the touchpad completely.  Changing the three palm related settings doesn't seem to have any effect though.  My palms always work brilliantly just like a big finger...  Here is a typical invocation:

synclient PalmMinWidth=10 PalmMinZ=10 PalmDetect=1

docs for these settings from 'man synaptics' indicate PalmDetect is a boolean, PalmMinZ and PalmMinWidth should be 16 bit values.  I've tried making both really small, really big, big and small, small and big, and various other combinations.  No joy.

On the chance that one of my other settings is conflicting with palm detection here is my complete lists of settings as reported by synclient:

```
Parameter settings:
    LeftEdge                = 1766
    RightEdge               = 5386
    TopEdge                 = 1640
    BottomEdge              = 4496
    FingerLow               = 25
    FingerHigh              = 30
    MaxTapTime              = 180
    MaxTapMove              = 235
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    EmulateMidButtonTime    = 0
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = -107
    HorizScrollDelta        = -107
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 1
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.0373134
    TouchpadOff             = 1
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 2
    RBCornerButton          = 3
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 0
    ClickFinger1            = 1
    ClickFinger2            = 3
    ClickFinger3            = 0
    CircularScrolling       = 0
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
    PalmDetect              = 1
    PalmMinWidth            = 10
    PalmMinZ                = 200
    CoastingSpeed           = 20
    CoastingFriction        = 50
    PressureMotionMinZ      = 30
    PressureMotionMaxZ      = 160
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    ResolutionDetect        = 1
    GrabEventDevice         = 1
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    HorizHysteresis         = 8
    VertHysteresis          = 8
    ClickPad                = 1
    RightButtonAreaLeft     = 3576
    RightButtonAreaRight    = 0
    RightButtonAreaTop      = 4130
    RightButtonAreaBottom   = 0
    MiddleButtonAreaLeft    = 0
    MiddleButtonAreaRight   = 0
    MiddleButtonAreaTop     = 0
    MiddleButtonAreaBottom  = 0
```

Any ideas?

PS. I have just upgraded to 13.10 and reinstalled the System76 drivers - still no joy.

PPS. Those parameters only have "TouchpadOff = 1" because I have disable while typing.  If I add a sleep 2 before the dump it is 0 - further evidence that synclient is working properly.

---

### Post by isantop on 2013-10-18
When you installed the System76 Driver, did you (afterwards) go to System Settings > System76 Driver and click on "Restore"?

---

### Post by moschops on 2013-10-20
No I did not click on Restore - that would restore the system to its state when it was delivered right?  I don't want that.

---

### Post by jbelmonte on 2013-10-21
> **moschops said:**
> No I did not click on Restore - that would restore the system to its state when it was delivered right?  I don't want that.

Restoring the System76 driver will not restore your system to factory default. Getting the System76 driver to work is a two step process. Step one is the installation, which you have done. Step two is restoring (or activating) the driver.  I agree that the wording is a little confusing. Disclaimer: I do not work for System76, so my advice comes as an owner.

---

### Post by moschops on 2013-10-30
Thanks for the info - I agree the wording is confusing.  Very confusing.

I have since heard from System 76 that the do not support palm detection at the moment.  That kind of sucks.  

This wouldn't be such a huge issue for me but since the keyboard on the Galago Pro bites so much I really have to pound on it and try to ensure every keystroke is hard and from directly above.  That requires moving my hands around which brings my palms beneath the thumb in contact with the touch pad a lot.  Without palm detection it often renders using the keyboard at best "really frustrating" or at worst "I want to send this thing back it is driving me so crazy..."

'nuff said.

---

### Post by el_garicimo on 2014-05-10
I can't get my palm detection to work either, although according to xinput, it should be able to. I talk about it on this thread (which I admittedly may have hijacked a little) [http://ubuntuforums.org/showthread.php?t=2221912&highlight=Multitouch+Driver](http://ubuntuforums.org/showthread.php?t=2221912&highlight=Multitouch+Driver)

Quick [COLOR=#000000] palm detection work around--change the value of your AreaRightEdge variable in synaptics (if that is the driver running your touchpad) to be a little less then the Right Edge-- my Right Edge was 5382, so setting my AreaRightEdge to 5300 made it so that the very right most part of my clickpad (about a finger's width worth) is deactivate in terms of actuallymoving the pointer. If i click there though, it's still a right click, which is nice.[/COLOR]

[COLOR=#000000]By default, your AreaRightEdge is probably 0, which means it extends to infinity in that direction (uses the entire area of the clickpad). My clickpad is super big though, so I don't really mind the one finger width's reduction in width, and it solves my problem! [/COLOR]:smile:

---

