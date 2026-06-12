---
title: "TESTING Backport: Gimp 2.2.0 Final"
date: 2005-01-05
forum: Ubuntu Backports
---

### Post by jdong on 2005-01-05
**Summary**
This is a fresh request today.

**Backporting Process**
This package is unchanged from Hoary, just recompiled.
During the process, a dependency on python-dev 2.4 couldn't be satisfied because the latest version in Warty is 2.3.x.
However, after examining Gentoo's ebuild dependencies and after a successful configure script, I concluded that it was not required.

**Upload Log**
```

building file list ...
216 files to consider
dists/warty-backports-staging/main/binary-i386/
dists/warty-backports-staging/main/binary-i386/Packages.gz
        2635 100%    0.00kB/s    0:00:00  (1, 3.2% of 216)
dists/warty-backports-staging/main/binary-i386/gimp-data_2.2.0+rel-2ubuntu1-4.10ubp1_all.deb
     6065414 100%   24.34kB/s    0:04:03  (2, 4.2% of 216)
dists/warty-backports-staging/main/binary-i386/gimp-helpbrowser_2.2.0+rel-2ubuntu1-4.10ubp1_i386.deb
      209400 100%   24.33kB/s    0:00:08  (3, 4.6% of 216)
dists/warty-backports-staging/main/binary-i386/gimp-python_2.2.0+rel-2ubuntu1-4.10ubp1_i386.deb
      283894 100%   24.41kB/s    0:00:11  (4, 5.1% of 216)
dists/warty-backports-staging/main/binary-i386/gimp-svg_2.2.0+rel-2ubuntu1-4.10ubp1_i386.deb
      209866 100%   24.33kB/s    0:00:08  (5, 5.6% of 216)
dists/warty-backports-staging/main/binary-i386/gimp1.2_2.2.0+rel-2ubuntu1-4.10ubp1_all.deb
      197708 100%   24.30kB/s    0:00:07  (6, 6.0% of 216)
dists/warty-backports-staging/main/binary-i386/gimp_2.2.0+rel-2ubuntu1-4.10ubp1_i386.deb
     3323930 100%   24.59kB/s    0:02:12  (7, 6.5% of 216)
dists/warty-backports-staging/main/binary-i386/libgimp2.0-dev_2.2.0+rel-2ubuntu1-4.10ubp1_i386.deb
      264546 100%   24.25kB/s    0:00:10  (8, 6.9% of 216)
dists/warty-backports-staging/main/binary-i386/libgimp2.0-doc_2.2.0+rel-2ubuntu1-4.10ubp1_all.deb
      681660 100%   24.32kB/s    0:00:27  (9, 7.4% of 216)
dists/warty-backports-staging/main/binary-i386/libgimp2.0_2.2.0+rel-2ubuntu1-4.10ubp1_i386.deb
      688246 100%   24.53kB/s    0:00:27  (10, 7.9% of 216)
dists/warty-backports-staging/universe/binary-i386/Packages.gz
        6592 100%  160.94kB/s    0:00:00  (11, 9.7% of 216)
dists/warty-backports/main/binary-i386/Packages.gz
        7354 100%   69.05kB/s    0:00:00  (12, 20.8% of 216)
dists/warty-backports/universe/binary-i386/Packages.gz
       20392 100%  130.16kB/s    0:00:00  (13, 36.6% of 216)
dists/warty-extras-staging/contrib/binary-i386/Packages.gz
          20 100%    0.12kB/s    0:00:00  (14, 88.9% of 216)
dists/warty-extras-staging/universe/binary-i386/Packages.gz
        2531 100%   12.30kB/s    0:00:00  (15, 90.3% of 216)
dists/warty-extras/contrib/binary-i386/Packages.gz
          20 100%    0.09kB/s    0:00:00  (16, 98.1% of 216)
dists/warty-extras/universe/binary-i386/Packages.gz
          20 100%    0.09kB/s    0:00:00  (17, 99.5% of 216)

```

**Known Issues**
None

**Testing Status**
Undergoing Testing
*Please test that python-related features are working.

**NOT Marked for Promotion** Reason: NO testing.

P.S. I'm not much of a GIMP user. I just click stuff and watch cool things happen. Please test for me.

---

### Post by thepoch on 2005-01-06
Will test this the first chance I get. I'm not much of a Gimp user, but I was hoping for the improved copy+paste that I read about in their release notes.

Judging from your other releases, this would most probably be problem free.

Thanks!

dex

---

