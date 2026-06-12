---
title: "Make Wireless Configuration Easier Using PCLOS' Method"
date: 2008-07-11
forum: Ubuntu Brainstorm
---

### Post by Lazy-buntu on 2008-07-11
One of the biggest reasons newbies give up on Linux is wireless configuration. Broadcom is one of the most dreaded names to many people, but it doesn't have to be that way.

I tried other distros (Ubuntu, Fedora, openSUSE), but the one thing that would never work was my wireless.

I could configure Ndiswrapper, it would activate my wireless card, I could see networks, but I could never connect. After multiple threads and attempts, I tried another distro: PCLOS Gnome 2008.

The amazing thing about PCLOS Gnome 2008: I could get my wireless card to work from the Live CD! I believe it uses drakconf or something along those lines. A GUI version of Ndiswrapper is used and you pick the driver from a list. You enter in your WEP or WPA key (if needed), and bam! wireless is up and working. It also configures wireless to work on startup.

I would love to multi-boot PCLOS and another distro, but the wireless never works in other distros.


Here's the point of the thread: why do other popular distros ignore this method? Maybe they haven't experienced this type of configuration before, but I wanted to suggest some cross-distro discussion. That way other distros could come up with similar methods or use the current drakconf.

I also posted this at: 
[http://www.pclinuxos.com/index.php?option=com_smf&Itemid=58&topic=47635.0](http://www.pclinuxos.com/index.php?option=com_smf&Itemid=58&topic=47635.0)
[http://linuxgator.org/forums/viewtopic.php?f=6&t=1115](http://linuxgator.org/forums/viewtopic.php?f=6&t=1115)

---

### Post by Lazy-buntu on 2008-07-11
Here are some visuals: (see attachments)

Of course, if you have no WEP or WPA, then you skip that step.

I think the step after that asks if you want the interface to load at startup.

It is very cut and dry, and works quickly :)

---

### Post by OBnascar on 2008-07-12
> **Lazy-buntu said:**
> One of the biggest reasons newbies give up on Linux is wireless configuration. Broadcom is one of the most dreaded names to many people, but it doesn't have to be that way.

And I'll add another: **Atheros** 



> The amazing thing about PCLOS Gnome 2008: I could get my wireless card to work from the Live CD! I believe it uses drakconf or something along those lines. A GUI version of Ndiswrapper is used and you pick the driver from a list. You enter in your WEP or WPA key (if needed), and bam! wireless is up and working. It also configures wireless to work on startup.
PCC is open source, so why wouldn't Ubuntu want to use it, something that makes wireless EASY !



> Here's the point of the thread: why do other popular distros ignore this method? That is the question of the year my friend.

---

### Post by basenvironment on 2008-07-13
debian based distros usually have ndisgtk which is a GUI to configure ndiswrapper....

---

### Post by MissionImpossible on 2008-07-13
> **Lazy-buntu said:**
> One of the biggest reasons newbies give up on Linux is wireless configuration. Broadcom is one of the most dreaded names to many people, but it doesn't have to be that way.

I tried other distros (Ubuntu, Fedora, openSUSE), but the one thing that would never work was my wireless.

I could configure Ndiswrapper, it would activate my wireless card, I could see networks, but I could never connect. After multiple threads and attempts, I tried another distro: PCLOS Gnome 2008.

The amazing thing about PCLOS Gnome 2008: I could get my wireless card to work from the Live CD! I believe it uses drakconf or something along those lines. A GUI version of Ndiswrapper is used and you pick the driver from a list. You enter in your WEP or WPA key (if needed), and bam! wireless is up and working. It also configures wireless to work on startup.

I would love to multi-boot PCLOS and another distro, but the wireless never works in other distros.


Here's the point of the thread: why do other popular distros ignore this method?
The "GENIUS" of PCLos (and some others with little to no assets to get sued for) is in the fact that they include the binary firmware packages on their distro Cds or in their repos but the MAINSTREAM - commercially owned/backed or ethically bound - distros do not because it is ILLEGAL to do so. Simple as that.

The following excerpt from a [Distrowatch ]("http://distrowatch.com/weekly.php?issue=20080114&mode=67")Comments sections discussion earlier this year might explain it more clearly:
[I]30 • @7 (by Adam Williamson on 2008-01-14)
There is, in fact, no reliable way to legally include a driver for a Broadcom wireless chip that will work without external downloads.

The native driver - bcm43xx, or b43 - requires firmware to work correctly. This firmware can *only* be acquired by extracting it from a Windows driver for the card. Every available copy of the Windows driver for Broadcom cards is licensed in such a way that it cannot legally be packaged into a Linux distribution.

Using ndiswrapper, the alternative method, of course also requires the Windows driver.

The only way either method can work without an external download is if you already have a Windows driver for the chip on your system, but this cannot be relied upon.

[COLOR="Red"]Any distro which allows a Broadcom chip to work out of the box without an external download (or without discovering a copy of the Windows driver already present on your machine) is breaking the law by including either a full Windows driver, or the firmware extracted from it, in clear breach of the license.[/COLOR]

67 • 7 • MiniMe (by Gene) (by Anonymous on 2008-01-15)
The ndiswrapper files are right on the livecd for bcm43xx support. I know because I tested it on an HP laptop and was up and going in less than a minute. ndiswrapper-bcmwl5 (bcm43xx driver) ,ndiswrapper-bcmwl5a (bcm43xx)a and ndiswrapper-lsbcmnds6.

74 • @67 (by Adam Williamson on 2008-01-15)
Then that is against the license of those drivers, as I wrote.
[/I]

---

### Post by Lazy-buntu on 2008-07-13
I've used ndisgtk before and it was no where near efficient as the drakconf method. I did manage to get a card working with it, but the connection was unstable after reboots.


As for the legality: why not provide something similar to drakconf, but have the user find the correct driver? I don't think many people have a problem finding the correct driver. Most of the problems arise from the installation or all the unnecessary steps preceding/following the installation of the driver.

A distro should not rely on a working internet connection out of the box. Some people don't have access to a wired connection, and shouldn't be damned just because the distro won't include an efficient configuration tool after install.



Bottom line, if people are serious about increasing the number of Linux users, then wireless compatibility has to be increased one way or another. Since Broadcom isn't exactly jumping on board, why not take the initiative to use a working configuration tool--or--create a similar tool that meets the distribution's 'ethics?'

---

### Post by smartboyathome on 2008-07-14
> **Lazy-buntu said:**
> Bottom line, if people are serious about increasing the number of Linux users, then wireless compatibility has to be increased one way or another. Since Broadcom isn't exactly jumping on board, why not take the initiative to use a working configuration tool--or--create a similar tool that meets the distribution's 'ethics?'

If we included the driver, using the above suggestion, then it has been told that it would be illegal, but if Ubuntu created a similar tool, it would mean that people would still have to go online and get the drivers. This is the problem with Ubuntu, unless they want to break the law in order to change it (like during the approx 1920-30s case where a teacher taught evolution even though it was banned from being taught in school), but elliminate itself as a competitor in the OS market.

---

### Post by OBnascar on 2008-07-14
> **smartboyathome said:**
> If we included the driver, using the above suggestion, then it has been told that it would be illegal, but if Ubuntu created a similar tool, it would mean that people would still have to go online and get the drivers. This is the problem with Ubuntu, unless they want to break the law in order to change it (like during the approx 1920-30s case where a teacher taught evolution even though it was banned from being taught in school), but elliminate itself as a competitor in the OS market.
Ubuntu will sooner or later **eliminate itself** from the OS market by not resolving the wireless issue, Ubuntu will never successfully be ready for prime time, converting MS user's to use Ubuntu is never going to happen unless something changes, but MS user's will find out that there are other Linux options, like find a distro that does support wireless better.

---

### Post by steeleyuk on 2008-07-14
Ubuntu will eliminate itself much sooner if it breaks copyright and licensing issues.

If people were that concerned about wireless and really willing to give Linux a go they'd make a small sacrifice and find a Linux compatible wireless card (btw, I know this isn't possible in all cases but there are plenty of people out there complaining about wireless but not actually willing to consider alternative ways of making it work - i.e. buying a new card).

---

### Post by OBnascar on 2008-07-14
> **steeleyuk said:**
> Ubuntu will eliminate itself much sooner if it breaks copyright and licensing issues.

If people were that concerned about wireless and really willing to give Linux a go they'd make a small sacrifice and find a Linux compatible wireless card (btw, I know this isn't possible in all cases but there are plenty of people out there complaining about wireless but not actually willing to consider alternative ways of making it work - i.e. buying a new card).Very good point indeed !

---

### Post by nitePhyyre on 2008-07-15
Unless, like most people using wireless, you are on a laptop.

---

### Post by steeleyuk on 2008-07-15
Support Intel by buying stuff with their kit in, presuming you're in the market for a laptop. I agree its more difficult in terms of laptops/tablet PC's but again, if people were that serious about trying Linux they could find a compatible USB or PCMCIA card.

---

### Post by Lazy-buntu on 2008-07-16
Buying a new card isn't a solution to the problem. Personally, I'm not willing to spend the money for a new wireless card for my laptop. Maybe for a desktop I'd be willing to, but not my laptop.

Creating an auto-ndiswrapper would be the most plausible and acceptable solution.


I just saw this on Digg today. I'll try it out with Hardy if I get around to it.

[https://launchpad.net/auto-ndiswrapprer](https://launchpad.net/auto-ndiswrapprer)

---

### Post by smartboyathome on 2008-07-16
> **Lazy-buntu said:**
> Buying a new card isn't a solution to the problem. Personally, I'm not willing to spend the money for a new wireless card for my laptop. Maybe for a desktop I'd be willing to, but not my laptop.

Creating an auto-ndiswrapper would be the most plausible and acceptable solution.


I just saw this on Digg today. I'll try it out with Hardy if I get around to it.

[https://launchpad.net/auto-ndiswrapprer](https://launchpad.net/auto-ndiswrapprer)

Though like has been said, that only possible solution may not be legal or if it is done legally will not be all that functional due to internet connectivity being required.

---

### Post by OBnascar on 2008-07-16
> **steeleyuk said:**
>  if people were that serious about trying Linux they could find a compatible USB or PCMCIA card.
Ok then, please list some Linux compatible USB & PCMCIA cards.

---

### Post by OBnascar on 2008-07-16
> **Lazy-buntu said:**
> 
Creating an auto-ndiswrapper would be the most plausible and acceptable solution.

I just saw this on Digg today. I'll try it out with Hardy if I get around to it.

[https://launchpad.net/auto-ndiswrapprer](https://launchpad.net/auto-ndiswrapprer)

Please post back with you results, I am interested, it is the first I have heard of it.

---

### Post by Lazy-buntu on 2008-07-16
:(

Didn't work...this was on a fresh install, ndiswrapper from the Hardy Heron CD, and using the bcmwl5.inf and .sys files from my working wireless on PCLOS 2008 Gnome. 

I also tried it a separate time with the bcmwl5.inf and .sys files from HP.


Note: I didn't have an internet connection, so I opted for the offline method.


Anyone have success with that tool?

---

### Post by OBnascar on 2008-07-18
> 
Quote:
Originally Posted by steeleyuk: 
if people were that serious about trying Linux they could find a compatible USB or PCMCIA card.

Quote:
Originall Posted by OBnascar:
Ok then, please list some Linux compatible USB & PCMCIA cards

I guess he does not know of any........lol

Here is a start:
[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)
Some good info on **Linux compatible wireless devices**.

---

