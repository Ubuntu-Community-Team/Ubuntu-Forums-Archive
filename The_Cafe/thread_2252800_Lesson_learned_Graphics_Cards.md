---
title: "Lesson learned Graphics Cards"
date: 2014-11-14
forum: The Cafe
---

### Post by frankennetbook on 2014-11-14
This might seem like an obvious comment to many on here regarding graphics cards.  I have recently bought a new laptop HP 13 x360; which has a Radeon R5 Graphics card in it.  Also the laptop came with Windows 8.1. I replaced Windows with a bit of difficulty due to UEFI and so on; although it was easily resolved with searches on here and other ubuntu forums.  Regardless the final hurdle I had was the resolution which I then read that I should use the proprietary driver not open source.  I gave it a try and with that all is good.

This made me think.  I had set up an older Dell Desktop for my parents TV so they could watch Netflix and other foreign tv available online.  The issue there was always choppy live streaming which made watching sports for my dad difficult.  I had installed a Radeon video card there too and now updated the driver.  No problems with live streaming anymore. To qualify this: its an old Dell with a single core processor and now its like watching cable tv online.  


The lesson I've learned is proprietary drivers whenever you can.  Like I said this might be a duh message for many on here but I thought I'd pass on my newly acquired "?wisdom?".

---

### Post by Rob Sayer on 2014-11-15
Actually the important thing with the old Dell was that you put a decent video card in it, not the driver per se.  From what I've seen in posts here by very knowledgeable people you can actually run the Unity DE quite well in a 1Gb RAM machine if you also put a good 1Gb video card in it.  Which most people don't do of course.

Another thing I learned the hard way is to never just go into additional drivers and click on it.  That driver may not actually be as well supported in linux by the card maker as you'd think.  I've borked my video that way.

Now I check whether it actually works and install the actual package involved with synaptic.

---

### Post by sp40140 on 2014-11-15
Agree with Rob.
The reason for performance jump is the better hardware. onboard graphics by Intel were horrible until the current version. Even the latest ones can't compare to Nvidia/ATI but they can manage.

---

### Post by frankennetbook on 2014-11-15
I have no doubt that the video card is the initial reason for the jump except when it was installed and running on the open source driver live streaming was pixely and choppy and netflix was just pixely.  Now with the proprietary drive the improvement is impressive; live streaming through vga was smooth and tv like except it was a bit pixely and with HDMI the best its been.  So with that I think its a mix of hardware and soft.  Also, on my laptop the change to the proprietary drive has given me a better picture.  I do find that (being relatively noob to ubuntu and linux) this is more of an art than a science at times.

---

### Post by Rob Sayer on 2014-11-16
The reason the proprietary driver worked better for your card is that with some AMD cards the nouveau driver doesn't have good 3D hardware acceleration support andwith others it does.

The ubuntu wikis have lists of which cards work well with the open source nouveau driver and the ones that don't work as well.  Again, I always check first before installing any proprietary driver.

It seems more of an art than a science when you don't know which doc sources to go to yet.

---

### Post by coffeecat on 2014-11-16
[quote=frankennetbook]This might seem like an obvious comment to many on here regarding graphics cards.[/quote]

The Multimedia section is a technical support area, and this thread seems to be more of a discussion, so...

*Thread moved to **The Cafe**.*

[quote=frankennetbook]The lesson I've learned is proprietary drivers whenever you can. [/quote]

Not necessarily. For the record, I’m posting from a machine with a Radeon HD6450 video card and I’m using the default open source radeon driver in Ubuntu 14.10. High definition videos from Netflix stream just fine in the Chrome browser. For some AMD cards, you will no doubt need the proprietary driver. My HD6450 has relatively modest performance compared with some, but I don’t need the proprietary driver.

[quote=Rob Sayer]with some AMD cards the nouveau driver doesn't have good 3D hardware acceleration support and with others it does.[/quote]

Agreed, except for the nouveau driver bit. Were you intending to refer to AMD or nvidia cards?

---

