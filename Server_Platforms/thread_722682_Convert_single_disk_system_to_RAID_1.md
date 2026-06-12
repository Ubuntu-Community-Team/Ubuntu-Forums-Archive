---
title: "Convert single disk system to RAID 1"
date: 2008-03-12
forum: Server Platforms
---

### Post by HereInOz on 2008-03-12
Hi All,

I am wondering if it is possible to convert a single disk system (Gutsy Server) to a RAID 1 configuration without formatting and re-installing.

Can anyone assist on this one?

---

### Post by lha on 2008-03-12
> **HereInOz said:**
> Hi All,

I am wondering if it is possible to convert a single disk system (Gutsy Server) to a RAID 1 configuration without formatting and re-installing.

Can anyone assist on this one?

Yes, it is possible. The mdadm package contains instructions (/usr/share/doc/mdadm/rootraiddoc.97.html). Some of the steps can be skipped, though. (Like kernel compiling)

---

