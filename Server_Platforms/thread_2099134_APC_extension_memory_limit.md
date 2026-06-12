---
title: "APC extension memory limit"
date: 2012-12-28
forum: Server Platforms
---

### Post by heretic381 on 2012-12-28
Hi,
I'm trying to speed up my server (Ubuntu 11.04 32M) and the hosted Drupal site, using APC.

The problem is when I run tests, like ab benchmark, I see that APC cache never exceeds 32M, even if I can allocate more memory by setting

apc.shm_size=



The 32M limit is set somewhere else, and I have no idea where.

I've tried

I've installed APC from the regular deb package.


Thanks in advance.

---

