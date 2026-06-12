---
title: "Altering caching behavior?"
date: 2010-11-30
forum: Server Platforms
---

### Post by Pro_D on 2010-11-30
Still running 9.04, plan to jump to 10.04LTS during a bit of a holiday break.  Ubuntu server with ubuntu desktop packages installed for vncserver and users to have something to work with.

What I would like to know is can I alter filesystem caching behavior or simply disable it.  For the moment I have disabled swap space which forces the kernel to free filesystem cache instead of degrading performance by throwing things to swap.

When swap is on, the system will use just about 70% of ram for caching the filesystem but programs and services under a 'full' load use no more than about 50-60% of ram.  Thats a lot of stuff that gets swapped out if swap is enabled - filesystem cache seems to take a high priority even with a low swappiness value.  Most of the services and programs have their own caching mechanism anyway so a lot of the cache is wasted memory...

I have spent a while trying to read on this but I guess I haven't asked google in the right way...

---

