---
title: "VMware Backup (Ubuntu)"
date: 2007-12-19
forum: Virtualisation
---

### Post by TheGameAh on 2007-12-19
Hey guys.  Check this out.

In the process of building a VMWare server.  Ubuntu 64 Bit is the host (to take advantage of oodles of RAM).   The guests are XP and 2003 Server.  I'm going to slowly move VMs to this server, 1 at a time, watch performance, etc.

Now I'm thinking backups.  I see no sense in backing up the entire server, as it can be rebuilt quickly.  I would think it would be easier to just backup the VMs.

Can anyone think of a script, or know of one, to kinda automate this?  Such as shutting down the VMs, tarring and perhaps FTPing the VM folders, then starting the VMs back up again?

Or is this even a good idea?  Does anyone already do something similar?

---

### Post by fjgaude on 2007-12-19
Well, what about using Unison, or even Grsync?

Either are fast and only copies changes in file, not the whole database.

---

