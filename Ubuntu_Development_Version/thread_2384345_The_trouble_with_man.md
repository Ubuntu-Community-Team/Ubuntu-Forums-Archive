---
title: "The trouble with man"
date: 2018-02-06
forum: Ubuntu Development Version
---

### Post by zika on 2018-02-06
```
:~$ man man
man: command exited with status 4: /usr/lib/man-db/zsoelim | /usr/lib/man-db/manconv -f UTF-8:ISO-8859-1 -t UTF-8//IGNORE | preconv -e UTF-8 | tbl | nroff -mandoc -Tutf8
```
Update&#8321;: man-db 2.8.0-2 resolved the issue with man...```
man-db (2.8.0-2) unstable; urgency=medium

  * Build without seccomp for now, until I work out how to make it play well
    with AppArmor on recent kernels (closes: #889608, #889626).


 -- Colin Watson <cjwatson@debian.org>  Mon, 05 Feb 2018 10:09:57 +0000
```
Update&#8322;: Will not mark it &#8222;Solved&#8220; yet until this seccomp/AppArmor glitch gets resolved...

---

