---
title: "NFS mount takes aaaaages"
date: 2005-10-26
forum: Server Platforms
---

### Post by caspar_wrede on 2005-10-26
I have a server running hoary. Mounting the root partition takes almost a minute. The problem occurs with two different laptops and still ocurred after upgrading from hoary to breezy on the clients. On the server I am running the kernel nfs daemon.

What's going on?

Caspar.

---

### Post by sassur on 2005-10-26
install portmap, that will make NFS mounting fast.

---

### Post by caspar_wrede on 2005-10-26
Portmap is installed (on the server)

---

