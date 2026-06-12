---
title: "Fifth Attempt With Ubuntu 14.04 Daily"
date: 2014-02-02
forum: Ubuntu Development Version
---

### Post by tdockery97 on 2014-02-02
Today (2 Feb) I made my fifth attempt with the 14.04 daily builds.  Previously my ATI Radeon HD 8650G had problems (perhaps kernel related) and I had to use nomodeset to boot to the desktop.  While everything seemed to work OK after reaching the desktop, I decided to wait until a build where nomodeset was not required.  That build is today's daily.  Not only did it boot properly, but I found that using only the opensource drivers worked better than on any other distro I've ever run, including previous Ubuntu versions.  Normally running videos would push my laptop temp up around 60C to 68C.  With TT my laptop now idles at 35C and runs up to 40C when playing full screen YouTube videos.  I've run the live DVD through the paces and everything is snappy and stable so far.  I'm going to install this one to metal and see how things now go through the last 2-1/2 months of the testing cycle.

---

### Post by grahammechanical on 2014-02-02
May I suggest that you do not install third party software during the installation process. That will give you a proprietary video driver and you may have a problem rebooting to a working desktop. Stick with the open source driver. I stopped using Nvidia drivers about 2 years ago. I never tick to install third party software when I test install a Ubuntu daily image.

Oh, and in the early days of the last development cycle I found it impossible to install a daily image without using nomodeset. That is not normally necessary for my hardware. Things got sorted out over the following days. Such is life.

Regards.

---

### Post by mike.mikowski on 2014-02-07
My advice: don't use ati with Linux.  Their proprietary driver's are much slower than their windows stack.  Compare this to nvda where their Linux drivers sometimes outperform the  windows drivers.  Look at any Linux system builder and count the number of systems that come with Amd graphics.  At least count, I see 0.  There is a reason.

The oss drivers for both are slow, but workable.  My brother the masochist insists on building Linux boxes with ati cards, and he has nothing but trouble.  My boxes, all built or spec'd with nvda cards over the last 15 years, rarely have any problems - and vastly outperform the ati boards.

I am sick of Amd treating Linux user like second class citizens.

---

