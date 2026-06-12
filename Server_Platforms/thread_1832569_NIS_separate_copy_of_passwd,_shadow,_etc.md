---
title: "NIS separate copy of passwd, shadow, etc"
date: 2011-08-24
forum: Server Platforms
---

### Post by vortmax on 2011-08-24
I'm setting up an NIS server to manage a small set of unix boxes.  The master and the slave also serve as the master and failover dhcp and bind servers, so I don't really want all the users in the NIS domain to have login rights to the machines.  I have configured the NIS server to serve an alternate set of files (located in /var/yp/auth/) which separates the local server authentication from the NIS domain, but now I'm faced with having to manually update the passwd and shadow files instead of simply using useradd.

I looked through the man page for useradd, but didn't see a flag to specify alternate files.  Is there a utility that I can use to update these files in the same fashion that useradd, usermod, groupadd, groupmod, etc update the system default files?

---

