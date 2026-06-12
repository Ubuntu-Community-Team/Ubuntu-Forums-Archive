---
title: "TESTING BACKPORT: k3b 0.11.18-0-4.10ubp1"
date: 2004-12-18
forum: Ubuntu Backports
---

### Post by jdong on 2004-12-18
**Summary**
This release contains many bugfixes.

**Backporting Process**
No Ubuntu or Debian packages were available for this version, so I took the 0.11.17 patches and applied it to the official new source. Everything went smoothly.

**Upload Log**
```

building file list ...
185 files to consider
dists/warty-backports-staging/main/binary-i386/Packages.gz
          20 100%    0.00kB/s    0:00:00  (1, 3.8% of 185)
dists/warty-backports-staging/universe/binary-i386/
dists/warty-backports-staging/universe/binary-i386/Packages.gz
        4578 100%   16.74kB/s    0:00:00  (2, 5.9% of 185)
dists/warty-backports-staging/universe/binary-i386/k3b_0.11.18-0-4.10ubp1_i386.deb
     2287378 100%   24.35kB/s    0:01:31  (3, 7.6% of 185)
dists/warty-backports-staging/universe/binary-i386/k3blibs-dev_0.11.18-0-4.10ubp1_i386.deb
       68658 100%   24.28kB/s    0:00:02  (4, 8.1% of 185)
dists/warty-backports-staging/universe/binary-i386/k3blibs_0.11.18-0-4.10ubp1_i386.deb
     1098438 100%   24.78kB/s    0:00:43  (5, 8.6% of 185)
dists/warty-backports/main/binary-i386/Packages.gz
        7354 100%  188.99kB/s    0:00:00  (6, 14.6% of 185)
dists/warty-backports/universe/binary-i386/Packages.gz
       20392 100%  258.62kB/s    0:00:00  (7, 33.0% of 185)
dists/warty-extras-staging/contrib/binary-i386/Packages.gz
          20 100%    0.23kB/s    0:00:00  (8, 94.1% of 185)
dists/warty-extras-staging/universe/binary-i386/Packages.gz
         317 100%    2.95kB/s    0:00:00  (9, 95.7% of 185)
dists/warty-extras/contrib/binary-i386/Packages.gz
          20 100%    0.17kB/s    0:00:00  (10, 97.8% of 185)
dists/warty-extras/universe/binary-i386/Packages.gz
          20 100%    0.16kB/s    0:00:00  (11, 99.5% of 185)

wrote 3439196 bytes  read 546 bytes  19488.62 bytes/sec
total size is 154567276  speedup is 44.94


```

**Known Issues**
None.

**Testing Status**
Functional For Me

**Marked For 12/22/2004 Promotion**

---

