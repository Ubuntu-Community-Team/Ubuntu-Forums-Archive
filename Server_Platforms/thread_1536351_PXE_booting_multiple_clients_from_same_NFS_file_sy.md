---
title: "PXE booting multiple clients from same NFS file system"
date: 2010-07-22
forum: Server Platforms
---

### Post by pengin80 on 2010-07-22
Hi, noob question on PXE booting multiple machines with the same filesystem.

I've set up a Lucid server with dhcp3, bind9, tftp etc so I can  boot a client machine over the network using PXE.  The client gets its  host name from dhcp depending on it's MAC, and the root file system is  mounted using NFS (following a tutorial like [this]("https://help.ubuntu.com/community/DisklessUbuntuHowto")). 

I seem to be able to boot multiple machines off the same PXE image and NFS root file  system, and when I make a file on one client it is seen on the other.  Will booting multiple clients with the same file system cause problems?  The "why do it" paragraph at the top of the [tutorial]("https://help.ubuntu.com/community/DisklessUbuntuHowto") suggests not, but I wanted to check.  E.g. if I run the same programs on the clients will they both  write to the same log/cache files and mess each other up?

Thanks

---

