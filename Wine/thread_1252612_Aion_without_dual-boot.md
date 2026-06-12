---
title: "Aion without dual-boot?"
date: 2009-08-29
forum: Wine
---

### Post by Tanetris on 2009-08-29
My brother wants to play Aion (has it preordered already and everything), and he also wants to make the switch to Linux (which he has recruited me to help him with, as I switched roughly a year ago). As one can imagine, these desires are in conflict.

I understand that Aion is unlikely (understatement) to work in Wine, CrossOver, etc due to Gameguard. I prefer not to take the dual-booting route, as my own experiences with it involved getting more frustrated over having to reboot back and forth, splitting my IM and IRC logs, keeping up two e-mail clients, two sets of bookmarks, etc than at the individual downsides of either OS.

I forget what set me on this track exactly, but at some point in googling around about Gameguard and Wine, some page or other mentioned VirtualBox, a VM program. After getting an XP VM up and running, and a bit of fiddling to get the Direct3D support enabled, I decided to test out Guild Wars as a trial-run, as it was the closest DirectX game I had on hand. Now this computer is not current top-of-the-line, but it's no slouch: Core 2 Duo 2.4GHz and a GeForce 8800GTS, with 1.5GB of RAM devoted to the VM. At minimum graphics settings, I was getting 1 fps in GW. Adding -dx8 and -noshaders command line arguments I managed to get that up to 15 fps, still quite unplayable, and considering the respective sysreqs of GW and Aion, I can't imagine something that runs GW that poorly even attempting to run Aion. My understanding based on reading VirtualBox's forums is that this is because of the way the VM must emulate the video card and can't let things access the actual video card directly for... Reasons I don't understand.

Now, it's entirely possible that Aion will have less of a reduced performance in VM than GW happens to, but I'm not holding my breath on that. So my question to you, my good ubuntuforumers, is are there any other options besides dual-booting? Is there another VM program with better Direct3D support? Is there some workaround for tricking Gameguard into not freaking out over being run in Wine/CrossOver/etc? Is there something else I'm plain not thinking of?

Apologies if this is poorly-placed, but the Gaming & Leisure stickies were pretty emphatic about Windows games questions going here, and this is more about getting Aion to work in whatever way than about VM as a possible solution.

Thanks in advance.

---

### Post by Tanetris on 2009-09-01
I'm gonna give this one less-than-optimistic bump, and if it falls off the first page replyless again, I'll just slink off to do a dual-boot. Thanks anyway, anyone who looked.

---

### Post by ElSlunko on 2009-09-02
I can't say I've tried it, but vmware is suppose to have good opengl support. Not sure if it will help or if it even applies to Aion specifically, but you can start your research there.

---

### Post by topcat5 on 2009-09-05
Gameguard installs and works like virus which is why it won't be allowed to run under Wine and most likely a VM because it doesn't play by the rules.    It's causes endless problems on Windows machines with apps that have nothing to do with the game.    I looked at Aion with interest, but after seeing what Gameguard does, I won't bother with Aion as I don't want even my windows machine permanently screwed up.   

It's a shame as the game looked promising, but vendors should not be so paranoid they are going to make these kinds of changes to the Windows OS.   (others simply don't allow it which is why there is trouble)

---

### Post by utdream on 2009-11-23
AION doesn't include gameguard any more. they didn't include it in the production release because there were too many complaints and too many problems with it in beta.

That said, I dont believe AION supports OpenGL - not that I can find anyway. Their engine config file is "encrypted" as well, so it's difficult to change by hand and experiment.

It's pretty frustrating when companies try to be "secure" and only succeed in screwing over those of us who legitimately want to use their software on various platforms.

---

### Post by Extol11 on 2009-11-23
I'm going to give it a try on my 4870 card with a spare drive I have ( I don't want to screw up my perfectly fine Ubuntu 9.10 install) and tell you how it goes. 

And yes, it no longer has gameguard. But we have to keep in mind they're still fixing a few bugs in the game. Nothing big, just a few rough edges but in wine it could be worse.

---

### Post by beastrace91 on 2009-11-23
Quiet a few people have [reported good results](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17877) with Aion since GameGaurd has been removed. Also worth noting is that all the Gold/Silver ratings there appear to be on Wine 1.1.32 (while the two under 1.1.33 are bronze rated)

Play with settings and see what you can do :)

Cheers,
~Jeff

---

### Post by ElSlunko on 2009-11-24
With a patch for WINE I find it marginally playable. The FPS is perhaps 20-30% of what it is in Windows so that kind of sucks. I believe the game uses Direct X so here's to hoping someone figures out how to up the FPS significantly.

---

### Post by beastrace91 on 2009-11-24
> **ElSlunko said:**
> With a patch for WINE I find it marginally playable. The FPS is perhaps 20-30% of what it is in Windows so that kind of sucks. I believe the game uses Direct X so here's to hoping someone figures out how to up the FPS significantly.

Give it a try in Cedega... I know it has much better FPS for some newer DX applications than Wine does.

~Jeff

---

### Post by Extol11 on 2009-12-01
I just gave it a try and installing from the disc is a no go. It tries to install Direct X 9.0C (without making an explicit warning about it first) and this messed up my wine. GW doesn't play well now thanks to that. I will continue testing as soon as I get another spare drive because the one I got wants to die (too many bad sectors).

---

### Post by brian70809 on 2009-12-01
It's a hassle to get this working, but I did get it done and it works pretty well.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=17877](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17877)

Wine HQ has the info on getting this working.

You have to do some customisation of Wine, use Winetricks, and install in windows or Virtualbox first to a sharefolder.   Then do the customisation they say to do for your region, etc.  You will launch the game directly and not use the launcher at all.

Some people have written some scripts to help start the game up.

There are some bugs and mouse issues but on my machine it was decent.

Q6600 at 3.2ghz
3 megs Ram
GTX 260 Nvidia card.

Good luck!

---

### Post by Extol11 on 2009-12-05
> **brian70809 said:**
> It's a hassle to get this working, but I did get it done and it works pretty well.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=17877](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17877)

Wine HQ has the info on getting this working.

You have to do some customisation of Wine, use Winetricks, and install in windows or Virtualbox first to a sharefolder.   Then do the customisation they say to do for your region, etc.  You will launch the game directly and not use the launcher at all.

Some people have written some scripts to help start the game up.

There are some bugs and mouse issues but on my machine it was decent.

Q6600 at 3.2ghz
3 megs Ram
GTX 260 Nvidia card.

Good luck!

I'll be trying it this week, hopefully.

---

### Post by imnotjack on 2013-01-26
i will try this as well a couple of different ways. there is an app on the software center called playonlinux. I will try a few things in that and see if it works. this app is the only thing that i can see that got pirates of the carrbean online to work under ubuntu. not that the games are remotly similar but i hold hope this might be able to help anyway. im running ubuntu 12.04 64 bit.fingers crossed.

---

### Post by imnotjack on 2013-01-26
aion is currently in testing in the playonlinux app. im installing it to see how it looks now. im using the most recent stable version of playonlinux that i downloaded from the website. when it is installed i will post back.

---

### Post by imnotjack on 2013-01-27
it works but its the international version. its not aion ascension. you cant use the same characters. i believe the servers for it are in europe. it plays well but it is jumpy at half the time on the lowest graphics. its not my hardware i know that. i have an amdfx processor black edition 3.3 ghz 6 core unlocked to 4.1ghz. 16 gb of ddr3 ram at 1866mhz. and an nvidia geforce 9400 gt series. anyways, thats all for tonight.

---

