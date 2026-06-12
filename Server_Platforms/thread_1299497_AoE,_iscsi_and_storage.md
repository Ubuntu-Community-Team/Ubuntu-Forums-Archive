---
title: "AoE, iscsi and storage"
date: 2009-10-23
forum: Server Platforms
---

### Post by iga3725 on 2009-10-23
Hi guys, I'd like to share experiences and knowledge about what should I use to install on a new storage server (with a lot of disks) in my network. What I want, is to move all domU's storage to this new storage server with AoE, iscsi or another thing. question:

1. Should I install openfiler or freenas or other NAS software on the storage or simple install a fresh linux operating system e.g, ubuntu and use it as the AoE or iscsi target server?

What do you suggests? use a NAS software or install ubuntu? AoE or icsci?


The scenario is:

1. several domU's working with the storage on the new server
2. Cisco switch between storage and domU's with LACP configure on the two ports used by the server
3. storage server with two NICs using bonding (802.3ad)

thanks tons
regards,
Israel.

---

### Post by windependence on 2009-10-24
See this post, we just discussed this very thing:

[http://ubuntuforums.org/showthread.php?t=1293516](http://ubuntuforums.org/showthread.php?t=1293516)

-Tim

---

