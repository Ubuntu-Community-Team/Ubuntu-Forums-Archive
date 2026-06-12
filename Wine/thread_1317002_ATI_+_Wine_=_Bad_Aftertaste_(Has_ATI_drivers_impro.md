---
title: "ATI + Wine = Bad Aftertaste (Has ATI drivers improve at all?)"
date: 2009-11-06
forum: Wine
---

### Post by Sugi on 2009-11-06
I am considering an upgrade for my video card.  Some of the lower-end video cards of ATI are quite cheap and powerful.  But in my own personal experience, ATI cards and drivers has only gave me headaches in the past with wine.  I have heard the ATI drivers are getting better.  Would anyone like to comment on their own ATI cards and wine experience?

Thanks,
Sugi

---

### Post by beastrace91 on 2009-11-06
While I do not personally own an ATI card any longer (gave the crap up a long time ago) I can attest to the fact that a good portion of the threads regarding "random crashes" or "poor performance" in Wine games are linked to ATI cards. So my money would be on they have not gotten much better. When it comes to hardware typically you get what you pay for - chip up (pun intended) the small bit of extra money and go nVidia. The 260 GTX is a pretty good card for a fair price currently.

~Jeff

---

### Post by Jguy on 2009-11-06
ATi for Windows rocks. I've never had an issue with an ATi card running anything. They have always stood up to the task in Windows. It seems that might bne my current issue with my wine crashing and slow fps's. 

I'll be switching to my onboard video to play a few games while I scrounge up the time and money to do a rebuild (I need to anyway)

---

### Post by handy on 2009-11-06
> **Sugi said:**
> I am considering an upgrade for my video card.  Some of the lower-end video cards of ATI are quite cheap and powerful.  But in my own personal experience, ATI cards and drivers has only gave me headaches in the past with wine.  I have heard the ATI drivers are getting better.  Would anyone like to comment on their own ATI cards and wine experience?

Thanks,
Sugi

The AMD/ATi closed driver used to be called fglrx, it is now called catalyst.

Catalyst has been a pain, for many users.  I use Arch, so most every day I get a full system upgrade, this puts Arch ATi users in the difficult position of dealing with the way Catalyst doesn't keep up with the fast changes happening in the GNU/FOSS world.

Currently Catalyst isn't too bad, but you never know what the next release will be like (due out around the end of this month apparently).  As they step forward & then regress.

As an example, a little over a week ago, Arch started using xorg 1.74, which of course the only recently released (for Ubuntu as AMD/ATi support Ubuntu) catalyst 9.10 is not compatible.  So those Arch users that want to continue using catalyst have to block the upgrading of 5 (or 6 if you use a notebook) packages, to prevent the black screen of death!

Ok, now for the good news.

The open-source ATi drivers are moving along rapidly.  The 2D is superb now.  I have a HD2600 pro, & the 2D is faultless, using the open-source packages.

The 3D is coming along.

There are developments in progress i.e. KMS is now a part of the kernel .31*, (experimental stage) & further support will continue to be implemented in the kernel & mesa.

The eventual outcome will be that the intel, ATi & other GPUs will be fully supported 2D/3D by the kernel & mesa.

This is most excellent news.

It is a pretty safe bet, that we can realisticly expect that nearly all of the ATi GPUs will have (apart from the best 2D) most excellent 3D, within the next year.  This will turn into the best 3D eventually, sooner for some chips trees than others.  Some will get great 3D in the coming couple of months.

If you are interested there are some useful links at the bottom of the first post in the following linked thread, there is also some other worthwhile info' in the remainder of the thread, though it is starting to get a bit long. ;)

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

---

### Post by edin9 on 2009-11-06
> **handy said:**
> The AMD/ATi closed driver used to be called fglrx, it is now called catalyst.

Catalyst has been a pain, for many users.  I use Arch, so most every day I get a full system upgrade, this puts Arch ATi users in the difficult position of dealing with the way Catalyst doesn't keep up with the fast changes happening in the GNU/FOSS world.

Currently Catalyst isn't too bad, but you never know what the next release will be like (due out around the end of this month apparently).  As they step forward & then regress.

As an example, a little over a week ago, Arch started using xorg 1.74, which of course the only recently released (for Ubuntu as AMD/ATi support Ubuntu) catalyst 9.10 is not compatible.  So those Arch users that want to continue using catalyst have to block the upgrading of 5 (or 6 if you use a notebook) packages, to prevent the black screen of death!

Ok, now for the good news.

The open-source ATi drivers are moving along rapidly.  The 2D is superb now.  I have a HD2600 pro, & the 2D is faultless, using the open-source packages.

The 3D is coming along.

There are developments in progress i.e. KMS is now a part of the kernel .31*, (experimental stage) & further support will continue to be implemented in the kernel & mesa.

The eventual outcome will be that the intel, ATi & other GPUs will be fully supported 2D/3D by the kernel & mesa.

This is most excellent news.

It is a pretty safe bet, that we can realisticly expect that nearly all of the ATi GPUs will have (apart from the best 2D) most excellent 3D, within the next year.  This will turn into the best 3D eventually, sooner for some chips trees than others.  Some will get great 3D in the coming couple of months.

If you are interested there are some useful links at the bottom of the first post in the following linked thread, there is also some other worthwhile info' in the remainder of the thread, though it is starting to get a bit long. ;)

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

Shameless self promotion FTW? On a different note, the open-source ATi drivers are actually surprisingly good with basic 3D already. I messed around with some of the opensource games from the repos (Neverball, Tux Racer, etc....) and was kind of surprised at how well it performed. It even works well with Urban Terror. Lucid will probably actually be usable with WINE on ATi.

---

### Post by beastrace91 on 2009-11-06
> **Jguy said:**
> ATi for Windows rocks.

Ehh. Even that is debatable. They are cheap, about the only thing they have going for them. 

~Jeff

---

### Post by spoons on 2009-11-06
> **beastrace91 said:**
> Ehh. Even that is debatable. They are cheap, about the only thing they have going for them. 

~Jeff

On Windows, ATi drivers are comparable to Nvidia's.

OP, ATi drivers and Wine play nicer in Karmic but they're still not as good as Nvidia cards in that area. Your mileage will vary, depending on the game.

---

### Post by edin9 on 2009-11-06
> **spoons said:**
> On Windows, ATi drivers are comparable to Nvidia's.

OP, ATi drivers and Wine play nicer in Karmic but they're still not as good as Nvidia cards in that area. Your mileage will vary, depending on the game.

No they're not. ATi's drivers are always 1 step behind nVIDIA's.

---

### Post by Melcar on 2009-11-06
That's all subjective.  For me ATI drivers never cause issues.  As for the OP question, WINE needs a big ol' TWIMTBP logo on it.  You will have better luck with the nvidia drivers.  If you play mostly on WINE nvidia will be the safest bet.

---

### Post by handy on 2009-11-06
> **edin9 said:**
> 
Shameless self promotion FTW?  

?

> **edin9 said:**
> 
On a different note, 

?

> **edin9 said:**
> 
the open-source ATi drivers are actually surprisingly good with basic 3D already. 

It depends on the GPU.

To get good results you have to be lucky, or have worked hard.  There are still all kinds of bugs, depending on your hardware & what you are running on which distro.  As some distro's, Fedora for instance, have put a lot more effort in than others in this regard.

To go down the hard road to the best, but still buggy 3D with the open-source packages have a look at this thread, & you will see, it ain't easy & it requires a lot of upkeep:

[http://bbs.archlinux.org/viewtopic.php?id=79509](http://bbs.archlinux.org/viewtopic.php?id=79509)

> **edin9 said:**
> 
I messed around with some of the opensource games from the repos (Neverball, Tux Racer, etc....) and was kind of surprised at how well it performed. It even works well with Urban Terror. Lucid will probably actually be usable with WINE on ATi.

Yes, compiz & the simpler 3D games give the best results, though many have artefacts, especially with compiz, & there are other anomalies, again, depending on your hardware & other variables.

Still, it won't be too long & this ATi driver hell will be forgotten.

Though really, it is probably Arch & other rolling release distro users that have experienced more of the hell than other distro's, especially Ubuntu, who, as I said before is officially supported by AMD.  Which means that AMD/Ubuntu try to have a good catalyst out with each new Ubuntu release.  The other catalysts have really been quite a lottery for all of this year & beyond.

---

### Post by Sugi on 2009-11-06
Like I thought, it hasn't really changed that much.  I haven't been testing current gen games lately due to lack of hardware.  It looks like I will upgrade to a nvidia card.  I have quite a bit of experience with nvidia and some ati cards.  I have to say, ATI cards has been anything but fun.  I was indeed looking at the gtx 260, because it's around my price range for a mini-upgrade.

Sugi

---

### Post by handy on 2009-11-06
If you are in a hurry, nVidia is the best choice.

Before 12 months is up I think the choice will be different. ;)

---

### Post by beastrace91 on 2009-11-06
> **handy said:**
> Before 12 months is up I think the choice will be different. ;)

Heres hoping. While I love nVidia one of the best things about Ubuntu is the choice it gives you in most all things - it would be nice to have this in graphics cards as well.

~Jeff

---

### Post by handy on 2009-11-07
> **beastrace91 said:**
> Heres hoping. While I love nVidia one of the best things about Ubuntu is the choice it gives you in most all things - it would be nice to have this in graphics cards as well.

~Jeff

Truly mate, there is a mountain of work going on to change our world in this regard.

There is no two ways to it.

In 12 months time 3D graphic card support will be unrecognisable in comparison to what we have now.

It will creep on us, so it won't stand out so much.

But you mark my words, & please, come back & hit me in the face with them if I'm feeding you BS, as if I am I deserve it. :D

---

### Post by edin9 on 2009-11-07
> **handy said:**
> Truly mate, there is a mountain of work going on to change our world in this regard.

There is no two ways to it.

In 12 months time 3D graphic card support will be unrecognisable in comparison to what we have now.

It will creep on us, so it won't stand out so much.

But you mark my words, & please, come back & hit me in the face with them if I'm feeding you BS, as if I am I deserve it. :D

I hope so.

---

### Post by alex.rayu on 2009-11-07
ATI - yes they have historically neglected Linux. They now have declared a whole list of cards obsolete under linux, including my x1700. There is currently a open-source driver, but it still is weak at some of 3d.

---

### Post by Pasdar on 2009-11-07
> **edin9 said:**
> No they're not. ATi's drivers are always 1 step behind nVIDIA's.

On Linux yes, but on Windows they have the most powerful cards (see benchmarks) and make great drivers. ATI has historically, and until this day always delivered the most powerful video cards... and they're cheap too.

---

### Post by Sugi on 2009-11-07
Let's stick to the topic of this thread.  I am afraid it will turn into flaming and a war between which company is better.

The topic is about people's own personal experience with ATI cards and wine.  I think the talk about open-source drivers can be linked to the main topic as well as it will hold a place for future experiences with testing games with ATI cards.

Sugi

---

### Post by handy on 2009-11-07
> **Sugi said:**
> Let's stick to the topic of this thread.  I am afraid it will turn into flaming and a war between which company is better.

The topic is about people's own personal experience with ATI cards and wine.  I think the talk about open-source drivers can be linked to the main topic as well as it will hold a place for future experiences with testing games with ATI cards.

Sugi

My points have nothing to do with company vs company, (I own both ATi & nVidia anyway) it is all about the changes in progress in the GNU/FOSS world, which I think are worth knowing about for anyone thinking about buying another card.

It may have no effect on which brand of grahics card is bought, but at least the purchaser can be slightly more informed before they make their choice.

---

### Post by Sugi on 2009-11-08
I am upgrading to a new nvidia card.  handy, I think you misunderstood my last post, but no wonders. :)

Sugi

---

### Post by doorknob60 on 2009-11-08
Right now, the drivers are pretty good. All native games work perfect for me, and most wine games do. The one game that doesn't work is CoD2. Steam games all work though, and without problems, as well as SimCity 4. I have integrated Radeon 3100 graphics with the latest catalyst drivers. I still think Nvidia is the best choice though, since ATI is lazy and haven't updated their drivers to work with the latest Xorg (that Arch uses, dunno about Karmic), but as usual Nvidia keeps their drivers compatible. Oh well using the previous Xorg no big deal.

---

### Post by Melcar on 2009-11-08
Fglrx only supports a few distros.  Additionally, it only supports "stable" (as in non-testing) kernels and xservers.  That is AMD's policy and it's not because they're lazy.  Fglrx is for supported platforms, the open drivers (which have been given wide support by AMD themselves) are for platforms that are in the upstream (the rolling releases and the "bleeding edge" ones).  That is how AMD has opted to work officially, relying on both open and closed drivers to provide the best Linux support.  If people don't like it then I guess they should petition AMD to stop supporting the open drivers and just beef up their proprietary drivers.

---

### Post by devguy on 2009-11-08
I've yet to encounter many problems with ATI in Linux.  Prior to Catalyst 9.1, they were a disaster, but since then, they've steadily gotten better.

Issues I have:
-No hardware acceleration of HD videos (but I have a 3.6 ghz quad, so no biggie for my machine)
-can't reasonably do anything 3D unless I disable Compiz (set visual stuff to none in visual settings)
-STILL no alteration of fan speed using overdrive (WTF?!  Even nVidia supports this now!)

As far as wine goes, I've played Half Life 2, Wolfenstein (2009), Halo 1, all with no issues.  FEAR Combat seems to not work though (might not be exclusive to ATI hardware there, though).  With nVidia, they seem to support older cards in linux (and in Windows) better.  For ATI, you cannot even use pre R6xx cards with the newer drivers.  But big whoop.  One can buy a 2400pro dirt cheap for AGP or PCIe and get full driver support.  The RV7xx series has great support, so I'd recommend those.  No support for the RV84x series, nor for the R680 series, so I'd stay away from those for now.

---

### Post by Duskao on 2009-11-08
Ati is decent. They are getting better, but for now they are decent.  Nvidia is still the way to go in the most case, but give it a little bit more time and Ati might actually overtake them *bracing self*. I don't mean the official fglrx/catalyst drivers, I mean the xorg Radeon/HD drivers. Next release of Ubuntu I wouldn't be surprised if you have 3D acceleration out of the box with most Ati cards to be honest. The reason I say this is because I'm using the open source drivers (on a radeon 4850) and I'm completely happy with them. They are almost to the point of the catalyst drivers. Sure they still have a way to go, and there are a few features that still need to be incorporated, but they are making leaps and bounds towards this. I have been able to run most stuff I throw at it with the open source drivers thus far. But still, alas as I mentioned before, Nvidia is still the way to go for now. You get good 3D acceleration, proper video acceleration, and more control through the nvidia control center. But be warned that Nvidia sometimes has security holes in their drivers for some reason. Ati's in that respect have mostly been solid in that respect. 

That probably didn't help at all. Hope you can take something away from all that babble. 

Best of luck.

---

### Post by beastrace91 on 2009-11-08
Haha yea I took away that ATI open source drivers are "getting better". Thats great and all but in the here and now nVidia is the way to go if you want to do gaming on Linux (especially Wine gaming).

I'd also like to throw out there that nVidia is not stopping driver development any time soon - so as ATI progresses so does nVidia and with their already sizable lead I don't see nVidia dropping behind anytime soon (if at all).

I know there is also the argument that the ATI drivers that are progressing are "open source". But to be honest for some things I don't mind having restricted code running - for instance almost every piece of software are running through Wine is also restricted.

~Jeff

---

### Post by Duskao on 2009-11-08
Actually both the open source and the official catalyst drivers for Ati are good was my point, although i don't think I said it. The fact of the matter is that Nvidia doesn't have that sizable of a lead anymore. Are they in fact ahead of the game right now?? yeah. But as every driver is released it closes the gap, and with the regimented releases of the Ati drivers it's a little step with each release, usually implementing 1 new thing each release. The Nvidia drivers haven't actually changed all that much in quite a while as far as performance. They have just added more cards to the list and fan tweaks and the like. Ati runs most stuff fine through wine as well, but there are a few exceptions. Always check the appdb. 

Either way, choose what you like. See how the future goes. Cross your fingers either way. Both have issues, and both have pluses.

---

### Post by EmEyKeYwAy on 2009-11-08
I built two computers with Biostar TA790GX A3+ (comes with an onboard ATI HD 3300). I've tried a couple of games on Windows Seven (Resident Evil 5, PES10) and they all worked great. I installed Ubuntu and I can't even play Counter Strike!    I don't like games but once in a while I play with my friends online. I'm not gonna buy a new graphic card just to play a game that works even on Windows 98 with 128 MB of RAM!

---

### Post by beastrace91 on 2009-11-08
That on board 3300 is actually a decent card. (DX10 support I think?). Just drivers yet again ;)

~Jeff

---

### Post by handy on 2009-11-09
> **EmEyKeYwAy said:**
> I built two computers with Biostar TA790GX A3+ (comes with an onboard ATI HD 3300). I've tried a couple of games on Windows Seven (Resident Evil 5, PES10) and they all worked great. I installed Ubuntu and I can't even play Counter Strike!    I don't like games but once in a while I play with my friends online. I'm not gonna buy a new graphic card just to play a game that works even on Windows 98 with 128 MB of RAM!

You need to install the catalyst drivers.

---

### Post by Faolan84 on 2009-11-17
I just find it ridiculous that ATI has decided to make their drivers so varying in quality and undependable that even Archlinux has blacklisted them from the main repos and moved them to AUR. I mean... really?!

I'm sorry, but I don't see the point in investing in ATI based hardware, because quite frankly I want to know that my drivers will be able to work with minimal fuss regardless of what distro I am using. ATI's Catalyst drivers are poorly designed and are full of surprises either way. I've never had trouble getting the NVIDIA drivers to work, on the other hand.

---

### Post by EmEyKeYwAy on 2009-11-24
> **handy said:**
> You need to install the catalyst drivers.

Of course I already installed them.

---

