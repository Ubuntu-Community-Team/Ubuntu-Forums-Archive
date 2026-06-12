---
title: "rkhunter querry..."
date: 2009-10-22
forum: Security
---

### Post by darms21 on 2009-10-22
After running rkhunter results came back with a warning:

Checking /dev for suspicious file types         [ Warning ]
[00:08:33] Warning: Suspicious file types found in /dev:
[00:08:33]          /dev/shm/pulse-shm-2769096950: data


Is this an false positive or is there something I need to do to fix the vulnerability?

---

### Post by phillw on 2009-10-22
It's a false positive.

The matter is discussed in this thread ...

[http://ubuntuforums.org/showthread.php?p=4908163](http://ubuntuforums.org/showthread.php?p=4908163)

It also details how to teach rkhunter to ignore it.

Phill.

---

