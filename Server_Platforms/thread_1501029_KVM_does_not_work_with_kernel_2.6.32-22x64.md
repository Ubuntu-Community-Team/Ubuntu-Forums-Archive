---
title: "KVM does not work with kernel 2.6.32-22/x64"
date: 2010-06-03
forum: Server Platforms
---

### Post by MartinSixta on 2010-06-03
Today, after upgrading kernel to version 2.6.32-22 (linux-image-2.6.32-22-server) all my KVM guests stopped working. I could not reach the guests over (bridged) network or connnect to the guests with virt-mangager (well, I could but all i could see was black screen). I was able to reproduce the issue on my second server. 

Reverting to kernel 2.6.32-21 resolved the issue.

Since I don't have that much experience with virtualization and Ubuntu in general, could somebody advise me on what action (if any) should I take / where to report my issues?

---

### Post by cjstokyo on 2010-06-04
Typically you'd want to first search bugs.ubuntu.com to see if someone's already reported the bug. If not, you can then run "ubuntu-bug -p linux" on the affected system (this being your host that won't boot the guests) and report it.

However, I just checked in on the freenode IRC channel #ubuntu-server, and I'm informed that there's now a fix for this problem. The update should apparently be out in the next 24 hours or so.

---

### Post by MartinSixta on 2010-06-04
> **cjstokyo said:**
> Typically you'd want to first search bugs.ubuntu.com to see if someone's already reported the bug. If not, you can then run &quot;ubuntu-bug -p linux&quot; on the affected system (this being your host that won't boot the guests) and report it.

However, I just checked in on the freenode IRC channel #ubuntu-server, and I'm informed that there's now a fix for this problem. The update should apparently be out in the next 24 hours or so.

 Thank you for your input. Next time I run into problems I will try to do as you advised me.  I'm glad the issue is known and being worked on.

---

