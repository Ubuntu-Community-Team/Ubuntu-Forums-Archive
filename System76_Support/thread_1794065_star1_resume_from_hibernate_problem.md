---
title: "star1 resume from hibernate problem"
date: 2011-06-30
forum: System76 Support
---

### Post by russblau on 2011-06-30
Hello. I have recently done a clean install of Natty Narwhal on my star1 netbook.  Since this install, whenever the computer is powered up from Hibernate, the graphics mode is incorrect and the screen is garbled; curiously, the right 1/4 of the screen appears to be in a different mode than the left 3/4, and the GUI is visible on the right 1/4 (although it flickers), which allows me at least to shut down the netbook.  I do not have this issue when restarting from Suspend, or from a full shutdown.

---

### Post by isantop on 2011-07-01
It sounds like there was an issue setting up the swap partitions on your machine. Does suspend function correctly?

---

### Post by russblau on 2011-07-01
Yes, suspend functions correctly.

---

### Post by russblau on 2011-07-17
Since there did not seem to be any further information forthcoming here, I did some further investigation based on your suggestion that there might be a problem with the swap partition.  I found [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) and went through the steps listed there.  The results were puzzling, to say the least.  I found that I did have a swap partition and that it was the right size (2 GB), but it wasn't set up for hibernation in /etc/default/grub.  So I edited that file and then updated both grub and initramfs per the FAQ.  However, this caused no change in the problem at all (and I did go back and check that the grub and initramfs files are still reading correctly after my changes).

This is really puzzling since the system *did* hibernate before, and still does; it just resumes in an invalid graphics mode.  I don't quite understand how it was able to hibernate before when /etc/default/grub was wrong, but in any case it's clear that wasn't the cause since the problem still exists.

Next step, I guess, will be even more detailed forensics as suggested in [https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume. ]("https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume")I haven't had time to go through all that yet.

---

### Post by isantop on 2011-07-18
Check that all of your UUID's you entered are accurate, and that the swap partition is actually bigger than the RAM. Sometimes, those can end up in odd sizes, preventing them from working fully.

---

### Post by russblau on 2011-07-25
Increasing the size of the swap partition (by a measly 32MB) seems to have fixed the problem!  That was a bit of an adventure in itself, but I got it done.  Thanks for your help!

---

