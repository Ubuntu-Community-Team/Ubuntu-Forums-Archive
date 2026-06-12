---
title: "Consolidating servers (Samba, Vmware)"
date: 2008-10-17
forum: Server Platforms
---

### Post by TheGameAh on 2008-10-17
Hey guys.

Looking to consolidate a few servers, mostly Windows.  Gonna use a Linux/VMware Server type approach (not ready for ESXi yet).

The file servers turn out to be about 200 gigabyte.  Don't want to put that in a Windows VM, so I figure I'll just use samba to share them out.

So this server will have:

200+ gigabyte file share(s) through samba
VMware server installed, and about 4-5 VMs (most very small, one at 50 gig)
Possibly an NFS server installed (little use)

Anyone see a problem with that?  Most everyone tells me that VMWare should just run by itself, nothing else ever running.  But not really an option in this case, and I don't want to create a 200+ gigabyte (and growing) VM.

---

