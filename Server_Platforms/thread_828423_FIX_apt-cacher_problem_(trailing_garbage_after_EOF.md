---
title: "FIX: apt-cacher problem (trailing garbage after EOF ignored)"
date: 2008-06-13
forum: Server Platforms
---

### Post by chrismyers on 2008-06-13
Hi Guys,

Since Ubuntu Hardy, I had a problem with apt-cacher.

when I did apt-get update I got variations of:

Get: 47 [http://192.168.x.x](http://192.168.x.x) hardy-security/multiverse Packages [3571B]                                                                          
99% [47 Packages bzip2 0] [Waiting for headers]                                                                                       13.8kB/s 0s
bzip2: (stdin): trailing garbage after EOF ignored


Instead of modifying your sources.list, do:

sudo nano /etc/apt/apt.conf

now paste:

Acquire::http::Proxy "http://192.168.x.x:3142/apt-cacher/";

Replace 192.168.x.x with your servers IP & save.

This should now work.

Cheers.

---

