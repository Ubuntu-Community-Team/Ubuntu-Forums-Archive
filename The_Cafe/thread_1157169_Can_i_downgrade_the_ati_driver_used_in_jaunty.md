---
title: "Can i downgrade the ati driver used in jaunty?"
date: 2009-05-12
forum: The Cafe
---

### Post by Yvan300 on 2009-05-12
I wanna know if their is somesort of way to be able to use the flgx drivers that were available in ibex,to power my ati card in jaunty. I know jaunty uses some new rendering engine, but still can i rever tothe previous engine without uninstalling jaunty?

---

### Post by Skripka on 2009-05-12
IIRC- ATi had big compatability problems with the new Xorg, which they only very recently fixed.  What driver version are you using?  I presume you're using Xorg 1.6.*?

---

### Post by Sand &amp; Mercury on 2009-05-12
If your card is still supported by ATi you can just wait it out and the new fglrx will land eventually.

If your card is not still supported by ATi (like mine), you're pretty much SOL.

The 'engine' you're talking about is Xorg, which is the framework that your whole desktop sits on. You can downgrade if you get source packages and compile them yourself I guess, but that's a mammoth task if you're not really familiar with the nuts and bolts of the Ubuntu and programming in general. If fglrx is mission critical to you and your card got dropped off ATI's support list you're just gonna have to stick with Intrepid.

---

### Post by Yvan300 on 2009-05-12
I guess i'll have to dual boot ibex and jaunty. WHy?

1. My external hard drive only works in jaunty
2. I can't play any game with a decent fps in jaunty due to the driver at hand
3. My card is no longer supported by ati (raedon xpress 200)

---

### Post by ssri on 2009-05-12
well, some dev compiled a deb of xserver 1.5.2 that supposedly works in Jaunty, thereby enabling one to install Catalyst 9.3, the last version to support legacy cards.  I have not tried it yet though, so I cannot say whether it works or not.

[http://www.kdedevelopers.org/node/3942](http://www.kdedevelopers.org/node/3942)

---

