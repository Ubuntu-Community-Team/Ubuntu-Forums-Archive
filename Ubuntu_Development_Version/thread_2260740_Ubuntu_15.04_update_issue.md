---
title: "Ubuntu 15.04 update issue"
date: 2015-01-14
forum: Ubuntu Development Version
---

### Post by mpmckinnon on 2015-01-14
Hi there can someone help me fix this issue please:  sudo apt-get install -f Reading package lists... Done Building dependency tree        Reading state information... Done Correcting dependencies... failed. The following packages have unmet dependencies:  gstreamer1.0-plugins-bad : Depends: gstreamer1.0-plugins-bad-faad (= 1.4.4-2ubuntu4) but it is not installed  gstreamer1.0-plugins-good : Depends: libgstreamer-plugins-base1.0-0 (>= 1.5.0.1+git20150102.cd45983e-0ubuntu1~15.04~ricotz0) but 1.4.5-1ubuntu1 is installed                              Depends: libgstreamer1.0-0 (>= 1.5.0.1+git20141229.0461c9f2-0ubuntu1~15.04~ricotz0) but 1.4.5-1 is installed E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages. E: Unable to correct dependencies

---

### Post by Mark Phelps on 2015-01-14
Ubuntu 15.04 is at best, an alpha -- and you shouldn't be using it unless you're very experienced at fixing stuff that breaks.

Besides, question on pre-release versions belong in the Development section, not here.  I'll be asking a Mod to move this post there -- where folks will see it and may be able to help you.

---

### Post by slickymaster on 2015-01-14
*Moved to the ***Ubuntu Development Version*** sub-forum*

---

### Post by grahammechanical on 2015-01-14
Why are you running apt-get install -f? Did you get some error message with apt-get update/upgrade? Was it related to any PPAs? I see this

> [COLOR=#000000]>= 1.5.0.1+git20150102.cd45983e-0ubuntu1~15.04~ricotz0)[/COLOR]

Is not "ricotz" referring to a PPA? What have you installed? Is the PPA valid for 15.04 or is it a PPA for 14.04 or 14.10? More information please about your particular install. I run Vivid Vervet as a daily driver and I update daily and I am not getting those errors. I do not see this problem as specifically related to the ongoing development of 15.04,  but to the special cirumstances of your system.

Regards.

---

