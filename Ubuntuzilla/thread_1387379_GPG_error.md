---
title: "GPG error"
date: 2010-01-21
forum: Ubuntuzilla
---

### Post by kansasnoob on 2010-01-21
I noticed this earlier today in Lucid but got busy. Now I'm modifying my chroot script and mounted Karmic:

```
W: GPG error: http://downloads.sourceforge.net all Release: The following signatures were invalid: BADSIG CCC158AFC1289A29 Daniel Folkinshteyn (Ubuntuzilla signing key) <nanotube@users.sourceforge.net>

```

BTW the update to FF 3.6 continues fine anyway:

```
Install these packages without verification [y/N]? y

```

---

### Post by nanotube on 2010-01-21
this may happen if you catch the update very shortly after i push it out to the servers. since sourceforge has a network of mirrors, it takes a few minutes for all the files to synchronize. if you just wait a couple of minutes and sudo apt-get update again, the gpg error should go away.

---

