---
title: "Buzzing + GRUB failure"
date: 2011-02-08
forum: System76 Support
---

### Post by xJimx on 2011-02-08
Hey,

I've had a Starling for three months, my second one (the first was stolen three months ago) and I really like it.  

Except, today, I turned it on to find a really strange low noise, like the motor of an old motorboat, which whirred away, and eventually gave way to more of a buzzing as it seemed to speed up.  When the computer is shut off, it slows down and sort of putts to a stop, also sounding like a motorboat.  

This would be odd, but not terrible, except that I also  get the message "reloc offeset is out of the segment" instead of the usual boot.  I gather this is associated with GRUB problems.  

So, I am currently going to try and reinstall the GRUB I guess.  What I am wondering is: is this familiar to anyone?  Is it obvious to anyone what is going on?  Any diagnostic suggestions?  Thanks.

---

### Post by isantop on 2011-02-08
I think I just answered an email form you about this issue. You can continue this wherever you'd like.  

Does the computer boot at all? The noise sounds like it's a problem with the fan. It could be that the BIOS is detecting a Fan issue during th P.O.S.T. and is halting the boot. What happens if you try to press F2 to enter the BIOS set up. Does it go in, or does it still halt?

---

### Post by xJimx on 2011-02-09
Hey,

Yep, that's me. I just thought I'd post here in case anyone had had the same problem and recognized it.

Entering BIOS and switching various settings are all unproblematic.  Also if you take off the hard drive as a boot option in the BIOS, the terrible sound stops while it attempts to boot from the other stuff--as it checks for Ethernet, USB, CD, etc.

---

