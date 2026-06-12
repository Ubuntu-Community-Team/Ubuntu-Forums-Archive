---
title: "Is Android Forking from Linux?"
date: 2010-02-03
forum: The Cafe
---

### Post by Ric_NYC on 2010-02-03
[B]Lack of interest, codebase problems may be creating separation from Linux kernel/B].



**On Monday this week, kernel developer Greg Kroah-Hartman removed the drivers for Android from the Linux kernel's staging tree, thus insuring that--for now--Android is not headed for the mainstream Linux kernel**.

**Which brings up this unpleasant question: did Android just become a fork from Linux?** And, if it did, what might that mean?

It should be noted that no one else in the discussion to date has used the term "fork," and at this moment in space-time, I am still trying to figure out if the term is even applicable. But let's take a look at what Kroah-Hartman (GregKH) said in his blog entry on the subject yesterday.

**In that entry, GregKH was insistent on pointing out that while he personally loves the Android platform, he had no choice but to remove the Android driver code from the kernel staging tree because no one seemed to be working on it**. In the workflow for Linux kernel development, code in the staging tree should be improved with an eye towards eventual inclusion into the mainstream kernel. This is perfectly reasonable, because staging is just that: staging of new kernel additions, not a perpetual warehouse for Code of the Dammed.

According to GregKH, however, there is more going on here than just Android developers forgetting to check this off their to-do list. Apparently, there are numerous infrastructure and security model problems with the drivers themselves. Big problems, too--the kind that would prevent mainline inclusion into the Linux kernel even if the Android team was working on the driver codes.

GregKH specifically calls out Google for this problem, and explains that this situation extends beyond Google to all of the hardware and software vendors developing on this branch of the kernel:

"Now branches in the Linux kernel source tree are fine and they happen with every distro release. But this is much worse. Because Google doesn't have their code merged into the mainline, these companies creating drivers and platform code are locked out from ever contributing it back to the kernel community. The kernel community has for years been telling these companies to get their code merged, so that they can take advantage of the security fixes, and handle the rapid API churn automatically. And these companies have listened, as is shown by the larger number of companies contributing to the kernel every release."

From my admittedly layman's point of view, any branch of kernel development that prevents upstream contributions isn't just a branch: it's a completely detached line of development, otherwise known as a fork. It's not permanent--yet--and GregKH has publicly offered to help fix the Android drivers codebase to pull it back into the mainstream Linux kernel. But he laments that thus far, no one from Google seems to be working on the issue.

**The choice, it seems, now lies with Google: either they work on the codebase for their version of the Linux kernel can become a fully functioning branch connected to the mainstream trunk, or they choose not to and plant the seed for a new Android kernel, one that could eventually become incompatible with the original Linux kerne**l.

I hope they make the right choice, but the cynic inside me says that Google may want to keep embedded Linux hardware companies close and give them a new platform upon which to work. [B]In other words, Google will use open source, but it will be their flavor of open source code, not one dependent on Linux.

This is one of those times I hope I am wrong.[/B]


[http://www.itworld.com/open-source/95221/is-android-forking-linux](http://www.itworld.com/open-source/95221/is-android-forking-linux)

---

