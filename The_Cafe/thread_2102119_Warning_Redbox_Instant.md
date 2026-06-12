---
title: "Warning Redbox Instant"
date: 2013-01-06
forum: The Cafe
---

### Post by mamamia88 on 2013-01-06
It looks like a good deal but if all you use is linux and a rooted android device don't sign up.  It won't even let you launch the app on android if rooted and it uses silverlight just like netflix

---

### Post by Lucradia on 2013-01-06
lol, Silverlight. Microsoft still trying to make use of that Frankenstein....

---

### Post by Bandit on 2013-01-06
> **mamamia88 said:**
> It looks like a good deal. But, if all you use is linux or a rooted android device then don't bother signing up.  It will not let you launch the app on an android if it has been rooted and it uses silverlight just like Netflix.
***CORRECTED GRAMAR...***


Thanks for the heads up despite the need to translate.. :popcorn:

---

### Post by Bandit on 2013-01-06
> **Lucradia said:**
> lol, Silverlight. Microsoft still trying to make use of that Frankenstein....

Not fond of Silverlight, but the reasoning behind using it is to prevent the copying of the video content.  If it was not for that single reason I doubt anyone would use this mess.

---

### Post by mamamia88 on 2013-01-06
> **Bandit said:**
> Not fond of Silverlight, but the reasoning behind using it is to prevent the copying of the video content.  If it was not for that single reason I doubt anyone would use this mess.
people will copy video content no matter how much drm it has on it.  the sooner these companies learn that they are only hurting paying customers the better.

---

### Post by forrestcupp on 2013-01-06
> **bandit said:**
> ***corrected gram[b]m**ar...*[/b]


thanks for the heads up despite the need to translate.. :popcorn:

*corrected spelling* :p

---

### Post by PhilGil on 2013-01-06
> **mamamia88 said:**
> It looks like a good deal but if all you use is linux and a rooted android device don't sign up. It won't even let you launch the app on android if rooted and it uses silverlight just like netflix
Dammit, that's extremely disappointing. I was hoping we'd finally have a Netflix alternative that will work in Linux.
  
> **Bandit said:**
> Not fond of Silverlight, but the reasoning behind using it is to prevent the copying of the video content.  If it was not for that single reason I doubt anyone would use this mess.Amazon, Hulu, Crackle, et al seem to be able to provide satisfactory DRM without Silverlight.

It's crap like this that makes it so hard for me to recommend Linux to my friends and family. Seems like there's always something an average user will want that isn't supported. I don't blame GNU/Linux, but I also don't know what the solution is.

---

### Post by pqwoerituytrueiwoq on 2013-01-06
> **mamamia88 said:**
> people will copy video content no matter how much drm it has on it.  the sooner these companies learn that they are only hurting paying customers the better.
someone needs to teach them about screen recorders, no matter how much DRM they use they can't prevent that, not like that would be hard for someone to do, and any way around DRM makes it pointless so i just annoys legitimate users

---

### Post by Dr. C on 2013-01-06
> **pqwoerituytrueiwoq said:**
> someone needs to teach them about screen recorders, no matter how much DRM they use they can't prevent that, not like that would be hard for someone to do, and any way around DRM makes it pointless so i just annoys legitimate users

 The current trend in DRM is
1) Lock the bootloader
2) Permit only approved operating systems to be installed 
3) Deny the end owner full administrative or root access
2) Permit the installation of software only from an approved store / source
The is the approach behind:
The TiVo
Game consoles. Xbox, PS3 etc,
ebook readers, Amazon Kindle etc
IOS devices iPod, iPhone, iPad 
Windows 8 RT and Windows 8 Modern UI
Windows phone
etc.
Locked Android devices (this is a requirement for DRM) on Android
It is also the real motivation behind the locked UEFI boot loaders in Windows 8, and the requirement for signed drivers in 64bit Windows Vista/7. Desktop Windows is in transition over time from the open Windows 98 / NT4 model to the complete lockdown in Windows 8 RT on ARM.

The idea is very simple. Do not permit software that can break the DRM to get past the censors in the store, and do not allow the end user to install their own software or software from a source that is not approved. 

Free Libre Open Source Software alone is not enough for example Linux and Android or GNU/Linux before GPL v3 such as the original Tivo can still be locked down in this fashion. One needs GPL v3 code deep enough in the operating system so that root or administrative access is required to modify the GPL v3 code. Modern GNU/Linux distributions such as Ubuntu 8.x or later (and yes this includes Ubuntu phone OS!) are safe from this kind of DRM.

Freedom from this kind of DRM is far more important in my opinion than the question of free vs propriety software. For example Windows NT4 is a far freer system than a tivoized gNewSense 1.0.

---

### Post by Lucradia on 2013-01-06
If you use CamStudio, it likely will record the Metro UI (not tested yet) if it can, then that's that. CamStudio doesn't require Admin rights to run. Fraps and hooking recorders do. gtk-recordmydesktop / recordmydesktop does that as well.

Hooking up a black magic HDMI input PCIe card inside your computer, then making your android phone output via HDMI into your computer will allow you to bypass DRM easy and record your videos.

So unless they remove HDMI output while playing these videos, then it's not going to help.

---

### Post by doorknob60 on 2013-01-06
> **Lucradia said:**
> 
So unless they remove HDMI output while playing these videos, then it's not going to help.

Or just use HDCP. But yeah, there are still many ways around it. I'm not saying they need to provide mp4s for everyone (but that would be nice), but they need to provide DRM in a way that does not negatively impact the users, like Silverlight does, as well as the ban on rooted Android devices.

---

### Post by Dr. C on 2013-01-06
> **Lucradia said:**
> If you use CamStudio, it likely will record the Metro UI (not tested yet) if it can, then that's that. CamStudio doesn't require Admin rights to run. Fraps and hooking recorders do. gtk-recordmydesktop / recordmydesktop does that as well.

Hooking up a black magic HDMI input PCIe card inside your computer, then making your android phone output via HDMI into your computer will allow you to bypass DRM easy and record your videos.

So unless they remove HDMI output while playing these videos, then it's not going to help.

CamStudio is licensed under GPLv3 so it will not make it past the censor board on the ARM Windows 8 RT.  It may work on Windows 8 on Intel and may record videos; however I suspect all the DRM added to Windows starting with Vista will block this. On XP I suspect it may work.  

Are we talking about a **routed** Android phone? This is critical. If it is not routed then the DRM in most Android devices will prevent output to an untrusted by the MPAA video sink. This is the whole point of HDCP. 

To illustrate how nasty this has become. I have a 24in monitor LG 246WP that will not work with Windows Vista or 7 with either the Nvidia or ATI proprietary drivers nor will it work with the  Nvidia or ATI  proprietary drivers on Ubuntu. This is because a bug in the monitor's firmware causes it to fail HDCP. When I purchased it back in 2007 it was sold as compatible with Windows Vista and it worked for a while; however a subsequent &#8220;upgrade&#8221;  to the  Nvidia and ATI proprietary drivers for stricter HDCP compliance turns the monitor into e-waste, unless of course one uses FLOSS drivers.  It works great with the FLOSS drivers because they do not have this HDCP malicious feature designed to promote the generation of e-waste.

---

### Post by pqwoerituytrueiwoq on 2013-01-06
> **Dr. C said:**
> To illustrate how nasty this has become. I have a 24in monitor LG 246WP that will not work with Windows Vista or 7 with either the Nvidia or ATI proprietary drivers nor will it work with the  Nvidia or ATI  proprietary drivers on Ubuntu. This is because a bug in the monitor's firmware causes it to fail HDCP. When I purchased it back in 2007 it was sold as compatible with Windows Vista and it worked for a while; however a subsequent &#8220;upgrade&#8221;  to the  Nvidia and ATI proprietary drivers for stricter HDCP compliance turns the monitor into e-waste, unless of course one uses FLOSS drivers.  It works great with the FLOSS drivers because they do not have this HDCP malicious feature designed to promote the generation of e-waste.
you may be able to mod the edid, that may allow you to work around this, the only thing i ever used a moded edid for was tricking the tv into thinking i was using a dvi output instead of hdmi to get analog audio (the 2.6 kernel does not support hdmi audio on my gtx 550 ti, HDMI audio is just a PITA)
does it work with vga input? i know dvi/hdmi were intended to make drm worse

edid thing:
[http://forums.opensuse.org/english/get-technical-help-here/laptop/445389-how-use-custom-edid-xorg-dvi-hdmi-converter-samsung-41-tv-edid-checksum-invalid.html](http://forums.opensuse.org/english/get-technical-help-here/laptop/445389-how-use-custom-edid-xorg-dvi-hdmi-converter-samsung-41-tv-edid-checksum-invalid.html)

---

### Post by Dr. C on 2013-01-07
> **pqwoerituytrueiwoq said:**
> you may be able to mod the edid, that may allow you to work around this, the only thing i ever used a moded edid for was tricking the tv into thinking i was using a dvi output instead of hdmi to get analog audio (the 2.6 kernel does not support hdmi audio on my gtx 550 ti, HDMI audio is just a PITA)
does it work with vga input? i know dvi/hdmi were intended to make drm worse

edid thing:
[http://forums.opensuse.org/english/get-technical-help-here/laptop/445389-how-use-custom-edid-xorg-dvi-hdmi-converter-samsung-41-tv-edid-checksum-invalid.html](http://forums.opensuse.org/english/get-technical-help-here/laptop/445389-how-use-custom-edid-xorg-dvi-hdmi-converter-samsung-41-tv-edid-checksum-invalid.html)

Yes VGA does work, but VGA at 1920 x 1200 is not good at all. Using a custom EDID in Xorg did work for me for a while with the Nvidia proprietary drivers and there was also a registry fix for Windows Vista/7 with the Nvidia proprietary drivers involving adding a custom EDID to a registry key. I could not get this to work with the more recent AMD/ATI drivers. The trouble here is that the driver can be "upgraded" to ignore a custom EDID since this could be used to break HDCP so there is no guarantee that it will continue to work. In any case I decided that since I run at least one computer with a 100% Free Software GNU/Linux distribution gNewSense or Trisquel, I can use the monitor on that computer over HDMI and not have worry about this issue at all. DVI/HDMI are not a problem if one is using 100% Free Software video drivers. The other option donate the monitor to the FSF since they would not have a problem with it. ;) 

I do thank you very much for your suggestion since this may be of help to someone else.

PS: Were you using a proprietary video driver (NVidia) when you ran into trouble with the audio?

---

### Post by forrestcupp on 2013-01-07
Redbox and Netflix don't give a rat's backside about trying to figure out a way to get it to work in Linux. I'll bet most of the people who work for them don't even know what Linux is.

---

### Post by pqwoerituytrueiwoq on 2013-01-07
> **Dr. C said:**
> 
PS: Were you using a proprietary video driver (NVidia) when you ran into trouble with the audio?
the only hdmi audio i have messed with was via a nvidia gpu, using analog audio is just easier, there is usually some misc. thing that wants to use analog no matter how you have the sound config set
as i said in my post the 2.6 kernel does not support hdmi audio (regardless of the gpu driver) on my gtx 550 ti (nvidia) it works fine on newer kernels, it is just everything defaults to analog audio (guest account and ogg123 for example)
i managed to make a work around for the guest account defaults on 12.10, but i cant get ogg123 to play on hdmi when it runs as root from a script, analog works, it does not sound any different, and it is less hassle
if you want details on my hdmi audio exp
[http://ubuntuforums.org/showthread.php?t=1926721](http://ubuntuforums.org/showthread.php?t=1926721)

---

### Post by scouser73 on 2013-01-07
> **forrestcupp said:**
> *corrected spelling* :p

lmao.

---

### Post by Bandit on 2013-01-07
> **forrestcupp said:**
> *corrected spelling* :p

LMAO.. Good catch :)

---

### Post by Lucradia on 2013-01-20
I'm pretty sure black magic can record HDCP. It can record 360 and PS3 video and audio, which the PS3 is encrypted HDMI video.

---

