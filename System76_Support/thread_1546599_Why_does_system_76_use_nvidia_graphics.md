---
title: "Why does system 76 use nvidia graphics?"
date: 2010-08-05
forum: System76 Support
---

### Post by tc101 on 2010-08-05
Why does system 76 use nvidia graphics?  Looking over the forums, there seem to be lots of problems with ubuntu and nvidia.

---

### Post by msrinath80 on 2010-08-05
It's not their fault. The laptops they sell are usually made by other ODMs like Clevo. They brand it and then install and provide support for Ubuntu. Unless I am mistaken and System76 also tweaks the hardware beneath the hood? In my opinion, nVidia and ATi graphics are awesome, but best suited to desktops. Using them in laptops is like using an industrial furnace to prepare bread instead of using your conventional toaster!

---

### Post by tc101 on 2010-08-05
I have a nvidia graphics card in an old computer, but it is running 10.04.  I can't adjust the resolution.

---

### Post by pipemartinm on 2010-08-05
> **tc101 said:**
> I have a nvidia graphics card in an old computer, but it is running 10.04.  I can't adjust the resolution.
Yeah, me too. I'm stuck with the 4:3 resolutions, <snip>

---

### Post by HotShotDJ on 2010-08-06
NVidia has historically offered the better support of the "big two" graphics card makers.  From what I understand, ATI has only recently caught up.

The only NVidia problems that I've run into involve Plymouth, which should never have been rolled out in a LTS release.  However, I suspect those problems will be fixed in short order.

Regarding your issues, have you asked for help in an appropriate forum?  Are your computers System76?  <snip of my reference to above snipped phrase> What steps have you taken to correct the issue?

---

### Post by corrytonapple on 2010-08-06
ATI doesn't work any better with Ubuntu. Between the two, Nvidia is better. Better driver support in general is the seller.

---

### Post by msrinath80 on 2010-08-06
> **corrytonapple said:**
> ATI doesn't work any better with Ubuntu. Between the two, Nvidia is better. Better driver support in general is the seller.

Exactly. That's why I chose Intel. It does everything I need :)

---

### Post by endotherm on 2010-08-06
> **tc101 said:**
> Why does system 76 use nvidia graphics?  Looking over the forums, there seem to be lots of problems with ubuntu and nvidia.
true, but not nearly so many as ubuntu and ati.

ati has really gotten their act together in the last 2 years, but until recently making ati work with linux was neigh impossible. also ATI because of their pairing with AMD makes nvidia a better choice for intel based systems  or lines that come in both amd and intel flavors. 

don;t get me wrong, there are problems with all of them, but until lucid the restricted driver ubuntu publishes was incompatible with EVERY model of ati card i own. since i had to use a driver package from ati directly, every other ubuntu update would unlink it from the kernel, at which point I had to rerun the installer. on one box, it seemed like I had to reinstall the driver every week....

---

### Post by endotherm on 2010-08-06
> **msrinath80 said:**
> Exactly. That's why I chose Intel. It does everything I need :)
except work well with ubuntu
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by corrytonapple on 2010-08-06
I'm using Intel right now. But I would prefer to be using Nvidia. I see more issues with ATi. Not to say there aren't issues with Nvidia though.

---

### Post by msrinath80 on 2010-08-06
> **endotherm said:**
> except work well with ubuntu
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Perhaps. But if one looks a little out of this fancy Ubuntu world, they see that there are relatively sane distributions out there that provide a much more pleasant experience (read: Debian). I've never had any problems with Intel chipsets in Debian (lenny and squeeze now). Perhaps there is some benefit to testing each release meticulously before calling it stable and releasing when ready, and not when a deadline is hit. I'm just saying :)

---

### Post by corrytonapple on 2010-08-06
See this:
[http://ubuntuforums.org/showpost.php?p=9685957&postcount=18](http://ubuntuforums.org/showpost.php?p=9685957&postcount=18)

---

### Post by endotherm on 2010-08-06
> **msrinath80 said:**
> Perhaps. But if one looks a little out of this fancy Ubuntu world, they see that there are relatively sane distributions out there that provide a much more pleasant experience (read: Debian). I've never had any problems with Intel chipsets in Debian (lenny and squeeze now). Perhaps there is some benefit to testing each release meticulously before calling it stable and releasing when ready, and not when a deadline is hit. I'm just saying :)

yeah, there were a lot of trouble with the open drivers for the 900 series chipsets that came up with Hardy and got worse with intrepid. Intel has addressed much of the problem but there isn't too much they can do for the lowend chipsets like the 915. the 915 was the reason Intel bribed MS into changing the "vista capable" certification to make it certify machines that were not actually capable of running areo. 
[http://arstechnica.com/hardware/news/2008/03/the-vista-capable-debacle-intel-pushes-microsoft-bends.ars](http://arstechnica.com/hardware/news/2008/03/the-vista-capable-debacle-intel-pushes-microsoft-bends.ars)

Mark Shuttleworth called intel out for bad drivers about 2 years ago, and then last year claimed publically that they had had trouble getting support from "one Very large manufacturer" but that the manufacturer (Intel) had since seen the light and come around and would be increasing its emphasis on support for the linux kernel.

I don't think your characterization that it is untested is fair. what do you do when you test someone elses software, and it doesn't work, but you don't have the time or expertise in the very niche area the software occupies to fix it yourself? does that mean that you kill the release and do nothing, all the while hoping that some other guy will get his own house in order? or do you release for everyone else and attempt to shame the bad actor into fixing his ways? if we had allowed this kind of thing to stop us, we never would have gotten linux 0.1, let alone 2.26.35.

---

### Post by msrinath80 on 2010-08-06
> **endotherm said:**
> 
I don't think your characterization that it is untested is fair. what do you do when you test someone elses software, and it doesn't work, but you don't have the time or expertise in the very niche area the software occupies to fix it yourself? does that mean that you kill the release and do nothing, all the while hoping that some other guy will get his own house in order? or do you release for everyone else and attempt to shame the bad actor into fixing his ways? if we had allowed this kind of thing to stop us, we never would have gotten linux 0.1, let alone 2.26.35.

Valid points, no doubt. But my point is that Debian has the same resources as Ubuntu does (coming from Intel that is). However, in addition, it has certain rules that decide whether or not a certain driver is release worthy. So they pick the best available version (with the lowest possible bugs NOT zero bugs) and then test it with all possible hardware (done by the community) and then it is released. My only gripe is that Ubuntu knows that display, sound etc. are key elements that need stability more than anything else. Despite this, they and distributions like Fedora keep repeatedly releasing drivers without proper testing. Actually, in hindsight, I don't blame Fedora. They've been outright in claiming that they are interested in bleeding-edge technology. But regarding Ubuntu, I'm not sure. Coming from a Red Hat background, I used to use Feisty a few years ago and I thought to myself wow this is really stable. Then when I tried Debian stable, I was like, OMG if Feisty was stable, this is crazy stable. You really have to run Debain to see what I mean :) Bottom line is that distros like Debian *really* work hard at any release they make.  They do not disappoint the masses. Ubuntu on the other hand, while proving a fancy desktop, sacrifices stability, a lot. It's all relative!

---

### Post by isantop on 2010-08-06
Here's my personal take on the Ubuntu graphics dilemma:

Intel has the best drivers. Their products aren't as powerful as discrete graphics, but they do a decent job at most things. Plus, the drivers are open source, which means the community can com in and fix, say, kernel mode setting for plymouth, for example. Thus, for most people, Intel is a good choice. We will (almost) always provide Intel grahpics in our lower half of systems (Ratel, Meerkat, Lemur, etc.) (The Ion NetTop is an exception).

ATI, on the other hand, has much better hardware. The big Ubuntu problem with these cards is that the drivers are missing some key features. Blur comes to mind, as does KMS.

Nvidia, on the other hand, has (in general) slightly less powerful hardware with much better drivers. True, there are some things missing, (like that darn KMS problem), but in general they are well supported. A good trade off between hardware and software.

---

### Post by msrinath80 on 2010-08-06
isantop, you'd make a wonderful diplomat :)

---

### Post by isantop on 2010-08-06
So I've been told. However, I'd rather be a System76 Support Technician. :)

---

### Post by Fait on 2012-08-18
Is there any word on if/when system76 laptops will get nvidia/ati graphics? Looking at buying a Gazelle Professional but thats a deal-breaker. Im not in a big hurry but its something that needs to happen for me and Im wondering whats in the works.  Also Ive read AMD has done alot for the open source driver, helped create it, - and formed a symbiotic relationship with it so that when the foss driver realeases a high enough level of maturity for a certain amd/ati card the official support is dropped.  Whilst I've not heard anything good about nvidia support. Optimus come to mind, as does Linus Torvalds flipping them off.  Any info is appreciated.

---

### Post by zenlunatic on 2012-08-19
isantop left out security.  Nvidia drivers have big enough security holes you could drive emacs through them.

---

### Post by Ubun2to on 2012-08-20
> **Fait said:**
> Is there any word on if/when system76 laptops will get nvidia/ati graphics?

Laptop graphics are good at best-if you are looking for a gaming rig, you need to be looking at desktops.

---

### Post by overdrank on 2012-08-20
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

