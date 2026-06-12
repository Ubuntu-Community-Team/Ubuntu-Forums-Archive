---
title: "Ubuntu broke my laptop"
date: 2008-10-01
forum: Testimonials &amp; Experiences
---

### Post by N00b-un-2 on 2008-10-01
now don't jump to conclusions.  I am still a happy linux user and have every intention of sticking it out with this operating system.  ubuntu is awesome... when it works.  but what frustrated me more than anything was how my drivers, my Intel graphics drivers in particular, would work just fine, and then they wouldn't work... and then they'd work again.  This would happen over and over as new updates would come out and be automatically downloaded.  For whatever reason when I first installed Ubuntu 8.04 on my laptop, after sorting out the wifi driver nonsense and having to tinker around with my Lexmark printer to get it to work I had it running just fine, with full 3d acceleration capabilities, no sound problems whatsoever and an overall solid and easy to use system.  but my problems began the day that I installed the 8.04.1 update and it'd been downhill from there.  As of yesterday, my laptop became a paperweight as long as I was installing Ubuntu.  I'd get the OS (Hardy 8.04.1) set up on my system and then as soon as it did it's "updates" (they should be called downgrades, or possibly label them '****_up_your_computer-8.04.1.deb') my computer would lose all graphics support aside from generic vesa drivers (which are useless).  And then simple fixes for things like my atheros wifi card would just simply cease to work.  So after having to reformat for the fourth time in three days (out of four reformats in the entire time I've been using ubuntu, one caused by a corrupted hard drive after eliminating my windows partition) I've been fed up.
I've decided to install Ubuntu 7.10 because from what I've read, it is a much more stable system than Hardy or Intrepid.  Hell, I've even had nothing but trouble installing Hardy.  I've literally had to burn a dozen copies of Hardy before getting a usable install disc.  I tried the regular install, the server edition and the alternate install disc and it really just seemed like luck of the draw.
But I'm in the middle of installing 7.10 on my laptop right now and so far it hasn't encountered any errors or given me any trouble, so we'll see how it goes.  I just wonder if it's possible to upgrade my linux kernel without having to upgrade the OS.
I realize that my experience is not the same as everyone else's.  In fact there are plenty of people who own laptops with the same exact chipset as my laptop has that experienced no problems (I have the intel GL965 X3100 chipset.  It uses the i810 intel driver and is supposed to work "out of the box" in Ubuntu... and it did, before version 8.04.1 came out)  And it irritates me to no end when I post something and ask for help or advice and all i get is a dozen "works fine on my computer" replies.  All you're doing by telling me that is pissing me off.   I mean, just a few days ago I had a perfectly working laptop that I could play games on, run compiz and do everything that I can do on my desktop, if not better.  My desktop's processor is more than twice as fast as my laptop, and I have nVidia graphics, although it has less ram.  My desktop is a few years old and I don't want to put any more money into it.  I'd rather just build a new computer when I get back from Iraq next year (yes, I'm in the military).  Somehow my laptop would rival the performance of my desktop in terms of speed and stability anyway (the desktop still had the lappy beat in terms of graphics/resolution hands down).

---

### Post by hansdown on 2008-10-02
Hi N00b-un-2.

You have the option to go back to the kernel version that works for you.

You can also opt out of updating anything that you are not sure of.

3D graphics are nice if your machine is not overtaxed.

These problems can be answered effectively by the many forum users who possess more skill than I have.

---

### Post by Crafty Kisses on 2008-10-02
Yeah, you can try reverting to an older kernel.

---

### Post by Thanh-BKK on 2008-10-02
Hi :)

Do like i did - 8.04, tweaked and customized my system the way i liked it (actually, LOVE it!) and then - tell Ubuntu: "Leave me alone with updates". 

Because my systems works, apart from one single flaw (which has NOT yet been fixed by any of the updates/kernels), absolutely perfect on the original kernel that it had when 8.04 Final was released. I have downloaded (manually!) a bunch of other updates, some of which did indeed speed things up or introduced new features/functions, but kernels? Nope. And i intend to keep it that way.

With kind regards.....

Thanh

---

### Post by rustybronco on 2008-10-03
> **N00b-un-2 said:**
> But I'm in the middle of installing 7.10 on my laptop right now and so far it hasn't encountered any errors or given me any trouble, so we'll see how it goes.  I just wonder if it's possible to upgrade my linux kernel without having to upgrade the OS.
Yes...
[http://ubuntuforums.org/showthread.php?t=646755](http://ubuntuforums.org/showthread.php?t=646755)

---

### Post by Riffer on 2008-10-06
I've had this problem a time or 2.  Its because the upgrade to the kernal didn't also upgrade the modules (graphics, sound, wifi etc.).  I had it with 7.04 and 7.10, I'm surprised that it has happened with hardy.

The fix is easy (well sorta), just redo all your tweaks.

---

