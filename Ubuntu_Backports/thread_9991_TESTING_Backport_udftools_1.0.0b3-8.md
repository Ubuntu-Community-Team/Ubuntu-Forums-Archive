---
title: "TESTING Backport: udftools 1.0.0b3-8"
date: 2005-01-03
forum: Ubuntu Backports
---

### Post by jdong on 2005-01-03
**Summary**
UDF is the disk format used on DVD's and packet-written CD's. This package provides necessary support for interfacing with the pktcdvd kernel patch, and providing native DVD+RW UDF support, along with using UDF on any other filesystem.

This updated version from Hoary includes a lot of Debian script bugfixes. I backported it because I was seriously ticked trying to write a UDF DVD+RW.


**Backporting Process**
This package is unchanged from Hoary, just recompiled.

**Upload Log**
```

building file list ...
207 files to consider
dists/warty-backports-staging/main/binary-i386/Packages.gz
         891 100%    0.00kB/s    0:00:00  (1, 3.4% of 207)
dists/warty-backports-staging/universe/binary-i386/
dists/warty-backports-staging/universe/binary-i386/Packages.gz
        6592 100%   36.17kB/s    0:00:00  (2, 5.8% of 207)
dists/warty-backports-staging/universe/binary-i386/udftools_1.0.0b3-8-4.10ubp1_i386.deb
       77030 100%   22.82kB/s    0:00:03  (3, 15.5% of 207)
dists/warty-backports/main/binary-i386/Packages.gz
        7354 100%  110.49kB/s    0:00:00  (4, 17.4% of 207)
dists/warty-backports/universe/binary-i386/Packages.gz
       20392 100%  130.16kB/s    0:00:00  (5, 33.8% of 207)
dists/warty-extras-staging/contrib/binary-i386/Packages.gz
          20 100%    0.10kB/s    0:00:00  (6, 88.4% of 207)
dists/warty-extras-staging/universe/binary-i386/Packages.gz
        2531 100%    8.02kB/s    0:00:00  (7, 89.9% of 207)
dists/warty-extras/contrib/binary-i386/Packages.gz
          20 100%    0.05kB/s    0:00:00  (8, 98.1% of 207)
dists/warty-extras/universe/binary-i386/Packages.gz
          20 100%    0.05kB/s    0:00:00  (9, 99.5% of 207)

wrote 92308 bytes  read 554 bytes  4319.16 bytes/sec
total size is 165450289  speedup is 1781.68

```

**Known Issues**
None

**Testing Status**
Undergoing Testing

**NOT Marked for Promotion** Reason: Minimal Testing

---

### Post by Averatec5400 on 2005-01-04
THANK YOU THANK YOU!!!

I have been needing this, and didn't even initially know it. :)

---

