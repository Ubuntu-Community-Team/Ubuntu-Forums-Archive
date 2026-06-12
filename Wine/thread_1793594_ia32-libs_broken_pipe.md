---
title: "ia32-libs broken pipe"
date: 2011-06-29
forum: Wine
---

### Post by Starmartyr on 2011-06-29
I am getting no where so far on trying to figure out why I cannot install the newer ia32-libs.  This is my error:

```
The following packages will be upgraded:
  ia32-libs
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/59.5MB of archives.
After this operation, 9,314kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 194863 files and directories currently installed.)
Preparing to replace ia32-libs 20090808ubuntu10~wineppa4 (using .../ia32-libs_20090808ubuntu10+maverick~xorgedgers0.20110325.1_amd64.deb) ...
Unpacking replacement ia32-libs ...
dpkg: error processing /var/cache/apt/archives/ia32-libs_20090808ubuntu10+maverick~xorgedgers0.20110325.1_amd64.deb (--unpack):
 trying to overwrite '/lib32/libncursesw.so.5.7', which is also in package lib32ncursesw5 5.7+20100626-0ubuntu1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/ia32-libs_20090808ubuntu10+maverick~xorgedgers0.20110325.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any ideas?  

Maverick 10.10
Installed latest nVidia driver 275...

Fixed: I had to delete my PPA for xorgedgers, then ran an update and it successfully pulled the correct file to update.  It still pulled from xorgedgers, so not sure what really was going on.  But, solved.

---

