---
title: "Bad performance on 18.04"
date: 2018-08-14
forum: Server Platforms
---

### Post by flok123 on 2018-08-14
I upgraded one of our build servers from 16.04 to 18.04. Everything is working fine until I checked the build times. A build that used to take ~8 minutes now takes twice as long.
What seems odd is an extremly high number of CPU context switches ~ 150k under high load. The server runs two lxd container + several docker containers. However I can't say how high the context switch number was before.

The CPU load is about the same as before. Nothing of the build environment itself changed except the OS and kernel version (4.4.0 -> 4.15.0).

Has anyone experienced the same? Any ideas how to debug this?

---

### Post by TheFu on 2018-08-14
Just a guess.  18.04 is too new for my use, so we don't have it here.

18.04 added snaps as the default method for many things.  Depending on the snaps, code RAM use may have raised significantly. It is a guess.

What does your performance monitoring show before and after the upgrade?  What has changed? RAM use, files opened, disk performance? Network performance?  Networking performance?  Buffers used?   "Working fine" isn't exactly specific. On a production server, performance monitoring isn't optional, IMHO.

---

### Post by flok123 on 2018-08-15
That is the problem that the RAM use, CPU use, disk performance etc. all looks as before. I can't find any differences in the server stats. Just a huge slowdown in build times.

I doubt that snaps are a cause as none is installed. The server runs just LXD (which was updated to v3 on 16.04 already, so no change there). LXD runs two machines with basically just docker (version stayed the same as before). The builds happen inside docker containers that didn't change. So the working software hasn't really changed.
That's the reason why I can't be more specific as working fine. Everything does what it is supposed to do just a lot slower.

First thought were the spectre/meltdown patches but they also were enabled in 16.04 already.

---

### Post by flok123 on 2018-08-16
Turns out the IO scheduler changed in 18.04 from deadline to CFQ which was desastrous in our case. Switching back to deadline fixed the performance loss.

---

