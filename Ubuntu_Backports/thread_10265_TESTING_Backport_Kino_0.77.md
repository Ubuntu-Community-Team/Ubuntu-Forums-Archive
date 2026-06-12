---
title: "TESTING Backport: Kino 0.77"
date: 2005-01-06
forum: Ubuntu Backports
---

### Post by jdong on 2005-01-06
**Summary**
Kino is a multi-purpose video editor, especially for DV.

I am gonna be editing & DVD'ing some home video for archiving, so I thought we might all appreciate a new Kino.

**Backporting Process**
Grabbed from Hoary and recompiled.

**Upload Log**

Kino:
```

building file list ...
219 files to consider
dists/warty-backports-staging/main/binary-i386/Packages.gz
        2508 100%  360.68kB/s    0:00:00  (1, 3.2% of 219)
dists/warty-backports-staging/universe/binary-i386/
dists/warty-backports-staging/universe/binary-i386/Packages.gz
        1747 100%   13.87kB/s    0:00:00  (2, 9.6% of 219)
dists/warty-backports-staging/universe/binary-i386/kino_0.75-2-4.10ubp1_i386.deb      824146 100%   24.33kB/s    0:00:33  (3, 10.5% of 219)
dists/warty-backports/main/binary-i386/Packages.gz
        7816 100%  195.71kB/s    0:00:00  (4, 13.2% of 219)
dists/warty-backports/universe/binary-i386/Packages.gz
       23940 100%  295.94kB/s    0:00:00  (5, 29.2% of 219)
dists/warty-extras-staging/contrib/binary-i386/Packages.gz
          20 100%    0.22kB/s    0:00:00  (6, 89.0% of 219)
dists/warty-extras-staging/universe/binary-i386/Packages.gz
         317 100%    2.84kB/s    0:00:00  (7, 90.4% of 219)
dists/warty-extras/contrib/binary-i386/Packages.gz
          20 100%    0.17kB/s    0:00:00  (8, 92.2% of 219)
dists/warty-extras/universe/binary-i386/Packages.gz
        2388 100%   14.85kB/s    0:00:00  (9, 93.6% of 219)

wrote 836949 bytes  read 560 bytes  21202.76 bytes/sec
total size is 178745801  speedup is 213.43


```

Kinoplus:
```

building file list ...
220 files to consider
dists/warty-backports-staging/main/binary-i386/Packages.gz
        2508 100%  360.68kB/s    0:00:00  (1, 3.2% of 220)
dists/warty-backports-staging/universe/binary-i386/
dists/warty-backports-staging/universe/binary-i386/Packages.gz
        2032 100%   14.07kB/s    0:00:00  (2, 9.5% of 220)
dists/warty-backports-staging/universe/binary-i386/kinoplus_0.3.3-3-4.10ubp1_i386.deb
       84708 100%   23.55kB/s    0:00:03  (3, 10.9% of 220)
dists/warty-backports/main/binary-i386/Packages.gz
        7816 100%  165.93kB/s    0:00:00  (4, 13.6% of 220)
dists/warty-backports/universe/binary-i386/Packages.gz
       23940 100%  254.12kB/s    0:00:00  (5, 29.5% of 220)
dists/warty-extras-staging/contrib/binary-i386/Packages.gz
          20 100%    0.18kB/s    0:00:00  (6, 89.1% of 220)
dists/warty-extras-staging/universe/binary-i386/Packages.gz
         317 100%    2.15kB/s    0:00:00  (7, 90.5% of 220)
dists/warty-extras/contrib/binary-i386/Packages.gz
          20 100%    0.12kB/s    0:00:00  (8, 92.3% of 220)
dists/warty-extras/universe/binary-i386/Packages.gz
        2388 100%   10.80kB/s    0:00:00  (9, 93.6% of 220)

wrote 99554 bytes  read 566 bytes  8706.09 bytes/sec
total size is 178830794  speedup is 1786.16


```

kino-timfx
```

dists/warty-backports-staging/main/binary-i386/Packages.gz
        2508 100%  360.68kB/s    0:00:00  (1, 3.2% of 221)
dists/warty-backports-staging/universe/binary-i386/
dists/warty-backports-staging/universe/binary-i386/Packages.gz
        2250 100%   14.65kB/s    0:00:00  (2, 9.5% of 221)
dists/warty-backports-staging/universe/binary-i386/kino-timfx_0.2.2-2-4.10ubp1_i386.deb
       59692 100%   23.04kB/s    0:00:02  (3, 10.4% of 221)
dists/warty-backports/main/binary-i386/Packages.gz
        7816 100%  169.62kB/s    0:00:00  (4, 14.0% of 221)
dists/warty-backports/universe/binary-i386/Packages.gz
       23940 100%  254.12kB/s    0:00:00  (5, 29.9% of 221)
dists/warty-extras-staging/contrib/binary-i386/Packages.gz
          20 100%    0.18kB/s    0:00:00  (6, 89.1% of 221)
dists/warty-extras-staging/universe/binary-i386/Packages.gz
         317 100%    2.15kB/s    0:00:00  (7, 90.5% of 221)
dists/warty-extras/contrib/binary-i386/Packages.gz
          20 100%    0.12kB/s    0:00:00  (8, 92.3% of 221)
dists/warty-extras/universe/binary-i386/Packages.gz
        2388 100%   10.75kB/s    0:00:00  (9, 93.7% of 221)

wrote 75093 bytes  read 566 bytes  7205.62 bytes/sec
total size is 178890704  speedup is 2364.43


```

**Known Issues**
None

**Testing Status**
Undergoing Testing

**NOT Marked for Promotion** Reason: NO testing.

---

### Post by jdong on 2005-01-06
Supporting packages (Kino+, kino-dvtitler, etc) are currently being built. This announcement will be edited to show these updates.

---

### Post by jdong on 2005-01-06
All done.

---

