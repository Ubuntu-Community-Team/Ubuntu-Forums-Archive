---
title: "Samba backport (3.0.14a-3ubuntu3~5.04ubp1) is buggy"
date: 2005-06-20
forum: Ubuntu Backports
---

### Post by infinito on 2005-06-20
The version of samba that was bacported has ha serious bug on smbclient that makes browsing win98/me shares imposible. This is the error you get browsing using smbclient, related with the "cd" command:```
ERRDOS - ERRbadfunc (Invalid function.)
```
You can read the Debian bug report here [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=307535](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=307535)

---

### Post by jdong on 2005-06-20
heh... it fixes several win2k domain issues... and breaks 98 compatibility. Argh, can't ever satisfy everyone..


Does 4ubuntu1 solve this? Is there any closure on the bug?

---

### Post by jdong on 2005-06-20
I'm assuming that since -4 was the Sarge revision, that wouldn't be buggy, right?

---

### Post by infinito on 2005-06-20
[QUOTE=jdong]I'm assuming that since -4 was the Sarge revision, that wouldn't be buggy, right?[/QUOTE]
 I'm using official Hoary version (3.0.10-1ubuntu3), and works ok with win98/me shares.

---

