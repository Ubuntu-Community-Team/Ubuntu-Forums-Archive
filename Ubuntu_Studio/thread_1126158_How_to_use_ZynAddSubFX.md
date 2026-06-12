---
title: "How to use ZynAddSubFX?"
date: 2009-04-15
forum: Ubuntu Studio
---

### Post by eye208 on 2009-04-15
I compiled LMMS 0.4.3 and the LMMS-extras package which makes ZynAddSubFX available as a plugin in LMMS. However, automation support for ZynAddSubFX seems to be very poor compared to the other plugins because the ZynAddSubFX GUI is separate from LMMS. The standalone version of ZynAddSubFX supports automation through a set of MIDI controllers and NRPNs.

Is there a way to control ZynAddSubFX parameters through LMMS? Should I use Rosegarden instead of LMMS? How did you integrate ZynAddSubFX in your setup?

---

### Post by TheMusicGuy on 2009-05-04
I was trying to figure out why Jaunty's LMMS doesn't have a Zyn instrument when I know it was using it under Hardy. I'm assuming the version of LMMS that has support for Zyn is not a part of the official repos.

Anyway, I don't think that any of Zyn's parameters are accessible to LMMS. Someone would have to extend Zyn to allow it to interface more completely with LMMS' automation system...I really don't know how either Zyn or LMMS work at the code level, but I'm guessing it would be tricky and likely to cause crashing if such a feature were to be implemented.

EDIT: You say that Zyn's parameters can be controlled via MIDI. If that's the case, then you may be able to "cheat" by outputting a LMMS instrument to an arbitrary, unused MIDI channel and connecting a Zyn parameter to it. Presumably you would use an LMMS instrument that didn't make any noise, like a AudioFileProcessor without any sample.

---

### Post by Becker-BR on 2009-06-02
Ubuntu Studio 9:04 didn't come with Zyn, it came an old version.
I made this to solve the problem, aind i am wit the new LMMS 0.4.4.3.
To solve the problem:
1- Uninstall LMMS;
2- Go to page:
 [https://launchpad.net/~tobydox/+archive/ppa](https://launchpad.net/~tobydox/+archive/ppa)

Note; PPA for Jaunty don't work.
Use Intrepid-ibex:
apt sources.list entries :

deb [http://ppa.launchpad.net/tobydox/ppa/ubuntu](http://ppa.launchpad.net/tobydox/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/tobydox/ppa/ubuntu](http://ppa.launchpad.net/tobydox/ppa/ubuntu) intrepid main


3- Go to Synaptic
   Search LMMS
   Install LMMS 0,4.4.3

---

