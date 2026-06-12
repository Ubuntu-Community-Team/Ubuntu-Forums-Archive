---
title: "apt-get sources issue"
date: 2009-02-17
forum: Server Platforms
---

### Post by stonneway on 2009-02-17
Hi chaps,

I've done an apt-get update on an old ubuntu 7.04 box and the all the sources come back with a 404 error. IS there somewhere I can find reliable up to date 7.04 sources to replace the ones I currently have ?

Olly

---

### Post by songshu on 2009-02-17
[https://wiki.ubuntu.com/Mirrors](https://wiki.ubuntu.com/Mirrors)

---

### Post by tubezninja on 2009-02-17
7.04 is more than 18 months old, and because it's not an LTS release, Ubuntu has stopped providing updates for it. This is likely why your apt-get sources are coming up 404.

You should consider [upgrading]("http://www.ubuntu.com/getubuntu/upgrading-8.04").  8.04 is an LTS release and will give you support on the server edition until April, 2013.

---

