---
title: "TESTING Backport: mozilla-thunderbird 1.0-0ubuntu1-4.10ubp1"
date: 2005-01-11
forum: Ubuntu Backports
---

### Post by jdong on 2005-01-11
**Summary**
This is the ubuntu-ized Thunderbird, freshly uploaded to Hoary. Recall the original backport for 1.0 was just 1.0 official sources with 0.9.x Debian Sid patches. This package should be of a higher quality.


**Backporting Process**
Grabbed + Compiled from Hoary

**Upload Log**
```
building file list ...
239 files to consider
dists/warty-backports-staging/main/binary-i386/
dists/warty-backports-staging/main/binary-i386/Packages.gz
        3878 100%  806.64kB/s    0:00:00  (1, 2.9% of 239)
dists/warty-backports-staging/main/binary-i386/mozilla-thunderbird-dev_1.0-0ubuntu1-4.10ubp1_i386.deb
     3561090 100%   24.35kB/s    0:02:22  (2, 8.4% of 239)
dists/warty-backports-staging/main/binary-i386/mozilla-thunderbird-inspector_1.0-0ubuntu1-4.10ubp1_i386.deb
      138366 100%   24.37kB/s    0:00:05  (3, 8.8% of 239)
dists/warty-backports-staging/main/binary-i386/mozilla-thunderbird-offline_1.0-0ubuntu1-4.10ubp1_i386.deb
       25252 100%   24.34kB/s    0:00:01  (4, 9.2% of 239)
dists/warty-backports-staging/main/binary-i386/mozilla-thunderbird-typeaheadfind_1.0-0ubuntu1-4.10ubp1_i386.deb
       78946 100%   18.05kB/s    0:00:02  (5, 9.6% of 239)
dists/warty-backports-staging/main/binary-i386/mozilla-thunderbird_1.0-0ubuntu1-4.10ubp1_i386.deb
    11535414 100%   24.63kB/s    0:07:37  (6, 10.0% of 239)
dists/warty-backports-staging/universe/binary-i386/Packages.gz
        3529 100%   88.37kB/s    0:00:00  (7, 11.3% of 239)
dists/warty-backports/main/binary-i386/Packages.gz
        7816 100%   96.62kB/s    0:00:00  (8, 20.5% of 239)
dists/warty-backports/universe/binary-i386/Packages.gz
       23940 100%  187.03kB/s    0:00:00  (9, 35.1% of 239)
dists/warty-extras-staging/contrib/binary-i386/Packages.gz
          20 100%    0.14kB/s    0:00:00  (10, 90.0% of 239)
dists/warty-extras-staging/universe/binary-i386/Packages.gz
         317 100%    2.00kB/s    0:00:00  (11, 91.2% of 239)
dists/warty-extras/contrib/binary-i386/Packages.gz
          20 100%    0.12kB/s    0:00:00  (12, 92.9% of 239)
dists/warty-extras/universe/binary-i386/Packages.gz
        2388 100%   11.43kB/s    0:00:00  (13, 94.1% of 239)

wrote 15214708 bytes  read 676 bytes  21908.40 bytes/sec
total size is 197038509  speedup is 12.95



```

**Known Issues**
[COLOR=SlateGray]I haven't recompiled the enigmail plugin -- The version in Hoary doesn't compile against 1.0. I **THINK** that the enigmail plugin from the previous Thunderbird backport will work fine.[/COLOR] **UPDATE: It works fine**

**Testing Status**
Fully functional for me.

**HELD against promotion**. I'd like to give this guy a bit more time.

---

