---
title: "4G/4G split kernel package?"
date: 2011-02-12
forum: Server Platforms
---

### Post by madoka on 2011-02-12
I have a server with 24 GB of memory, running karmic with linux-image-generic-pae kernel, and I'm running out of low memory:
```
$ grep -i low /proc/meminfo
LowTotal:         433844 kB
LowFree:           63840 kB
```

I'm looking for a kernel image that's equivalent to the "hugemem" kernel in [Redhat]("http://lwn.net/Articles/39283/") for karmic.  Does such thing exist?

I'm already using linux-image-generic-pae, so the system can see all 24 GB of memory.  Eventually I'll migrate to the 64-bit kernel, but just not right now.

---

### Post by CharlesA on 2011-02-12
Using the 32-bit kernel is the hang up. I don't know of any such kernel in Ubuntu.

Migrating to the 64-bit kernel will fix the problem.

EDIT: I found some info about [how redhat does it]("http://linux-redhat.net/Prentice.Hall.PTR-A.Practical.Guide.to.Red.Hat.Linux-Fedora.Core.and.Red.Hat.Enterprise.Linux.Third.Edition/0132280272/app05lev1sec12.html").

---

