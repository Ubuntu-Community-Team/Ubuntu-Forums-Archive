---
title: "Appropriate kernel for KVM guest server"
date: 2009-05-04
forum: Server Platforms
---

### Post by vetch101 on 2009-05-04
Hi all,

I am running a couple of KVM guest servers on my main host server.

Should I be running them on the linux-image-server kernel or the linux-image-virtual kernel...?

What are the key differences?

Many thanks,

Jx

---

### Post by dendrobates on 2009-05-08
The virtual flavor only contains the drivers necessary to run as a guest in the supported hypervisors, and it is, therefore, smaller.

---

