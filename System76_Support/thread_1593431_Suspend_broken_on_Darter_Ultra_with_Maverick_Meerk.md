---
title: "Suspend broken on Darter Ultra with Maverick Meerkat"
date: 2010-10-11
forum: System76 Support
---

### Post by peterih on 2010-10-11
After upgrading to 10.10 my Darter Ultra (model daru3) is able to suspend when closing the lid, but doesn't recover when opened again. It sounds like the machines wakes up, but the screen doesn't turn on. The only way I can get back to a usable system is by powering down and up.
I tried restoring the system76 drivers but that didn't make a difference.

---

### Post by arepaking on 2010-10-15
I performed a fresh install on my daru3 and is working fine with the suspend.

The only problem that I am facing is that I cannot connect to a Wireless N network. Works fine with Wireless G though.

---

### Post by leptogenesis on 2010-10-20
> **peterih said:**
> my Darter Ultra (model daru3) is able to suspend when closing the lid, but doesn't recover when opened again. 

I'm seeing something very similar on a Serval Professional, which has a fresh install of Maverick.  It seems to happen randomly though--sometimes it will resume from suspend just fine.  Other times it almost comes on--the power light will come on, and I can eject the CD tray--but the screen doesn't come on.

---

### Post by leptogenesis on 2010-10-20
> **leptogenesis said:**
> It seems to happen randomly though

I take that back--it seems to happen if and only if it's the *second* time the machine has been suspended since it was last booted.  peterih, is it the same for you?

---

### Post by peterih on 2010-10-23
It's also my experience that it happends randomly, but very rarely on first suspend after boot. I'll try and keep a statistic.

---

### Post by Temposs on 2010-10-25
I am also experiencing this inconsistent failure of suspend on my daru3. Sometimes it suspends and resumes just fine. Other times it suspends fine, but on resuming, the screen stays black and the fourth indicator light to the left of the power button turns on. Sometimes it doesn't suspend but instead the screen disables and the fan goes on high speed.

In each case the only solution is to manually power off.

---

### Post by isantop on 2010-10-25
Perhaps this is a widespread issue. I'll add it to the list of bugs. We'll see what we can do to get it fixed up.

---

### Post by leptogenesis on 2010-10-29
isantop, do you have a link to a bug report?  I'd like to know when this gets fixed, since it's very annoying not to be able to suspend my computer for the ride to work.

---

### Post by isantop on 2010-10-29
Hi.

We haven't got one up yet, but we should by next Tuesday. I'll post a link here when we get it up.

---

### Post by peterih on 2010-11-20
isantrop, was a bug ever filed on this, or did you forget to post a link to it?

---

### Post by isantop on 2010-11-22
We're doing some more work on it first before filing a bug. It may be linked to a particular type of system, and we want to make sure we have the most accurate bug possible.

---

### Post by peterih on 2010-12-12
Please let us know what we can do to help.

---

### Post by leptogenesis on 2011-03-21
I just checked again with the latest kernel updates and suspend is still broken.  When is this bug of yours going to get posted?

---

### Post by Temposs on 2011-03-21
Actually, this issue seems to have gone away about two weeks ago on my machine, due to one of the kernel updates I assume. Evidently it wasn't fixed for everyone.

---

### Post by isantop on 2011-03-21
Sorry the link never got posted. The bug is actually fairly widespread, and not linked to the DarU3. We've actually been tracking it for some time, but we've yet to find out exactly what causes it. It is fixed in Ubuntu 11.04, and while I don't recommend upgrading yet, this issue should go away when it's released in a month. Here's the link:

[Bug# 690241](https://bugs.launchpad.net/system76/+bug/690241)

---

