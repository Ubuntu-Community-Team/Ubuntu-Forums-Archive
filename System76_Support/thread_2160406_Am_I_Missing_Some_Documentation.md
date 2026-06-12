---
title: "Am I Missing Some Documentation?"
date: 2013-07-06
forum: System76 Support
---

### Post by JerryC on 2013-07-06
I bought a new Bonobo Extreme this week and I have several questions.  I must be missing the documentation that tells me how to vary the brightness and colors of the keyboard lighting.  Neither do I find anything on how to use the fingerprint reader.  This is also the first time I have ever seen a Touchpad without buttons, so I couldn't figure out how to click on anything.  At least tapping didn't do any good.  That doesn't matter though because I have disabled the touchpad. I really, really don't like them.

If you could lead me to documentation on how to use these items, I would really appreciate it.

---

### Post by rorschachwalter on 2013-07-07
The System76 site has documentation. From System76.com, click Support, then under the picture of the Bonobo Extreme you'll find a link called "Quick Start Guide", which takes you to [this pdf]("http://knowledge76.com/images/Bonx6-welcome-front.pdf").

Change keyboard brightness: Press Fn and + (on the numberpad) to increase, Fn and - to decrease.
Change keyboard color: Press Fn and / (on the numberpad).

As for **clicking**, these touchpads are sometimes called "clickpads" because they're not just for moving the mouse, but also for clicking. Press down on the touchpad (lower left corner is best) to click. Depending on the clickpad, sometimes clicking in the lower right produces a right-click, and other times clicking anywhere with two fingers slightly apart produces a right-click. I prefer distinct physical buttons, so I got a Gazelle, but I also had to get used to a MacBook (with a clickpad) for a while, and I think you'll get used to it after a while.

To clarify: I think clicking almost anywhere on the touchpad will produce a left-click, it's just easier to click near the bottom (because the entire touchpad is hinged at the top, so clicking is easier at the bottom). And if you imagine a chunk of the touchpad maybe .5-inch high, and half the width of the touchpad, in the lower right hand corner, that's probably your right-click button area.

---

### Post by JerryC on 2013-07-07
Thank you so very much.  Exactly what I was looking for.

---

### Post by JerryC on 2013-07-07
Does anyone know how to activate the fingerprint reader?

---

### Post by rorschachwalter on 2013-07-07
Do you have fingerprint-gui and polkit installed and updated?

---

### Post by JerryC on 2013-07-07
I would have thought they would come pre-installed, but I'll look for them and install them.

Thanks.

---

### Post by JerryC on 2013-07-07
Well, it turns out Synaptic Package Manager, even after updating, doesn't find anything about fingerprint.  And Polkit looks like a policy manager for KDE.  I use Gnome classic, so I didn't install that.  Any other ideas?

---

### Post by rorschachwalter on 2013-07-07
I'm sort of shootig in the dark here, because I've never used a reader myself. It looks like ThinkPads work with fprintd and libpam-fprintd. Try installing those packages and see if you can find a program somewhere having to do with fprint that will setup your reader for you. If not, try running fprintd-enroll and hopefully it will recognize and help setup your fingerprint reader.

---

### Post by isantop on 2013-07-09
We've temporarily dropped support for the fingerprint readers due to a large security issue. We're working on expanding the native Ubuntu fingerprint reader integration.

---

