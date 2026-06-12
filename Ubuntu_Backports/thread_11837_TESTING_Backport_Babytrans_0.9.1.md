---
title: "TESTING Backport: Babytrans 0.9.1"
date: 2005-01-19
forum: Ubuntu Backports
---

### Post by jdong on 2005-01-19
**Summary**
Requested by community


**Backporting Process**
Grabbed + Compiled from Hoary.

**Upload Log**
```

building file list ...
267 files to consider
dists/warty-backports-staging/main/binary-i386/Packages.gz
        1262 100%    0.00kB/s    0:00:00  (1, 2.6% of 267)
dists/warty-backports-staging/universe/binary-i386/
dists/warty-backports-staging/universe/binary-i386/Packages.gz
        5524 100%   19.62kB/s    0:00:00  (2, 5.6% of 267)
dists/warty-backports-staging/universe/binary-i386/babytrans_0.9.1-0.3-4.10ubp1_i386.deb
       54596 100%   21.72kB/s    0:00:02  (3, 6.4% of 267)
dists/warty-backports/main/binary-i386/Packages.gz
       10904 100%  280.22kB/s    0:00:00  (4, 19.1% of 267)
dists/warty-backports/universe/binary-i386/Packages.gz
       25759 100%  326.69kB/s    0:00:00  (5, 38.2% of 267)
dists/warty-extras-staging/contrib/binary-i386/Packages.gz
          20 100%    0.22kB/s    0:00:00  (6, 91.0% of 267)
dists/warty-extras-staging/universe/binary-i386/Packages.gz
         317 100%    2.89kB/s    0:00:00  (7, 92.1% of 267)
dists/warty-extras/contrib/binary-i386/Packages.gz
          20 100%    0.17kB/s    0:00:00  (8, 93.6% of 267)
dists/warty-extras/universe/binary-i386/Packages.gz
        2388 100%   15.14kB/s    0:00:00  (9, 94.8% of 267)

wrote 75953 bytes  read 620 bytes  2686.77 bytes/sec
total size is 233691641  speedup is 3051.88

```

**Known Issues**
None

**Testing Status**
Untested.

---

### Post by Alessio on 2005-01-20
Thank you but..
Dipendences problems..
 babytrans-common is not installable
E: Packet not integer
What?

---

### Post by Alessio on 2005-01-22
[QUOTE=Alessio]Thank you but..
Dipendences problems..
 babytrans-common is not installable
E: Packet not integer
What?[/QUOTE]
 :(

---

### Post by jdong on 2005-01-22
babytrans doesn't have a source package that builds babytrans-common... :(

---

