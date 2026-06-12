---
title: "Best Ubuntu Flavor for a Video Player?"
date: 2015-04-14
forum: Ubuntu, Linux and OS Chat
---

### Post by Kpenguin on 2015-04-14
Hi everyone,
I'm thinking of using my old desktop computer as a video player that I'll plug into my TV. What Ubuntu flavor would be best to put on it?

---

### Post by pmi2 on 2015-04-14
This might depend on the processor/memory/video/disk in your old desktop.  
If you post what hardware you have, you may get better advice, ;)

---

### Post by Kpenguin on 2015-04-14
It has a single core Intel Celeron 1.7 ghz processor, 1gb of RAM, a Nvidia GeForce graphics card, two CD drives (I plan on getting a DVD drive), and an 80 gb HDD.

---

### Post by Mike_Walsh on 2015-04-14
That's, ummm....QUITE an old machine. Circa 2003/4? I had a 2.2 GHz Celeron single-core in my elderly Dell laptop (since changed for a P4, with which it runs MUCH better); videos were barely watchable  with it.....lots of stuttering and/or choppiness & lag. And yours is running considerably slower.

If you want to still use this machine, find out what socket your CPU uses. If it's Socket 478, then you can upgrade to a P4; a 2.4 or 2.6 GHz will make a world of difference, and they can be picked up for a song on eBay (anywhere from £5-£15...$8-$24, approx). It'll mean a little bit of work, fitting it.....but it will transform it. The biggest snag with the single-core Celerons is the very small L2 cache; 128 k. The P4's have 4 times this, at 512 k.

And if you can increase the RAM.....so much the better. Doubling that to 2 GB will make a BIG difference.


Regards,

Mike. :)


Regards,

Mike.

---

### Post by Kpenguin on 2015-04-14
I have already maxed out the memory. If I upgrade the processor to a Pentium 4 2.6ghz, what Ubuntu flavor will work best for a media center like setup?

---

### Post by pmi2 on 2015-04-14
Two different scenarios:

1) Playing a video, output to a TV via VGA or HDMI cable
2) Media Center setup (for example Mythbuntu)

Take a look at the minimum and recommended requirements at the link below for Media Center operation,  I would also think really hard about what max resolution you want, because otherwise you may be disappointed.  Note the small print... HD video requires something like a 2GHz, Dual Core processor to guarantee playback in true HD for some formats (!)

[http://www.mythbuntu.org/support](http://www.mythbuntu.org/support)

---

### Post by mörgæs on 2015-04-14
It's not only a question of CPU, also the graphics processor is likely to be a bottleneck.
You could try Mythbuntu or some of the light distros like Lubuntu or Puppy but be prepared that you might need stronger hardware.

---

### Post by grahammechanical on 2015-04-14
Nvidia might no longer support that video adapter and all flavours of Ubuntu automatically install the latest proprietary video drivers if we tick the box "Install Third Party Software." So, do not tick that box and after installation install Ubuntu Restricted Extras to get those audio and video codecs. And search the software centre for an older video driver to install.

Regards.

---

### Post by mörgæs on 2015-04-15
> **grahammechanical said:**
> Nvidia might no longer support that video adapter

We don't know this, because we don't know the adapter. Graham, it would be appreciated if you told original poster to find out which adapter he has before posting like this. 

> **grahammechanical said:**
> all flavours of Ubuntu automatically install the latest proprietary video drivers if we tick the box "Install Third Party Software." 
and if one is available, of course. If there are only open source drivers then the option makes no difference.

---

### Post by Mike_Walsh on 2015-04-15
> **mörgæs said:**
> It's not only a question of CPU, also the graphics processor is likely to be a bottleneck.

Yes; quite right. The CPU is only one part of the equation, of course. The graphics card/adapter is the other, rather larger part of it. 

Two questions:-

1) Do you happen to know what year of manufacture your desktop is? That might give us a clue as to which generation of Celeron you're talking about. Some of the earlier ones were truly basic.....budget versions of the current Pentiums. The later ones were, in some cases, better than the earlier Pentiums; but it helps to have some idea of WHICH one you're talking about, because my earlier advice of upgrading to a Pentium4 might not apply.....depends a lot on which socket you have. Some used socket 775, but the majority used the earlier socket 478.

2) Is your GeForce graphics integrated into the motherboard.....or do you have a separate graphics card? And if so, can you tell us whether it's PCI, AGP or PCI-e (which is the current standard)? And of course, what model it is, please?


Regards,

Mike. :)

---

### Post by Bucky Ball on 2015-04-15
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Not a support request. With those specs suggest you try Lubuntu or Xubuntu.

Once you have found a video player you like it is not really about what Ubuntu flavour you use. If the video app is in the repositories, it is available to install in all the flavours since they all use the Ubuntu base kernel.

I'd be tempted to go with a [minimal install]("https://help.ubuntu.com/community/Installation/MinimalCD") and just install something like Xbmc, but that might be quite a learning curve. Good luck. ;)

---

### Post by Tar_Ni on 2015-04-15
The only flavor that will work decently on these specs is Lubuntu.

[http://lubuntu.net/](http://lubuntu.net/)

I am typing this on a 2GB RAM, Pentium 4 - 2.80 Ghz proc, Nvdia GeForce 8400 Rev. 2 desktop computer it works perfectly fine with Xubuntu 14.04.
But with 1GB of RAM and a 1.7 Ghz proc I would go for an OS that is even lower on ressources usage so as to get the most out of your old hardware.

---

### Post by Kpenguin on 2015-04-15
> **Mike_Walsh said:**
> 
Two questions:-

1) Do you happen to know what year of manufacture your desktop is? That might give us a clue as to which generation of Celeron you're talking about. Some of the earlier ones were truly basic.....budget versions of the current Pentiums. The later ones were, in some cases, better than the earlier Pentiums; but it helps to have some idea of WHICH one you're talking about, because my earlier advice of upgrading to a Pentium4 might not apply.....depends a lot on which socket you have. Some used socket 775, but the majority used the earlier socket 478.
Yes, It's a Dell Dimension 2350 made in 2000. It uses socket 478.

> **Mike_Walsh said:**
> 2) Is your GeForce graphics integrated into the motherboard.....or do you have a separate graphics card? And if so, can you tell us whether it's PCI, AGP or PCI-e (which is the current standard)? And of course, what model it is, please?
The graphics card is separate and is plugged into a PCI slot. It's a PNY Nvidia GeForce FX5200.

---

### Post by Mike_Walsh on 2015-04-15
> **Kpenguin said:**
> Yes, It's a Dell Dimension 2350 made in 2000. It uses socket 478.

Hm. I'm having a job getting these dates sorted out. According to you, it was built in 2000.....yet, according to Dell, it didn't hit the market until 2002/3. I DO need the right date here from you, because this was the exact time frame when Intel were transitioning the early Celerons/P4s from the previous socket 370 to socket 478. Socket 478 wasn't released onto the market until April, 2001. So if your machine definitely uses socket 478, and it's a 1.7 GHz, then it has to be an early Willamette-core, 'Netburst' architecture Celeron; can't be anything else. So your machine must be newer than you think it is.....IF you're sure about your dates, that is.


> **KPenguin said:**
> The graphics card is separate and is plugged into a PCI slot. It's a PNY Nvidia GeForce FX5200.

This is a bit trickier. This card is not a PCI-e (current standard) card; it uses the older PCI CardBus slot. It was also manufactured in the AGP slot format. Whichever it uses, however, you wouldn't be able to upgrade the card to a modern one.....so you're kinda stuck with that. The GeForce FX5200 was, however, reckoned to be a very powerful budget card at the time of its release, so you're probably okay on that score. 

However, if you're 'maxed out' at 1 GB RAM (which I find hard to believe in a PC of that era), then you're rather 'pushing the envelope' for what you envisage doing with the machine. I find myself agreeing with Tar_Ni here; I think you'll have a job running anything other than Lubuntu on those specs; or, as Bucky Ball has suggested, a minimal install with perhaps XBMC added ( apparently now known as Kodi). I suspect Bucky knows a wee bit more about this side of things, as he is, I believe, a musician.....among his many other talents..!


Regards,

Mike.

---

### Post by Kpenguin on 2015-04-15
> **Mike_Walsh said:**
> Hm. I'm having a job getting these dates sorted out. According to you, it was built in 2000.....yet, according to Dell, it didn't hit the market until 2002/3.
Oops, sorry about that. I was remembering another computer I had. :oops: It was made on February 14th, 2003.

---

### Post by Vt3c on 2015-04-15
Xubuntu is my two cents. It's really lightweight and it's turned some of my old junkers into beasts. But that's pretty much all I can recommend for something that dated.

---

### Post by mörgæs on 2015-04-16
The best way of getting hardware specifications is asking people to run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags. Much safer than letting people answer as good as they can.

---

### Post by Mike_Walsh on 2015-04-16
> **mörgæs said:**
> The best way of getting hardware specifications is asking people to run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags. Much safer than letting people answer as good as they can.

Thanks for that, morgaes. I'll remember in future (if I can kick the old grey matter into life, that is!).....

Regards,

Mike. :)

---

### Post by mattharris4 on 2015-04-17
> **Kpenguin said:**
> Hi everyone,
I'm thinking of using my old desktop computer as a video player that I'll plug into my TV. What Ubuntu flavor would be best to put on it?

The first question would be does your TV have a VGA plug on it?  Older computers usually do not have an HDMI outlet, most TVs require that type cord to be used to connect the two.  If your TV has a VGA plug on it, you can buy a refurb computer with a P4 3.0GHz processor and the ability to run video (assuming you install Flash Player on it) for less than $100 shipped, if you search carefully you can even find one with a DVD-RW drive installed (almost all of them have at least a DVD-ROM nowadays).  It will also come with Windows 7 which should be compatible with almost any video site out there after installing the proper drivers -- there are some video sites that are just not compatible with Linux (unfortunately) -- especially adult entertainment sites (I don't dare list any examples here as i don't want any minors reading this to then log onto them).  I am tempted to file a bug report with the sites listed but again I am afraid minors on this forum (yes, some kids do have an interest in computers) will then attempt to view the sites with that information, I really don't want to indirectly encourage 14 year old kids to watch porn (maybe moderators here have a solution to that issue, I would be interested to hear others thoughts on this issue).  Sites such as Hulu and YouTube do work fine with Linux after installing Pepper Flash, however.

---

