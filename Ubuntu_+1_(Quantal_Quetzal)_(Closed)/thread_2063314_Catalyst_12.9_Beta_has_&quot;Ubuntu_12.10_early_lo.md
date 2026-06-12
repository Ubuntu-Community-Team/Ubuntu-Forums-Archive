---
title: "Catalyst 12.9 Beta has &quot;Ubuntu 12.10 early look support&quot;"
date: 2012-09-26
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by MilesRdz on 2012-09-26
Finally some official support.
[http://support.amd.com/us/kbarticles/Pages/AMDCatalyst129betadriver.aspx](http://support.amd.com/us/kbarticles/Pages/AMDCatalyst129betadriver.aspx)

---

### Post by jfernyhough on 2012-09-26
Still doesn't support xserver 1.13. Just tried upgrading from 1.12 to 1.13 and got the usual "unknown symbol" error with an incompatible xorg version.

Downgraded back to 1.12; now I have to work out which packages I need to get keyboard and mouse back in X. :D (I'm reckoning xserver-xorg-input-evdev, -mouse, -synaptics).

---

### Post by tjeremiah on 2012-09-27
thanks for the heads up OP.

---

### Post by yaji on 2012-09-27
I hope they will relase drivers for legacy users. The drivers im using now are compatibile with kernel 3.5 but I dont now how will they work with xserver 1.12.

---

### Post by christian667 on 2012-09-27
Same for me,
running ubuntu 12.10 x64 with an AMD E-350, the "unknown symbol" error comes up to Xorg.0.log, but the fglrx mod gets build without problems and is loaded after boot. fglrxinfo points out that the driver isn't running.. that annoying, no way for me to get ubuntu 12.10 running with catalyst :(
Switched back to radeon..

---

### Post by christian.convey on 2012-09-27
> **MilesRdz said:**
> Finally some official support.
[http://support.amd.com/us/kbarticles/Pages/AMDCatalyst129betadriver.aspx](http://support.amd.com/us/kbarticles/Pages/AMDCatalyst129betadriver.aspx)
How are you guys trying to install the Catalyst driver, anyway?

I assumed we were supposed to just install the "fglrx" package, but that didn't work, leading me to file this bug:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1054992](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1054992)

What's confusing me is that so many people would be surprised to find that AMD's closed-source driver couldn't be installed on a beta version of Ubuntu, that there would be bug reports and complaints about it all over the place.  I don't understand the (near complete?) silence on this issue.

---

### Post by christian667 on 2012-09-27
That seems as strange to me to.. but Ubuntu 12.10 is still beta, therefore just the pros are testing it and they yet don't complain about the missing driver support because radeon works fine for simple testing. (Just a theory ;) )
The problem is (or was?!) that the new Xorg 1.13 stuff has a new interface which needs the driver developer to get their driver to work with. This took some time and now ubuntu decided to switch to this new xorg version, which isn't yet supported by AMD.
The new beta driver promised an "early look" support to ubuntu 12.10, which leads me to the suggestion that they should have implemented the new xorg 1.13 interfaces.
There are nearly no informations if somebody had success in installing the new beta driver with ubuntu 12.10, I tried for my own minutes ago and failed. Small Howto:
[http://ubuntuxtreme.com/howto/amd-catalyst-12-9-install-guide-ubuntu/](http://ubuntuxtreme.com/howto/amd-catalyst-12-9-install-guide-ubuntu/)

---

### Post by tjeremiah on 2012-09-27
I installed it and unity goes boom/disappears.

---

### Post by christian667 on 2012-09-28
Did your resolution change to something like vga? ;)
Try to open up a terminal (crtl+t) and execute fglrxinfo.
I guess there will an error appear with something like "blabla driver not running bla". The same for me, the module (fglrx) is loaded but the driver still doesn't work with the nex xorg..

---

### Post by tjeremiah on 2012-09-28
I got it to work by initiating the 2nd optioned AMD driver in "additional drivers." Rebooted and installed the beta by selecting the one made for this specific distributions only. Rebooted and all seems well so far.

---

### Post by christian667 on 2012-09-28
Agreed, the fglrx-updates package in the reps has been fixed - found it somewhere launchpad.. fresh installed version runs fine.
The self created packages (see mentioned howto above) still doesn't work, but who matters ;)

---

