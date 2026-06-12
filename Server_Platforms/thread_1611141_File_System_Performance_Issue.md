---
title: "File System Performance Issue"
date: 2010-11-01
forum: Server Platforms
---

### Post by kitplane01 on 2010-11-01
We have been benchmarking Ubuntu 10.04 vs OpenSuse 11.  We notice that the OpenSuse file system is just faster than Ubuntu.

For example, tar -xf linux-2.6.36-rc3.tar.bz2 runs in 35 seconds on OpenSuse, and 45 seconds on Ubuntu.  Both systems are using ext4 and bunzip 1.05 and tar 1.22 or 1.23.

Is Ubuntu mounting it's root filesystem with some journalling option that is slower than OpenSuse?   Any other guesses?

-Thanks
-Kitplane01

---

