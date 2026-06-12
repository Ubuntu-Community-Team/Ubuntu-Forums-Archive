---
title: "[SOLVED] Mac OS X 10.5 Leopard on VirtualBox"
date: 2008-07-25
forum: Virtualisation
---

### Post by ffohwx on 2008-07-25
I was wondering if anyone knows if, or has tried, to run Mac OS X 10.5 Leopard as a guest in VirtualBox. I'm not asking if it can run on PC hardware, as I have a Mac. I would just rather use Ubuntu as my main OS and boot OS X via VirtualBox only when I need some app from it (i.e., GarageBand)Right now, I have it the other way around, and am running Ubuntu in the VirtualBox on Mac. Any ideas on if it is even possible are appreciated.

---

### Post by HotShotDJ on 2008-07-25
> **ffohwx said:**
> I was wondering if anyone knows if, or has tried, to run Mac OS X 10.5 Leopard as a guest in VirtualBox.[No]("http://www.virtualbox.org/wiki/Guest_OSes").

---

### Post by Phil Urich on 2009-12-24
HotShotDJ is wrong, pure and simple.

Well sure it isn't officially supported . . . but I don't think it's as cut and dry as that.  For one, for political reasons VirtualBox really can't be saying that they're able to (or working towards) running OSX.  But in the past it has been done (some anecdotal examples and instructions can be found on this VirtualBox forum thread: [http://forums.virtualbox.org/viewtopic.php?t=2076](http://forums.virtualbox.org/viewtopic.php?t=2076)) and it is indeed possible.  The caveats so far are rather extensive, consisting of quite a few technical and a crapload legal, although I stress that yes it can be done, and done legally.

**EDIT:** It just occurred to me that I should perhaps be clear where I've been vague.  I preface this by stating that I am not a lawyer, this is not legal advice, yada yada whatever.  As it stands if you live in a country where Apple's EULA is enforceable or you fear it (and in my not-a-lawyer capacity I'd like to point out that EULAs haven't stood up well in court) then as per the EULA the following restrictions apply to running OSX: it can only be run on Apple hardware, and only OSX Server can be run in a virtual environment.

So in other words, if you own Apple hardware and have a legal license for OSX Server, then even under the terms of the EULA you are perfectly allowed to run a copy of OSX Server using your license as a VirtualBox guest on an install of Ubuntu on that piece of Apple hardware.

So for example: iMac -> install of Ubuntu -> OSX Server as VirtualBox Guest

---

### Post by eksasol on 2010-05-10
> **HotShotDJ said:**
> [No]("http://www.virtualbox.org/wiki/Guest_OSes").
Speak for yourself: [http://hackaday.com/2010/05/03/virtualbox-beta-runs-mac-os-x/#more-23751](http://hackaday.com/2010/05/03/virtualbox-beta-runs-mac-os-x/#more-23751)

---

### Post by Perryg on 2010-05-10
VirtualBox 3.2.0 Beta-2 release has support for OSX guest as long as it is on Apple/MAC hardware.  Right now there are a few issues with it on Linux OS on Apple/MAC hardware but it is still working.  They hope that by release it will work with Linux OS as well.  Of course it is PUEL version right now but I suspect the Ubuntu guys will get it to OSE as soon as it is released.

---

### Post by BobVila on 2010-05-13
> **Perryg said:**
> VirtualBox 3.2.0 Beta-2 release has support for OSX guest as long as it is on Apple/MAC hardware.  Right now there are a few issues with it on Linux OS on Apple/MAC hardware but it is still working.  They hope that by release it will work with Linux OS as well.  Of course it is PUEL version right now but I suspect the Ubuntu guys will get it to OSE as soon as it is released.

If you have a less-than-legitimate copy of Leopard or Snow Leopard (I.E. one with EFI emulation), 3.2 PUEL will run it just fine.

---

### Post by Cardale on 2010-05-30
I was wondering this as well.  Will 10.6 work?

---

### Post by Phil Urich on 2010-06-29
> **Cardale said:**
> I was wondering this as well.  Will 10.6 work?

It should; I actually picked myself up an older iMac the other day, and a legitimate version of 10.6 from the local Apple store.  I'll get back to you on it . . .

[Edit] First hurdle, the iMac I have only has 1GB of RAM.  That's okay for installing 10.6 non-virtually, but to have it run in VirtualBox I'd have to dedicate the entirety of that to the virtual machine, which of course can't be done.  Time for a jaunt down to my local mom-and-pop parts store for some SODIMMs!

---

### Post by HotShotDJ on 2010-06-30
> **eksasol said:**
> Speak for yourself

> **Phil Urich said:**
> HotShotDJ is wrong, pure and simple.

Please take a look at the date of my reply.  At the time I answered the OP, I was correct.  Support for Leopard was added in subsequent versions.  I don't mind being corrected when I'm wrong.. but tossing out rude comments because I didn't forecast the future is an entirely different matter.

---

### Post by Phil Urich on 2010-11-23
I swore I replied here ages ago, hmm.  Anyways. For the record:

No, you were wrong at the time too; it has gotten WAY easier, and is outright supported, but back that far people had already patched VirtualBox and OSX in ways that allowed them to live in harmony.  It was just all at best quasi-legal and finicky.  There were people who had success long before mid-2008 when you posted your unequivocal "No."

I really didn't mean it rudely per se, I just meant that your statement was entirely false.  One would have had to really dive into the depths of certain forums and torrent sites to know otherwise at the time you originally posted, though, so it wasn't a mark against you.  You just happened to be wrong; none of us are omniscient.

---

### Post by reiki on 2010-11-25
running OS X on non-Apple hardware is against the Apple EULA. That being said, I went on to experiment...

Using an unaltered and legitimate OS X Snow Leopard DVD, I was able to install OS X into a VirtualBox VM on my Dell Zino HD. This did require the use of a non-Apple EFI loader. 

I could boot to the desktop and run some simple apps, but for anything substantial, the VM was not presenting a sufficiently powerful graphics card to the OS and the apps refused to install or run.

So as an experiment, it was fun, but not very practical in terms of actually using it.

Conclusion: If I want to run an Apple OS, I'll buy an Apple computer. The new Mac Mini looks interesting, if a bit short on memory in its stock configuration.

---

### Post by FunnyLookinHat on 2011-03-20
I've been trying to install OS X so that I can package some JAR files into .app Application files for distribution - something that I certainly can't justify running a fully-fledged OS X implementation for...  I keep running into an issue where, after I install, it seems as though it won't boot into the OS.  It'll only spew error codes via the console or show the installer again (if the CD is still in).   How did you spoof the EFI stuff?

---

