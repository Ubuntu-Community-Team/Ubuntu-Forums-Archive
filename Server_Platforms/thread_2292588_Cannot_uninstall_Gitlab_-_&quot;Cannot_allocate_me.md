---
title: "Cannot uninstall Gitlab - &quot;Cannot allocate memory&quot;"
date: 2015-08-29
forum: Server Platforms
---

### Post by andy146 on 2015-08-29
Hi,

I have Ubuntu server which is basically a LAMP running on 512mb ram.

Today I decided I'd mess around and install git, and gitlab. As soon as I installed gitlab SSH is basically unusable and the websites it hosts take forever to load.

I'd like to just remove gitlab as I believe this must be the issue. However, when I try and run most commands it says 'Cannot allocate memory'.

I managed to view all running services and it doesn't appear to be there. When running 'sudo gitlab-ctl uninstall' I get 'Cannot allocate memory'. Even when I try running 'free' or 'top' I get Cannot allocate memory.

What can I do to get this box usable again?

---

### Post by cariboo on 2015-08-29
How did you install git and gitlab, did you install them from the repositories, or via some other method, and were the packages you installed debs?

---

### Post by andy146 on 2015-08-29
Thanks for the response. I had installed through the repo. However, the RAM usage would lower for a few seconds every so often - just long enough for me to set up a swap file and remove it.

---

