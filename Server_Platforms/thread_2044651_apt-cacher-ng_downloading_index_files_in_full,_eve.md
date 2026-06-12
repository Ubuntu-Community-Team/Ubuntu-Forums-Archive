---
title: "apt-cacher-ng downloading index files in full, even when no changes"
date: 2012-08-19
forum: Server Platforms
---

### Post by Irihapeti on 2012-08-19
I have apt-cacher-ng installed on my PC (running 12.04 desktop version) on my home network.

I notice that every time I run apt-get update through acng, it downloads the package index files in full, which is 11MB or so in my case.

This seemed like it might be related to this bug: [https://bugs.launchpad.net/ubuntu/+bug/1001780](https://bugs.launchpad.net/ubuntu/+bug/1001780).

The bug has been fixed for direct repository access, but I'm still getting the big downloads when I update through acng.

Is this expected behaviour? If not, what should I be looking at on my own system before I go reporting a bug?

---

