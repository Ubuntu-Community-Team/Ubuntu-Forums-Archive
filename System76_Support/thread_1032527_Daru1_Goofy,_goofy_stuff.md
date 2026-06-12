---
title: "Daru1 Goofy, goofy stuff"
date: 2009-01-06
forum: System76 Support
---

### Post by MarkID on 2009-01-06
I don't know if my problems are Daru1 related or Ubuntu related, but here it goes.

Recently, after coming out of Suspend, the Brightness control applet is reversed.  To make it brighter I move the slider toward "-" (negative) and to make it dimmer, I move it to "+" (positive).

Lately, when I pick up my wifi network, the Network Manager creates another unprotected network with the same name.  That is, if my network is "XYZ" and I click on the Network Manager applet, there are two networks there.  One is called "XYZ" and ***is*** secure, and one is called "XYZ" but is ***not*** secure.  They both appear. (I connect only to the secure one.)

What's up?

---

### Post by thomasaaron on 2009-01-06
> Recently, after coming out of Suspend, the Brightness control applet is reversed. To make it brighter I move the slider toward "-" (negative) and to make it dimmer, I move it to "+" (positive).

Did you file this bug report? If not, you probably should weigh in on it. If so, have you tried a fresh install of Intrepid (versus an upgrade from Hardy)? There was a similar issue in a previous Ubunutu version. But I've not been able to duplicate this with our shop DarU1. So, I'm thinking it may have something to do with obsolete scripts from a previous version.

[https://bugs.launchpad.net/system76/+bug/313024](https://bugs.launchpad.net/system76/+bug/313024)

> Lately, when I pick up my wifi network, the Network Manager creates another unprotected network with the same name. That is, if my network is "XYZ" and I click on the Network Manager applet, there are two networks there. One is called "XYZ" and is secure, and one is called "XYZ" but is not secure. They both appear. (I connect only to the secure one.)

I've not seen that one before. Are you sure it is not a problem with your router? Can you see the ghost AP with a different computer? If so, it is definitely your router.

Can you actually connect to the unsecure one?

Try re-setting your router. Does that make it go away?

---

