---
title: "Is minimization bug fixed in 13.04?"
date: 2013-03-15
forum: Ubuntu Development Version
---

### Post by andreasrasholm on 2013-03-15
Hi there

I was wondering if anyone running the Ubuntu 13.04 daily build would help me figuring out if a certain bug in 12.10 has been taken care of.

The bug made me change to Mint and whether it is fixed or not will influence my decision on whether to change back to Ubuntu when 13.04 stable is released.

The bug is this: [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1069451](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1069451) - the global menu and the launcher disappears when you minimize a program running full screen in 12.10.

The easiest way to test it would be to run Firefox fullscreen (f11) and then minimize it (ctrl+alt+0). Does this go as expected or are the global menu and laundher invisible until clicked?

Replies greatly appreciated - thanks!

---

### Post by mörgæs on 2013-03-15
As you can see in the bug report, it's still 'confirmed' meaning that it has not been actively solved. It might have been solved by coincidence as a consequence of another bug fix, but it's not likely.

The best answer is that you download the beta and test for yourself. 

Moving your post to the development forum. When you participate in discovering and reporting bugs (and thanks for that) you will have better chances of getting a bug-free 13.04.

---

### Post by sersang on 2013-03-15
Still exist.

---

### Post by mörgæs on 2013-03-16
Please confirm the bug for 13.04 in Launchpad. It's not likely that developers read the forum.

---

### Post by screaminj3sus on 2013-03-16
so far for me 13.04 has been introducing more compiz bugs than it has been fixing :p

---

### Post by grahammechanical on 2013-03-16
I have confirmed the bug in Raring. As Firefox is number 2 in the Launcher then super+2 will un-minimize Firefox and restoring it using F11 will bring back the global menu and the Launcher.

I am guessing that this has something to do with the secret max, min and close buttons on the right hand side of a full screen Firefox conflicting with the notification area.

---

