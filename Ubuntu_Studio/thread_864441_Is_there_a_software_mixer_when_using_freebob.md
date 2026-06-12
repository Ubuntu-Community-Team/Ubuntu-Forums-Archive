---
title: "Is there a software mixer when using freebob?"
date: 2008-07-19
forum: Ubuntu Studio
---

### Post by yoni1 on 2008-07-19
I'm interested in the Presonus Inspire firewire interface, which is reported to work under freebob.  However, when using a firewire audio interface with the freebob driver, is there any mixer interface provided?  I'm asking because the Inspire does not have any physical knobs or buttons; everything is done through the control panel that is provided for Windows or OSX.

For devices supported by alsa, we have alsamixer which can control the device settings such as levels, mute, gain, etc.

Is there some equivalent for freebob?

---

### Post by Stochastic on 2008-07-20
Nope, freebob has none of said features.  It's successor [FFADO]("http://www.ffado.org") - which is currently in beta stages - does have a software mixer, but I think presonus cards don't have any settings programmed for it (I'm not %100 sure of this, do your own reading on that one).

---

