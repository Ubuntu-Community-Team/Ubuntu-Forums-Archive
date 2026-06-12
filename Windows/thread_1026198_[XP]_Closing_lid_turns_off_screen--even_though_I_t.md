---
title: "[XP] Closing lid turns off screen--even though I told it not to"
date: 2008-12-30
forum: Windows
---

### Post by fiddler616 on 2008-12-30
Hello,
I bought myself a KVM  with a Christmas giftcard, and am *very* pumped about it (forget dual-booting or virtualization, I can switch OSs at the touch of a button!).
However, my one complaint is that with the two laptops I'm using closing the lid makes the LCD turn off, which makes the CRT monitor turn off, which is a problem. I've been to "Power Management" and set it so that "When the lid is closed: Do nothing". However, nothing still isn't happening (geez, that did not come out articulately).
Isn't there a way to let me close my lid in peace? I'm wasting a lot of desk space having two laptops open.
Thank you.
PS: I'm experiencing the same thing in Ubuntu, but I think that's just a case of me not finding the right setting yet.

---

### Post by rickyjones on 2008-12-30
> **fiddler616 said:**
> Hello,
I bought myself a KVM  with a Christmas giftcard, and am *very* pumped about it (forget dual-booting or virtualization, I can switch OSs at the touch of a button!).
However, my one complaint is that with the two laptops I'm using closing the lid makes the LCD turn off, which makes the CRT monitor turn off, which is a problem. I've been to "Power Management" and set it so that "When the lid is closed: Do nothing". However, nothing still isn't happening (geez, that did not come out articulately).
Isn't there a way to let me close my lid in peace? I'm wasting a lot of desk space having two laptops open.
Thank you.
PS: I'm experiencing the same thing in Ubuntu, but I think that's just a case of me not finding the right setting yet.

I'm going to guess that that is hardware based. Check the BIOS, that might have an option to disable it.

Thanks,
Richard

---

### Post by fiddler616 on 2008-12-31
> **rickyjones said:**
> I'm going to guess that that is hardware based. Check the BIOS, that might have an option to disable it.

Thanks,
Richard
I'll give it a shot next time I reboot--thanks for the tip. The one thing that kind of gets me, though, is how it's happening to two different machines that are even from different companies (Sony and Dell). I guess stranger things have happened though.

---

### Post by rickyjones on 2008-12-31
> **fiddler616 said:**
> I'll give it a shot next time I reboot--thanks for the tip. The one thing that kind of gets me, though, is how it's happening to two different machines that are even from different companies (Sony and Dell). I guess stranger things have happened though.

I would expect the screen to turn off on most, if not all, laptops when the lid is closed. It saves power and there is no need for the screen to be on when it is in a closed state - normally.

Another option would be to physically disable the lid closed switch/sensor. Most laptops have some sort of button that is pressed when the lid is closed to signal the hardware/software to turn off the screen.

-Richard

---

### Post by fiddler616 on 2008-12-31
Great, I went into the BIOS of the Dell, and found a setting about what to do when the lid is closed. It still said "do nothing" when on AC power, but it suspended when on battery, which I changed (it *shouldn't* have done anything since I'm always on AC (the battery is quite dead) but it seems to have done the trick) I'll try it with the Sony soon. Thanks!

---

### Post by fiddler616 on 2008-12-31
I jumped the gun. Closing the lid when booting does nothing, closing the lid once Windows loads turns everything off. Groan.

---

