---
title: "Virt-manager remote access; cannot use shared psyical device"
date: 2009-11-01
forum: Server Platforms
---

### Post by tall-male on 2009-11-01
I managed to use a _local_ virt-manager to connect to my _remote_ libvirtd using tls/ssl.
Quite nice, I don't have to give root access using remote access now.

However: if I want te create a new virtual machine remotely I cannot give it a shared physical (network) device, bridge interface that is. This option is grayed out in  virt-manager.

When I use virt-manager on the remote machine (using X-forwarding) I can use the shared  physical (network) device. (Oh yes, br0 is set up well and working)

Anyone knows how to use the bridging interface when using remote access?

Thanks!

---

### Post by hermanhobnob on 2009-11-06
I have the same problem. Noticed it in Jaunty and Karmic. It's most annoying and I'm afraid I haven't found a solution. Please post back if you find one!

---

