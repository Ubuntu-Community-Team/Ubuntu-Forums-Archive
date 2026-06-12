---
title: "Now THIS is why it's important to get OEM support for Linux!"
date: 2007-09-21
forum: The Cafe
---

### Post by Anthem on 2007-09-21
Not because "people don't know how to install the OS."  Not because it gives Linux a higher profile.  Those are nice, but the real issue is right here:

> This afternoon Intel's Chief Linux and Open-Source Technologist, Dirk Hohndel, talked about why Intel's commitment to open-source drivers creates a difference and advantage for Intel's architecture platforms.  . . . **He also mentioned that a major OEM is requiring that by next year their hardware suppliers must either have an open-source driver available or be able to provide an open-source driver within the next twelve months. **The likely company that comes to mind is Dell but Dirk refused to comment any further.

[http://www.phoronix.com/scan.php?page=article&item=850&num=1](http://www.phoronix.com/scan.php?page=article&item=850&num=1)

That's the deal.  Add in the fact that companies can have drivers written for free just by opening the specs, and open-source drivers will become a major factor in the hardware arena.

The journey towards global occupation continues apace.

---

### Post by Anthem on 2007-09-21
And it's not like having Linux drivers hurts their Windows drivers.  On the contrary, my experience is that anything that's well-supported in Linux seems to have a better chance of being well-supported in Windows.

Everybody wins.

---

### Post by Pekkalainen on 2007-09-21
I find it wonderful that they are finally talking about releasing specs and not just provide binary blobs, it makes a huge difference :KS

---

### Post by davahmet on 2007-09-21
From my days as a Linux integrator at HP's Imaging and Printing Lab, there are two important business lessons that Intel seems to have grasped very well.

1.  The cost of integrating firmware into an existing system can be very high when dealing with binary code blobs.  While the potential loss of IP may lead to significant  losses, the realities of software engineering dictate that the additional development costs that come from trying to integrate complex bits in a proprietary framework may far exceed any revenue protection of the proprietary solution.  Low cost integration demands developing to open standards free from proprietary encumbrance.

2.  Another extraordinary cost of firmware development comes from the high cost of code maintenance after delivery.  After-release maintenance costs run magnitudes higher in revenues, resources and time delays.  However, when firmware code is released as open-source, with the full transparency expected of OSS, community support is quick, efficient, and provides highly reliable code fixes at nearly zero cost to the sponsor.

With these two principles, as Intel as realized, the ability to develop and maintain a competitive advantage shifts heavily in favor of design and implementation, unburdened by the heavy costs of integration and post-release maintenance.  That is, the competitive advantage for a company's products is based on its own merit, rather than the company's unilateral ability to force interoperability on its own terms.  

To further enhance its position in the marketplace, the sponsoring company is best served by supporting and encouraging community participation.  As Linux users, we know quite well that the transparency of open source along with clear documentation are the best ways to quickly gain community support.

---

### Post by Anthem on 2007-09-21
The more I think about this, the more I'm just in awe.

If the "major OEM" is Dell, then you're really starting to see the benefit of Shuttleworth's relationship w/ Dell.  This might be the biggest influence that the man has in the open-source world.  If Dell demands that all hardware have open-source drivers, then it's a whole new world.  That explains a ton about ATI/AMD opening their drivers... they want to be able to deal with Dell.  And they won't be the only ones... anybody who wants to sell hardware to Dell (which is everybody) will have to do the same.

And if Dell gets benefit from the requirement (again, good Linux drivers usually implies good Windows drivers), then other OEMs will start doing the same thing just to keep up.  If we get HP and Lenovo onboard in the next year, then the move will almost be unstoppable.

---

### Post by angryfirelord on 2007-09-21
It's amazing how quickly some of these major companies are adopting open-source policies. Intel just released a new project called Lesswatts.org
[http://www.lesswatts.org/](http://www.lesswatts.org/)

Very exciting!

---

### Post by regomodo on 2007-09-21
i don't know why but all i can think is that something bad will come of this. Sort of a gut feeling. I must be right as there are more nerve endings than in your brain. Look it up

---

### Post by robert_pectol on 2007-09-21
> **regomodo said:**
> i don't know why but all i can think is that something bad will come of this. Sort of a gut feeling. I must be right as there are more nerve endings than in your brain. Look it up
That's called hunger!  Go eat!  :-D

---

### Post by Anthem on 2007-09-21
A major OEM is requiring open-source drivers from all of their component suppliers, and you consider this a BAD thing?

Wacky.

---

### Post by ~~Tito~~ on 2007-09-21
This is gonna be awesome, now I will be able to build a computer that will be very powerful and not be limited to things that are supported in linux, they will have to be supported so then I can build what ever I want with out that fear!

---

### Post by BoyOfDestiny on 2007-09-21
> **Anthem said:**
> The more I think about this, the more I'm just in awe.

If the "major OEM" is Dell, then you're really starting to see the benefit of Shuttleworth's relationship w/ Dell.  This might be the biggest influence that the man has in the open-source world.  If Dell demands that all hardware have open-source drivers, then it's a whole new world.  That explains a ton about ATI/AMD opening their drivers... they want to be able to deal with Dell.  And they won't be the only ones... anybody who wants to sell hardware to Dell (which is everybody) will have to do the same.

And if Dell gets benefit from the requirement (again, good Linux drivers usually implies good Windows drivers), then other OEMs will start doing the same thing just to keep up.  If we get HP and Lenovo onboard in the next year, then the move will almost be unstoppable.

Seriously. Some will say this was bound to happen though, and likely will have a domino effect. Excellent hardware support out of the box. I've seen people complain about installing binary drivers, I've done that once (for a radeon, but then stuck to the open driver...) and once for ndiswrapper. These issues won't exist anymore with open drivers. Let alone the inability to fix the driver by anyone but the vendor...

I'm hoping the complaints will be limited to, where is photoshop and dreamweaver? Then either they start porting or use wine...

Anyway, I can vouch on my dell laptops (2 others I maintain as well), gutsy doesn't need that i915resolution hack anymore, and onboard sound support is perfect (something I can't say about any other ubuntu release...) So it's come to a point where from a fresh install, the only tweak I do out of preference is disable the sound server, and let alsa + dmix do it's thing.

That's it. Every single other thing is configured perfectly. Of the devices in the house, all plug and play hp laserjet, epson scanners... The part with the scanner is ridiculous. Plug it in... and that's it. Fire up gimp or xsane and scan. Now if more hardware was like that... talk about smooth. 

So yes it's a very good thing.

---

### Post by linux23dragon on 2007-09-22
The move towards "Open drivers" (and specs) makes sense.  Microsoft is killing the PC industry with false hardware and driver specification contracts (with Vista and DirectX 10).  And now, Microsoft is allowing the OEM to sell XP again? 


Microsofts actions goes against any standard, and can only waste money in both short and long term.  For the OEM, this will be a very big support issue.

Open device drivers for the OEM will improve their hardware support. It will benefit todays (and tomorrows) marketing demands, without having to deal with high resource and development costs.

Having Open device drivers means the OEM can provide better quality products that is (now) unimaginable to todays market standards.  We now have a chance to move forward (not backwards) in computing technology.

---

### Post by brokenstrides on 2007-09-22
My problem hasn't been with hardware in Linux. I had to install my wireless driver through NDISwrapper, but that required just a couple more steps than just inserting the CD. Whoop de doo. Although, having all that native support could make it run more efficiently and everything...

I want some more software support! Where's my native WoW client? Photoshop? iTunes and iPod support? I suppose more software like that will come once we have the backing for it, though.

---

### Post by BoyOfDestiny on 2007-09-23
I almost wanted to start another thread over this.

[http://www.linux-watch.com/news/NS7536907294.html](http://www.linux-watch.com/news/NS7536907294.html)

"Dell and Linux distributors have been working on DKMS for about five years now. Its purpose is to create a framework where kernel-dependent module source can reside, so that it is very easy to rebuild modules. In turn, this enables Linux distributors and driver developers to create driver drops without having to wait for new kernel releases. For users, all this makes it easier to get up-to-the-minute drivers without hand compiling device drivers."

All I can say is amazing. OEM support will make waves. I'm glad all the laptops in this household as of late are DELLs. Vote with your wallet folks. :)

Additional quote because it's so important
"This isn't pie in the sky technology. Dell already uses it. "Dell uses DKMS to distribute updated device drivers for RHEL (Red Hat Enterprise Linux), SLES (SUSE Linux Enterprise Server), and Ubuntu built against those products' gold kernels. "This lets us fix and replace individual device drivers to support new hardware without having to respin the whole CD like we wound up doing for Ubuntu," said Domsch."

Awesome. Awesome to max!

:guitar:

---

### Post by pek on 2007-09-24
do you know if/when those patches will be integrated in mainstream kernel?
i do not like to mess with that, not enough time.

---

### Post by Kowalski_GT-R on 2007-09-24
> **BoyOfDestiny said:**
> 
OEM support will make waves. 

Don't know why, but this sentence is particularly inspiring.

open standards, they can't come soon enough for me.

ciao,

Andre

---

### Post by LowSky on 2007-09-24
Well if it is Dell, then it makes sense why ATI went open source with its code, as ATI does supply alot of graphic chips to intel based computers.

I bet Nvidia will be following suite, and most likely Logitech as they supply many companies perpherals.

---

