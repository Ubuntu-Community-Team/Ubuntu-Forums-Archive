---
title: "TESTING BACKPORT: mozilla-thunderbird 1.0-0ubuntu0-4.10ubp1"
date: 2004-12-18
forum: Ubuntu Backports
---

### Post by jdong on 2004-12-18
**Summary**
This was quite a popular request, so I decided not to wait for Ubuntu/Debian Sid people and backport it from source.


**Backporting Process**
I took the official Thunderbird 1.0 source, and applied the Ubuntu 0.9-6 diff.gz to it.
*Note: One patch didn't cleanly apply -- the custom Debian startpage, with the Debian advertising. It wasn't important, so I just ommitted it.

**Upload Log**
```

building file list ...
182 files to consider
dists/warty-backports-staging/main/binary-i386/Packages.gz
          20 100%    0.00kB/s    0:00:00  (1, 3.8% of 182)
dists/warty-backports-staging/universe/binary-i386/
dists/warty-backports-staging/universe/binary-i386/Packages.gz
        3004 100%   15.44kB/s    0:00:00  (2, 6.0% of 182)
dists/warty-backports-staging/universe/binary-i386/mozilla-thunderbird-dev_1.0-0ubuntu0-4.10ubp1_i386.deb
     3350392 100%   24.27kB/s    0:02:14  (3, 7.7% of 182)
dists/warty-backports-staging/universe/binary-i386/mozilla-thunderbird-inspector_1.0-0ubuntu0-4.10ubp1_i386.deb
      138182 100%   24.41kB/s    0:00:05  (4, 8.2% of 182)
dists/warty-backports-staging/universe/binary-i386/mozilla-thunderbird-offline_1.0-0ubuntu0-4.10ubp1_i386.deb
       25318 100%   24.26kB/s    0:00:01  (5, 8.8% of 182)
dists/warty-backports-staging/universe/binary-i386/mozilla-thunderbird-typeaheadfind_1.0-0ubuntu0-4.10ubp1_i386.deb
       78672 100%   18.02kB/s    0:00:02  (6, 9.3% of 182)
dists/warty-backports-staging/universe/binary-i386/mozilla-thunderbird_1.0-0ubuntu0-4.10ubp1_i386.deb
    11457252 100%   24.62kB/s    0:07:34  (7, 9.9% of 182)
dists/warty-backports/main/binary-i386/Packages.gz
        7354 100%  123.82kB/s    0:00:00  (8, 13.2% of 182)
dists/warty-backports/universe/binary-i386/Packages.gz
       20392 100%  203.20kB/s    0:00:00  (9, 31.9% of 182)
dists/warty-extras-staging/contrib/binary-i386/Packages.gz
          20 100%    0.18kB/s    0:00:00  (10, 94.0% of 182)
dists/warty-extras-staging/universe/binary-i386/Packages.gz
         317 100%    2.40kB/s    0:00:00  (11, 95.6% of 182)
dists/warty-extras/contrib/binary-i386/Packages.gz
          20 100%    0.14kB/s    0:00:00  (12, 97.8% of 182)
dists/warty-extras/universe/binary-i386/Packages.gz
          20 100%    0.13kB/s    0:00:00  (13, 99.5% of 182)

wrote 14920637 bytes  read 574 bytes  24683.56 bytes/sec
total size is 151111228  speedup is 10.13


```

**Known Issues**
FIXED: *Enigmail plugin currently won't work due to version conflict. I will be uploading updated enigmail packages soon.*

**Testing Status**
Fully Functional for me.

**PROMOTED**

---

### Post by HiddenWolf on 2004-12-30
What's the news on the TB backport?

---

### Post by atom on 2005-01-02
[QUOTE=jdong]
**Testing Status**
Fully Functional for me.

**Marked For 12/22/2004 Promotion**[/QUOTE]


fully functional here as well.

---

### Post by aerials on 2005-01-03
Works very well for me, even my custom user.js that I wrote for TB 1.0 under Windows and which didn't work with the 0.8x version :)

---

### Post by ZakZak on 2005-01-03
Just a quick post from another user who is anxiously awaiting ThunderBird 1.0 promotion from backports testing to backports stable!

---

### Post by jdong on 2005-01-03
Promotion will occur with the next issue of UBP weekly news, probably this friday.

---

### Post by HiddenWolf on 2005-01-06
[QUOTE=jdong]Promotion will occur with the next issue of UBP weekly news, probably this friday.[/QUOTE]
Good news!

---

### Post by jdong on 2005-01-06
It's been promoted with today's issue of UBP Weekly.

---

### Post by ZakZak on 2005-01-06
[QUOTE=jdong]It's been promoted with today's issue of UBP Weekly.[/QUOTE]
 Thanks, jdong!

-Zak

---

### Post by HiddenWolf on 2005-01-06
[QUOTE=jdong]It's been promoted with today's issue of UBP Weekly.[/QUOTE]
 Yihaa!

---

### Post by thtde on 2005-01-08
The language packs are missing (also for Firefox).

---

### Post by HiddenWolf on 2005-01-11
Thunderbird just went into hoary. :-)

---

### Post by jdong on 2005-01-11
Okey, I'll package it.

---

