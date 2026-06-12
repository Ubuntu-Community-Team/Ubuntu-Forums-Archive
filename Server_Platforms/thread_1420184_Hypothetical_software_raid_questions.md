---
title: "Hypothetical software raid questions"
date: 2010-03-02
forum: Server Platforms
---

### Post by whoop on 2010-03-02
I tested the reliability of a software raid 1 array "quite drastically" via formatting one of the partitions in an array (with a live cd) and then rebooting the machine. After starting the system with the degraded array and adding the formatted partition back to the array everything started working again.

So, I think I have two questions:
*I can understand that mdadm would figure out something was wrong with a disk if (smart for instance) was reporting it was failing, but when an array is out of sync (one file is slightly different for instance) how does mdadm know which partition is "wrong".

*If you have selected not to boot from a degraded array (during install of ubuntu server), how do you resolve the problem? I have only done this via booting the degraded array but I have read that this could lead to data loss in some occasions.

---

### Post by KiLaHuRtZ on 2010-03-03
Personally, all my experiences with mdadm lead me to just buy decent hardware controllers in the end.  Specifically 3ware as they are supported right in the kernel.  They aren't cheap, around $400-$500.  It all depends on how valuable your data is to you and how much time you want to spend recovering it.  The old adage,...you get what you pay for. ;)

---

### Post by whoop on 2010-03-03
> **KiLaHuRtZ said:**
> Personally, all my experiences with mdadm lead me to just buy decent hardware controllers in the end.  Specifically 3ware as they are supported right in the kernel.  They aren't cheap, around $400-$500.  It all depends on how valuable your data is to you and how much time you want to spend recovering it.  The old adage,...you get what you pay for. ;)

Thanks for your response, although you didn't answer any of my questions :D

My experience with mdadm has been remarkable (over the last few years), performance wise and concerning reliability. My questions didn't concern the quality or reliability of mdadm.
I do agree with your argument, but mdadm is suiting me just fine, for the moment.

---

