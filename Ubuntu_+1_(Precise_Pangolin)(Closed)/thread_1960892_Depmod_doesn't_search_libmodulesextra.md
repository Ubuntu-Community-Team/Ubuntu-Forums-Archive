---
title: "Depmod doesn't search /lib/modules/*/extra"
date: 2012-04-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by NHclimber on 2012-04-18
Just discovered that depmod no longer searches /lib/modules/*/extra anymore.
That change now obsoletes a number of long-standing wiki instructions about how to build out-of-tree modules 'the ubuntu way' -- like here [https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild)

I ended up changing /etc/depmod.d/ubuntu.conf to:
```
search [COLOR=Blue]extra [/COLOR]updates ubuntu built-in
```

I checked oneiric first and the .conf file is the same as precise. Where did that change?

---

