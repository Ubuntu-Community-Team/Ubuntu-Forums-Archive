---
title: "Apache Server Load increase after security update"
date: 2013-08-05
forum: Server Platforms
---

### Post by Geoff_Butterfield on 2013-08-05
I recently ran security updates on 2 of 3 identical web servers, all running 12.04 LTS. After the update:

apache2-mpm-prefork:amd64 (2.2.22-1ubuntu1.2, 2.2.22-1ubuntu1.4),
apache2-utils:amd64 (2.2.22-1ubuntu1.2, 2.2.22-1ubuntu1.4),
apache2.2-bin:amd64 (2.2.22-1ubuntu1.2, 2.2.22-1ubuntu1.4),
apache2.2-common:amd64 (2.2.22-1ubuntu1.2, 2.2.22-1ubuntu1.4),
apache2:amd64 (2.2.22-1ubuntu1.2, 2.2.22-1ubuntu1.4),
... [edited for length]

I'm noticing the updated servers are running with a load 3x-4x higher then the un-updated server. These servers are all part of the same round-robin cache pool, so the loads should be roughly the same. So I'm sniffing about for clues -- anyone have any suggestions?

---

