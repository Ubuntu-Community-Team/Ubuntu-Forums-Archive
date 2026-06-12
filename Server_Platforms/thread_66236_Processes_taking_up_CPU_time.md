---
title: "Processes taking up CPU time"
date: 2005-09-16
forum: Server Platforms
---

### Post by Ciaran on 2005-09-16
Hi,

I've noticed some processes taking up a high precentage of CPU time on two new servers I've installed.  They don't appear to be degrading performance, so it occurred to me they might be an equivalent to the Windows "System Idle" processes.

The process names are ahd_dv_0 and ahd_dv_1.  They seem to take up all the available CPU that it not being used for other processes, i.e. system idle as shown by top and vmstat is always 0.0%.

Should I be concerned about them?

Regards

Ciarán

---

### Post by Ciaran on 2005-09-20
It seems this is a driver for the Adaptec U320 controller which is installed in the server.  I say it "seems" because Google has found me very little documentation on it :(  I don't know why the processes are running in user space, but I can't kill them.  Apparently the inability to kill the processes is a known issue with 2.6.12 pre-release kernels.  I'm running 2.6.11-1-686.

I still don't know if it's supposed to eat all the CPU in this way, but server performance is fine all the same.

So I'm not panicking about this but any insight would be appreciated :)

---

