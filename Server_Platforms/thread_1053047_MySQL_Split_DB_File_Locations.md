---
title: "MySQL: Split DB File Locations?"
date: 2009-01-28
forum: Server Platforms
---

### Post by mobcdi on 2009-01-28
I'm running ubuntu server 8.04 and was hoping it was possible to specify where on my file system the MySQL database logs and files should be stored. 

From searching the forums its possible to move the location _of all_ databases on the server to somewhere new but can't find out if its possible to move _just 1 _of the databases hosted?

Anyone able to help me out?

---

### Post by kidders on 2009-01-29
Hi there,

> **mobcdi said:**
> can't find out if its possible to move _just 1 _of the databases hosted?

Your MySQL datadir should contain directories for each database. In theory, I imagine you could make some/all of them symlinks or mount points, depending on what you want to achieve. The only potential issue I can imagine is that MySQL *might* not be expecting bits of its datadir to be spread across multiple filesystems ... Just something you might want to check.

I wouldn't recommend running such a configuration without taking precautions (eg backup/replication), to cover the increased possibility of something odd happening somewhere down the line.

---

