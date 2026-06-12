---
title: "With LVM/LUKS - if you upgrade kernels, will you have a problem?"
date: 2008-05-27
forum: Security
---

### Post by kevdog on 2008-05-27
If I have installed Hardy with LVM/LUKS whole disk encryption and then later upgrade to the latest generic kernel, will I have a problem?  Is yes, is there a workaround?

---

### Post by p_quarles on 2008-05-28
You'd have a problem if you compiled a kernel without crypto support, but aside from that I can't envision any trouble. I mean, you could even do a fresh installation on the same LVM and it will work fine (this isn't particularly straight forward, but it works).

---

### Post by hyper_ch on 2008-05-28
if you do normal upgrade to a kernel that also has crypto module enable (which is now default by the ubuntu desktop kernels) you have no problem.

---

### Post by kevdog on 2008-05-28
I tried updating to Ibex's developing kernel -- I believe the ppa version as described here:
[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/204996/comments/192](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/204996/comments/192)

Definitely the LVM login process on boot hangs.  I have no idea if the crypto lib was compiled.  I responded to launchpad days ago, however have received no response (as seems my experience with launchpad in the past!)

Any ideas?

---

