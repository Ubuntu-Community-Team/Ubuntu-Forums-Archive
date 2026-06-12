---
title: "WoW in Jaunty"
date: 2009-04-23
forum: Wine
---

### Post by horgabob on 2009-04-23
So I posted about this in an already existant thread, but no one had an answer, so hopefully posting here will bring up some fresh ideas.

I just installed Jaunty and I'm trying to get WoW to work with Wine. I followed the guides on installing/configuring Wine and installing WoW. When I load WoW, I will freeze either as I'm loading into the game, or directly after the game loads. 

When I had 8.10 there was a driver to activate under System>Administration>Hardware Drivers, and in Jaunty there is nothing there so this might be the reason, though I'm not sure. (Note: I never ran WoW in 8.10 so I'm not sure if it would have worked then, is there a way to downgrade and try?)

Also note that I am running it with opengl.

Here are some specs:
120GB Hard Drive
1 GB RAM
2.8 GHz processor
X1300/X1500 ATI Graphics card

Please help! I hate playing on my laptop!

---

### Post by hikaricore on 2009-04-23
You may need to install your video drivers manually.

---

### Post by horgabob on 2009-04-23
any guidance on how to do that/where to find them?

---

### Post by hikaricore on 2009-04-23
I'm not familiar with ATI and don't have much time to dig around right now, but I'm sure there are guides around the forum if you give it a search.  :)

---

### Post by NightMKoder on 2009-04-24
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by horgabob on 2009-04-24
ok so, before seeing that last post, i followed another guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)
and now when I log on I get a black screen with random lines at the top....

Not good, I can't see anything. I also tried recovery mode, and it doesn't seem to help...

---

### Post by =^,^= on 2009-04-24
You cant install the latest ati drivers in jaunty!

They dropped support for pre hd2000 cards in their latest drivers!

And jaunty will only take the latest drivers!

---

### Post by horgabob on 2009-04-24
Wonderful....is there a way to undo it now? Or am I pretty much screwed unless I reinstall?

---

### Post by =^,^= on 2009-04-24
> **horgabob said:**
> Wonderful....is there a way to undo it now? Or am I pretty much screwed unless I reinstall?

I would install hardy.

You get longer support and its well matured and stable!

Plus you can install the latest ati driver available for x1000 cards.

---

### Post by hikaricore on 2009-04-24
Or you could just manually install an older version of the driver instead of installing an older outdated version of Linux..

---

### Post by =^,^= on 2009-04-25
> **hikaricore said:**
> Or you could just manually install an older version of the driver instead of installing an older outdated version of Linux..

Only the old drivers wont let you install them on jaunty......

---

### Post by Laibcoms on 2009-04-25
Just get [PlayOnLinux](http://www.playonlinux.com/en/download.html#ubuntu).  It should work fine ;)

That's what I use now after doing a clean-upgrade to Jaunty.  Less time wasted on WINE configuration, and allows me to run as many games as possible w/o re-tweaking wine for a particular game.

For mine tho, since I have a WinXP and my games are installed there by default (shared PC), I just tweaked it a little to point to my WinXP installation (Make Link) [except for NWN2].

See if it will help.

---

### Post by =^,^= on 2009-04-25
> **Laibcoms said:**
> Just get [PlayOnLinux](http://www.playonlinux.com/en/download.html#ubuntu).  It should work fine ;)

That's what I use now after doing a clean-upgrade to Jaunty.  Less time wasted on WINE configuration, and allows me to run as many games as possible w/o re-tweaking wine for a particular game.

For mine tho, since I have a WinXP and my games are installed there by default (shared PC), I just tweaked it a little to point to my WinXP installation (Make Link) [except for NWN2].

See if it will help.

Hes having difficulty with drivers for their ati card!

Playonlinux wont be much help until thats sorted! ^,-

---

### Post by hikaricore on 2009-04-25
I just kinda assumed that ATI released binary driver installers like NVIDIA does.
It shouldn't matter what distro of Linux or what realease you try to install them on.

---

### Post by =^,^= on 2009-04-25
> **hikaricore said:**
> I just kinda assumed that ATI released binary driver installers like NVIDIA does.
It shouldn't matter what distro of Linux or what realease you try to install them on.

Well it does!

---

### Post by Laibcoms on 2009-04-25
> **=^,^= said:**
> Hes having difficulty with drivers for their ati card!

Playonlinux wont be much help until thats sorted! ^,-

Oh... my mistake... I missed that :/

:KS

---

### Post by horgabob on 2009-04-26
It's OK, I just went back to Intrepid 8.10 and it works now. Only problem is I get terrible lag.

I set it to open in opengl, but I get all kinds of crazy lines and random colors.

Either way, the bad performance is probably my computer:

2.8GHz Single Core CPU
1 GB RAM
ATI X1300/X1550 Video Card

---

### Post by weezerisrock on 2009-04-27
This page should be able to help you with any issues you have.

[http://www.wowwiki.com/Troubleshooting_Wine](http://www.wowwiki.com/Troubleshooting_Wine)

There are a lot of fixes in there for ati cards.  And welcome back to intrepid.  I have to do the same thing tomorrow. :(

The reason you had a problem with Jaunty is because ati removed support for your video card in their new drivers.  At the same time, Ubuntu uses the updated x server which is only compatible said new drivers from ATI.

TL;DR, you're screwed unless you want the open source drives which at the moment are way slow.

---

### Post by zoward on 2009-04-28
ATI dropped support for the X1xxx line of video cards in their latest proprietary driver (Catalyst version 9.4).  Unfortunately, the version of X that Jaunty uses has an overhauled driver system that is only supported by - you guessed it - Catalyst 9.4!  You are stuck with the open source driver.  There are a lot of tweaks you can  use to speed the driver up, and compiz works great with it - it's worth spending some time with Google on this.  Unfortunately  3D support is still being worked on.  ATI has a full time programmer working on adding full 3D support to the open source drivers.

I feel your pain.  I'm typing this on a Jaunty-based laptop with an ATI x1200 chipset.  I get about a frame a second in WoW - totally unplayable.  Then again, it didn't work at all under 8.10.  I suspect it would work under 8.04, but my wireless chipset probably won't.  So it's Vista or wait.  And I'm waiting.

---

### Post by weezerisrock on 2009-05-01
what problems did you have in 8.10?  Wow has been very stable for me in 8.10.  I don't mind helping you through it if you like.

---

### Post by NightMKoder on 2009-05-01
> **Laibcoms said:**
> Just get [PlayOnLinux](http://www.playonlinux.com/en/download.html#ubuntu).  It should work fine ;)

That's what I use now after doing a clean-upgrade to Jaunty.  Less time wasted on WINE configuration, and allows me to run as many games as possible w/o re-tweaking wine for a particular game.

For mine tho, since I have a WinXP and my games are installed there by default (shared PC), I just tweaked it a little to point to my WinXP installation (Make Link) [except for NWN2].

See if it will help.

You are suggesting a serious bad idea here - [http://wiki.winehq.org/FAQ#head-497f1a295d53dd3444f211df2b13312c7767afa2](http://wiki.winehq.org/FAQ#head-497f1a295d53dd3444f211df2b13312c7767afa2) . NEVER point wine to a windows installation. I'm sort of amazed anything still worked. Wine is *not* an emulator, and it CANNOT read the windows registry files, so there is no reason to do it. You're best off just copying the games to your linux partition instead of risk wine messing with your windows.

As for playsonlinux, it's a nice suite, but I personally don't think its very useful. Many pol scripts are outdated and then you hear complaints about low fps when people are actually running wine 1.0. You may get some support on the pol forums, but the majority of support for wine is either wine or crossover (and maybe cedega, but not sure).

---

### Post by jprophet420 on 2009-05-05
> **NightMKoder said:**
> You are suggesting a serious bad idea here - [http://wiki.winehq.org/FAQ#head-497f1a295d53dd3444f211df2b13312c7767afa2](http://wiki.winehq.org/FAQ#head-497f1a295d53dd3444f211df2b13312c7767afa2) . NEVER point wine to a windows installation. I'm sort of amazed anything still worked. Wine is *not* an emulator, and it CANNOT read the windows registry files, so there is no reason to do it. You're best off just copying the games to your linux partition instead of risk wine messing with your windows.

As for playsonlinux, it's a nice suite, but I personally don't think its very useful. Many pol scripts are outdated and then you hear complaints about low fps when people are actually running wine 1.0. You may get some support on the pol forums, but the majority of support for wine is either wine or crossover (and maybe cedega, but not sure).

Im sorry but that information is incorrect, you do not need the registry settings in WoW or WC3, you can even run WoW in a windows system without an install, i do it all the time. Its not true of all games/apps, but i have tried and tested it with WoW many times.

*edit* Just tried it, works great (in linux now)

As far as Play on Linux, its meh, wine is better IMHO also. wine 1.1.20 and winetricks work great together, winetricks can DL and install directX 9 for you. Its running at just about the same speed (fps) as vista, however slower than XP.

---

### Post by MonkeyPlus on 2009-05-06
I have a slight problem in Jaunty

I'm installing WoW and BC for my fiancee - note that she does not have WotLK and isn't likely to buy it any time soon - and I've a problem with blizzard's updating software.

Basically, to play BC without WotLK you need a special update that puts you into version 3 without the expansion. The file that has been downloaded is called 

WoW-installer-2.x.x.x-to-3.0.1.8874-x86-Win-enGB.exe

When I run it, it goes through a new BC installer but when it gets to the EULA, I can't click 'Agree' even after I have scrolled to the bottom. I have tried with scroll wheel, scroll bar and keys with the exact same results.

Anyone know a work around?

---

### Post by jprophet420 on 2009-05-07
> **MonkeyPlus said:**
> I have a slight problem in Jaunty

I'm installing WoW and BC for my fiancee - note that she does not have WotLK and isn't likely to buy it any time soon - and I've a problem with blizzard's updating software.

Basically, to play BC without WotLK you need a special update that puts you into version 3 without the expansion. The file that has been downloaded is called 

WoW-installer-2.x.x.x-to-3.0.1.8874-x86-Win-enGB.exe

When I run it, it goes through a new BC installer but when it gets to the EULA, I can't click 'Agree' even after I have scrolled to the bottom. I have tried with scroll wheel, scroll bar and keys with the exact same results.

Anyone know a work around?

Yep, get connected on a previous client and download the patch from bliz directly. The only way that wont work is if youre connecting to certain 'private' servers.

---

### Post by jmadgin on 2009-05-07
That window, uses something related to MS Internet Explorer. All you need to do is either install IE in wine or in crossover.

---

### Post by jprophet420 on 2009-05-12
> **MonkeyPlus said:**
> I have a slight problem in Jaunty

I'm installing WoW and BC for my fiancee - note that she does not have WotLK and isn't likely to buy it any time soon - and I've a problem with blizzard's updating software.

Basically, to play BC without WotLK you need a special update that puts you into version 3 without the expansion. The file that has been downloaded is called 

WoW-installer-2.x.x.x-to-3.0.1.8874-x86-Win-enGB.exe

When I run it, it goes through a new BC installer but when it gets to the EULA, I can't click 'Agree' even after I have scrolled to the bottom. I have tried with scroll wheel, scroll bar and keys with the exact same results.

Anyone know a work around?

have you installed directX9 yet? there are at least 2 ways i know of. with winetricks or if youre using playinlinux (both mentioned earlier).

2 make the launcher work you need to install 'gecko'. it (wine) will ask you if you wish to install it. It should work after replying yes and finishing the installation.

as amatter of fact that will only make the html work, you only need to use the buttons on the bottom of the client, which work by default. I took the time to install mine because now that im paying for it, i want it to look pretty.

---

