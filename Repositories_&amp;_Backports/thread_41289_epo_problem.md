---
title: "epo problem"
date: 2005-06-12
forum: Repositories &amp; Backports
---

### Post by Poul on 2005-06-12
For about a week or so I've been getting this error while refreshing repos:
```
ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/Packages.gz: MD5Sum mismatch

```
And this after clicking ok:
```
W: Couldn't stat source package list ftp://ftp.nerim.net stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)

```

---

### Post by Xian on 2005-06-12
There's a checksum issue at present with the ftp.nerim.net repos. I'd advise that you comment those out in your /etc/apt/sources.list until such time as they are resolved. It's not a local issue so there is no fix for it on your system.

---

