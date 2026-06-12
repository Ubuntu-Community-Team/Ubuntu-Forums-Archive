---
title: "filesystem lots of small files"
date: 2010-02-15
forum: Server Platforms
---

### Post by korncola on 2010-02-15
Hi,

i have a question about the best choice for a filesystem:
We have in our company a productive webserver running debian with nginx webserver to serve images. The number is about 15 million, they are around 2kb or 3kb of size each and they are stored under some subdir in /home with a hashed subdirectory tree which is 2 leves deep. the images are copied with nfs from some other machine time to time. We get high load when this copying is running.
Currently we are using ext3, and considering moving to jfs, cause its relativly low load impact, but i am still courios about the performance.
 I think serving lots of images is often practiced thing, so i would be interested what others are using as filesystem in this scenario, or if someone could make a recommendation for our case.

Thanks in advice. :)

---

### Post by HermanAB on 2010-02-15
Yup, JFS would be the better choice.

---

