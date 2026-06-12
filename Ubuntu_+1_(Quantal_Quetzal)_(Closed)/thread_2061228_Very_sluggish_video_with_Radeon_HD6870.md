---
title: "Very sluggish video with Radeon HD6870"
date: 2012-09-22
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by MadNachos on 2012-09-22
I have had very sluggish video with my HD6870 during the early alpha stages and it has continued up until today. Is this a relic of broken upgrades from early alphas or does the current radeon driver not work well with this card? I also don't see an option in Ubuntu to install the proprietary driver. Normal or is my old system just jacked up?

---

### Post by QIII on 2012-09-22
Hard to say about the Radeon driver in a development version.  Mine works well.  Can you define "sluggish" a little more qualitatively?

The reason you don't see an option to install fglrx is that the current driver from AMD will not work without manually installing it and doing some patching and there is no driver in the repo yet.

The 12.10 driver should drop in to the Canonical repo around the time of the RC.

Patience.

---

### Post by MadNachos on 2012-09-22
> **QIII said:**
> Hard to say about the Radeon driver in a development version.  Mine works well.  Can you define "sluggish" a little more qualitatively?


Yes, when moving windows around its not smooth at all, and window animations are very slow. When moving a window across the screen its more like 6 or 8 renderings instead of a smooth high FPS one if that makes sense. Its usable, but the performance is very poor. I should add that I am using two 24" monitors with a spanning desktop but when I have run in single monitor mode the performance is similar. I am cool with being patient if this is just the current state of the driver, I have been making a living off Linux for over 15 years and certainly remember when just getting X to run was a huge accomplishment, its nice to see that these days having it work poorly is even an option ;)

---

### Post by QIII on 2012-09-22
I don't think that's the general current state of the driver.

I have Quantal in Ubuntu and Xubuntu flavors on an ATI machine and both work just fine.

I'm in the middle of trying to finish a project for a client and burning the midnight oil, so I'll have to check into this later if someone else doesn't get to it first.

---

### Post by MadNachos on 2012-09-25
I ran 12.10 off a usb stick, the video seemed good, so I did a clean install and it seemed the video issues were cleared up as everything smooth. However, after a few hours of use the display slows down and moving windows around is very slow. I can restore performance by switching my two displays into 'mirrored' mode and then back into the spanning desktop. I have not noticed it suddenly getting laggy so I think its just a gradual degradation, but I need to use it more to be sure.

---

### Post by MadNachos on 2012-09-25
Looks like I found a workaround. Logging in with my desktop spanning both displays results in poor video performance. Going to mirrored mode and then back to spanning in the same session fixes it. If I log in with mirrored mode enabled performance is good and remains good if I switch to a spanning desktop.

---

