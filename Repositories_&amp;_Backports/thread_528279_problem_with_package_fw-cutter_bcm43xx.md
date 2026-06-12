---
title: "problem with package fw-cutter bcm43xx"
date: 2007-08-17
forum: Repositories &amp; Backports
---

### Post by drascus on 2007-08-17
This package includes an option to extract and install the firmware for you. for some reason this option does not work. I have linked the problem to an issue connecting with the site [www.boredklink.googlepages.com](www.boredklink.googlepages.com) I am not sure who to report this issue to in order to get it resolved.  Any help would be appreciated. 
~mike~

---

### Post by Jamie Jackson on 2007-08-17
Is [this]("https://bugs.launchpad.net/ubuntu/+source/bcm43xx-fwcutter/+bug/127624") what you're talking about?

BTW, if you want to try ndiswrapper, you could go [here]("http://ubuntuforums.org/showthread.php?t=475963"). Apparently, if you can get ndiswrapper working, it's preferable to fwcutter (the latter having reduced bandwidth).

---

### Post by maestrobwh1 on 2007-08-18
I have the BCM 4318 and used ndiswrapper with edgy.  The only thing I did not like was that it always showed signal at 100%.

fwcutter is used in feisty and gutsy by the restricted manager package and runs my broadcom at 24 mbps, rather than the 54 it is capable of, however; since I don't do file transfers via a network and just use the net, anything over 10 mpbs won't really have any effect.  Wireless g is no faster than wireless b really if a person is just using the internet.

If you have feisty or higher, download the restricted-manager (use adept or synaptic to find exact name, as I think it is hyphenated and different items exist for kde or gnome).

In kde, it creates an applet in system settings and then when launched, it will give you a list of hardware on your computer that has proprietary drivers.  It even went over the net to get the firmware.  I didn't even have to find my own *inf and *sys files.  I was pleased with the simplicity.

Feisty and now gutsy (not quite ready yet) have made leaps and bounds in so many aspects, I recommend that anyone who is using something else to upgrade to Feisty.

---

### Post by Jamie Jackson on 2007-08-18
With ndiswrapper, I'm getting speeds of 23 Mbps WPA, and 25 Mbps unencrypted, so I'm not sure I'm getting any advantage out of it anyway.

I'm running Gnome, and I've got restricted-manager installed. This appears to install an applet: System >> Administration >> Restricted Drivers Manager.

[[IMG]http://img137.imageshack.us/img137/4296/screenshotrestricteddriyl9.th.png[/IMG]](http://img137.imageshack.us/my.php?image=screenshotrestricteddriyl9.png)

Does this look different than yours? There doesn't seem to be much I can do from this applet (besides uncheck some stuff that's already there).

---

