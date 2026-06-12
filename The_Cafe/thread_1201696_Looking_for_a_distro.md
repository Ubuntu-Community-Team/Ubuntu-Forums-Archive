---
title: "Looking for a distro"
date: 2009-07-01
forum: The Cafe
---

### Post by cguy on 2009-07-01
Before I begin, let me ask you if the Ubuntu minimal CD installer can handle PPPoE connections. Well, does it? :)

---

I have an old laptop with a dodgy CDROM and a diskette drive which I am reluctant to use. Booting over the network is impossible.
It's specs are:
- PIII - 700Mhz
- 128 MB of RAM

I am looking for a not very lightweight distro which must suit these requrements:
- it must have a user friendly desktop manager - Xfce, LXDE or others
- maintained repositories or support for Ubuntu's/Fedora's/Debian's etc. repositories
- since Ubuntu .deb files are so popular, I prefer a distro which supports them; or rpm
- **the CD iso must be small;** This CDROM fails to read CDs every now and then and may ruin an installation, plus it puts a lot of stress on my nerves.
- easy installation and configuration (user friendliness). I don't want to spend a whole day just to get it going as I want it to go


Is there such a distro?

---

### Post by swoll1980 on 2009-07-01
[Puppy Linux]("puppylinux.com/") meets all your requirements.

---

### Post by cguy on 2009-07-01
People seem to have problems with installing rpms or debs on Puppy. I don't want to turn program installation into a nightmare. Any other suggestions?

It's a nice distro, though, and will keep it among the favorites.


EDIT:
I might turn the laptop into a server in near time future, so please take that into consideration when making the suggestions.

Thank you all.

---

### Post by swoll1980 on 2009-07-01
> **cguy said:**
> People seem to have problems with installing rpms or debs on Puppy. I don't want to turn program installation into a nightmare. Any other suggestions?

It's a nice distro, though, and will keep it among the favorites.

puppy has it's own package management system called pup. It has it's own repos as well.

---

### Post by cguy on 2009-07-01
Yes, but most of the programs can be found in rpm/deb packages and I want to take advantage of this.

Plus, Puppy's repos may not be complete or may not contain the lastest versions of some of the programs of interest.

---

### Post by nmccrina on 2009-07-01
Try Arch.

---

### Post by unknownPoster on 2009-07-01
> **nmccrina said:**
> Try Arch.

Did you even read the OP's post?

He wants ease of configuration and support for RPM or DEB...Arch doesn't do that OOTB.

Anyway, I would recommend Mepis Antix. It supports .DEBs and it runs on hardware such as yours...

[http://antix.mepis.org/index.php/Main_Page](http://antix.mepis.org/index.php/Main_Page)

Alternatively, you could try a minimal/netinstall of Ubuntu or Debian.

---

### Post by nmccrina on 2009-07-01
> **unknownPoster said:**
> Did you even read the OP's post?



Sorry, it was kind of a joke. I couldn't resist.

:popcorn:

---

### Post by swoll1980 on 2009-07-01
> **nmccrina said:**
> Sorry, it was kind of a joke. I couldn't resist.

:popcorn:

Hey if you wouldn't have said it, someone else would have, and they would have been serious.

---

### Post by nmccrina on 2009-07-01
> **swoll1980 said:**
> Hey if you wouldn't have said it, someone else would have, and they would have been serious.

There you go. I pre-emptively prevented a great evil :p

---

### Post by Pogeymanz on 2009-07-01
Just do a minimal Debian install. It takes a little longer than just popping in an Ubuntu CD and letting it do to town, but it certainly wont take all day.

And it will run totally fine on that machine as long as you use XFCE or LXDE.

---

### Post by XubuRoxMySox on 2009-07-01
> **Pogeymanz said:**
> Just do a minimal Debian install. It takes a little longer than just popping in an Ubuntu CD and letting it go to town, but it certainly wont take all day.

And it will run totally fine on that machine as long as you use XFCE or LXDE.

+1 There's a minimal Debian/LXDE available as a download from the [LXDE]("http://lxde.org") site.

---

### Post by ramnarayan on 2009-07-01
check out slitaz 

[http://distrowatch.com/table.php?distribution=slitaz](http://distrowatch.com/table.php?distribution=slitaz)

---

### Post by anaconda on 2009-07-01
I have an old 266Mhz laptop with 196MB RAM, with no CD-rom , and I succeeded in  installing xubuntu to it.

I installed it from USB-drive. (it was a bit difficult, because the machine is so old that it wont even boot from USB..

You could do the same. I also have DamnSmallLinux on another partition, and it is good, because it is fast even with thet old machine..

---

### Post by nitehawk777 on 2009-07-01
Slitaz says it runs "speedily" on 286mb ram,....
but maybe it could do OK with your 128mb..(?) 
However,...the new Puppy 5 just coming out,...can use the repositories of other distros (Debian, Ubuntu, Slackware, etc.)
I have run Puppy on an HP Vectra 500Mhz--286Mb ram before, (ran very well).
With a 700Mhz machine,...I'd put some more ram on it.  Should actually run pretty well with lightweight distros....(a 700Mhz can be a _good_ Linux box)...

EDIT: > I have an old 266Mhz laptop with 196MB RAM, with no CD-rom , and I succeeded in installing xubuntu to it.
Wow,..Anaconda,...
just saw your post after I did this,...
and I gotta say that sounds like you did great in re-cycling that old box!!!

---

### Post by cguy on 2009-07-01
I tried the net installation of Ubuntu; it didn't work due to lack of support for PPPoE connections. I believe it's the same with Debian's net install, right?

I tried Antix M8. Man, is that distro for real? It's full of bugs.
The X server started only when it was in the right mood; the installer didn't start/crashed when I began typing the password/crashed after inserting the password and clicking next; the apps also start when they feel like it; even shutdown is problematic! :lolflag:
Could this all be caused by my configuration?


The maximum iso should be around 400MB. Anything too big causes CDROM issues.
Right now I am downloading Debian Live - LXDE which I must say I am excited about. I wanted to try that DE for a long time. I hope it works.

Is Puppy 5 suitable for everyday use? It's still under development, right?

-----------
It must be my computer. I get the same SQUASHFS, input/output errors and X server issues with Debian. Fvck, it's getting frustrating!

---

### Post by anticapitalista on 2009-07-01
> **cguy said:**
> 
I tried Antix M8. Man, is that distro for real? It's full of bugs.
The X server started only when it was in the right mood; the installer didn't start/crashed when I began typing the password/crashed after inserting the password and clicking next; the apps also start when they feel like it; even shutdown is problematic! :lolflag:
Could this all be caused by my configuration?



Yes it probably is. And antiX-M8 is not full of bugs.
Check the md5sum and if you burn to a cd, use a slow speed x4 for example.

---

### Post by Geoff918 on 2009-07-01
I've never used, but heard good things about, DSL (D@mn Small Linux). Also, you may be interested in Knoppix if you can boot from a USB device.

---

### Post by monsterstack on 2009-07-01
TinycoreLinux. Requires at least 32mb of RAM, though. Oh and the ISO is 11mb. Other than that, it may be a bit too streamlined for your needs.

---

### Post by doorknob60 on 2009-07-01
Puppy is probably your best bet. I used it on a computer with the same specs and a 1 GB hard drive (yeah :-P) and it works fine. Until I took it apart the next day XD. Waiting to get a new case before I put it back together, long story. (was only a few days ago). Crunchbang and Debian+LXDE are also good alternatives that will run well but might use a little more resources (those are too big for that tiny HD of mine so I went straight for Puppy on that box).

---

### Post by gymophett on 2009-07-01
Crunchbang. You may be reluctant to OpenBox, but Crunchbang makes it amazingly easy with all the codecs pre-installed. It uses very little ram, and is based on Ubuntu. It is one of my favorite distros, give it a try. :)

---

### Post by XubuRoxMySox on 2009-07-02
> **gymophett said:**
> Crunchbang. You may be reluctant to OpenBox, but Crunchbang makes it amazingly easy with all the codecs pre-installed. It uses very little ram, and is based on Ubuntu. It is one of my favorite distros, give it a try. :)

+1 to [Crunchbang]("http://crunchbanglinux.org"), I am a fan too. But **Crunchbang does not "play nice" with LXDE.** I know because I tried and tried like crazy, changing setting after setting, tweaking this, installing that... but I was plagued with minor issues like muted sound, and a major issue with forced shutdowns.

I still have no idea why an ubuntu-based distro should be so incompatible with LXDE, but if you insist on a graphical desktop environment, Crunchbang is not for you. It has *no desktop environment at all*, only the window manager (Openbox) which, actually, is awesome! When you first see the Crunchbang "desktop," with it's stark black-and-white background and keyboard menu, you think, "Omygosh, what do I click on??"

Heh heh. **RIGHT-click the desktop.** Bingo! This whole awesome menu appears and off you go. And what a ride! Mind-bending speed, easy access to all your applications, everything just works. Sweet! And that stark, minimalist balck-and-white desktop can be customized with Conky for all kindsa wicked stuff. Some of their screenshots are just unbelievable.

+1 to Crunchbang - but only if you can do without a traditional desktop environment.

---

### Post by Sublime Porte on 2009-07-02
You might want to check out [TinyME Droplet](http://en.wikipedia.org/wiki/Tinyme).

It seems to meet all your requirements.

It uses apt (synaptic) with rpm's, and uses the PCLinuxOS repos, so quite a lot of software available.
It uses pretty much LXDE for it's desktop (might be missing one or two of the LX* tools).
It has a very appealing look out of the box, no need to configure anything.
InstallCD is only 150mb in size.
It's quite fast and lightweight, doesn't come with much installed though, but it's easy enough to do in Synaptic, only installing the stuff you want.
Uses the PCLinuxOS control panel to configure everything from one central location, very nice feature.

---

### Post by anticapitalista on 2009-07-02
TinyMe is a nice distro but it is broken at the moment and the dev advises waiting for the next version.

---

### Post by credobyte on 2009-07-02
128MB RAM, 8GB HDD space - Debian runs just fine ( a lot faster than Ubuntu on 256MB RAM :D ).

---

### Post by magikx21 on 2009-07-02
> **gymophett said:**
> Crunchbang. You may be reluctant to OpenBox, but Crunchbang makes it amazingly easy with all the codecs pre-installed. It uses very little ram, and is based on Ubuntu. It is one of my favorite distros, give it a try. :)

I had an old PC (700mhz, 256MB RAM) running Slitaz. It ran good but I had a hard time getting used to Slitaz. I recently installed CrunchBang (By install Ubuntu 9.04 CLI install and running the CrunchBang scripts) and I can say I am much happier with it now. It runs good and gives me the Debian package system I am used to.

---

### Post by khelben1979 on 2009-07-02
[Comparison of Linux distributions - Wikipedia]("http://en.wikipedia.org/wiki/Comparison_of_Linux_distributions")

You can do your own judgement based upon the document above, I think.

---

### Post by Blacklightbulb on 2009-07-02
What about [Zenwalk]("http://www.zenwalk.org/")?

Oh and you probably already know about [DamnSmallLinux]("http://www.damnsmalllinux.org/")!

---

### Post by cguy on 2009-07-05
Since the extra busy days are over, I've come back to give another try.

Debian + LXDE - didn't work
two Zenwalk 5 disks I had laying around - didn't work (couldn't even copy the first file)
xubuntu 9.04 - install failed after copying a few files
Crunchbang - can't even load it
ubuntu 9.04 - the desktop loads but it takes about 10 minutes to load the installer and every time I click "next" it takes another 10-15 minutes to load the next screen

Except for the Zenwalk CDs which were pretty old, all the others were indicated to be written correctly.

Before I started this thread I succeeded to install an old Knoppix, but apt was broken beyond repair. I am trying a Knoppix 6.0.1 install now. *fingers crossed*

Quite a pain in the *** this laptop :)

I wonder if it's a hardware problem or a BIOS one. If it's the latter, I wonder if Gericom will send me a BIOS for a 10 y.o. laptop. :)

--

Thank you all for the recommends.

---

### Post by cguy on 2009-07-05
I finished installing Knoppix!!!
yaaaay! :D
No problems whatsoever!
Was it a some-Linux-distros issue so far? A Windows issue? A BIOS issue?
I don't know! It certainly wasn't a hardware problem since Knoppix rolled GREAT from start to end.

The 6.0.1 version is sweet. The live CD boot time was so, so small, I couldn't believe it. It loads 1000 times faster than Knoppix 4.
Second: it's using LXDE. Pretty fast, but fugly :). I'll have to put it to some real tests before I can say more.

------------------------------------------

The real sweetness of this experimentation is... #!
#!Crunchbang !!!
I love OpenBox, I love Conky, I love the stylish looks, I love the minimality, I love the speed, I love that it uses GTK+ apps.
It is so freakin awesome! :) :D

---

### Post by cirabisi2009 on 2009-07-06
> **cguy said:**
> I finished installing Knoppix!!!
yaaaay! :D
No problems whatsoever!
Was it a some-Linux-distros issue so far? A Windows issue? A BIOS issue?
I don't know! It certainly wasn't a hardware problem since Knoppix rolled GREAT from start to end.

The 6.0.1 version is sweet. The live CD boot time was so, so small, I couldn't believe it. It loads 1000 times faster than Knoppix 4.
Second: it's using LXDE. Pretty fast, but fugly :). I'll have to put it to some real tests before I can say more.

------------------------------------------

The real sweetness of this experimentation is... #!
#!Crunchbang !!!
I love OpenBox, I love Conky, I love the stylish looks, I love the minimality, I love the speed, I love that it uses GTK+ apps.
It is so freakin awesome! :) :D


CONGRATS!! glad to know that you found something that finally works.

---

