---
title: "TESTING Backport: gthumb 2.6.1"
date: 2005-01-07
forum: Ubuntu Backports
---

### Post by jdong on 2005-01-07
**Summary**
Requested by Alessio today.

**Backporting Process**
Took Hoary package + recompiled it.
It required Automake 1.9, but I forced it to use Warty's, and it appears to be fine.

**Upload Log**
```

building file list ...
233 files to consider
dists/warty-backports-staging/main/binary-i386/
dists/warty-backports-staging/main/binary-i386/Packages.gz
        2962 100%    0.00kB/s    0:00:00  (1, 3.0% of 233)
dists/warty-backports-staging/main/binary-i386/gthumb_2.6.1-3-4.10ubp1_i386.deb
     2354608 100%   24.50kB/s    0:01:33  (2, 6.9% of 233)
dists/warty-backports-staging/universe/binary-i386/Packages.gz
        3234 100%   80.98kB/s    0:00:00  (3, 9.4% of 233)
dists/warty-backports/main/binary-i386/Packages.gz
        7816 100%   89.80kB/s    0:00:00  (4, 18.5% of 233)
dists/warty-backports/universe/binary-i386/Packages.gz
       23940 100%  187.03kB/s    0:00:00  (5, 33.5% of 233)
dists/warty-extras-staging/contrib/binary-i386/Packages.gz
          20 100%    0.14kB/s    0:00:00  (6, 89.7% of 233)
dists/warty-extras-staging/universe/binary-i386/Packages.gz
         317 100%    2.00kB/s    0:00:00  (7, 91.0% of 233)
dists/warty-extras/contrib/binary-i386/Packages.gz
          20 100%    0.12kB/s    0:00:00  (8, 92.7% of 233)
dists/warty-extras/universe/binary-i386/Packages.gz
        2388 100%   11.38kB/s    0:00:00  (9, 94.0% of 233)


```

**Known Issues**
None

**Testing Status**
Undergoing testing *Appears to work for me.

---

### Post by arakno on 2005-01-08
It appears OK here too.

Too bad it still can't even remember my windows settings :(

I think I will still be using gqview for a while.

---

