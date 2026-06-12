---
title: "Adobe Reader 'full screen' blocks Ubuntu's screensaver"
date: 2009-01-21
forum: The Cafe
---

### Post by Mark_in_Hollywood on 2009-01-21
I was reading a .pdf when the Gnome Screensaver would not un-save when I moved the mouse around. The space-bar key did restore power to the monitor (CRT). I was reading the .pdf in full screen mode, so I don't know if this would happen otherwise.

This isn't much a a problem, and I'm only putting this info up, FYI.

---

### Post by Mr. Picklesworth on 2009-01-21
I've seen that happen with a lot of software, lately. Specific applications just grab all mouse events then proceed to hang, leaving me with an unusable desktop until I can kill the offending application with whatever input methods remain.

---

### Post by FuturePilot on 2009-01-21
I don't think that's Adobe Reader's fault, sounds like this bug.
[https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/273142]("https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/273142")

> **Mr. Picklesworth said:**
> I've seen that happen with a lot of software, lately. Specific applications just grab all mouse events then proceed to hang, leaving me with an unusable desktop. Something is seriously broken with the X window system for that to happen.
I think that's a feature, not a bug&#8482;. I'm pretty sure you can only have one thing grabbing the input at a time.

---

