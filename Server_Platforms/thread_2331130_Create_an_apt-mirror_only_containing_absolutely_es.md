---
title: "Create an apt-mirror only containing absolutely essential updates and packages?"
date: 2016-07-18
forum: Server Platforms
---

### Post by Shampyon on 2016-07-18
I'm doing some volunteer work for a rural education institution. They do a lot of installs and reinstalls of ubuntu that require updates and a few select packages from the repos. The internet out here is terrible, and they have very limited resources. Setting up a VM apt-mirror would help a lot, but from what I see it requires a 100GB+ download - that might not be a big deal to a lot of you working in professional environments, but for this school it's enormous.

Is it possible to set up a VM with apt-mirror or a similar app that only pulls the essential security updates and the select few packages/dependencies they need for class? If so, how would I go about it?

---

### Post by Tadaen_Sylvermane on 2016-07-19
Look into apt-cacher-ng. I use it at home. It downloads the new package from the internet only if not in cache, otherwise everything comes from the cache. Cuts bandwidth and download time to nearly nothing for cached packages.

http://www.tecmint.com/apt-cache-server-in-ubuntu/

---

