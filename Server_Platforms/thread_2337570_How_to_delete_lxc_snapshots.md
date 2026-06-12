---
title: "How to delete lxc snapshots"
date: 2016-09-19
forum: Server Platforms
---

### Post by courtney2 on 2016-09-19
I created some container snapshots but want to go to an older snapshot. The thing is, I have to delete newer snapshots to get to it. I can't find anything anywhere that tells me how to delete them. What's the command to delete container snapshots in lxc?

---

### Post by DuckHook on 2016-09-19
This tutorial may help: [https://www.stgraber.org/2013/12/27/lxc-1-0-container-storage/](https://www.stgraber.org/2013/12/27/lxc-1-0-container-storage/)

In particular, look at the last example under "snapshots". In summary, you don't have to delete the more recent ones in order to use an older snapshot. Any snapshot can be converted into its own container instance.

---

