---
title: "Is now a good time to install Breezy?"
date: 2006-02-11
forum: The Cafe
---

### Post by gingermark on 2006-02-11
Hi,

(K)Ubuntu is the only Linux distro I have ever used. Started with Warty, switched to Kubuntu with Hoary and Breezy. I like it.

Recently I have upgraded my computer, and will soon install the OS. Some of the hardware came out after the release of Breezy, so I am concerned about it being recognised. The Linux Questions HCL says Breezy may well have trouble recognising my new motherboard's onboard ethernet card unless I use the "uli526x module".

I'm not great with hardware setup.

I was thinking I might well try another KDE-centric Debian-based distro until Dapper comes out. SimplyMEPIS recently released a new version. I was wondering if, in the short term, a recently released distro would provide better hardware support? And if, say I installed SimplyMEPIS or another Debian-based distro, could I then upgrade to Dapper in April by altering the sources.list? Or would that just lead to one hell of a mess?

I suppose another option could well be to just install Dapper now, but I'm not sure if I have the expertise to sort out any problems I might run into.

So I'm really not sure whether I should have fun checking out a few other distros, or stick with what I know and like, and bite the bullet and try to resolve any problems I come across.

Any thoughts on the matter would be appreciated.
Best regards,
gingermark.

---

### Post by BoyOfDestiny on 2006-02-11
[QUOTE=gingermark]Hi,

(K)Ubuntu is the only Linux distro I have ever used. Started with Warty, switched to Kubuntu with Hoary and Breezy. I like it.

Recently I have upgraded my computer, and will soon install the OS. Some of the hardware came out after the release of Breezy, so I am concerned about it being recognised. The Linux Questions HCL says Breezy may well have trouble recognising my new motherboard's onboard ethernet card unless I use the "uli526x module".

I'm not great with hardware setup.

I was thinking I might well try another KDE-centric Debian-based distro until Dapper comes out. SimplyMEPIS recently released a new version. I was wondering if, in the short term, a recently released distro would provide better hardware support? And if, say I installed SimplyMEPIS or another Debian-based distro, could I then upgrade to Dapper in April by altering the sources.list? Or would that just lead to one hell of a mess?

I suppose another option could well be to just install Dapper now, but I'm not sure if I have the expertise to sort out any problems I might run into.

So I'm really not sure whether I should have fun checking out a few other distros, or stick with what I know and like, and bite the bullet and try to resolve any problems I come across.

Any thoughts on the matter would be appreciated.
Best regards,
gingermark.[/QUOTE]
I hate to recommend it, but I'm loving dapper. Right now it feels "just right", everything I use/do works (with the exception of checkinstall ;) ). It has been rock solid...

Anyway my recommendation is to wait for dapper flight 4, maybe try a live cd to see how it likes your hardware. 

If you don't like reinstalling because of hassle, put /home on another partition. It makes it much easier to re-install ubuntu (if need be), and keep all your settings and personal data intact (usually I can have things as I like them in under 30min.)

Best of luck.

---

### Post by stoeptegel on 2006-02-11
[QUOTE=gingermark]And if, say I installed SimplyMEPIS or another Debian-based distro, could I then upgrade to Dapper in April by altering the sources.list? Or would that just lead to one hell of a mess?
[/QUOTE]

I wouldn't try that, that's just dancing with the devil if you ask me.

I run dapper myself by coincidence, i hit the wrong update button in adept without looking properly. So that made me upgrade from breezy to dapper, and i can say it is pretty usable already. 

Problems for me where:
konqueror crashes sometimes 
alsa complains sometimes 
media:/ slave isn't fixed (but that's the same in breezy AFAIK)
kopete needs work

For the rest i dunno about your hardware, there might be better support but i can only guess meself. Better if someone else with more knowlegde about this shares his/her thought.

---

### Post by ssam on 2006-02-11
try the breezy live CD, that should give you a good indication of whether it'll work.

dapper still is unstable. in the last few days networking broke for quite a few people. have a look at [https://wiki.ubuntu.com/DapperReleaseSchedule](https://wiki.ubuntu.com/DapperReleaseSchedule) . the feature freeze is fairly soon. after that risk of breakage should be lower.

---

