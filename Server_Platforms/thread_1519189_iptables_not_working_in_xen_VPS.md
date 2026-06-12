---
title: "iptables not working in xen VPS"
date: 2010-06-27
forum: Server Platforms
---

### Post by graeme_p on 2010-06-27
When I try to run anything that uses iptables, even just iptables -L, I get:
```

1+drm33.2/modules.dep: No such file or directory
iptables v1.4.4: can't initialize iptables table `filter': iptables who? (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.
```

This is on a fresh Ubuntu minimal install, using my VPS hosts image (so they could have messed something up).

I know there have been issues in the past with iptables on Ubuntu on xen. Is this a Ubuntu bug? Is there a solution? 

incidentally depmod -a gives:

```
WARNING: Couldn't open directory /lib/modules/2.6.32.11+drm33.2: No such file or directory
FATAL: Could not open /lib/modules/2.6.32.11+drm33.2/modules.dep.temp for writing: No such file or directory
```

---

### Post by graeme_p on 2010-06-28
Solved: it turned that /lib/modules had the wrong modules in it.

---

