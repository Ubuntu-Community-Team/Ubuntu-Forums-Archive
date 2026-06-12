---
title: "weird problems with shared folder with virtualbox"
date: 2009-07-29
forum: Virtualisation
---

### Post by laplace/d on 2009-07-29
i am able to share folders between ubuntu(host) and winXP (guest). when i open the folder in windows, it doesnt display any content, but if i drag a file into it, i will see that content on ubuntu.

---

### Post by EndersJ on 2009-07-29
> **laplace/d said:**
> i am able to share folders between ubuntu(host) and winXP (guest). when i open the folder in windows, it doesnt display any content, but if i drag a file into it, i will see that content on ubuntu.

This problem may be firewall related. It would make sense that the host can see the guest files (the guest isnt as heavily firewalled) but the guest cannot see the host files.? Maybe you could play around with the host firewall to get it allow content from that client/guest?

---

### Post by laplace/d on 2009-07-30
ubuntu 8.04 doen't have a firewall by default... so i dont have one

---

