---
title: "Sticky mouse button"
date: 2010-09-08
forum: System76 Support
---

### Post by asoundmove on 2010-09-08
Hi all,

I have come across a strange mouse issue. The left button seems to stick (I have a Logitech wireless mouse on my brand new System76 with Ubuntu 10.04).

The effect or symptom of this issue is that I can't use the mouse for things such as switching viewports, closing a window, changing to a different window... The cure is to right click (or left click with the touchpad) and then keep going until the problem occurs again (which can be very frequent at times, so much so that the computer becomes virtually unusable). In fact it also affects how X reacts to keyboard events (again I noticed this when trying to switch viewports (I use Expo), with keyboard shortcuts such as Super-Shift-Right and other similar shortcuts).

I saw information about the same issue in different places, but the problem seems to be dismissed.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-mouse/+bug/444674](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-mouse/+bug/444674)
[http://ubuntuforums.org/showthread.php?t=1297928](http://ubuntuforums.org/showthread.php?t=1297928)
[http://ubuntuforums.org/showthread.php?t=1449443&highlight=left+mouse+button+stuck+lucid](http://ubuntuforums.org/showthread.php?t=1449443&highlight=left+mouse+button+stuck+lucid)

I'd love to hear of a fix if any exists or register this as a bug for correction in 10.04.

Regards,
asm.

---

### Post by asoundmove on 2010-09-08
I discovered an older thread reporting similar issues :
[http://ubuntuforums.org/showthread.php?t=259103](http://ubuntuforums.org/showthread.php?t=259103)

I have a suspicion (unproven yet) that the sticky mouse problem only manifests itself when a given application has started. Right now I'm having no issues and I'm running one instance each of Skype, Pidgin, Firefox, Thunderbird, Gnome-terminal, Open Office writer.

I try a few options and report.

So long,
asm.

---

### Post by isantop on 2010-09-09
Yep, keep us updated. We're looking for solutions here, but we're not seeing this across the board.

It may also be the mouse itself. Try a different mouse to see if it works. 

If you get the same issues with a different mouse, it may be time to try out the Ubuntu 10.10 beta to see if it will be fixed for maverick.

---

### Post by zitch on 2010-09-09
I've noticed this too, and it seems related to how I type on the keyboard and my palm brushes against the touchpad and when I have "Enable mouse clicks with touchpad" turned on.  Basically, the symptoms seem to be that the trackpad gets stuck in "text-select" mode, and no amount of clicking on the external mouse buttons seem to get out of it (left click didn't seem to do anything, while right-click brings up the context menu but still doesn't release the text-selection).  I've only linked it to the trackpad when tapping on it or pushing the left trackpad button which seems to get the trackpad out of the click-and-drag mode.

I can't seem to replicate how it happens, but you can simulate it by having an external mouse plugged in, having your trackpad on, do a "click and drag" select of some text, but do not release the button, then try to use the external mouse to do stuff.  As long as you have the trackpad button held down, trying to click on menus and what-not on the external mouse would be an exercise in frustration.  

You end up doing stuff like accidentally create folders that you can't seem to delete, accidentally overwrite text that got highlighted as you're typing, and what not. 

I've seemed to eliminate this issue for myself by either turning off the "Enable mouse click with touchpad" options in Mouse Preferences or by disabling the touchpad using FN-F1 when I'm using an external mouse.  As it is, I don't like the tap functionality of touchpads in general, so I've gladfully disabled that functionality.  Also, taking care not to brush up on the touchpad while typing would work as well.

---

### Post by El King on 2010-09-20
I have the same problem on Ubuntu 10.10 Beta 1. If i increase/decrease the volume using the volume button on my keyboard (Microsoft Digital Media Keyboard 3000) i completely loose the left mouse click functionality! I can however right click. The only solution is to do a reboot using keyboard shortcuts.

---

### Post by Chris1274 on 2010-09-20
This isn't just a System76 issue. It happens to me on my Dell Inspiron 1440 laptop with a Logitech mouse plugged in.

---

### Post by HopfAlgebra on 2010-09-28
> **El King said:**
> I have the same problem on Ubuntu 10.10 Beta 1. If i increase/decrease the volume using the volume button on my keyboard (Microsoft Digital Media Keyboard 3000) i completely loose the left mouse click functionality! I can however right click. The only solution is to do a reboot using keyboard shortcuts.

Yes, I have the same problem. I upgraded recently from 10.4 to 10.10 Beta. Before that the special buttons (volume, email, browser, logout buttons) of my Microsoft Digital Media Keyboard 1.0A were working perfectly. Now, pressing one of them causes the left mouse button to get stuck (= no response). 
I also tried to swap left-right mouse button behaviour in the preferences (like for left-hander), but then the right mouse button gets stuck. So something is screwed-up in the logical behaviour of the system.

Any suggestion ?

P.S.: It seems that the problem found its way to launchpad:  [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/636311](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/636311)

and to other threeads like [http://ubuntuforums.org/showthread.php?t=1573294](http://ubuntuforums.org/showthread.php?t=1573294)

---

### Post by M1GEO on 2010-11-20
> **El King said:**
> I have the same problem on Ubuntu 10.10 Beta 1. If i increase/decrease the volume using the volume button on my keyboard (Microsoft Digital Media Keyboard 3000) i completely loose the left mouse click functionality! I can however right click. The only solution is to do a reboot using keyboard shortcuts.

Just for the record, I have the same keyboard to yourself, and I fix the issue by unplugging the keyboard from USB port, clicking the mouse until it returns to normal, and then reconnecting the keyboard.  Greatly annoying, but saves you restarting the computer.

Does anyone know of a solution to this?

---

### Post by keithwwalker on 2011-06-18
I have a very similar issue.
I thought it was only when firefox is running, but I have been able to replicate the issue with a very simple test.

This issue is intermittent and was a problem in 10.04, went away, upgrade to 10.10 and 11.04 and still have it.

The best way I can describe the issue is that it seems that the left mouse click is not working.  

BUT, it is working, only that the mouse cursor position is actually frozen and is stuck in one (invisible) place.  This is not readily apparent, because the mouse cursor is still moving and visible, but relative to the left mouse click, it thinks it is in the old frozen position.

It took a long time for me to realize this, it is like proving a ghost is in a room, whenever you are NOT in the room, lolz.

So that the effect is if you are left clicking, or double clicking on what you think is an active button or field and nothing registers, because the left button click thinks it is somewhere else.

The test which proves this is to open:
Preferences
Mouse

Then proceed to the test area for double clicking the light bulb test for the mouse.  Once I am successful in double or single clicking the mouse (indicated by the lightbulb turning half or full on), I then go to click on the 'close' button, but the click doesn't register.  BUT the single and double clicks will turn the lightbulb on and off!  No other fields or buttons can be activated.

Is there a way to shoot a screen shot movie of this phenomenon?  Perhaps then, people will be able to watch the movie and back deduct what is going on.

Similar to asoundmove, I can right click and this seems to reset the mouse with varying degrees of success.
Please help!  I don't wanna go back to windows...

Another observation is that my scroll wheel often doesn't work, but when it does, the left click issue goes away totally.

Keith Walker



> **asoundmove said:**
> Hi all,

I have come across a strange mouse issue. The left button seems to stick (I have a Logitech wireless mouse on my brand new System76 with Ubuntu 10.04).

The effect or symptom of this issue is that I can't use the mouse for things such as switching viewports, closing a window, changing to a different window... The cure is to right click (or left click with the touchpad) and then keep going until the problem occurs again (which can be very frequent at times, so much so that the computer becomes virtually unusable). In fact it also affects how X reacts to keyboard events (again I noticed this when trying to switch viewports (I use Expo), with keyboard shortcuts such as Super-Shift-Right and other similar shortcuts).

I saw information about the same issue in different places, but the problem seems to be dismissed.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-mouse/+bug/444674](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-mouse/+bug/444674)
[http://ubuntuforums.org/showthread.php?t=1297928](http://ubuntuforums.org/showthread.php?t=1297928)
[http://ubuntuforums.org/showthread.php?t=1449443&highlight=left+mouse+button+stuck+lucid](http://ubuntuforums.org/showthread.php?t=1449443&highlight=left+mouse+button+stuck+lucid)

I'd love to hear of a fix if any exists or register this as a bug for correction in 10.04.

Regards,
asm.

---

### Post by thomasaaron on 2011-06-20
keithwwalker, this doesn't sound like something System76 can fix, but it sounds like it is well known across the board.

I assume you are still  using the same wireless mouse? Does it happen with a USB mouse too? What about a different model wireless mouse?

---

### Post by eablola on 2012-04-05
Hi, I have recently switched from Mac OS X to Ubuntu 11.10 and I am encountering this intermittent issue as well.  I was wondering if anyone found the solution yet?

I'm experimenting with different mouse/touchpad settings to see if it would help.

---

