---
title: "Dual-Booting and Wine"
date: 2009-07-04
forum: Wine
---

### Post by kurt1288 on 2009-07-04
I'm dual booting Windows and Linux. Is there a way for me to run a program that I've installed on the Windows partition from Linux? The program is EVE, which is supposed to be able to run using WINE, but I haven't installed EVE onto the Linux partition (and would rather not if I could get it working as is). I've tried running the EVE.exe file using WINE, but after the splash screen nothing happens (which I guess doesn't surprise me too much). So, anything I can do short of installing it on the Linux partition that will get it to work?

I guess there's also a larger question here, which is do I have to install any (Windows) program using Wine (on the Linux partition) before I can use it? Or can I just install it onto the Windows partition and someone run it using Wine when I boot Ubuntu?

---

### Post by cogadh on 2009-07-04
Wine is not designed to work with an existing Windows installation and trying to do that can very easily corrupt that Windows install and make it useless (though the Wine devs have taken steps to prevent that). Generally speaking, any Windows apps you wish to use within Linux should be installed locally with Wine. There are exceptions (of course), but the safest course is always to install within Wine.

---

