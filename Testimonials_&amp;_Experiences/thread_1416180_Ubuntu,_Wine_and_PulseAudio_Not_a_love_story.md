---
title: "Ubuntu, Wine and PulseAudio: Not a love story"
date: 2010-02-25
forum: Testimonials &amp; Experiences
---

### Post by MrNatewood on 2010-02-25
I must admit I do not posses great technical knowledge of how a dsitribution works or how a sound system works but I do believe I got the 'gist' of it.

Seems to me as if you would rank Ubuntu packages say in 5 tiers, 1 being an integral part of the system and 5 being some obscure package only two people have ever installed, an MS Windows API would rank at "tier 2" and a sound system at "tier 1".

Point being both of them are very important to at least new users.
It would seem to logically follow that a distribution aimed at users with minimal technical linux skills and high probability of needing windows apps to work would make a big effort to make those two parts of the system compatible.

I am sure I'm not to only one who had a killer app in windows and had to get it working in wine before doing the big switch.

Nowadays the task has become much harder, Ubuntu has switched from the good old ALSA/dmix sound system to the new PulseAudio, which isn't compatible with Wine.

Now, it really doesn't matter who is at fault here, the wine guys or the pulse guys, the end result is that you have two very important packages that are just simply not compatible.

If an Ubuntu user would post at WineHQ to get help the first answer he will get is "remove pulseaudio", which would have been tolerable if you could. Today it is such an integral part of the system you can't even get a proper volume control applet without it.

It would seem to me as the role of the distribution to make sure the packages "play nice" with each other.

It's not as if there aren't any viable solutions out there. Granted, I do not know much about the inner workings of a linux system, but from what i gather it is possible to have a modern distro with both of these components working properly. You could fix it at either end, both windows api and sound system.

One approach would be the way fedora handles it, there is an "unofficial" patch to wine which adds support for pulseaudio. Fedora ships with it in the official repositories. In ubuntu I have to go to an unsupported PPA in order to get wine-pulse, which did not work well for me.

The other approach would of course be using a different sound system, lord knows linux isn't short of sound systems. Wine should play nice with ALSA, OSS, EsounD, JACK and NAS(whatever that is).

Truth be told, I got my way around it, Found alternatives to all my windows apps except one, and fiddled my way into running that one app smoothly, But I believe that for the sake of newbies this must change.

This should be taken as less of a rant and more a call for debate, I would love to hear what someone who actually knows a thing or two about how Ubuntu works thinks of this.

---

### Post by Tamlynmac on 2010-02-25
> MrNatewood

Thank you for sharing your experiences & opinions. Since this isn't a debating section of the forum, I will not comment on either.

But will wish the best and good luck with your quest on behalf of new users.

---

### Post by kostkon on 2010-02-26
> **MrNatewood said:**
> I must admit I do not posses great technical knowledge of how a dsitribution works or how a sound system works but I do believe I got the 'gist' of it.

Seems to me as if you would rank Ubuntu packages say in 5 tiers, 1 being an integral part of the system and 5 being some obscure package only two people have ever installed, an MS Windows API would rank at "tier 2" and a sound system at "tier 1".

Point being both of them are very important to at least new users.
It would seem to logically follow that a distribution aimed at users with minimal technical linux skills and high probability of needing windows apps to work would make a big effort to make those two parts of the system compatible.

I am sure I'm not to only one who had a killer app in windows and had to get it working in wine before doing the big switch.

Nowadays the task has become much harder, Ubuntu has switched from the good old ALSA/dmix sound system to the new PulseAudio, which isn't compatible with Wine.

Now, it really doesn't matter who is at fault here, the wine guys or the pulse guys, the end result is that you have two very important packages that are just simply not compatible.

If an Ubuntu user would post at WineHQ to get help the first answer he will get is "remove pulseaudio", which would have been tolerable if you could. Today it is such an integral part of the system you can't even get a proper volume control applet without it.

It would seem to me as the role of the distribution to make sure the packages "play nice" with each other.

It's not as if there aren't any viable solutions out there. Granted, I do not know much about the inner workings of a linux system, but from what i gather it is possible to have a modern distro with both of these components working properly. You could fix it at either end, both windows api and sound system.

One approach would be the way fedora handles it, there is an "unofficial" patch to wine which adds support for pulseaudio. Fedora ships with it in the official repositories. In ubuntu I have to go to an unsupported PPA in order to get wine-pulse, which did not work well for me.

The other approach would of course be using a different sound system, lord knows linux isn't short of sound systems. Wine should play nice with ALSA, OSS, EsounD, JACK and NAS(whatever that is).

Truth be told, I got my way around it, Found alternatives to all my windows apps except one, and fiddled my way into running that one app smoothly, But I believe that for the sake of newbies this must change.

This should be taken as less of a rant and more a call for debate, I would love to hear what someone who actually knows a thing or two about how Ubuntu works thinks of this.
Err, the latest versions of Wine work just fine with PulseAudio. Do you know that by default in Ubuntu (versions >= 8.10), all the ALSA sounds from the various applications pass through PulseAudio, as long as the application is well written and sends its sound to dmix instead of trying to access the hardware device directly (like the older versions of Wine were doing).

---

### Post by Docaltmed on 2010-02-26
I always found fiddling with Wine to be a little bit beyond me. I just made a virtual machine running XP and called it a day. I haven't had any sound or installation problems, at least that weren't XP related or intrinsic to the application.

I've got Wine on my system, I just don't use any Windows software that can use it (truth be told, I don't really use any Windows software anymore. Just a couple of vendor-supplied legacy programs).

---

### Post by sophicsage on 2010-02-26
I agree with him completely.  The horrible lack of usability for Wine and Pulse Audio was my main reason for being forced back to Windows.  I'll try Ubuntu 10.04 when it comes out, but it's as bad as 9.10 for audio support, I'll have to avoid i

---

### Post by MerlinW on 2010-03-13
I made a script for build **wine-git** with **pulseaudio** and **directx 9**. I'm using it, so it's working well. Enjoy:)

The latest version has:
* wine 1.3.17 (2011.04.10)
* winepulse 0.3.11 (2011.01.21)
* winetricks (2011.04.02)
* git (1.7.3.5)

* PPA installer - not always up-to-date, but faster. The PPA version doesn't include DirectX.

More details:
[Wine+Pulse+DX9 Installer v1.3.17-311.31]("http://merlinw.org/index.php?cid=312")

Script download:
[winepulse_installer.sh]("http://merlinw.org/downloads/download.php?id=2") (1.3.17)

Uninstaller download:
[winepulse_uninstaller.sh]("http://merlinw.org/downloads/download.php?id=3")

PPA installer download:
[winepulse_installer_ppa.sh]("http://merlinw.org/downloads/download.php?id=8") (1.3.17)

---

### Post by cjejuni on 2011-04-16
help. so i used merlinw's installer. it got stuck on line101, no winecfg in system. i just used it before this installer. it looked like got wiped out by the installer. 
linux is not always friendly when uninstalling. does not always find dependencies properly. 

SO BEWARE OF THIS WINE, PULSEAUDIO, DX9 INSTALLER. NOT NEWBIE FRIENDLY!

---

### Post by Sef on 2011-04-18
Locked. Necromancing.

---

