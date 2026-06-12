---
title: "[SOLVED] Quick question about encrypting Ubuntu"
date: 2007-09-17
forum: Server Platforms
---

### Post by slughappy1 on 2007-09-17
So I followed the how to guide at [http://news.softpedia.com/news/Encrypted-Ubuntu-7-04-61312.shtml](http://news.softpedia.com/news/Encrypted-Ubuntu-7-04-61312.shtml) and everything seemed to be going fine. Until I got to step 3 when it says to input to terminal: umount root. I got an error saying there was not enough space, but when I continued through the how to it seemed to work. But now that I am at step 4 , the apt-get part, I get an error: apt-get: error while loading shared libraries: /usr/lib/libapt-pkg-libc6.4-6.so.3.53: file too short. What's up with those?

---

### Post by kidders on 2007-09-18
Hi there,

Are you out of disk space? That would explain "I got an error saying there was not enough space" and "/usr/lib/libapt-pkg-libc6.4-6.so.3.53: file too short".

Incidentally, I took a look at the URL you mentioned. The "umount" command is essential. _Do not_ try to skip it.

---

