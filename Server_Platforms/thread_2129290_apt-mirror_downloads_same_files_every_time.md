---
title: "apt-mirror downloads same files every time"
date: 2013-03-25
forum: Server Platforms
---

### Post by summersab on 2013-03-25
So, I'm not sure what I'm doing wrong. I followed the following guide pretty much to a T:
[http://www.packtpub.com/article/create-local-ubuntu-repository-using-apt-mirror-apt-cacher](http://www.packtpub.com/article/create-local-ubuntu-repository-using-apt-mirror-apt-cacher)

I built the local repository, and all was fine. Now, whenever I run apt-mirror to update, it downloads the same files every time as if it didn't save any of the files the first time I ran the update. Every time:

```
241.4 MiB will be downloaded into archive.
Downloading 24 archive files using 24 threads...
```

. . . etc etc - every time I run it, the same size, the same number of files. What on earth am I doing wrong?

---

