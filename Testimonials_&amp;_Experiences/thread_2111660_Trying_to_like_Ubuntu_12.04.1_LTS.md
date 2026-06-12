---
title: "Trying to like Ubuntu 12.04.1 LTS"
date: 2013-02-02
forum: Testimonials &amp; Experiences
---

### Post by TrakerJon on 2013-02-02
I've been using Ubuntu for quite some time...you may have seen my posts "Ubuntu Desktop Computing Made Easy" for various releases. It's my goal to help others (as much as possible) to have a good experience with Ubuntu, mainly because I've I truly have enjoyed the product as an alternative to the "we know what you want and you better damn well like it" model that Microsoft pushes on the masses. Having said that...I have some concerns about the latest Ubuntu 12.04.1 LTS release from Canonical Ltd.

I typically use older Dell GX260 and GX270 computers with 256 nVidia 6200 graphics cards and 2Gb of physical RAM to test new releases so that folks that can't afford a new computer will know what to expect. The 10.04.4 LTS version of Ubuntu works absolutely great on these boxes. I wish I could say the same about Ubuntu 12.04.1 LTS.

Starting with the installation... 

If the options to download updates and third party software is selected (after connecting to the internet) the installation hangs at the end. Yes, I've tried several times with the same results on different boxes.

There is no intuitive way to install Ubuntu on a specific partition, it's an all or nothing proposal unless you really know what you're doing by selecting "something else" to manually partition the drive.

After using the base install method (without connecting to the internet) Ubuntu 12.04.1 LTS installed fine but was notably slower when loading the Unity desktop. The security updates went ok but when I activated the nVidia drivers my system locked up tight when loading the desktop after the reboot. I deactivated the nVidia drivers and decided that maybe it was the video card causing my problems so I moved on to some simple software installations. I started installing a few favorites like VLC, Inkscape, Shutter, Audacious, etc. but almost immediately I started receiving error messages prompting me to send them to support for review. Needless to say I wasn't having a good time at this point. 

My video card wasn't activated...application installs were creating error messages and it's got me thinking I've got hardware problems. Out comes another Dell box...same thing all over again. I couldn't even get something as simple as the ttf-mscorefonts-installer to load fonts to use with Libre Office without giving me problems.

Conclusion...I haven't tried Ubuntu 12.04.1 LTS on a newer computer with stronger processor and better graphics capabilities yet so I'm not quite ready to write it off but I seriously think Canonical may want to consider revising their minimal installation requirements regarding hardware. Until then or after some serious effort has been made towards an OS revision I'm holding off on Ubuntu Desktop Computing Made Easy for 12.04.1 LTS. The same applies to Ubuntu 12.10, I don't know what Canonical is up to but they may be losing a significant amount of potential customers and long time users in the dust if they continue on this path.

TrakerJon

---

### Post by cwblanch on 2013-02-02
I haven't used Ubuntu since 10.04 so I was also a bit concerned with how it was running on my laptop (an Acer Aspire 5735Z with 2GHz processor and 2GB of RAM, which is a fairly basic computer) I was also getting the update errors and a few hangs and system locks. But it seems after using it for a while the errors have stopped, as well as the hangs and locks.

---

### Post by snowpine on 2013-02-02
12.04 has higher system requirements than 10.04 because: [http://en.wikipedia.org/wiki/Moore%27s_law](http://en.wikipedia.org/wiki/Moore%27s_law)

---

### Post by Tamlynmac on 2013-02-03
> snowpine

The catch in Moore's Law is obsolescence. Obsolescence implies that we're all using obsolete technology. As companies dole out the technology, profit becomes the primarily goal. I have no problem with profit, only that consumers receive the maximum for their dollars and not be duped into believing their receiving the most advanced technology.

The so-called consumer has become accustomed to believing what's available today in consumer electronics is "state of the art". When in reality, technology advances exponentially while consumer electronics are released based solely on profit. This creates a dilemma for consumers, should they buy the most recent and costly hardware or should they purchase what they can afford without going into debt? Both are obsolete based on Moore's Law, but obviously one must purchase hardware that's required by their OS/software. Assuming they wish to keep up with trends and the most recent releases.

The solution IMHO is to purchase that which one can afford and not buy into all the marketing hype. Unfortunately,this option falls short when considering that advancements in OS/software may dictate hardware improvement. A vicious circle. This might suggest one establish exactly what their computing needs are and will be in the near future. Then only purchase that which is necessary. I know few that can afford to constantly upgrade from antiquated to obsolete hardware, in an effort to keep up.

It appears, the only way to keep up is either to be wealthy or to stay in consumer debt - while remaining under the misconception that one's using "state of the art" technology. When at best, it might be considered "todays state of the art" consumer technology.

Just my $0.02

---

### Post by monkeybrain2012 on 2013-02-03
> My video card wasn't activated...application installs were creating error messages and it's got me thinking I've got hardware problems. Out comes another Dell box...same thing all over again. I couldn't even get something as simple as the ttf-mscorefonts-installer to load fonts to use with Libre Office without giving me problems.

That is a Nvidia problem. They no longer support your card for the new xorg. 

As long as the graphic card works, you can install Lubuntu if Ubuntu with Unity is too heavy on resources. The option is there, provided the hardware remains compatible, but compatibility has more to do with upstream and hardware makers such as Nvida than Canonical. So I don't understand why this insistance that new Ubuntu with all the bell and whistles must work with ancient machines while you have other choice of DEs and flavours.

---

