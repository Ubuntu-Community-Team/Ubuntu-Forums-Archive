---
title: "Developers, I challenge you to fix this before RC!"
date: 2012-09-24
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by DisappearingOak on 2012-09-24
Sorry about the thread title. I reported this bug quite a while ago and it's still present even in Quantal Beta 1 and no one seems to care. Please do something about it. Graphical glitches really hurt the user experience. It seems that whereas our arch-enemy Windows is released after so much testing and polishing, the good thing about it is that it's consistent on all hardware and provides a consistent experience. But I'm losing faith in Ubuntu because small bugs which affects few users go unnoticed. Maybe the short release cycle is to blame.

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1034160](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1034160)

---

### Post by Stinger on 2012-09-24
Ahem.. This bug only seems to affect 1 person. Maybe it's a hardware specific bug that only affects you because of some odd hardware failure ?

---

### Post by jerrylamos on 2012-09-24
This is [Radeon HD 6310]
I don't see any dashes.

However if I bump the scroll wheel up when on the top line Firefox disappears.

Very disconcerting.

Then If I move the cursor to the middle of the screen the scroll wheel flips back and forth between a workspace chooser.  I got a workspace chooser on the panel, I don't need a squirrelly one from the mouse scroll wheel.

I found if I put the mouse cursor back on the top line and scroll down Firefox re-appears.  Whew.

I've another radeon or two to try for the dashes.

---

### Post by cariboo on 2012-09-24
> **jerrylamos said:**
> This is [Radeon HD 6310]
I don't see any dashes.

However if I bump the scroll wheel up when on the top line Firefox disappears.

Very disconcerting.

Then If I move the cursor to the middle of the screen the scroll wheel flips back and forth between a workspace chooser.  I got a workspace chooser on the panel, I don't need a squirrelly one from the mouse scroll wheel.

I found if I put the mouse cursor back on the top line and scroll down Firefox re-appears.  Whew.

I've another radeon or two to try for the dashes.

Are you sure you aren't seeing the *** window-blind*** effect, that has been a part of many Linux distributions for years. 

To check, double click the top bar of any window, it should roll up, and only the top bar should be visible.

---

### Post by DisappearingOak on 2012-09-25
> **jerrylamos said:**
> This is [Radeon HD 6310]
I don't see any dashes.

However if I bump the scroll wheel up when on the top line Firefox disappears.

Very disconcerting.

Then If I move the cursor to the middle of the screen the scroll wheel flips back and forth between a workspace chooser.  I got a workspace chooser on the panel, I don't need a squirrelly one from the mouse scroll wheel.

I found if I put the mouse cursor back on the top line and scroll down Firefox re-appears.  Whew.

I've another radeon or two to try for the dashes.

Mine is Radeon HD 4250, open source radeon driver. the bug is not ALWAYS reproducible, but does happen often, and I think using it for a couple days will probably show the bug. This is Ubuntu-specific, I think, because I've only seen the bug on Ubuntu and it's derivative distros. Not in other distros.

---

### Post by jerrylamos on 2012-09-25
> **cariboo907 said:**
> Are you sure you aren't seeing the *** window-blind*** effect, that has been a part of many Linux distributions for years. 

To check, double click the top bar of any window, it should roll up, and only the top bar should be visible.Didn't get any response to double clicks.  

The Firefox vanish/re-appear is instantaneous.  Once I figured out what was happening I can put up with it.

---

### Post by balloons on 2012-09-26
So you are using the open source drivers? likely something on that end then. I've seen similar artificats happen reliably, but it was when I had an nvidia card and the nvidia drivers running on my machine. Since the switch to amd and open drivers, everything is so nice ;-)

---

### Post by mc4man on 2012-09-26
> **jerrylamos said:**
> Didn't get any response to double clicks.  

The Firefox vanish/re-appear is instantaneous.  Once I figured out what was happening I can put up with it.
While Not a default enabled option perhaps you have the option highlighted in screen set to shade?

---

