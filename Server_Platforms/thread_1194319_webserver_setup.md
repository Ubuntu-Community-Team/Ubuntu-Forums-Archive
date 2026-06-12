---
title: "webserver setup"
date: 2009-06-22
forum: Server Platforms
---

### Post by sunflash2 on 2009-06-22
I am setting up a webserver to run off of my home internet connection with the 8.04 mini install disk.  All that i really want to be able to do with it is have it run Apache, and an ftp server, as well as an ssh server and maybe run webmin (with a firewall of course).  It only has a 7 GB hdd and is running a 300mHz processor, so should I just go with a cli and the server kernel or should I go all out and do the full server install?

edit:
i was also wondering what would be the best filesystem to use for the hdd since the computer is so old and only has 128MB of ram, i was thinking of using ext2 anyone know of one that would be better?

---

### Post by CP1256 on 2009-06-22
I'd go with nginx instead of Apache since it's far more light weight. I've also heard that the JFS filesystem is very light on the CPU.

---

### Post by mothes on 2009-06-29
For install nginx server, I used this how to

[http://www.linuxspace.org/archives/1576]("http://www.linuxspace.org/archives/1576")

---

