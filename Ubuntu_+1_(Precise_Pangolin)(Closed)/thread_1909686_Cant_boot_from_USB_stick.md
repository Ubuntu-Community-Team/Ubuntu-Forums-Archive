---
title: "Cant boot from USB stick"
date: 2012-01-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by tkk99 on 2012-01-15
Hello,

I wanted to boot newest Ubuntu (precise-desktop-i386, put it on an USB stick with Universal-USB-Installer) on my old netbook(32bit, 4gb ram), but it just does not load the right kernel, it always says:

"This kernel requires following features not present on the cpu pae unable to boot please use the appropriate kernel for your cpu."

Any solution for this problem?

---

### Post by Mark Phelps on 2012-01-16
Precise is an early Alpha -- which you should not even attempt using unless you are very experiences with Ubuntu.

Also, you need to post Precise-related questions in the Precise development forum, not here.  This forum is for versions of Ubuntu that have already been released.

---

### Post by VMC on 2012-01-16
> **tkk99 said:**
> Hello,

I wanted to boot newest Ubuntu (precise-desktop-i386, put it on an USB stick with Universal-USB-Installer) on my old netbook(32bit, 4gb ram), but it just does not load the right kernel, it always says:

"This kernel requires following features not present on the cpu pae unable to boot please use the appropriate kernel for your cpu."

Any solution for this problem?

What iso did you download? I think you may have downloaded the wrong one. Use the i386 iso found [here]("http://cdimage.ubuntu.com/daily-live/current/precise-desktop-i386.iso").

---

### Post by jerrylamos on 2012-01-16
Last week one of the daily build images wouldn't run on my ThinkPad T40 which has a pentium M which doesn't support PAE.  A couple days later daily build does run non-PAE.  I have seen a thread on this forum which mentioned that non-PAE might be dropped for the next release.  I have no clue.

The 1.5 gHz Pentium M runs Unity-2D precise pentium just fine, good response time.

Jerry

---

