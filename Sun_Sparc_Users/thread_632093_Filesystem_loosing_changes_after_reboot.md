---
title: "Filesystem loosing changes after reboot"
date: 2007-12-05
forum: Sun Sparc Users
---

### Post by swellnuts on 2007-12-05
Here's a weird one.

```
Linux brick 2.6.20-15-sparc64-smp #2 SMP Sun Apr 15 07:03:03 UTC 2007 sparc64 GNU/Linux
```

Running on Feisty.

The install worked great, the system boots fine, and its a joy to use.

One small problem:  changes to files are lost over a reboot.

No kidding, I add users, I config the network, I change the root password, and after a reboot, all my changes are gone.  Entire files are missing, or else the edits I made are not there any more.

The only thing I noticed, is that the system wont power itself off when I say "reboot" but instead hangs at what I thought was the last line of the shutdown script.

Could it be that the file systems are not flushing, and the journal is rolling back?

---

