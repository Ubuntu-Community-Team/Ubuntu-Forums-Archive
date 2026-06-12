---
title: "The infamous - and STILL unsolved - libwfb bug"
date: 2007-07-11
forum: The Cafe
---

### Post by dv_ on 2007-07-11
Hey,

I have a 8800 GTS, and am amazed that the libwfb-related bug is STILL unsolved.
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/98641](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/98641)

This bug is caused by a faulty packaging script, NOT by broken cs drivers. The fix is easy and small, as Alberto Milone showed here: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/98641/comments/25](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/98641/comments/25) , yet the devs care exactly zero about this (even though its practically solved; they just need to insert this fix in the scripts).

I managed to solve this manually, but bugs like this one are showstoppers and should have TOP priority. Also, Ubuntu is notorious for having broken nvidia packages even though the vanilla nvidia drivers are fine. What is going on?! I am posting this in the Cafe because its not about a technical fix, rather I am a bit concerned about the developers' attitude towards cases like this one.

---

