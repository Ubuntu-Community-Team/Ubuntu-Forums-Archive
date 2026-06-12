---
title: "Horrible SSH Performance"
date: 2010-10-15
forum: Server Platforms
---

### Post by gencha on 2010-10-15
Yesterday I installed a new kvm VM on one of our servers and the SSH performance is horrible and the connection itself very unstable.

Most of the time I don't even get to the login. If I can login, the connection will die shortly after. The error is usually "Software caused connection abort".

What's confusing about this is that there are multiple other VMs (same Ubuntu version) on the same server. And they all work perfectly fine.

It's a 8.04 system, fully updated.

---

### Post by gencha on 2010-10-15
Ok, I finally realized my mistake shortly after opening this thread. In the kvm command line, I forgot to change the MAC address of the primary NIC...

---

