---
title: "Replicate Windows DFS?"
date: 2008-05-13
forum: Server Platforms
---

### Post by licensedorchid on 2008-05-13
I was wondering if it was possible to use Ubuntu 8.04 to replicate windows DFS shares. We have about 12 sites that I would like to move to ubuntu-based site servers, but will need to do this.
Specifically, we have AD-based DFS, and would like to make the servers root servers.
Thanks!

---

### Post by licensedorchid on 2008-05-14
Apparently, it is possible with the CIFS module in the 2.6 kernel, but I can't find any good information on it. Thoughts?

---

### Post by Dogers on 2008-05-14
Look lower - check out the Coda filesystem. You should be able to use that to distribute your data, then just use Samba to share out the data on each server (you might want to look at putting config files in CVS or similar, then you can do a check out on each server).

---

