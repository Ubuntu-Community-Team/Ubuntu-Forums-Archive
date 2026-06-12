---
title: "Trouble with Ubuntu and HP-UX 11 NFS boot"
date: 2015-08-17
forum: Server Platforms
---

### Post by le_jawa on 2015-08-17
I'm trying to boot an Ubuntu 12.04 thin client from an HP-UX 11 server.   The TFTP portion works fine, but once the kernel loads and has to pull the OS from NFS, we run into trouble. We keep getting an error saying NFS over TCP is not available, and a reference to /scripts/nfs-premount.  I've added proto=udp to the root mount in fstab, thinking that TCP vs. UDP was the issue, but that didn't help.  Also the directory with the OS is world-readable.  

The previous thin client OS (Fedora 10) worked.  If this isn't a matter of the transport protocol being used, any thoughts on what it could be?

Also, we've looked at the network - no firewall or connectivity issues.

Thanks everyone!

-Jason

---

