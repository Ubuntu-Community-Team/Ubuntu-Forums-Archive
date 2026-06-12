---
title: "A week or two with 9.10"
date: 2009-11-16
forum: Testimonials &amp; Experiences
---

### Post by TBerk on 2009-11-16
Well, I had been dual booting XP and Ubuntu 8.x then 9.04 Studio. (I use XP to burn media in the DVD-RW drive, Ubuntu still won't burn DVD/CDs correctly. Yet.)

I had trouble initially trying to update the 1st day, over the top of 9.04. Luckily I had set up my /Home directory on another partition.

Wiping out the / Partition I installed 9.10 <plain> then began patching it via Update Manager and Synaptics over the next few days. 

I resolved my SB Audigy's lack of output (again) by toggling the Audigy Analog/Digital Output Jack (sane 'fix' as in 9.04).

I resolved my Axim X5 not being seen as an external device in Nautilus just this evening by adding 
```
sudo apt-get install synce-gvfs
```  to my existing Multi-sysnc/SynCE install.

I also had no trouble with a 'new to me' Epson inkjet printer; it was almost like all I had to do was plug it in. (Not quite, but it was extremely painless.)

This last year I have been Linux 85% and the remainder has been WinXP and some enduser's w/ Vista.  (I really should be doing more with Win7 to stay current, but it's boring...)


berk

---

### Post by Zoot7 on 2009-11-16
> **TBerk said:**
> This last year I have been Linux 85% and the remainder has been WinXP and some enduser's w/ Vista.  (I really should be doing more with Win7 to stay current, but it's boring...)


berk
Gotta agree there. I really don't see anything all that exciting in 7, the only reason I'll be picking it up is to take advantage of the student offer while I can, on account of being a gamer.

---

### Post by dE_logics on 2009-11-16
> DVD-RW drive, Ubuntu still won't burn DVD/CDs correctly.

The hal daemon might be giving problems, just before burning try this - 

```
/etc/init.d/hald stop
```

Then - 

```
pkill hal
```

---

### Post by HappyFeet on 2009-11-16
> **TBerk said:**
> (I use XP to burn media in the DVD-RW drive, Ubuntu still won't burn DVD/CDs correctly. Yet.)


Strange. In my 3 years using ubuntu, I've never had a problem burning cd's or dvd's in ubuntu. But then again, I must be the only one it works for.

---

### Post by Zoot7 on 2009-11-16
> **HappyFeet said:**
> Strange. In my 3 years using ubuntu, I've never had a problem burning cd's or dvd's in ubuntu.
Ditto, except it's 2 years in my case.

---

### Post by solwic on 2009-11-16
> **HappyFeet said:**
> Strange. In my 3 years using ubuntu, I've never had a problem burning cd's or dvd's in ubuntu. But then again, I must be the only one it works for.

Brasero was borked in 9.04 for me and another guy I know.  Didn't matter, really; Brasero is junk anyway, and a simple apt-get for k3b fixed the issue.  :)

Other than that, no problems here either.

---

### Post by Tamlynmac on 2009-11-16
> solwic
			 		 	 	 Brasero was borked in 9.04 for me and another guy I know. Didn't matter, really; Brasero is junk anyway, and a simple apt-get for k3b fixed the issue. :smile:

I also had problems with Brasero on 9.04 (no problem with previous releases). As solwoic indicates I too switched to K3b and haven't had a problem since. Possibly a hardware driver issue, but with all the available FOSS options it's a non-issue.

It's great to have so many free choices to pick and choose from....:D

---

### Post by TBerk on 2009-11-18
> **dE_logics said:**
> The hal daemon might be giving problems, just before burning try this - 

```
/etc/init.d/hald stop
```

Then - 

```
pkill hal
```

I'm going to try that soonest, currently I am installing k3b per other posters' suggestions.

btw- it (k3b) sure wants to install a bunch, doesn't it?

```

$ sudo apt-get install k3b
[sudo] password for xxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libboost-test1.40.0 libboost-regex1.40.0 libboost-wave1.40.0
  libboost-program-options1.40.0 libopenmpi1.3 smplayer-translations
  libibverbs-dev libboost-thread1.40.0 libboost-serialization1.40.0
  libboost-date-time1.40.0 libnss3-dev libboost-signals1.40.0
  libboost-graph1.40.0 libboost-math1.40.0 libboost-graph-parallel1.40.0
  mpi-default-dev libboost-iostreams1.40.0 libibverbs1 libboost-mpi1.40.0
  openmpi-common libboost-filesystem1.40.0 libopenmpi-dev
  libboost-system1.40.0 libboost-python1.40.0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  akonadi-server k3b-data kde-icons-oxygen kdebase-runtime
  kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common
  kdebase-workspace-bin kdebase-workspace-data
  kdebase-workspace-kgreet-plugins kdebase-workspace-libs4+5 kdelibs-bin
  kdelibs5 kdepim-runtime kdepim-runtime-data kdepim-runtime-libs4
  kdepimlibs-data kdepimlibs5 khelpcenter4 libakonadiprivate1 libclucene0ldbl
  libk3b6 libkcddb4 libknotificationitem1 liblzma0 libplasma3 libpolkit-dbus2
  libpolkit-grant2 libpolkit-qt0 libpolkit2 libqimageblitz4 libsoprano4
  libstreamanalyzer0 libstreams0 libstrigiqtdbusclient0 mysql-server-core-5.1

```

Not being able to burn media is my main ongoing Ubuntu failing, I'll report back w/ results. Other than that it's my main OS and does it well.


berk
(ps- I'll consider the autoremove option later...

---

### Post by gtrtx on 2009-11-18
> btw- it (k3b) sure wants to install a bunch, doesn't it?

It's a KDE application, so it installs a bunch of KDE packages. 

However, looking at what you have posted, it appears you have as many unneeded package installed already that you can get rid of by doing:
```

sudo apt-get autoremove
```

---

### Post by TBerk on 2009-11-18
> **gtrtx said:**
> It's a KDE application, so it installs a bunch of KDE packages. 

However, looking at what you have posted, it appears you have as many unneeded package installed already that you can get rid of by doing:
```

sudo apt-get autoremove
```

Yeah, as I said, I'll get around to it.

So far I have installed k3b and tried a burn of a CD-R; no joy.

I am investigating the hardware to see if DMA support is at fault and if I need to remove the DVD read only drive on the same IDE chain as the DVD-RW drive.

btw, keep in mind this thread was "9.10 works great, mostly..." in nature.

The fact that Ubuntu won't burn media while WinXP, et all can on the same computer is a problem, but work-around-able.

(My only other big gripe at the moment is better [whole file] buffering support in Totem, but that is another thread...)


berk

---

