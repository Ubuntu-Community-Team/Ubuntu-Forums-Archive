---
title: "Whats not in Ubuntu......"
date: 2006-08-10
forum: The Cafe
---

### Post by KingBahamut on 2006-08-10
that is in the Proprietary build of Freespire 

there top 20 list 
    * 1 Microsoft Windows Media Technology
    * 2 Quicktime 7 Software
    * 3 mp3 Software Decoder
    * 4 RealPlayer Software
    * 5 Sun Java 2 Platform Standard Edition Runtime Environment 5.0
    * 6 Macromedia Flash Plug-In
    * 7 Bitstream Fonts
    * 8 Gizmo Project
    * 9 Agere Systems Modem Drivers
    * 10 ATI Technologies Linux Driver
    * 11 Conexant/Linuxant HCF PCI Modem Driver
    * 12 Conexant HSF Modem Driver
    * 13 Intel Modem Drivers
    * 14 QEMU Accelerator Module (aka kqemu)
    * 15 Lucent linmodem driver
    * 16 MADWIFI Wireless Drivers
    * 17 NVIDIA Accelerated Video Drivers
    * 18 PCTEL Modem Driver
    * 19 Ralink Wireless Driver
    * 20 SmartLink Modem Driver

Im assuming these are preconfigured at install. What my question is, how much of this is easily installed? Used? Difficult to install?

---

### Post by DoctorMO on 2006-08-10
* 1 Microsoft Windows Media Technology - Not allowed, should be banned from all computers in the world. (copyrights, parents)
* 2 Quicktime 7 Software - Not allowed (copyrights, patents)
* 3 mp3 Software Decoder - Not allowed in the USA (patents)
* 4 RealPlayer Software - Not allowed (copyrights, patents)
* 5 Sun Java 2 Platform Standard Edition Runtime Environment 5.0 (copyrights (soon maybe))
* 6 Macromedia Flash Plug-In (copyrights)
* 7 Bitstream Fonts (copyrights)
* 8-X Drivers Binary only, copyright issues, not allowed.

Sorry but all those things have problems which makes them unsuitable for a Linux computer, installing them could have undesirable effects such as price increases, law suits, going to jail, system instability, system insecurity and general foo bar ness.

---

### Post by Brunellus on 2006-08-10
I think that's a fair set of packages to include for commercial redistribution on a desktop, provided software freedom is not the main criterion of evaluation.

Java, flash, media codecs--that adds up to a useable "out of the box" system.  Not bad, I say.  (but why qemu?!)  

Now if only Linspire would fix that stupid "w00t w00t we're all r00t!" permissions scheme they run by default, they could step up and see how they stack up against SLED.

---

### Post by John.Michael.Kane on 2006-08-10
Ubuntu has fonts with the label **Bitstream** listed under font preferences. unless thats a diffrent version.

---

### Post by AndyCooll on 2006-08-10
19. Ralink wireless drivers.

Aren't these in Ubuntu? I'm not a wireless drivers expert, however my pcmcia and usb wireless connections have interface names ra0 and rausb which installed "out of the box". I thought this was because they were using Ralink drivers?!

---

### Post by GuitarHero on 2006-08-10
Most of those things are easy to install.  Whether they are legal or not is a different question.

---

### Post by TravisNewman on 2006-08-10
> **Brunellus said:**
> I think that's a fair set of packages to include for commercial redistribution on a desktop, provided software freedom is not the main criterion of evaluation.

Java, flash, media codecs--that adds up to a useable "out of the box" system.  Not bad, I say.  (but why qemu?!)  

Now if only Linspire would fix that stupid "w00t w00t we're all r00t!" permissions scheme they run by default, they could step up and see how they stack up against SLED.
Why qemu? It's not qemu so much as **k**qemu, the non-free acceleration driver that someone created for it.

---

### Post by Iandefor on 2006-08-10
> installing them could have undesirable effects such as price increases, Freespire is distributing them for free.
>  law suits, going to jail,  How are they going to get sued when they're fully licensed?
> system instability, system insecurity and general foo bar ness. This reeks of FUD. Can I get a more in-depth statement?

The only problems I can see are the binary-only drivers.

---

### Post by atrus123 on 2006-08-10
I guess I don't really understand just how it is that Freespire is able to bundle this stuff with their upcoming release.  I mean, some of it must be downright illegal to bundle in many countries.  For example, doesn't the SUN Java license prohibit this sort of deployment?

---

### Post by John.Michael.Kane on 2006-08-10
KingBahamut could it be that linspire paid the licence fees,and thus the are able to offer these programs.

---

### Post by bruce89 on 2006-08-10
> **SD-Plissken said:**
> KingBahamut could it be that linspire paid the licence fees,and thus the are able to offer these programs.

This is the case, AFAIK.

> **SD-Plissken said:**
> Ubuntu has fonts with the label **Bitstream** listed under font preferences. unless thats a diffrent version.

These are the Bitstream Vera fonts, which are available here - [http://www.gnome.org/fonts/](http://www.gnome.org/fonts/)

Not sure what fonts in Freespire are nonfree.

---

### Post by Kernel Sanders on 2006-08-10
> **Brunellus said:**
> I think that's a fair set of packages to Now if only Linspire would fix that stupid "w00t w00t we're all r00t!" permissions scheme they run by default, they could step up and see how they stack up against SLED.

IIRC they fixed that a few versions ago, the rumour didnt die with the problem though. Its a common Linspire misconception.

---

### Post by Brunellus on 2006-08-10
> ***John* said:**
> IIRC they fixed that a few versions ago, the rumour didnt die with the problem though. Its a common Linspire misconception.
Fixed?  Really?

The shop down the road from me sells linspire OEM'd boxes.  I went on Saturday and did a CTRL + ALT + F1 to get to a console. 

login:  root
password :  

I hit return, leaving the password blank.

I was greeted with

root@linspire #

w00t w00t, we're all r00t.

---

### Post by TravisNewman on 2006-08-10
That could be a lousy setup issue though. It's easy for anyone to set up a blank root password.

But still that's a mess if they're doing that.
If you have root access you should go in when they're busy sometime and change things up on them. I guarantee they'd change that assuming they know what they're doing.

---

