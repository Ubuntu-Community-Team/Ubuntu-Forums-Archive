---
title: "TESTING Backport: wine 20050111-1"
date: 2005-01-12
forum: Ubuntu Backports
---

### Post by jdong on 2005-01-12
**Summary**
New upstream release. The new WINE .deb maintainer is WONDERFUL at response times!

**Backporting Process**
Grabbed official WineHQ Ubuntu packages, recompiled.

**Upload Log**
```

building file list ...
252 files to consider
dists/warty-backports-staging/main/binary-i386/Packages.gz
        3878 100%  806.64kB/s    0:00:00  (1, 2.8% of 252)
dists/warty-backports-staging/universe/binary-i386/
dists/warty-backports-staging/universe/binary-i386/Packages.gz
        6012 100%   19.38kB/s    0:00:00  (2, 10.7% of 252)
dists/warty-backports-staging/universe/binary-i386/libwine-dev_0.0.20050111-1-4.10ubp1_i386.deb
     1041668 100%   24.15kB/s    0:00:42  (3, 18.3% of 252)
dists/warty-backports-staging/universe/binary-i386/libwine_0.0.20050111-1-4.10ubp1_i386.deb
     1041682 100%   24.33kB/s    0:00:41  (4, 18.7% of 252)
dists/warty-backports-staging/universe/binary-i386/wine-dev_0.0.20050111-1-4.10ubp1_i386.deb
     2245392 100%   24.34kB/s    0:01:30  (5, 22.6% of 252)
dists/warty-backports-staging/universe/binary-i386/wine_0.0.20050111-1-4.10ubp1_i386.deb
    13911416 100%   24.79kB/s    0:09:07  (6, 23.0% of 252)
dists/warty-backports/main/binary-i386/Packages.gz
        7816 100%  149.66kB/s    0:00:00  (7, 24.6% of 252)
dists/warty-backports/universe/binary-i386/Packages.gz
       23940 100%  220.56kB/s    0:00:00  (8, 38.5% of 252)
dists/warty-extras-staging/contrib/binary-i386/Packages.gz
          20 100%    0.13kB/s    0:00:00  (9, 90.5% of 252)
dists/warty-extras-staging/universe/binary-i386/Packages.gz
         317 100%    1.72kB/s    0:00:00  (10, 91.7% of 252)
dists/warty-extras/contrib/binary-i386/Packages.gz
          20 100%    0.09kB/s    0:00:00  (11, 93.3% of 252)
dists/warty-extras/universe/binary-i386/Packages.gz
        2388 100%    9.11kB/s    0:00:00  (12, 94.4% of 252)

wrote 18006744 bytes  read 668 bytes  24684.59 bytes/sec
total size is 215788646  speedup is 11.98


```

**Known Issues**
None

**Testing Status**
Working. Marked for UBP Promotions #4.

---

### Post by wallijonn on 2005-01-12
What did you define "section": as?

I wasn't that easy to install. I had to [COLOR=Red]sudo gedit /etc/apt/sources.list[/COLOR] and two kick starts.

---

### Post by jdong on 2005-01-12
This is in Warty-backports-staging.

At the time, I probably was in the middle of uploading. (i.e. Permission Denied errors, missing files, etc).

I can't think of a better way of updating, short of doing "double-buffering" of the entire APT tree. Boy, would SourceForge be PLEASED that I'm constantly copying and removing ~300MB of 1MB files on their project web services!

---

