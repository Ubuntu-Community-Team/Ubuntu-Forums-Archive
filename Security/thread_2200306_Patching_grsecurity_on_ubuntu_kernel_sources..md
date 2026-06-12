---
title: "Patching grsecurity on ubuntu kernel sources."
date: 2014-01-18
forum: Security
---

### Post by bryn1u on 2014-01-18
Hi,

I have a problem witch patching grsecurity on ubuntu kernel sources 3.2

I used apt-get source linux-sources-3.2, and then was trying to patch kernel. After that i got:
```

patching file Documentation/dontdiff
patching file Documentation/kernel-parameters.txt
Hunk #1 succeeded at 881 (offset 22 lines).
Hunk #2 succeeded at 1987 (offset 24 lines).
patching file Documentation/sysctl/fs.txt
patching file Makefile
Hunk #2 succeeded at 417 (offset 9 lines).
Hunk #3 succeeded at 574 (offset 9 lines).
Hunk #4 succeeded at 777 (offset 9 lines).
Hunk #5 succeeded at 1001 (offset 9 lines).
Hunk #6 succeeded at 1012 (offset 9 lines).
Hunk #7 succeeded at 1052 (offset 9 lines).
Hunk #8 succeeded at 1165 (offset 11 lines).
Hunk #9 succeeded at 1182 (offset 11 lines).
Hunk #10 succeeded at 1241 (offset 11 lines).
Hunk #11 succeeded at 1279 (offset 11 lines).
Hunk #12 succeeded at 1440 (offset 11 lines).
Hunk #13 succeeded at 1568 (offset 11 lines).
Hunk #14 succeeded at 1592 (offset 11 lines).
patching file arch/Kconfig
Reversed (or previously applied) patch detected!  Assume -R? [n] ^C
root@ks3360102:/usr/src/linux-3.2.0#


```

I tryied on grsec:
> 
[grsecurity-3.0-3.2.54-201401160931.patch]("http://grsecurity.net/stable/grsecurity-3.0-3.2.54-201401160931.patch")


Kernel sources:
```

dpkg-source: info: extracting linux in linux-3.2.0
dpkg-source: info: unpacking linux_3.2.0.orig.tar.gz
dpkg-source: info: applying linux_3.2.0-58.88.diff.gz
root@ks3360102:/usr/src# ls
linux-3.2.0

```

Someone can help ?

---

### Post by Hungry Man on 2014-01-18
Download kernel source from kernel.org.Download the *associated grsecurity patch for that version*. A patch for 3.12 is not going to work for any other version. Patches are *only* for the latest or the stable branch, old patches are not available.

---

