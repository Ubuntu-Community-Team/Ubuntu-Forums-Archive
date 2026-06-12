---
title: "Accessing shared drives and folders"
date: 2009-04-21
forum: Wine
---

### Post by dsmithnc on 2009-04-21
Is there a way in Wine to access shared folders on other machines?  I would like to be able to get to drives/folders on another pc on the network, but can't seem to figure out how to do it or whether it, indeed, can be done.

thanks

Dick

---

### Post by asdfoo on 2009-04-21
> **dsmithnc said:**
> Is there a way in Wine to access shared folders on other machines?  I would like to be able to get to drives/folders on another pc on the network, but can't seem to figure out how to do it or whether it, indeed, can be done.

thanks

Dick

Yes, but you need to configure access to the shared folders on the other machines in Ubuntu first (it uses samba) so that it's mounted to a point on your filesystem, then you use winecfg to assign a drive letter to that path.

---

### Post by dsmithnc on 2009-04-22
Thanks for that tip.  No if I can get myself through all of the confusing stuff that I have read about Samba I'll be ok.  I'll get there it'll just take some time.

Dick

---

