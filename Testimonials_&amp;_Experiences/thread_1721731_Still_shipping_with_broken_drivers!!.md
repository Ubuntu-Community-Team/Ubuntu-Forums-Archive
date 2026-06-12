---
title: "Still shipping with broken drivers!?!"
date: 2011-04-04
forum: Testimonials &amp; Experiences
---

### Post by Shmantiv_Radio on 2011-04-04
I just installed 11.04 Beta and I'm truly amazed. For the THIRD successive release, Canonical are shipping the broken RTL8192e driver.  To put into context how broken this driver is, Fedora has removed it altogether.

They're numerous bug reports and forum threads for this problem, so WHY, I repeat WHY is it still there?

---

### Post by mastablasta on 2011-04-05
why report it here? I mean did you report it in launch pad? Perhaps they are broken, but stable :-P

---

### Post by Philsoki on 2011-04-05
So... What's so bad about this driver?

---

### Post by 3Miro on 2011-04-05
Well isn't a broken driver better than no driver. A broken one may at least get you some functionality.

---

### Post by ventrical on 2011-04-05
I don't like to say too much negative about Ubuntu but the (natty-beta) is not anything like Maveric was. (natty) is having a real hard time with wireless detections and even when it does detect it seems that the drivers are busted or something. The Live CD works great but when you install it, it appears to grab some upstream drivers/programs/upgrades and can really mess up a fresh install.

 (many bug reports submitted from me ).

peace

---

### Post by Shmantiv_Radio on 2011-04-06
> **Philsoki said:**
> So... What's so bad about this driver?

The connection will randomly stop when under heavy load. Streaming video/downloading/podcasts etc.

Ironically the bug also happens if you use the repo version of ndiswrapper, as it has the 'invalid cmd 12' bug which causes the exact same problem.
The only way I've found to get a better experience is to compile & patch ndiswrapper 1.56 from source and use that instead, but it still has the error, just much less so.

---

### Post by stchman on 2011-04-06
Isn't the RTL8192e a wireless card?

It has been my experience that Intel and Atheros have good wireless driver support.

My recommendation is to take that wireless NIC out of your laptop and install an Intel 4965AGN mini PCI wireless card.

---

### Post by tlcstat on 2011-04-08
Greetings,
> I just installed 11.04 Beta and I'm truly amazed. For the THIRD  successive release, Canonical are shipping the broken RTL8192e driver.

Earth to Shmantiv_Radio!  11.04 hasn't shipped yet. That is why it's called a Beta.

---

