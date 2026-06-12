---
title: "create repository for public access"
date: 2008-07-03
forum: Server Platforms
---

### Post by bigie on 2008-07-03
hi, I have plan for create repository server for my campus and I want my repository accesable for public. can anybody give some advice for create it please :D

---

### Post by dominiquec on 2008-07-03
[http://ubuntuforums.org/showthread.php?t=599479](http://ubuntuforums.org/showthread.php?t=599479)

---

### Post by promodus on 2008-07-03
1. apt-proxy is what I use.
Pro: Least amount of bandwidth used.
Con: Only downloads what is needed when it's needed. 

2. apt-mirror
[http://www.howtoforge.com/local_debian_ubuntu_mirror](http://www.howtoforge.com/local_debian_ubuntu_mirror)
Pro: More specific about what you mirror

3. You could also rsync a mirror and share it via apache.
Pro: Gets everything
Con: Space, Bandwidth, possibly overkill.

---

