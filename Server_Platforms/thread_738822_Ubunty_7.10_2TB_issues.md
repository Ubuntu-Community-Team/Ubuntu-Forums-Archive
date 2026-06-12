---
title: "Ubunty 7.10 2TB issues"
date: 2008-03-29
forum: Server Platforms
---

### Post by curtishall on 2008-03-29
I have two Dell poweredge 2950 servers.  One has 1tb of space the second has 2tb of space.

The first installed 7.10 without any problems.  The second has given me nothing but problems. I'm adding 4GB for swap and the rest (2.2tb) as XFS.  I can install 7.10 and get through LILO just fine.  However when I reboot I it throws all kinds of xfs errors and will not boot.  I've read several forums about 2tb filesystems problems but I haven't found a good solution on how 
to fix this. 

Any suggestions and step by step instructions would be most excellent.

Thanks

---

### Post by Paul Weaver on 2008-04-02
> **curtishall said:**
> I have two Dell poweredge 2950 servers.  One has 1tb of space the second has 2tb of space.

The first installed 7.10 without any problems.  The second has given me nothing but problems. I'm adding 4GB for swap and the rest (2.2tb) as XFS.  I can install 7.10 and get through LILO just fine.  However when I reboot I it throws all kinds of xfs errors and will not boot.  I've read several forums about 2tb filesystems problems but I haven't found a good solution on how 
to fix this. 

Any suggestions and step by step instructions would be most excellent.

Thanks

You might be having issues with a >2TB root partition, if that's what you do indeed have. I can confirm 7.10 and xfs is perfectly happy with > 2TB.

---

