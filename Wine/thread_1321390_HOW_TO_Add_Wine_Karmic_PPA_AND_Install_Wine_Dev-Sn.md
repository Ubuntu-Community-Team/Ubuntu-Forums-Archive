---
title: "HOW TO: Add Wine Karmic PPA AND Install Wine Dev-Snapshot To Karmic Koala"
date: 2009-11-10
forum: Wine
---

### Post by coldReactive on 2009-11-10
1. Go into software sources like normal, add the GPG/PGP Key in authentication.

2. go to third-party software and add a new entry. Now, instead of a DEB line, we're going to add that fancy shmancy new ppa line where our old deb lines go: **ppa:ubuntu-wine/ppa** (put that as the deb line)

3. Reload the software/etc. Then **sudo apt-get install _*wine1.2*_**

Notice the 1.2? Yes? No? Well, you should! wine1.2 is the new devel-snapshot package rather than wine.

---

### Post by ThomasGHenry on 2009-11-18
```
E: wine1.2: subprocess installed post-installation script returned error exit status 1
```

s'not working for me so much... 



```
(Reading database ... 270896 files and directories currently installed.)
Preparing to replace chromium-browser 4.0.251.0~svn20091117r32171-0ubuntu1~ucd1~karmic (using .../chromium-browser_4.0.252.0~svn20091118r32323-0ubuntu1~ucd1~karmic_i386.deb) ...
Unpacking replacement chromium-browser ...
Selecting previously deselected package wine1.2.
Unpacking wine1.2 (from .../wine1.2_1.1.33-0ubuntu1~ppa1_i386.deb) ...
Preparing to replace wine-gecko 0.1.0-0ubuntu1 (using .../wine-gecko_1.1.33-0ubuntu1~ppa1_all.deb) ...
Unpacking replacement wine-gecko ...
Selecting previously deselected package wine1.2-gecko.
Unpacking wine1.2-gecko (from .../wine1.2-gecko_1.0.0-0ubuntu3_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Setting up chromium-browser (4.0.252.0~svn20091118r32323-0ubuntu1~ucd1~karmic) ...

Setting up wine1.2 (1.1.33-0ubuntu1~ppa1) ...
start: Job failed to start
dpkg: error processing wine1.2 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up wine1.2-gecko (1.0.0-0ubuntu3) ...
Setting up wine-gecko (1.1.33-0ubuntu1~ppa1) ...
Errors were encountered while processing:
 wine1.2
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up wine1.2 (1.1.33-0ubuntu1~ppa1) ...
start: Job failed to start
dpkg: error processing wine1.2 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 wine1.2

```

---

