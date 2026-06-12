---
title: "Ubuntu server with 3 types of jobs?"
date: 2024-06-13
forum: Server Platforms
---

### Post by rbcc-12 on 2024-06-13
Can one installation of server be a printer server , backup and a media server?  JTM

---

### Post by TheFu on 2024-06-13
Yes.

However, there are security risks in placing backups on the same system as media that will be shared across the network.  Just be certain that the areas where backup data is stored is NOT shared on the network AND it locked down to prevent any local access by non-root accounts.  Since almost all backup programs require running as root to get data from other systems AND retain permissions, owner, group, ACLs, and xattrs, this isn't really all that hard.

---

