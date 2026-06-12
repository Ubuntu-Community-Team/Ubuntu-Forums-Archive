---
title: "Unace 2"
date: 2005-12-01
forum: Repositories &amp; Backports
---

### Post by Bou on 2005-12-01
I noticed that unace 2.0 is not in the repositories, even though I have universe, multiverse, backports... ¿where can I find it?

---

### Post by Xian on 2005-12-01
The package version 1.2b-3 is in the Universe repos.
There is no other version in any Breezy source.

```
$ apt-cache policy unace
unace:
  Installed: (none)
  Candidate: 1.2b-3
  Version table:
     1.2b-3 0
        500 http://archive.ubuntu.com breezy/universe Packages
```

---

### Post by Bou on 2005-12-01
[QUOTE=Xian]The package version 1.2b-3 is in the Universe repos.
There is no other version in any Breezy source.

```
$ apt-cache policy unace
unace:
  Installed: (none)
  Candidate: 1.2b-3
  Version table:
     1.2b-3 0
        500 http://archive.ubuntu.com breezy/universe Packages
```[/QUOTE]

So, how can I uncompress .ace files that version 1.2b-3 can't handle?

---

### Post by z-vet on 2005-12-03
[http://www.winace.com/ftp/linunace25.tgz](http://www.winace.com/ftp/linunace25.tgz)

---

