---
title: "Important change - install problem"
date: 2007-10-21
forum: Ubuntu Brainstorm
---

### Post by dolomite792 on 2007-10-21
Here's one that really pisses me off, say you have a video card that isn't supported.
(Such as an Nvidia)

Next so your stuck with having to install ubuntu under that crappy *** safe graphics mode.  (Shouldn't Ubuntu be able to scan your windows partiton and pull the Nvidia driver from it incase you don't have internet access?  Or is a special Nvidia driver needed from the ubuntu repos?)

So then you go to install once fully booted off of cd

Guess what?

You can't f-ing hit next or see the bottom of the install window.  Nor can you move it high enough to see those buttons.

The best part is, is that you can't resize the f-ing window!!!

So not only do new users with new hardware find themselves unable to get proper video support from the first load, they won't even be able to see the bottom of the installer.

Is this a known issue?

Cause it should be with laptop users.

Its happened to me quite a few times, even on older laptops.

There's a post in the blueprint for hardy heron asking what does your everyday user want?

How about an operating system they can actually install? Lol

---

### Post by FrankQuist on 2007-10-21
I have the same things when using the LiveCD with my Nvidia card. It boots into a low resolution because the restricted drivers weren't loaded. Enabling these at LiveCD time is quirky or impossible (I can restart the x server for the drivers but it doesn't work). 

The real issue here (even though the restricted drivers process not working well together with the LiveCD idea is also an issue) is that the install window does not degrade gracefully on lower resolutions. This is actually an issue with a lot of GNOME applications on a low resolution, it seems.

---

### Post by dolomite792 on 2007-10-21
Yes Exactly!

I tried to load the restricted drivers and it didn't work at all, it crashed and went blank.

I would so love to see this one fixed as it is integral and seems like a fairly simple fix.

Thanks for your reply!

---

### Post by FrankQuist on 2007-10-22
Tip for you btw, you can use the alt key to drag windows combined with the left mouse button. You can use the installer/partitioner that way on low resolutions.

---

### Post by dolomite792 on 2007-10-25
wrong spot...

---

### Post by pdlethbridge on 2007-10-25
Have you tried alt f2 and in the box put ***_[COLOR="Navy"]gksudo nvidia-settings[/COLOR]_***?

---

### Post by 23meg on 2007-10-25
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/38442](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/38442)

---

