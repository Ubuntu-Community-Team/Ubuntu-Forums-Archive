---
title: "Kernel-source-2.6.12 does not exist"
date: 2005-09-18
forum: Repositories &amp; Backports
---

### Post by visto on 2005-09-18
Breezy Badger ships with kernel 2.6.12-8-386
but kernel-source for the installed version does not exist.

apt-get can only fetch 2.6.11, which does not match, and so gives a huge amount of errors.

I have not installed the 2.6.11 kernel made from the old source, but I suspect it would just crash the system anyway.

---

### Post by Xian on 2005-09-19
The package you want is linux-source-2.6.12.

---

### Post by .abe on 2005-11-23
Am using Breezy Badger 5.10.
I tried downloading the kernel sources with the command:

```
sudo apt-get install kernel-tree
```

the response:
```
E: Couldn't find package kernel-tree
```

Anybody know anything about this? TIA.

---

