---
title: "system time ticks incorrectly"
date: 2006-06-20
forum: Server Platforms
---

### Post by nihilocrat on 2006-06-20
I've been noticing that every time I access my server, the time is set to something wildly off. Even running a cron script to run ntpdate every day doesn't seem to help. I noticed that the time is significantly inaccurate (30 secs or so) after just a minute or two of leaving it alone. It seems to actually be ticking, but it must be amazingly slow.

It is probably important to point out that this is a VMWare virtual machine. I didn't really pay attention to how I set up time when I installed it, so I must've chosen the defaults (except that the server runs on local time). I think it might be an issue with the system clock: something might be screwing up and thus I would want to switch over to using a software timer (if possible).

I'm wondering what the issue might be, or how I might be able to stop using system time.

---

### Post by x64Jimbo on 2006-06-20
VMWare guest machines have an option to sync or not sync with the host system's time. This option is accessed in the VMWare tools that you install. If it's Windows, you can access those options through the VMWare icon in the systray. Not sure about Linux guests since I haven't run any of them yet.

---

### Post by nihilocrat on 2006-06-20
The real kicker is that I'm running a CentOS VM on the same physical machine... and its clock is working just fine! I will try and see if there are any options via the VMware control center, though.

---

