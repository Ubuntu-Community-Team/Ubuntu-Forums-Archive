---
title: "Linux is very diffecult to install (NOT)"
date: 2011-09-12
forum: Testimonials &amp; Experiences
---

### Post by georgemc on 2011-09-12
For all of you who think installing Linux any distro is a nightmare, this is what I encountered today with MS XP.
 

 Equipment and setup:
 I had a triple boot test system with XP SP3, Fedora15 Gnome3, Ubuntu 11.04 Unity on it; with an Intel DP35DP mobo and a 2.6MHz 775 Intel Dual core CPU, 70GB Sata HD, Nvidia GTS 250, DVD etc; nothing fancy or exotic, just a plain DIY Home Brew box.
 

 Precursor OOPPPSS:
 I decided I need more XP space and my Linux/Gnome3/Unity testing is done and I proceeded to wipe the Linux partitions and expand the XP partition with a my Partition Commander CD, done this several times so no biggie.  OOOPPPS some how I wiped every thing.  No biggie I'll just re-install XP.  Probably needed a fresh install any way.
 

 I have all my XP CDs, activation keys, Mobo & Nvidia CDs, driver downloads and much more on my home server ready to copy/move any where on my home network.
 

 XP install:
 Blue screened on me about 1 Minute into “Loading stuff”, cleaned CD and reboot, tried again and same thing.  Well maybe just a bad CD, no biggie got a different XP CD and continued.
 

 Got further with this one and it blue screened while loading the drivers, i.e. where it says it will take another 35 minutes.  Kinda stumped I looked for the error “IRQL_NOT_LESS_OR_EQUAL” on Google, not really descriptive but it looked familiar and low a behold after perusing a few posts it popped in my mind: “The olde XP doesn't like Sata drives thing!”.  Booted into Bios and changed that setting to “Legacy” and continued with the install.
 

 Needless to say every step of the way you need to click on a Yes/No, Continue, Accept EULA, after 2 dozen clicks or so I stopped counting.
 

 Finished installing and booted into XP.  Yay! Now just need SP3 and the Nvidia drivers.
 

 Not!
 

 No ethernet drivers!  OK got the DP35DP mobo CD and installed all the drivers from there.  Yay!
 

 Installed SP3 and rebooted. Yay!
 

 Download Nvidia drivers.

Not!

Need to install Adobe Flash first on IE6.  Gonna change that soon.
 
Install some software from Nvida to check my video cards.  LOL the smart scan failed to identify my video card.  Looking manually.
 

 Yay! Found the latest drivers.  More clicks to Yes/No/Continue/Accept EULA/Install/Next etc.
 

 Installed and reboot.  Yay!
 

 Next is “MS Security Essentials”!
 

 Not!
   
 Downloading and installing IE8 first because “MS Security Essentials” web page does not work with IE6. Go figure.  More clicks to Yes/No/Continue/Accept EULA/Install/Next etc.
 

 Installed and reboot.  Yay!
 

 Downloaded and attempted to install “MS Security Essentials”!
 

 Not!
 

 The error is “Installation is not Genuine”!  LOL OOPS Need to activate first.
 

 Yay! Activated.
 

 Many  Yes/No/Continue/Accept EULA/Install/Next clicks later it wants to scan this fresh installation, I of course decline and it updates itself.
 

 Yay!
 

 Now I have a minimal XP SP3 installation with an up-to-date IE and “MS Security Essentials”.
 

 Now just all those Applications like Libre Office and Tools to maintain this thing.
 

 Summary:
 All of this took me about 4 hours to do and it is still missing applications and tools that are loaded by default in Ubuntu.
 Last time I loaded either Fedora, Ubuntu, Centos, Debian, on this hardware the system was on the network with applications loaded and ready to go within 30 minutes.
 

 Conclusion:
 For all of you out there that say loading Linux is hard.  Try XP from scratch. LOL
 

 Need to ice down my right click finger now.
 

 George

---

### Post by hansdown on 2011-09-12
Nice post, georgemc.

I had a similar experience installing vista, for a friend.

---

### Post by 3rdalbum on 2011-09-12
To be fair, you're comparing a version of Windows from 2001 to a version of Ubuntu from 2011.

A better comparison would be to compare XP to a major Linux distro from 2001; I'm sure Windows XP would require less hassle than a turn-of-the-century distro.

Or, compare the latest Ubuntu to the latest Windows. IMHO Ubuntu would still come out on top, but at least it's a fair comparison.

---

### Post by jasonrisenburg on 2011-09-13
until windows 7 came out the, the last time windows did anything worth mentioning was 2001...lol. so we wlii discuss 2001 ubuntu in comparability to xp.. other than brown... Ubuntu wins... It is the warlock, it is bi-winning, it wins here.. it wins there bi-winning.

---

### Post by rjbl on 2011-09-13
> **3rdalbum said:**
> To be fair, you're comparing a version of Windows from 2001 to a version of Ubuntu from 2011.

A better comparison would be to compare XP to a major Linux distro from 2001; I'm sure Windows XP would require less hassle than a turn-of-the-century distro.

Or, compare the latest Ubuntu to the latest Windows. IMHO Ubuntu would still come out on top, but at least it's a fair comparison.

Lets be really fair, the OP was actually comparing installing XP SP3  - release date April 29 2008, with current Ubuntu. It looks like he has installed from an earlier release installer - probably XP SP2 (release date August 2004) and patched up to SP3. The original XP installer is no longer installable on any current generation kit. It don't work because it cannot detect HD(s) correctly and returns 'fatal error'.

Other than that the OP's description of the nausea of installing Windows is pretty accurate. Comparative installs of Windows versus the major GNU/Linux have always been like that - or at least since Red Hat 5 in '95(ish).

OK So Windows 7 is better? Not really. The proprietary hw drivers installed with Win 7 are pretty limited and Windows generic drivers are crappy - they always are. If you want to run a Windows 7 box then the best advice is buy it ready made and installed otherwise you must be prepared to spend a couple of days scratching round for the right drivers and installing them - 'Twas always so, hasn't been so for any GNU/Linux I know since Red Hat 5.5 days.

The flash-to-bang time for building a new Windows 7 system on a reasonably common bare-bones hardware is about 1 - 2 days to running OS, and up to about 5 days to completely re-install and configure a complex application set and legacy data transfer.

The comparable time for a similar Ubuntu system is in, my experience, between half a day and a full eight hour working day.

rjbl

---

### Post by armandh on 2011-09-13
just re-did my daughters P4 laptop; Twice!
with all the usual struggles.

Dual Boot XP-sp3/Ubuntu 10.10
 
had to DL the XP wifi driver to DL 6 others then updates
and AV and Libre office and VLC
the 10.10 was OOTB except updates, medibuntu, compiz manager and VLC
then I went to reduce the windows partition for a storage partition
and wound up doing it all over again. insert bad words [lots of 'em]

on the redo I planed ahead for the storage partition.

the Linux took half the time of win

---

### Post by georgemc on 2011-09-13
Well, didn't expect all these reactions.  Thank you all responders.
 

 3rdalbum: post #3
 Thank you for pointing this out.  If I recall 10 some years ago I would be inclined to say that any Linux distro of that era was on par with XP or worse.
 

 To all:
 By no means am I trying to slam XP or Win7.  My family and in the work place we use them both, and they do have their place in the computing world.
 

 This was just my experience of the day, and I do recognize I did plenty of mistakes prior to and during the installation.  I was recording my experience as I was doing and I did chuckle and laugh plenty.
 

 I personally prefer any thing *NIX.  Been using *NIX since the mid 80's.  So I think I am a *NIX fanboy at heart.
 

 I do botch Linux installs plenty of times.  That&#8217;s why I have a spare box to play with and push the proverbial envelope.  Learned these lessons in the Data Centers, some times the hard way.
 

 Recording as you go does help with finding a path that is more streamlined.  So next time around I should have more &#8220;Yay's&#8221; than &#8220;NOT's&#8221;.  I also created a XP-SP3 slip streamed CD in the meantime and that should take some of the pain out of a re-install.
 

 Still icing down my right click finger.
 

 George

---

### Post by hansdown on 2011-09-14
It's all good, georgemc.

Thanks for the feedback.

---

### Post by tommpogg on 2011-09-14
I have installed Windows 7 a couple of months ago (I need it on work). It was a very long time since my last windows installation, probably 5 years or so.
Man, reinstalling windows helped me to realise how simple is a Ubuntu installation! When I finally had my system installed after 10000 steps of Yes/No, Continue, Accept, I realised that nothing was working properly and I still had to install drivers and basic applications!

A decade has passed since Win XP but it seems that things haven't changed too much. Even the graphic is almost the same, just a bit more fancy and lucid.

---

### Post by Elfy on 2011-09-14
This is a forum for 

> This space is provided for users to post their reviews of Ubuntu.

not for a dig at how to install windows years ago - Closed

---

