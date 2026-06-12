---
title: "Where do ATI users go from here?"
date: 2009-05-01
forum: The Cafe
---

### Post by stwschool on 2009-05-01
Just wondering if anyone knows what happens from here for people with older ATI cards? My main machine is fine on Jaunty, I've got an NVidia card so it's cool. However, my laptop has a mobility X1300. It's not exactly ancient, it's a dual-core PC and cost a fair whack a few years ago, so to be called legacy by ATI at this point is rather insulting.

So with most of the major linux distros having upgraded xorg those with older ATI cards are left in the cold. For me, it means my laptop stays on Intrepid for now, which is not really a huge problem. However, in 12 months it will be a problem, as support ends. No security patches.

So the question, short of buying a new laptop, where does an ATI-user go from here?

(PS I bought the laptop way before I started using linux so I wasn't able to plan for this, wheras now I would never touch anything with an ATI card, it still doesn't solve the immediate problem though).

---

### Post by Saint Angeles on 2009-05-01
i have an X1550 (almost the same as yours) but i don't know what you are talking about.

i had to use FGLRX with feisty through intrepid but jaunty uses the open source driver beautifully. give it a try (although i suggest doing a fresh install through the live CD).

or at least test out the live CD, if compiz works from the live CD, then you know you're good!

---

### Post by gnomeuser on 2009-05-01
Using the free software driver for ATI cards would be the obvious choice here.

Aside that ATI is one of the best decisions when running Linux. They give us specifications and have people working on X as well as the official driver maintained by X.

Currently this driver has kernel modesetting support as well as 3D acceleration and other goodies.

I would urge you to continue supporting the companies that support us, if you have problem please file bugs and they will be looked at. You can also partake in the Fedora Test days, they recently had one to test ATI 3D acceleration support, that way you will have good test cases to fill out and direct access to the developers writing the code. These days always end up producing lots of bug fixes and ensure that support is stable. Even if you do not like Fedora, remember that the code will flow back to Ubuntu since work is done upstream.

---

### Post by stwschool on 2009-05-01
> **Saint Angeles said:**
> i have an X1550 (almost the same as yours) but i don't know what you are talking about.

i had to use FGLRX with feisty through intrepid but jaunty uses the open source driver beautifully. give it a try (although i suggest doing a fresh install through the live CD).

or at least test out the live CD, if compiz works from the live CD, then you know you're good!

I did test it out and it was absolutely awful. Slow, with annoying lines, etc. The open drivers just aren't up to it yet, the proprietary drivers are better, and as much as I support the idea of free software, as far as I'm concerned I want my computer to work, and that means decent graphics drivers.


> **gnomeuser said:**
> Using the free software driver for ATI cards would be the obvious choice here.

Aside that ATI is one of the best decisions when running Linux. They give us specifications and have people working on X as well as the official driver maintained by X.

Currently this driver has kernel modesetting support as well as 3D acceleration and other goodies.

I would urge you to continue supporting the companies that support us, if you have problem please file bugs and they will be looked at. You can also partake in the Fedora Test days, they recently had one to test ATI 3D acceleration support, that way you will have good test cases to fill out and direct access to the developers writing the code. These days always end up producing lots of bug fixes and ensure that support is stable. Even if you do not like Fedora, remember that the code will flow back to Ubuntu since work is done upstream.

The open drivers are horrendous to be honest. I lose a lot of performance and the annoying lines on the side of the screen are a major deal-breaker. Compared to the quality of my NVIDIA drivers it's just not good enough.

In essence, moving from 8.10 to 9.04 is an upgrade as long as you're not on an 'old' ATI card. What I'm wondering is what happens when the support runs out. I don't particularly want to have to buy a new laptop just because the support has run out for 8.10.

---

### Post by billgoldberg on 2009-05-01
> **stwschool said:**
> I did test it out and it was absolutely awful. Slow, with annoying lines, etc. The open drivers just aren't up to it yet, the proprietary drivers are better, and as much as I support the idea of free software, as far as I'm concerned I want my computer to work, and that means decent graphics drivers.




The open drivers are horrendous to be honest. I lose a lot of performance and the annoying lines on the side of the screen are a major deal-breaker. Compared to the quality of my NVIDIA drivers it's just not good enough.

In essence, moving from 8.10 to 9.04 is an upgrade as long as you're not on an 'old' ATI card. What I'm wondering is what happens when the support runs out. I don't particularly want to have to buy a new laptop just because the support has run out for 8.10.

I have an old Radeon X1200 (or something like that) and on Jaunty the OS drivers work really well.

Before they couldn't even play an xvid video on full screen with compiz on without lagging.

I don't have a reason to use the CS drivers anymore.

---

### Post by Kosimo on 2009-05-01
> **gnomeuser said:**
> Using the free software driver for ATI cards would be the obvious choice here.

Aside that ATI is one of the best decisions when running Linux. They give us specifications and have people working on X as well as the official driver maintained by X.

Currently this driver has kernel modesetting support as well as 3D acceleration and other goodies.

I would urge you to continue supporting the companies that support us, if you have problem please file bugs and they will be looked at. You can also partake in the Fedora Test days, they recently had one to test ATI 3D acceleration support, that way you will have good test cases to fill out and direct access to the developers writing the code. These days always end up producing lots of bug fixes and ensure that support is stable. Even if you do not like Fedora, remember that the code will flow back to Ubuntu since work is done upstream.



Would be the best option if you want to go with open source drivers, that's for sure.  But: In terms of quality, nVidia proprietary drivers are ages ahead in almost all areas, plus you get VDPAU video hardware acceleration.

---

### Post by b@sh_n3rd on 2009-05-01
Hi, im planning to build a PC on the Foxconn A7DA 3.0 mobo which has a built-in ATI Radeon HD3300. I'll be using Ubuntu for Primary OS. Will I have prob's with this card and the open source driver? I noticed the driver in Jaunty's repos though.

---

### Post by Tristam Green on 2009-05-01
I'll attest that the open source drivers don't cut the mustard (ATI card listed in my sig, only 2 years old, yet legacy by ATI standards?)

For regular browsing and so-forth they're fine, but once I try to get WINE gaming going, it falls apart.  Horrendously slow, poor performance, etc.

I understand well where the OP is coming from.

---

### Post by Muffinabus on 2009-05-01
Yeah, I was also a bit upset with ATI's decision to turn my 2 year old graphics card into a 'legacy' card.  I'm using an X1950GT.

With that said, I actually find the free drivers to be quite nice.  I can run Compiz and watch full screen movies at the same time, which I wasn't able to do when using the proprietary drivers.  Haven't tried any gaming yet, but then I don't really run Linux to play games.  I'm pleasantly surprised with how these drivers are performing thus far (:

---

### Post by eldragon on 2009-05-01
if you got a "legacy" ati card, you are left out in the cold. i suggest to buy something else, or use the open source drivers instead..

even in legacy mode, they should still release new builds against the newer servers.. i dont understand why they didnt..

---

### Post by Muffinabus on 2009-05-01
> **eldragon said:**
> if you got a "legacy" ati card, you are left out in the cold. i suggest to buy something else, or use the open source drivers instead..

even in legacy mode, they should still release new builds against the newer servers.. i dont understand why they didnt..

Nah, apparently they are only going to update legacy drivers for 'critical fixes' in Windows XP and Vista, not Linux.

"AMD may periodically provide Windows XP and Windows Vista driver updates (for the products listed above) for critical fixes only.  No new features will be provided in future driver updates.  The Linux ATI Catalyst™ driver will only be supported in Linux distributions prior to February 2009 for the legacy products listed above."

---

### Post by Skripka on 2009-05-01
> **Muffinabus said:**
> Yeah, I was also a bit upset with ATI's decision to turn my 2 year old graphics card into a 'legacy' card.  I'm using an X1950GT.

With that said, I actually find the free drivers to be quite nice.  I can run Compiz and watch full screen movies at the same time, which I wasn't able to do when using the proprietary drivers.  Haven't tried any gaming yet, but then I don't really run Linux to play games.  I'm pleasantly surprised with how these drivers are performing thus far (:

I ran a X1900XTX for a few days before I was able to solve my problems with their drivers....said solution being to buy an Nvidia card.

---

