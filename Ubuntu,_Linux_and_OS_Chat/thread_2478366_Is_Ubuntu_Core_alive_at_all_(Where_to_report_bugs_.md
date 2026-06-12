---
title: "Is Ubuntu Core alive at all? (Where to report bugs to?)"
date: 2022-08-24
forum: Ubuntu, Linux and OS Chat
---

### Post by hadmut on 2022-08-24
Hi,

every now and then I try Ubuntu Core on Raspberry Pi, but whenever I run into a problem – which I do sometimes, which makes me believe not many people are actually using it – it is very hard to find a place to drop a bug report. Launchpad doesn't seem to have a core project, just a "snappy" (which might have been the earlier name for core), but I am not sure whether this actually covers common bug reports. 

There is github projects, but not obvious whether and where to drop bug reports there. 

Not even the sales agent that automatically appears on Ubuntu's own webpage for Ubuntu Core did know anything beyond "have you tried the community forum?". 

And here in this forum I did not immediately find a core-related forum. 


Is Ubuntu Core actually a maintained product/project, or is this abandoned and dead, and I am just using it because I didn't realize that?


Background: I just ran into the problem that I couldn't run Ubuntu Core 22 on a Raspberry Pi CM4 Compute module, because on the CM4 – in contrast to regular RPI – there is no USB3 and the USB2 is disabled by default. So there is no keyboard available and the system hangs at boot time in the "Press enter to configure." step, because I can't press enter without a running keyboard. This is a known problem and usually it helps to add dtoverlay=dwc2,dr_mode=host to the boot command line, but editing /ubuntu-seed/cmdline.txt didn't change anything. I noticed, that – except for the advertising page and a pretty simple getting started page, there seems to be no support, no documention about boot process, no bug reports, just nothing about Ubuntu Core.

Other problems make be believe that no one really cares about Ubuntu Core. 


Does this project actually still exist, or is this just an undead zombie, abandoned product?

Hadmut

---

### Post by guiverc on 2022-08-25
The *main* snap website is [https://snapcraft.io/](https://snapcraft.io/) which includes details on the snap forum being [https://forum.snapcraft.io/](https://forum.snapcraft.io/)

Yes a few *snap* packages are watched on launchpad for bug reports, but for best results you go to github, or snapcraft sites, as launchpad.net is mostly traditional *deb* packaged software (*though a [quick look at seeds]("https://people.canonical.com/~ubuntu-archive/seeds/"), and even Ubuntu Core seeds exist on launchpad so I'm betting Ubuntu Core is built on launchpad like all standard images*)

Yes Ubuntu Core is a maintained product/project, but for many of us (*myself as a Desktop user*) we have little need for it (*yet anyway*). There is less *community* involved in the Ubuntu Core project though.

---

