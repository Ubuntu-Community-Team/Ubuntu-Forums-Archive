---
title: "battery discharge option in grub"
date: 2008-12-03
forum: The Cafe
---

### Post by suoko on 2008-12-03
is there an app like memtest to discharge the battery ?
i usually prefer to completely discharge it before recharging since i never believed the no memory effect.
it could just throttle CPU at max speed with some fullscreen blinking colors

---

### Post by Kosimo on 2008-12-03
> **suoko said:**
> is there an app like memtest to discharge the battery ?
i usually prefer to completely discharge it before recharging since i never believed the no memory effect.
it could just throttle CPU at max speed with some fullscreen blinking colors

Have a look if your BIOS may have this option. Many laptops do.

---

### Post by mihai.ile on 2008-12-04
Did you read about on the net about how laptop battery works?
From what I know on the net you are destroying the battery.

Ok now from my own experience. My laptop has 3 years and a half and my battery is 41% at full capacity. What I noticed over the years is that the capacity decreased only when I had to discharge the battery below 5% of energy or when I had the battery out of the laptop for some weeks (I had to send the laptop in for repairs)

Now it's up to you if you want to discharge the battery but be sure you read about it so you don't ruin your battery.

---

### Post by suoko on 2008-12-04
unfortunately the eeePC doesn't have a BIOS option for battery discharge.
regarding the 5% minimum charge, i hope that's handled by the battery itself.
i must admit that's true for mobiles, which go off when battery ends but if you try to re-switch them on, they usually have some energy left.
the eeePC seems to consume it all since you can't do anything when the battery ends. 
probably i could safely start rechargin when the battery led blinks...

---

### Post by ssam on 2008-12-04
i recommend that you find out what chemistry is used in your battery, and what is the best way to look after it.

---

### Post by mintochris on 2008-12-04
the eepc battery will last longer if you do not completely drain it every time.
It prefers to be topped up. This isn't a matter of whether you believe it or not, but that the battery has different chemicals inside.

---

### Post by jdong on 2008-12-04
To the OP, lithium-ion and lithium-polymer batteries **DO NOT** like being completely discharged. In fact, doing so over time will lead to shorter battery lifespan. It's rarely necessary to do a full discharge and recharge -- in fact on modern batteries I'd estimate less than once per 6 months to re-calibrate the remaining charge meter. It doesn't have ANY effect on the capacity, just on the calculation of the remaining capacity. Do this when your battery indicated 40% but the system suddenly shut off 2 seconds later, or when the system has been indicating 0% for the past 2 hours but the system is still running ;-)



Historically, only NiCd had a memory effect where a non-full recharge would reduce in temporarily reduced capacity. NiCds were designed so that deep-draining them does not hurt them.


Newer NiMH'es are also designed to be charged whenever you want to. A deep discharge of a NiMH 1.2V cell below 0.90V also causes damage to the cell -- this is a well-known phenomenon in the LED flashlight enthusiast community, where NOBODY wants to use their expensive $5 2800mAh AA's to do a low-output-mode runtime test. Active testers have reported loss of half of battery capacity in just 5 or so of these discharge cycles.

PbSO4 (lead-acid automobile) batteries are also not designed to be full-discharged, unless they are the marine deep-cycling variant, which has a lower peak amperage. In fact, a full low-current discharge of a lead-acid car battery almost ruins it.


For more info on battery chemistries and care, I'd strongly recommend reading [http://www.batteryuniversity.com/partone.htm](http://www.batteryuniversity.com/partone.htm)

---

### Post by mihai.ile on 2008-12-05
in reply to OP, about the post above, i could not agree more. That's why I said that my battery loosed capacity when fully discharged, it doesn't matter if it gone to only 5% or 15%, it's too low for the battery.
I'm trying not to let my li-ion batteries discharge, and I'm charging them whenever possible.

---

