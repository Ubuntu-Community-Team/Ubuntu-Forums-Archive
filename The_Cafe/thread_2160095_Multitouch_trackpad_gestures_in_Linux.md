---
title: "Multitouch trackpad gestures in Linux"
date: 2013-07-05
forum: The Cafe
---

### Post by u-noob-tu on 2013-07-05
I just got a lightly used Lenovo ThinkPad X220 for only $200 (it was going to be scrapped despite being in perfect condition) and I love it so far, but I was curious about gesture support in Linux. I have installed Xubuntu on my laptop, and out of the box the only gesture I can find is two finger scrolling and two finger tapping. What I'm really looking for is is swipe gesture support, particularly in a browser (e.g. two finger swipe left to go back one page, etc.). I know my laptop has a Synaptics trackpad, but I don't know what it supports as far as gestures. I found a program called Touchegg that can create actions for gestures but I'm having trouble getting it to work.

---

### Post by Copper Bezel on 2013-07-05
I'm using Touchégg myself. I never bothered with it until I got a trackpad capable of three- and four-finger events, and its pinch and rotate gestures are finicky to the point of nonfunctional (and I think "pinch in" is further actually broken, so that it reports "pinch out) but two-finger drags seemed to work tolerably well. (I gave them back to Synaptics for other reasons.) It's still the go-to gesture catcher for Linux. Where are you running into trouble?

Should warn you that if you use two-finger drag left and right for browser functions, you'll almost inevitably trigger them sometimes by accident while scrolling, which *could* become just irritating enough to not be worth the bother (I haven't had *too* much trouble with this, but it's worth keeping in mind.)

You can also use Touchégg to check which gestures your trackpad can actually detect. By default, Synaptics is going to catch all two-finger events, so you need to use synaptics -l to see what two-finger events are enabled (right click, scroll, etc.) and switch them off. (You'll need to set them back up as events through Touchégg to get them back, but this shouldn't be too much a hangup.) However, it'll read three- and four-finger events out of the box, so you can run it from a terminal, where it'll give you an interface to see whether or not it responds when you use those gestures.

---

### Post by u-noob-tu on 2013-07-05
When I run Touchegg from the terminal, it tells me to make a gesture to see if it is recognized. The problem is that no gesture I make is recognized, not even a tap. Not sure what the deal is.

Also, the command "synaptics -l" doesnt work on my system.

---

### Post by Copper Bezel on 2013-07-05
Damn, sorry - I meant *synclient -l* . You should get something a bit like this:

```
Parameter settings:    LeftEdge                = 130
    RightEdge               = 3130
    TopEdge                 = 96
    BottomEdge              = 1697
    FingerLow               = 1
    FingerHigh              = 1
    FingerPress             = 256
    MaxTapTime              = 180
    MaxTapMove              = 163
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 0
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = -74
    HorizScrollDelta        = -74
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 1
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.0537634
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 30
    EdgeMotionMaxZ          = 160
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 297
    EdgeMotionUseAlways     = 0
    TouchpadOff             = 0
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
    ResolutionDetect        = 1
    GrabEventDevice         = 1
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    HorizHysteresis         = 18
    VertHysteresis          = 18
    ClickPad                = 0
```

Then you can clear all the two-finger gestures you see - for me, it'd be this:
```
synclient ClickFinger2=0 TapButton2=0 VertTwoFingerScroll=0 HorizTwoFingerScroll=0
```
Now try running Touchégg again and see if it catches your two-finger gestures. Make sure you get all of them (the above command should actually work for you, too.) If you have synaptics catching any two-finger events, it'll intercept *all* of them, even if they're not assigned to anything. 

Unity intercepts three- and four-finger gestures, but Xfce doesn't, so if Touchégg isn't responding to them, then your trackpad doesn't support them. But after shutting off two-finger actions in synaptics, Touchégg *should* catch *those*.

---

### Post by u-noob-tu on 2013-07-05
Okay, "synclient -l" works and I cleared all two finger gestures and touchegg started working. It doesn't recognize anything more than two fingers, so I guess my touchpad doesnt support anything more than that. I was having trouble with "flicks" though, I couldnt get one to be recognized. What exactly is defined as a "flick"? I even looked in the config file for touchegg and couldnt find "flick" mentioned anywhere. I think a flick is the gesture I want to use in the browser to navigate back and forward between pages.

---

### Post by Copper Bezel on 2013-07-05
I don't think Touchégg *does *recognize flicks as separate from drags. It's limited to drags and taps, so if you don't have three- and four-finger support, you don't have a plethora of options. (And two-finger drag left and right is really useful as horizontal scrolling, for that matter.) Sorry. = / 

As for "flicks," I've not seen anything like that implemented on Linux. I think that in other systems, "flick" and "swipe" are the same thing, and they're essentially drags with a timeout ("flick" may be a shorter timeout, while "swipe" might require a longer drag.) Edge swipes are used in Ubuntu Touch, and that's just a single-finger drag coming in from the outside of the screen, but that doesn't apply to trackpads so much. Windows 8 uses edge swipes on the trackpad itself - entering the trackpad from one side or the other brings up the running apps or Charms bar - but again, I haven't seen this duplicated in Linux. (Too bad, too; it'd be nice for app or tab switching.)

I'm using three-finger drags left and right to switch tabs and down for "back" (along with up for "spread windows" from the shell.) It seems mostly reliable - I don't often accidentally go back when I mean to switch tabs or vice versa. So try the drags, and if that doesn't turn out to be reliable, you can always change everything back.

You'll also need a startup script to disable the synaptics two-finger event catching, like this:

```
#!/bin/bash
synclient ClickFinger1=1
synclient TapButton1=1
synclient ClickFinger2=0
synclient TapButton2=0
synclient ClickFinger3=0
synclient TapButton3=0
synclient HorizTwoFingerScroll=0
synclient VertTwoFingerScroll=0
```

Synclient settings don't persist - they're lost on logging out. I've not played with Xfce enough to know whether these settings might get reset under other circumstances; under Gnome or Unity, they get reset when the machine suspends and wakes, which requires a little configuring to get the script above to run again on wake, too. I don't know whether or not you'll have the same problem under Xfce.

---

