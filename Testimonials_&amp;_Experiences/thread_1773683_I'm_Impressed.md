---
title: "I'm Impressed"
date: 2011-06-02
forum: Testimonials &amp; Experiences
---

### Post by silverglade00 on 2011-06-02
I recently inherited a Gateway M1300 Tablet PC. This is an older machine that came with Windows XP Tablet Edition. Of course I wanted to put Linux on it. It has a stylus touchscreen, so I thought it might work well with Unity and I tried to install Natty on it. Booted to black screen and never got anywhere.

I did some searching around and found out that Ubuntu 7.04 configures this thing like it was built specifically for it. Sweet! Loaded it up and everything worked great. Found some other threads on here to create screen rotation scripts and it was all happy. Only one problem... there was a warning about SSL bug and to install updates right after installing. This version is EOL though, so the repos weren't exactly cooperating with me.

I found some good information on how to change my /etc/apt/sources.list and upgrade the system. Ok great. Started out on the journey. I have now upgraded from 7.04 to Natty one by one (except for jumping from LTS to LTS). There were a few video issues along the way that I had to resolve. Switching to vesa during the 8.x releases got me through. acpi=off has been my friend through this journey as well.  

On Natty, everything went bad. No more video except vesa. No more touchscreen. Time for me to start over. I am impressed that everything worked this well through all of the upgrades as far as I got though.

---

### Post by wolfen69 on 2011-06-02
It's either going to work with 11.04 or it isn't. Upgrading version by version isn't going to make a difference. Better off just starting with 11.04. You can heed my warning or waste *many* more hours. Good luck.

---

### Post by silverglade00 on 2011-06-02
Even more impressed now. And learning enough that I could probably get it working with a straight 11.04 install. Adding ```
ln -s /dev/ttyS0 /dev/input/wacom
``` to /etc/rc.local let me get the stylus working again. Only problem I am having is needing acpi=off just to boot up, but intel driver needs acpi to work. Tried acpi=force and that got it working once, but never again since then.

The part I was impressed with was how much config was retained even though the technologies changed so much under the hood.

---

