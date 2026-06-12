---
title: "Deleted contents of /var/cache by mistake"
date: 2016-09-17
forum: Server Platforms
---

### Post by bluexmas on 2016-09-17
Hey guys,

I am using Ubuntu Server 14.04 and I deleted by mistake the contents of /var/cache (was working on a magento deployment, it has a var/cache and changed directory to **/**var/cache by mistake, then rm -rf *).

I did an "aptitude update" and haven't received any errors, seems that "apt" directory was recreated inside /var/cache.

I rebooted the server and everything also seems fine.

Will perform maintenance tonight and update, then "aptitude upgrade" this server.

Should I worry anything might get broken? It's a live machine under heavy load.

Thank you,

---

