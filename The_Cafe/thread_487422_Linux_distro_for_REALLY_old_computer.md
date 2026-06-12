---
title: "Linux distro for REALLY old computer"
date: 2007-06-29
forum: The Cafe
---

### Post by dragobr on 2007-06-29
I have a very old computer here... a pentium 100 mhz, with 64mb of RAM and 1.2gb of hd...

i used it mainly to run coyote linux, as a router, but i bought a wireless router and this great computer is going to be free

it runs windows 98 very well, but.. you know..

anyone know a good linux distro, apt based, for it?

thanks!

---

### Post by jrusso2 on 2007-06-29
Deli linux, puppy linux and Damn Small Linux are things that should run.  Of those Damn Small  has apt.

---

### Post by Tux Aubrey on 2007-06-29
I'd try puppy or elive - although both would be better with 128meg.

---

### Post by pseudonym on 2007-06-29
If you feel like geeking out you can try [Cubuntu]("https://wiki.ubuntu.com/Cubuntu?highlight=%28cubuntu%29") , which is an Ubuntu distro which uses console-based apps exclusively. Should fly on your machine :)

---

### Post by Circus-Killer on 2007-06-29
hmmm......just curious, does anyone know how Xubuntu would run on those specs? 
Cos if it would run fine, then that would be my recommendation.

---

### Post by pseudonym on 2007-06-29
> **Circus-Killer said:**
> hmmm......just curious, does anyone know how Xubuntu would run on those specs? 

Very poorly, if usably at all. My second PC is a 550MHz PIII with 384MB RAM and, while Xubuntu installs and runs *OK*, it's still too slow if you want to be productive (even with a slew of tweaks and hacks designed for speed). I think XFCE has become a little more bloated in recent releases, making it more accurately described as a distro for 'medium spec' hardware ie. around 1GHz CPU and 512MB RAM.

For a low spec desktop you want to be looking at [Fluxbuntu]("http://fluxbuntu.org/") or a [custom install]("http://www.psychocats.net/ubuntu/minimal#barebones")using the [Minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD") and running a window manager like [Openbox]("https://help.ubuntu.com/community/Openbox?highlight=%28openbox%29") . That's what I have on my second machine and it runs great.

---

### Post by koenn on 2007-06-29
> **pseudonym said:**
> 
For a low spec desktop you want to be looking at [Fluxbuntu]("http://fluxbuntu.org/") or a [custom install]("http://www.psychocats.net/ubuntu/minimal#barebones")using the [Minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD") and running a window manager like [Openbox]("https://help.ubuntu.com/community/Openbox?highlight=%28openbox%29") . That's what I have on my second machine and it runs great.
I agree. I've done something similar (mini install, X, Fluxbox) - it's fun.

---

### Post by dptxp on 2007-06-29
I have P-100 with 32 MB RAM. I run Windows 98.
I plan to use Puppy Linux on it, but I shall make a nice SWAP partition of 2 MB first
with GPARTED.

---

### Post by Rumor on 2007-06-29
+1 for Deli Linux. [http://delili.lens.hl-users.com/](http://delili.lens.hl-users.com/)

There is a fairly recent review of Deli Linux here: [http://distrowatch.com/weekly.php?issue=20070521#feature](http://distrowatch.com/weekly.php?issue=20070521#feature)

---

### Post by Zzl1xndd on 2007-06-29
I'm gonna back damn Small.

---

### Post by Bungo Pony on 2007-06-29
I downgraded my garage computer to a Pentium 133 with 36M RAM. Damn Small Linux is still working fabulous - it only needs 16M of ram to run, but a little more will make it run smoothly. And you only need 50M of drivespace.

---

### Post by cunawarit on 2007-06-29
DSL worked very well on my old PII 300. I'd personally give that a go, and it is apt based, it is Debian.

---

### Post by DR_K13 on 2007-06-29
Damn Small Linux (Hard drive install )

---

### Post by macogw on 2007-06-29
cunawarit, regular Ubuntu runs on my Pentium II

I found a comp older than that in the office yesterday.  It had a 286 and Windows 3.11.  If it wasn't for the lack of CD and USB drives (yeah..just 3.5" and 5.25" floppies), I would've tried to install DSL.  I didn't want to go get 40 3.5" floppy disks to do it though.  Gave it (and a dot matrix printer, and the printer switch that let it work on 2 comps, and the 2ft x 2ft x 3in "surge protector") to Goodwill.  Their computer store will either do something about it (like put in a cd drive and bigger hard drive to make it usable) or it'll go on the shelf of ancient computing, with the Apple ][, Commodore PET, and Radio Shack TRS-80.  Either way, better than giving it to the place that's getting our other (much newer...Pentium 3) donation.  They would've thrown it out as useless, and I hate to see computers that still function get ditched.  Besides, bad for the environment.

---

### Post by pseudonym on 2007-06-29
> **macogw said:**
> I found a comp older than that in the office yesterday.  It had a 286 and Windows 3.11.  If it wasn't for the lack of CD and USB drives (yeah..just 3.5" and 5.25" floppies), I would've tried to install DSL.  I didn't want to go get 40 3.5" floppy disks to do it though. 
You don't need 40 floppies to install DSL. If you have a fast internet connection you can do a ['poor man's install']("http://www.damnsmalllinux.org/wiki/index.php/Floppy_Only_Install_with_Netcard_%28Poormans_Install%29"), which is one boot floppy and the rest of the system installed over the network (like Debian's [netinst]("http://www.debian.org/distrib/netinst") or Ubuntu's [Minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD") ).

I tried this once with a 486/16MB RAM machine someone was going to throw out, and it worked...sort of. The machine only had ISA and [VLB]("http://en.wikipedia.org/wiki/VESA_Local_Bus") expansion slots, but I picked up an ISA ethernet card for 15c off ebay (which I still use in my PIII) so I could hook it up to my cable internet. DSL installed a treat via the poor man's (*sic*) method. But X was as slow as hell. Even the lightweight Dillo web browser had trouble running. Forget about anything else. Such a machine would be OK for console-only apps, I guess, although it may have trouble decoding an mp3. I didn't invest any more time in it to find out, however.

---

### Post by macogw on 2007-06-29
> **pseudonym said:**
> You don't need 40 floppies to install DSL. If you have a fast internet connection you can do a ['poor man's install']("http://www.damnsmalllinux.org/wiki/index.php/Floppy_Only_Install_with_Netcard_%28Poormans_Install%29"), which is one boot floppy and the rest of the system installed over the network (like Debian's [netinst]("http://www.debian.org/distrib/netinst") or Ubuntu's [Minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD") ).

I tried this once with a 486/16MB RAM machine someone was going to throw out, and it worked...sort of. The machine only had ISA and [VLB]("http://en.wikipedia.org/wiki/VESA_Local_Bus") expansion slots, but I picked up an ISA ethernet card for 15c off ebay (which I still use in my PIII) so I could hook it up to my cable internet. DSL installed a treat via the poor man's (*sic*) method. But X was as slow as hell. Even the lightweight Dillo web browser had trouble running. Forget about anything else. Such a machine would be OK for console-only apps, I guess, although it may have trouble decoding an mp3. I didn't invest any more time in it to find out, however.
Right so a 286 doesn't have ethernet.  It has like...if lucky a 56K, most likely something much slower.  And we don't have dialup here.  We have a laptop with Verizon wireless internet via USB.  And I'm not buying an ethernet card for it when we're about to give it away.  I'm not quite sure how that'd work anyway.  The slots on the back of the case were horizontal (it's a lay-down box, not a tower) which would make the slots parallel to the motherboard, I think, and I don't know how a PCI card could be inserted that direction.

And it didn't run console-only apps on Windows ;) Window 3.11 had a GUI, just not a good one :p

---

### Post by misconfiguration on 2007-06-29
I'm opting Slackware, I've installed Slackware on a 50mb hard drive. This was part of a laptop with a broken screen, after I hooked vga up to it and got the OS and CUPS daemon working, I sold it for $100 bucks to a small printing company, it's been their dedicated print server for 2 years now! :)

---

### Post by Lord Illidan on 2007-06-29
I tried DSL on a Pentium 1 133 mhz with 32 mb of RAM. It worked fine as a live cd. Not blazing fast, but for its age, quite good.

---

### Post by Super TWiT on 2007-06-30
> **pseudonym said:**
> Very poorly, if usably at all. My second PC is a 550MHz PIII with 384MB RAM and, while Xubuntu installs and runs *OK*, it's still too slow if you want to be productive (even with a slew of tweaks and hacks designed for speed). I think XFCE has become a little more bloated in recent releases, making it more accurately described as a distro for 'medium spec' hardware ie. around 1GHz CPU and 512MB RAM.

For a low spec desktop you want to be looking at [Fluxbuntu]("http://fluxbuntu.org/") or a [custom install]("http://www.psychocats.net/ubuntu/minimal#barebones")using the [Minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD") and running a window manager like [Openbox]("https://help.ubuntu.com/community/Openbox?highlight=%28openbox%29") . That's what I have on my second machine and it runs great.

I have gotten Ubuntu regular running on a laptop with the same cpu and 192 mb of ram.  I had to use the alternate install cd to get it installed though.  It runs quite smoothly.

---

### Post by darkfox on 2007-07-19
I'd have to agree with earlier posts: Ubuntu minimal and then if you want a graphical environment go for a 'box (Openbox is my personal choice).  This is fun and manageable plus you get all manner of Ubuntu yumminess.  DSL also a great alternative of course.

---

### Post by ubanchaos on 2007-07-19
try xbuntu

---

### Post by Frak on 2007-07-19
[http://en.wikipedia.org/wiki/KolibriOS](http://en.wikipedia.org/wiki/KolibriOS)

---

### Post by notwen on 2007-07-19
+1 Dsl

---

### Post by Bungo Pony on 2007-07-19
Only 486 and up will do MP3s (there needs to be a math co-processor on the motherboard). If you want to get DSL running on a really old computer, try putting the hard drive in a newer PC, install DSL, and then put the hard drive back in the old PC. DSL looks for hardware on startup.

However, I wouldn't bother with an old 286. Might be good for running DOS and maybe recieving faxes through a modem. I usually take advantage of using serial ports on old PCs to transfer files, with both the source and destination running Telix. It works very well for retrieving data, and you don't have to futz around with unreliable floppies. Buying a serial cable to connect two PCs together is a great investment!

---

### Post by Kowalski_GT-R on 2007-07-19
I just finished a custom installation of Xubuntu 7.04 from a command line on a 233MMX Pentium PC with 64Mb RAM.

Out of curiosity I decided to install the entire Xubuntu desktop, and it's, well, unusable.

I doubt any tweaks aimed at speed and usability would save the situation.
Can't comment on how Fluxbox or Openbox would work.

Puppy on a similar specced machine runs a charm though. Didn't install it myself, it's very "responsive", if you go beyond the cheap-ish standard look.

ciao,

Andre

---

