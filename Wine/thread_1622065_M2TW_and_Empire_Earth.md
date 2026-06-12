---
title: "M2TW and Empire Earth"
date: 2010-11-15
forum: Wine
---

### Post by Urhungry on 2010-11-15
I have used Ubuntu off and on for around a year now, however every distro I try just dosent seem to work quite as well, so I always wind up back here. Anyway, I currently have a dual boot of Windows 7 and Fedora 14. I would like to change this to all Ubuntu. I used a Mac for several years, and missed many of my games dearly while I did, so I am reluctant to remove Windows entirely. This brings me to my question and my reason for this post. I only have a few games that I really need to retain the ability to play. These are:
Medieval 2 Total War (preferably kingdoms as well)
Empire Earth (expansion or regular)
Age of Empires 2 (expansion or regular)
Sim City 3000 (has a Linux version)
Steam(and Portal)

Everything else I can live without. I know that I could install ubuntu in virtualbox and test each of these games in wine, but that would take several hours, so I figured that if someone else already had the answer, why not ask them?
I have managed to get Age of Empires 2 Expansion working in 9.10, but I haven't tried it in 10.10. I am a fairly competent computer user, so I can try complicated solutions if necessary. And yes, I did check winehq, most of these were untested.  Thanks for any help!

---

### Post by Urhungry on 2010-11-15
Anyone? Any info is helpful.

---

### Post by nerdy_kid on 2010-11-16
I would check out the app database at [http://appdb.winehq.org/](http://appdb.winehq.org/)
Should have all those apps in there :)

---

### Post by Urhungry on 2010-11-16
I mentioned that I already did. Most of these are untested with 10.10. Thanks though.

---

### Post by nerdy_kid on 2010-11-16
> **Urhungry said:**
> I mentioned that I already did. Most of these are untested with 10.10. Thanks though.

oh sorry, missed that :/

---

### Post by Urhungry on 2010-11-16
That's ok.

---

### Post by ka9qlq on 2011-02-19
Well if you find out throw me a bone. ok?

---

### Post by mike-laptop-dot-local on 2011-03-19
Urhungry,

I found this thread while tracking down a M2TW problem for myself. I can help with M2TW and Steam:

I've had good success with TW games by 'building' Steam on its own wine prefix (using wine 1.3.15), then using winetricks to install DirectX and a few other packages (corefonts, a few vcruns) to the same prefix.

Unfortunately, the M2TW Launcher via Steam needs either 1.1 or the 2.0 .NET package via winetricks, and right now I'm experiencing a nasty 'can't uninstall, therefore can't re-install' situations with it. However, there's a [workaround on the Steam forums]("http://forums.steampowered.com/forums/showthread.php?t=784119") that should get around this.

Installing mods is a bit hit and miss. I had good luck in Steam with 'add a non-Steam game' and then pointing to the mod installer files. Success with DLV and TATW; Stainless Steel installed and ran but refused to install the campaign.

It ran well for me, but (of course) I have to run a patched compile of wine to run Empire or Napoleon, which doesn't seem to play nice with M2TW.

Edit: If you already have M2TW/Kingdoms with mods installed in Windows, you can [run wine/Steam and use the same installs as in Windows]("http://developer.valvesoftware.com/wiki/Steam_under_Linux#Step_2:_installing_steam").


Good luck with it

---

### Post by ka9qlq on 2011-03-22
Darn....that looks complex

---

