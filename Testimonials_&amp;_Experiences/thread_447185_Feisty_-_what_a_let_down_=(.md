---
title: "Feisty - what a let down =("
date: 2007-05-17
forum: Testimonials &amp; Experiences
---

### Post by Footissimo on 2007-05-17
Before I continue, let me say that I am in awe of what Ubuntu has done..and I think the community is just great...however..

**Feisty is just pants**.  I've only just gotten over the problems with resolutions and drivers for my Nvidia 7300GT..then I buy a Belkin F5D7000 (the one with the RaLink 2500 chipset) so I can go wireless whilst I am renovating my house...and, not only does it not work, but it crashes ubuntu as nearly each time I use it. I chose this card because it was supposed to work better with linux =( =(

Anyway, after much fiddling about I see something in launchpad and someone recommending installing linux-image-386 to get this chipset working...so I do it.

Now X crashes and I can't do anything to make it work again - everytime I boot up, it errors out before hitting GDM. Doesn't seem to matter what I do, it's just the same.  I'm not a techie person, so my patience with using the command line is very limited...and frankly after problems with graphics drivers, sound drivers and now this...I'm tempted just to go with XP until Gutsy comes out..or perhaps go look at some other distros.  I don't know, I just know that Feisty has managed to make this 'ordinary user' move away from linux for the first time in nearly 3 years =(

Before someone has a go about me 'giving up' - please note that I spent **several days** with the issue of the nvidia drivers/poor resolutions/frequencies before getting it worked out.  I'm NOT a techie type.

Anyhoo, many thanks Ubuntu people - you have been great =)

---

### Post by exploder on 2007-05-17
I understand your frustration, I have been there! I had no luck at all with Ubuntu until I bought my HP computer, now everything just works. In the past I had always built my own systems but just didn't have the time. The HP has Intel everything and is well supported.

You might give MEPIS and PCLinux a shot, both have very good hardware support. Both distro's also have good forums with helpful, knowledgeable people. 

I hope you stick with Linux. I was tempted to go back to Windows when problems seemed overwhelming but I just couldn't do it. Another good distro you might want to try is Fedora Core 6. My last PC "worked out of the box" with Fedora. and it had problematic hardware. It takes a Google search to get multimedia working in Fedora but there are some very good guides available

I wish you luck and don't give up! You will have success, you just need to consider other distro's that can resolve your hardware issues. Hopefully Gutsy will work well on your system when it comes out.

Hang in there!

---

### Post by newlinux on 2007-05-17
Perhaps use an older release, like 6.06. Good luck and hope you come back...

---

### Post by Morkalin on 2007-05-17
> **Footissimo said:**
> **Feisty is just pants**.  I've only just gotten over the problems with resolutions and drivers for my Nvidia 7300GT..then I buy a Belkin F5D7000 (the one with the RaLink 2500 chipset) so I can go wireless whilst I am renovating my house...and, not only does it not work, but it crashes ubuntu as nearly each time I use it. I chose this card because it was supposed to work better with linux =( =(

You have to remember that Feisty is in the "Proceed with caution" category of release streams.  If you have this much trouble you should probably use 6.06 LTS (Long Term Support - much more thoroughly tested and "stable").  If you use a bleeding edge release you **have to** expect a few hiccups.

Regards,
Wayne

---

### Post by Footissimo on 2007-05-18
Hiya,

Apologies for previous rant..though I'm still distinctly unimpressed with Feisty (apart from the video resolution/frequency, multiple soundcard and wireless problems, it's also been a right bugga with compiz).  I will try going back to Edgy - Ubuntu has been (relatively) stable for me for all releases from Hoary to Edgy and hopefully the above problems will be resolved with much less fiddling!

Regards

Foot

---

### Post by megabyte405 on 2007-05-18
The current RTxxxx drivers will hang if you try to disconnect from a network - they know this, it can be fixed if you compile your own kernel, but they're re-writing the driver (which will hopefully be done soon - I have several rt2570's) to solve th problem for good.  Until then, instead of using the disconnect in software, configure the card, then insert it to connect to the default network.  If you need to switch, remove the card rather than disconnecting.

---

### Post by weatherman1293 on 2007-05-20
I'm having the same problem with v.7000 of the card. It shows up as Belkin, and I've gotten ndiswrapper to install drivers, yet I had to manually tie the driver to it, and still no wireless connection in network-manager.

---

