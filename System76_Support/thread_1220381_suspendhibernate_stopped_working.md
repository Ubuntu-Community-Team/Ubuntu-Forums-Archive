---
title: "suspend/hibernate stopped working"
date: 2009-07-22
forum: System76 Support
---

### Post by bsnh on 2009-07-22
I have a Starling NetBook running the factory installed 9.04 plus updates as they become available. (I believe this is the netbook remix, but I'm not sure how to check.)

Following a recent (within the past 1-2 weeks) update, suspend and hibernate stopped working. These had been working ok.

I have the power button configured to hibernate. When I press the power button, the screen goes to black and I see a blinking white "underline" cursor in the upper left. I've tried waiting ~30 minutes with no change. Requires holding down the power button to shut off. When it comes back up, it cold boots (does not resume/unhibernate). Same behavior if I use the pm-hibernate command, suspend button, or pm-suspend command.

Suggestions?

Thanks.

---

### Post by thomasaaron on 2009-07-23
Try running your System76 driver (System > Administration > System76 Driver > Install (tab) > Install (buttom). 

Then reboot. Then try suspending.

---

### Post by bsnh on 2009-07-23
Already tried that based on advice seen in another thread.

Tried it again anyway.

Not fixed. Same behavior.

---

### Post by thomasaaron on 2009-07-23
OK, I just tested on my shop Starling, completely updated, and both suspend and hibernate work fine. So, I doubt that an update is the problem.

By your first post, it isn't exactly clear to me whether the problem is suspend, hibernate or both.

What if you suspend and/or hibernate from the shutdown icon (as opposed to the power button). Do they work then?

---

### Post by bsnh on 2009-07-23
> **thomasaaron said:**
> OK, I just tested on my shop Starling, completely updated, and both suspend and hibernate work fine. So, I doubt that an update is the problem.

By your first post, it isn't exactly clear to me whether the problem is suspend, hibernate or both.

What if you suspend and/or hibernate from the shutdown icon (as opposed to the power button). Do they work then?

The following tests all fail in the same way described in my first post (black screen, "underline cursor"):

1. Power button to hibernate.
2. Suspend button (Fn-F1)
3. sudo pm-hibernate
4. sudo pm-suspend
5. Home Screen->Quit...->Suspend
6. Home Screen->Quit...->Hibernate

After reading your "doubt that update is a problem" I remembered that one of my updates may not have cleanly applied. Here's what I did to fix the problem:

$ uname -a
Linux hostname 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

But I had 2.6.28-13 installed, this clued me to the fact that something was incomplete.

$ sudo aptitude remove linux-image-2.6.28-13-generic
(answer yes to everything)

Reboot

$ sudo aptitude install linux-image-2.6.28-13-generic

Reboot

$ sudo aptitude install linux-backports-modules-2.6.28-13-generic linux-backports-modules-jaunty linux-backports-modules-jaunty-generic linux-generic linux-image-2.6.28-13-generic linux-image-generic linux-restricted-modules-2.6.28-13-generic linux-restricted-modules-generic

Reboot

Now test #2 above works. I'm going to post this before attempting the rest (to avoid the risk of losing this post if something is still broken). If you don't see another post, assume it all works.

Thanks for inspiring me to look in the right place, lack of suspend was getting annoying.

---

