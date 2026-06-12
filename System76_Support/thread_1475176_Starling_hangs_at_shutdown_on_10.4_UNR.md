---
title: "Starling hangs at shutdown on 10.4 UNR"
date: 2010-05-06
forum: System76 Support
---

### Post by Ghidora on 2010-05-06
I updated my Starling to 10.4 last week and I'm having an issue.  When I go to shutdown with the menu at the top right of the screen the system will occasionally hang on the Ubuntu splash screen with the flashing "LED's."  It will sit on this until it is manually powered off.

Is anyone else having this issue, and is there a fix for it?

Thanks!

---

### Post by thomasaaron on 2010-05-07
The flashing LEDs is a kernel panic.

First, completely remove your battery and then re-install it, making sure the lock tabs are in the locked position.

Then, if the problem occurs again, please reboot your machine and *make note of the time when your system is all the way up*. Then, please go to System > Administration > System76 Driver > Support (tab) > Create (button). This will create an archive called logs.tar in your home directory. Please attach that archive to this thread.

I'll have a look at it and see what I can figure out.

---

### Post by Ghidora on 2010-05-10
I haven't seen the issue since reseating the battery.  I'll leave this open for a few more days just to be sure before marking it as solved.
 
Thanks.

---

