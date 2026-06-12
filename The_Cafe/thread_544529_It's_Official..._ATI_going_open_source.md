---
title: "It's Official... ATI going open source"
date: 2007-09-06
forum: The Cafe
---

### Post by igknighted on 2007-09-06
[http://www.linux.com/feature/119049](http://www.linux.com/feature/119049)

In four days the code (or at least specs) will be available!

EDIT: Congrats to AMD for turning around ATI.  Between this and the most recent drivers and the news of AIGLX coming soon, they have really done a bang up job.

---

### Post by @trophy on 2007-09-06
One step closer to total world domination.

I hope the Dell thing is responsible for this, and I hope ATI is just the first domino to fall...

---

### Post by timcredible on 2007-09-06
that's good news, because ati card linux drivers are not good now.  i guess i can put ati back on my list of products i'll buy.

---

### Post by aks44 on 2007-09-06
[Duplicate thread]("http://ubuntuforums.org/showthread.php?t=543388").

---

### Post by Kingsley on 2007-09-06
I'm not sure of how to interpret this news. Does this mean all the Radeon Xpress cards will have better performance in the future? I'd like to be able to use Compiz on my Radeon Xpress 200 without the choppy XGL some day.

---

### Post by igknighted on 2007-09-06
> **aks44 said:**
> [Duplicate thread]("http://ubuntuforums.org/showthread.php?t=543388").

These are different news items.  The thread you linked is about the recent 8.41.x driver and the great improvements there in.  This is about the impending release of the 2d driver code and the specs for writing proper 3d OSS drivers within the next week.  Same company, same time frame, different news.

Unless I missed something in the other thread, but I've been following it pretty closely, so i don't think so.

---

### Post by igknighted on 2007-09-06
> **Kingsley said:**
> I'm not sure of how to interpret this news. Does this mean all the Radeon Xpress cards will have better performance in the future? I'd like to be able to use Compiz on my Radeon Xpress 200 without the choppy XGL some day.

AIGLX should be available within the next month in the proprietary drivers.  This is from the other thread.  This open-sourcing means that once drivers are fully written, they can be distributed with the kernel like intel's drivers.  There will be no need to install any proprietary drivers or anything else after install.  Possibly as soon as 8.04 (extremely optimistic) ATI cards could be fully capable for Compiz-Fusion right out of the box.

---

### Post by aks44 on 2007-09-06
> **igknighted said:**
> These are different news items.  The thread you linked is about the recent 8.41.x driver and the great improvements there in.  This is about the impending release of the 2d driver code and the specs for writing proper 3d OSS drivers within the next week.  Same company, same time frame, different news.

I knew I read that news on phoronix.com yesterday, but I didn't remember it was one click away from the article linked in the other thread. So I guess, my bad, this news indeed isn't part of the very article that was linked...

---

### Post by igknighted on 2007-09-06
> **aks44 said:**
> I knew I read that news on phoronix.com yesterday, but I didn't remember it was one click away from the article linked in the other thread. So I guess, my bad, this news indeed isn't part of the very article that was linked...

:D its all good, both are great news

---

### Post by aks44 on 2007-09-06
> **igknighted said:**
> :D its all good, both are great news

Indeed, as a 9600 owner I'm tired of having to choose between performance (radeon OSS driver) and "stability" (fglrx, although their stability is quite discutable too).

I'm eager for those new OSS drivers.

---

### Post by Anthem on 2007-09-06
> **igknighted said:**
> Possibly as soon as 8.04 (extremely optimistic) 
You think?  Given the amount of interest, I would be the cards have solid 3d drivers by Christmas.  They'll be improved over time, of course, but if we really get specs on Monday I'm betting there will be working 3d by the end of the year.

Next up is nVidia.  The dominos are starting to fall.  It's a very good day for open source.

---

### Post by igknighted on 2007-09-06
> **Anthem said:**
> You think?  Given the amount of interest, I would be the cards have solid 3d drivers by Christmas.  They'll be improved over time, of course, but if we really get specs on Monday I'm betting there will be working 3d by the end of the year.

Next up is nVidia.  The dominos are starting to fall.  It's a very good day for open source.

Within the next week there should be a driver (of pre-release quality, of course) out there.  Now, it will be a long process to get it fully working, but I would hope that by 8.04 (remember, it would have to be in before the feature freeze in like January or February) there is a driver that is sufficient.  That would be great timing for Ubuntu to get something major like that in time for an LTS release.

Gamers will still need to use fglrx for top level 3d performance, but compiz should run fine on the OSS driver.  It is unclear whether this is only for x1XXX cards and newer, or if cards not fully supported (*cough*x200*cough*) will see benefit as well.

This is going down much quicker than I expected, I am very excited.  Hopefully the community gets behind this, because we really do need to flock away from nvidia fast enough that they see a real need to follow suit or lose linux business.

---

### Post by CarpKing on 2007-09-06
This is great!  It's been so much of a problem before choosing between the proprietary and open source drivers.  Both have some strengths, but neither makes you feel that you got your money's worth on the hardware.  Hopefully we'll soon be able to use all our cards' features to their fullest on the operating system of our choice.

---

### Post by Polygon on 2007-09-06
woo and yay! i bet there are loads of people just waiting for that to be released so they can start hacking away at the drivers :D

---

### Post by user1397 on 2007-09-06
Great news, but a personal disappointment to me...the only computer I had with an AGP slot recently died, and now my ati card is useless!! :(

---

### Post by forrestcupp on 2007-09-06
The way I understand it is that they are only releasing the 2D part of it and we are still left to figure out the 3D part.  So how is it really going to help things, seeing we already have open source ATI drivers that do good with 2D?

---

### Post by WishingWell on 2007-09-06
> **forrestcupp said:**
> The way I understand it is that they are only releasing the 2D part of it and we are still left to figure out the 3D part.  So how is it really going to help things, seeing we already have open source ATI drivers that do good with 2D?

From the article:

> They confirmed the rumors reported earlier on Slashdot, that everything necessary for community-driven and -maintained 2-D and 3-D drivers for ATI Radeon X1000 and HD 2000 graphics will be made available next week.


---

### Post by forrestcupp on 2007-09-06
> **WishingWell said:**
> From the article:

Nice

---

### Post by Dimitriid on 2007-09-06
WIll it work with my notebook's mobility x1100? I sure hope so, strangely enough its detected as x200 on the restricted drivers right now :confused:

---

### Post by juxtaposed on 2007-09-06
> or if cards not fully supported (*cough*x200*cough*) will see benefit as well.

I hope very much.

Even if it doesn't work for my graphics, this is still great news.

---

### Post by Billy_McBong on 2007-09-06
[COLOR="Blue"]cool
i don't have an ATI card but still good news[/COLOR]

---

### Post by Dapilot1 on 2007-09-06
So, will my 9800XT benefit from this or is it only for new cards?

---

### Post by Rhapsody on 2007-09-06
Assuming that all new ATI cards end up with stable, open source drivers that can handle serious 3D, and that NVIDIA doesn't follow suit, then I'll be switching back to ATI for my next PC. This PC will remain with NVIDIA graphics, but nouveau should eventually take care of open source drivers in that case.

---

### Post by Lux Perpetua on 2007-09-06
> **aks44 said:**
> Indeed, as a 9600 owner I'm tired of having to choose between performance (radeon OSS driver) and "stability" (fglrx, although their stability is quite discutable too).

I'm eager for those new OSS drivers.Apparently only R500 and later cards will have open specifications. I'm in the same boat as you with my X600 clone. I wasn't sure about the timeline, but here's a nice list: [http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units](http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units)

Lest I come across as overly unhappy about this affair: this is still wonderful progress for the open source movement.

edit: Oops, it looks like the specs won't be open; only the driver will be, anyway. [http://www.phoronix.com/scan.php?page=article&item=826&num=1](http://www.phoronix.com/scan.php?page=article&item=826&num=1)

---

### Post by pay on 2007-09-07
I wonder what the new driver will be named..

---

### Post by blackhowling on 2007-09-07
should be nice can go back to ATI instead of Nvida

---

### Post by samb0057 on 2007-09-07
This is great! We should all show support for ATI/AMD by choosing them over other brands if this really comes through.

---

### Post by aerials on 2007-09-07
Yeah great, just when Lenovo finally switched to nVidia cards for ThinkPads. I even ordered my new machine with intel graphics for the sake of drivers. 
But I still get better battery life with intel than with an ATI or nVidia card :)

---

### Post by Lord Illidan on 2007-09-07
> **Rhapsody said:**
> Assuming that all new ATI cards end up with stable, open source drivers that can handle serious 3D, and that NVIDIA doesn't follow suit, then I'll be switching back to ATI for my next PC. This PC will remain with NVIDIA graphics, but nouveau should eventually take care of open source drivers in that case.

Same here.

---

### Post by stuh84 on 2007-09-07
Doesn't look like they'll be sorting out my laptop's card (200M), but I'm still quite happy about this, opens up what I can choose for when I eventually get a new PC for Linux-only, I don't have to think about Nvidia only.

Or I can just steal my Dad's PC when he isn't looking :P

---

### Post by K.Mandla on 2007-09-07
> **Rhapsody said:**
> I'll be switching back to ATI for my next PC.
+1

---

### Post by tbroderick on 2007-09-07
Interesting that Novell is writing the driver.

---

### Post by nowshining on 2007-09-07
that makes me feel sad, as I should of bought an ATI card or is the Gforce fx5200 better?? who knows??

---

### Post by Anonii on 2007-09-08
Aw man, after reading this on digg (Yeah a bit late, but I just came back from my vacations), I thought that ubuntuforums would already have an 18-page thread discussing it, but I just see two 4-page threads.. Pfff..

Aw well, freaking great news, if this goes well, I may consider getting an ATI instead of an nVidia for my next PC (The following January).

---

### Post by K.Mandla on 2007-09-08
> **tbroderick said:**
> Interesting that Novell is writing the driver.
I noticed that. I'm not sure how I feel about it. ... :-k

---

### Post by dptxp on 2007-09-08
When is ENE going to fall in line ? The drivers for their card readers.

---

### Post by mech7 on 2007-09-08
:guitar: Great news lets hope nvidia will follow :D

---

### Post by miggols99 on 2007-09-08
I'll put ATI back onto the "good graphics card" list :) Next month comes AIGLX...woot!

---

### Post by mips on 2007-09-08
[http://www.desktoplinux.com/news/NS2568321546.html](http://www.desktoplinux.com/news/NS2568321546.html)

---

### Post by yimmmy on 2007-09-08
THIS IS AWESOME ive bbeen trying to get compiz fusion to work for the longest time now with my ati mother board im going to pimp it the heck out now 
THANKSS AATI  
and for the longest time i thought they sucked :lolflag:

---

### Post by forrestcupp on 2007-09-08
I'm glad they're doing this, but I'm not just going to ditch nvidia because of this.  Nvidia has always been great about supporting Linux and getting us quality drivers that support all of their features.  Even if they have been proprietary, they have been very good to us.  I'm not just going to jump ship and switch to a company who has been pretty crappy to us because of this one instance of goodness when nvidia has been good to us all along.

---

### Post by mips on 2007-09-08
> **forrestcupp said:**
> I'm glad they're doing this, but I'm not just going to ditch nvidia because of this.  Nvidia has always been great about supporting Linux and getting us quality drivers that support all of their features.  Even if they have been proprietary, they have been very good to us.  I'm not just going to jump ship and switch to a company who has been pretty crappy to us because of this one instance of goodness when nvidia has been good to us all along.

The only thing I can hope for is that nVidia follows suite and also makes the spec (&maybe some code) available as well. Then you would basically have 3 options for oss drivers, Intel, ATI, nVidia.

---

### Post by Lord Illidan on 2007-09-09
If the 3D card manufacturers will do their utmost to support Linux, one can only hope that games manufacturers will do the same..

---

### Post by Perfect Storm on 2007-09-09
> **forrestcupp said:**
> I'm glad they're doing this, but I'm not just going to ditch nvidia because of this.  Nvidia has always been great about supporting Linux and getting us quality drivers that support all of their features.  Even if they have been proprietary, they have been very good to us.  I'm not just going to jump ship and switch to a company who has been pretty crappy to us because of this one instance of goodness when nvidia has been good to us all along.

Ditto.

Every year I've heard the old same story that the next release of the ATI would be great and much better than Nvidia without it ever happen.

I've heard the story so many times that I need to see it before I believe it.

---

### Post by the.dark.lord on 2007-09-09
Sorry to go off-topic, but I've got a related question to ask:

The drivers I installed from 'Restricted Drivers Manager' for my ATI Mobility Radeon X1600 are open source, right?

---

### Post by forrestcupp on 2007-09-09
> **the.dark.lord said:**
> Sorry to go off-topic, but I've got a related question to ask:

The drivers I installed from 'Restricted Drivers Manager' for my ATI Mobility Radeon X1600 are open source, right?

No.  The drivers you had before you used the Restricted Drivers Manager were open source.  The purpose of the RDM is to install Restricted proprietary drivers.

---

