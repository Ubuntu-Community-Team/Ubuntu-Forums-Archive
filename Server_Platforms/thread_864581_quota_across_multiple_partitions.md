---
title: "quota across multiple partitions"
date: 2008-07-19
forum: Server Platforms
---

### Post by RiskySeven on 2008-07-19
Hello.  I want to setup quota to track across multiple partitions.  If I setup quota on two partitions, let's say /home and /share...and user 'A' is limited to 1GB of space.  If they have 500MB in /home and 700MB in /share, will this trigger a quota violation?  If not, is there an option in quota to do this?  Thanks.

---

### Post by pdwerryhouse on 2008-07-19
No, quotas are only determined over one filesystem. There isn't a way to do what you want on the current filesystems available under Linux; the only feasible way for you to do something like this would be to merge the two filesystems into one.

---

### Post by RiskySeven on 2008-07-19
Thanks for the quick response.  Time to do some partition juggling. :)

---

