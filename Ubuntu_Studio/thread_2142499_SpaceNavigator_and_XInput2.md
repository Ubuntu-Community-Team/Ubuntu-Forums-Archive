---
title: "SpaceNavigator and XInput2"
date: 2013-05-05
forum: Ubuntu Studio
---

### Post by nwillis on 2013-05-05
I'm trying to figure out how to use a 3Dconnexion SpaceNavigator as a general-purpose XI2 input device.  For example, I'd like to have it available as an input controller in GIMP (2.8 on 12.10), so I could map it to scroll the canvas, zoom in and out, rotate, etc. etc. ....

I can get Udev to recognize it and assign it to the evdev driver.  However, XI2 assigns it as a slave to the Virtual Core pointer -- it's really not clear to me if that's what we want or not.  As it stands now, moving the controller seems to send mouse pointer events -- you can move the pointer U/D/L/R, but only while applying pressure; as soon as you let go it snaps back to dead center of the screen, regardless of where the pointer was beforehand.

Also, GIMP's "Input Controller" settings do not work.  I can add the navigator to the list of active controllers (on the right), but assigning actions does not work (i.e., you can make the assignment in the UI alright, but subsequently, even after a save, moving the controller doesn't execute the action, it keeps moving the mouse instead).  Well, slight correction -- assigning actions to *motion* events does not work; I can assign actions to the buttons just like you can to any mouse.  The "dump events for this controller" button does not capture any events either.

For a while I thought that perhaps I needed to have XI2 make the controller a separate pointer device (master), but when I did that GIMP didn't seem to see it at all.

Any help?

N
[ PS - just in case anyone wonders, I'm trying to do all this solely through X. I do *not* have 3dconnexion's drivers installed or spacenavd, or any other software that would contend with X for control of the device. ]

---

### Post by nwillis on 2013-05-10
I don't suppose someone with mod privileges would mind moving this to the General Help forum, would they?  Doesn't look like this forum is going to lead anywhere.  Thanks,
N

---

