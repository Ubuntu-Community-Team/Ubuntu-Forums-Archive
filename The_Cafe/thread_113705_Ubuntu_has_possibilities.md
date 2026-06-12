---
title: "Ubuntu has possibilities"
date: 2006-01-06
forum: The Cafe
---

### Post by sga826 on 2006-01-06
Hello,

Just signed up, they suggested I say hello here so hi.

Thanks for the cd's. I have installed Ubuntu on 2 pc's at work and one at home. I work at a Windows/Novell shop and have installed Novell Suse Linux but never went much further. So might as well say my Linux experience is null.

The faq guide is fantastic. Had no problems with installation, configuration etc. One of my duties at work is to create and distribute msi's (Microsoft Installers) so the whole repositories, Synaptic Package Manager thing was alien but I found it easy to grasp and pretty cool.

My goal was to install Ubuntu on a partition at home and try to do everything I do on XP with the intention of migrating to Linux. I am also creating an Ubuntu file server from a surplus pc at work to use on my home network.

I am pretty much on schedule. Interesting note: at Christmas I was trying to print out directions to my network printer from my XP machine and was receiving an RPC error. I was unable to resolve it and unhappily scribbled out the directions by hand. Later after I installed Ubuntu and configured networking I had no problem printing to the same printer.

I use my computer pretty much like the average user: surfing, email, music etc. And I think Ubuntu Linux will be a good fit. My main interests are digital photography and music.

Now to the downside: apparently I am not alone in being unable to coax sound from my Turlte Beach Santa Cruz sound card. I have spent way too much time on this. I have tried every suggestion I found: disabling the onboard, installing OSS software etc. Since listening to music is one of my priorities and playing silent games isn't much fun I boot to Ubuntu to learn and XP to play.

This is where I change from Tech guy to consumer:

I could buy another card or use my onboard but I don't want to. I AM THE CUSTOMER. If Linux is going to compete or be a reasonable alternative to Windows the user should be able to purchase mainstream hardware and expect it to work.

I have seen posts stating that for compatability one should only buy Creative Soundcards and NVidia video cards. That is unacceptable (Btw my ATI video card works fine). 

Why should someone choose an OS other than Windows and then not be able to choose the hardware of their choice?

I am back to Tech guy now. 

I do think Linux is a good alternative and want it to succeed. I am pushing for my company to eventually to move to Linux Desktop. And yes I know it is different than Windows but if even technically savvy folks can't get their computers to function as they would like, than Linux will never be more than a niche market.

---

### Post by aysiu on 2006-01-07
[QUOTE=sga826]
I could buy another card or use my onboard but I don't want to. I AM THE CUSTOMER. If Linux is going to compete or be a reasonable alternative to Windows the user should be able to purchase mainstream hardware and expect it to work.

I have seen posts stating that for compatability one should only buy Creative Soundcards and NVidia video cards. That is unacceptable (Btw my ATI video card works fine). 

Why should someone choose an OS other than Windows and then not be able to choose the hardware of their choice?[/QUOTE] The same reason my wife had to look specifically for a Mac-compatible printer and a Mac-compatible MP3 player for her Powerbook. You buy compatible hardware for your computer/operating system--not vice versa.

---

### Post by BSDFreak on 2006-01-07
[QUOTE=sga826]Hello,

Just signed up, they suggested I say hello here so hi.

Thanks for the cd's. I have installed Ubuntu on 2 pc's at work and one at home. I work at a Windows/Novell shop and have installed Novell Suse Linux but never went much further. So might as well say my Linux experience is null.

The faq guide is fantastic. Had no problems with installation, configuration etc. One of my duties at work is to create and distribute msi's (Microsoft Installers) so the whole repositories, Synaptic Package Manager thing was alien but I found it easy to grasp and pretty cool.

My goal was to install Ubuntu on a partition at home and try to do everything I do on XP with the intention of migrating to Linux. I am also creating an Ubuntu file server from a surplus pc at work to use on my home network.

I am pretty much on schedule. Interesting note: at Christmas I was trying to print out directions to my network printer from my XP machine and was receiving an RPC error. I was unable to resolve it and unhappily scribbled out the directions by hand. Later after I installed Ubuntu and configured networking I had no problem printing to the same printer.

I use my computer pretty much like the average user: surfing, email, music etc. And I think Ubuntu Linux will be a good fit. My main interests are digital photography and music.

Now to the downside: apparently I am not alone in being unable to coax sound from my Turlte Beach Santa Cruz sound card. I have spent way too much time on this. I have tried every suggestion I found: disabling the onboard, installing OSS software etc. Since listening to music is one of my priorities and playing silent games isn't much fun I boot to Ubuntu to learn and XP to play.

This is where I change from Tech guy to consumer:

I could buy another card or use my onboard but I don't want to. I AM THE CUSTOMER. If Linux is going to compete or be a reasonable alternative to Windows the user should be able to purchase mainstream hardware and expect it to work.

I have seen posts stating that for compatability one should only buy Creative Soundcards and NVidia video cards. That is unacceptable (Btw my ATI video card works fine). 

Why should someone choose an OS other than Windows and then not be able to choose the hardware of their choice?

I am back to Tech guy now. 

I do think Linux is a good alternative and want it to succeed. I am pushing for my company to eventually to move to Linux Desktop. And yes I know it is different than Windows but if even technically savvy folks can't get their computers to function as they would like, than Linux will never be more than a niche market.[/QUOTE]

I know poofyhairguy have used Turtle Beach Santa Cruz in Ubuntu, PM him with a question and he may just help you to make it work.

I have a Sparc machine, that is standard hardware but you know what, Windows won't install on it, damn MS and their crappy HW support. ;)

The point of the above comment is that you can't expect everything to work out of the box with ANY OS (and not at all with some OS/HW combinations).

-------------------------

Actually, the Cirrus Logic CS 4614/22/24 (which is the controller on the TB SC) is natively supported by alsa, i just checked the kernel it's marked as a module by default. No need to install any extra drivers to make it work IOW.

SND_CS46XX_NEW_DSP is a new DSP image, i'm not sure in which kernel it was introduced but maybe an upgrade is in order if you are using an older kernel.

---

