---
title: "Ubuntu 10.04 NFS storage behind firewall"
date: 2010-10-19
forum: Server Platforms
---

### Post by UffTec on 2010-10-19
Hello, I connect an external esxi host to a datastore server hosted on an Ubuntu 10.04 on which I created the export mounted in the internal hosts.
I have seen with the command rpcinfo-p all ports used by the NFS service (portmapper  mountd , nfs status nlockmgr) and verified that the last three are actually dynamic gates that change each time you start
On the web I found several guides on how to fix these doors, but are for older versions of ubuntu or linux distributions different, so follow the guide services and configuration files are missing or cmq are different.

I wonder if someone can tell me the correct way to 10.04, and even if coming from the outside at the level of permission do I have other controls on exports already fully functional in r / w by internal hosts esxi that use it

Thanks

---

