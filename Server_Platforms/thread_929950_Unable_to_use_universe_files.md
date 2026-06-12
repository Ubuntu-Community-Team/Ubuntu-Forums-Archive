---
title: "Unable to use universe files"
date: 2008-09-25
forum: Server Platforms
---

### Post by bigbpdx on 2008-09-25
Hi, my first post here, glad to find this place! I've been trying to build an Ubuntu SIP server using Ubuntu 8.04, but running into a consistent problem. Even though I enabled the "universe" files, when I try to use/add any of them I get the response that none of them exist.... any thoughts? This includes trying to add a desktop (ubuntu-desktop)...  I did update the source list.

---

### Post by sisco311 on 2008-09-25
post the output of:
```
cat /etc/apt/sources.list
```
did you update your source.list?
```
sudo apt-get update
```

---

