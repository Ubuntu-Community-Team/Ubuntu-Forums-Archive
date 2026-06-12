---
title: "Nautilus search current folder ignores generic * outside home"
date: 2024-06-19
forum: Ubuntu Development Version
---

### Post by corradoventu on 2024-06-19
Open a directory in a partition outside home, search current folder, search ignores generic character *
example: search for 'LG' I see all files starting with 'LG'
search for 'LG*' I see NO MATCHES.
Same search in a home subdirectory works fine.
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/2069835](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/2069835)
same problem on Ubuntu 24.04 Noble and 24.10 Oracular

---

### Post by Claus7 on 2024-06-19
Hello,

I tried it under Recent folder and I noticed the same thing. Marked me as affected.

Regards!

---

