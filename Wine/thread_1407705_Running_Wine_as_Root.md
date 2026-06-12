---
title: "Running Wine as Root"
date: 2010-02-15
forum: Wine
---

### Post by hauj0bb on 2010-02-15
Hi,

I understand the security implications of running wine as root, but I have a very special case. 

My issue is this: WARNING: Trying to use ICMP (network ping) will fail unless running as root.

I'm running a work application that needs direct access to ICMP, which I've tried to work around (setcap, kernel patch etc), but to no avail. 

So my only other option seems to be to run wine as root. So, how do I do it without changing permissions/ownership to my normal .wine directory? (wine: /home/user/.wine is not owned by you)

Thanks

---

### Post by gsmanners on 2010-02-15
Since running Wine as root is a major security breach, your only option is to not use that application. Sorry, but I just don't see any alternative but the kernel patch.

---

### Post by teward on 2010-02-15
> **gsmanners said:**
> Since running Wine as root is a major security breach, your only option is to not use that application. Sorry, but I just don't see any alternative but the kernel patch.

Got to agree with this.  NOBODY on these forums will help you to use something if its a security risk, heck, if someone asked me to enable somethign even thoguh its a risk, I'd say no even if they paid me to do it.

---

