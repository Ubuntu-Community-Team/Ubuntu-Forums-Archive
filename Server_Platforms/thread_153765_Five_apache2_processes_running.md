---
title: "Five apache2 processes running?"
date: 2006-04-01
forum: Server Platforms
---

### Post by K.Mandla on 2006-04-01
Hi. I'm VERY new to Apache (and MySQL and PHP) -- I just got it installed today. I checked the system monitor once I got it going, and there are five processes, all named apache2 running at once. Is this normal? Or did I mess something up? Everything seems to be working fine, but I thought I should ask if that was a problem.

---

### Post by LordHunter317 on 2006-04-01
Yes, this is normal.  If you run with PHP a version of Apache known as 'prefork' is installed (for Apache 1.3 this is all there is).  It spawns one process per request to service.  Since spawning a process takes time, it keeps a pool of idle processes around to serve requests.

One should always size the pool to be at least the size of the expected number of concurrent connections, with a maximum based on expected burst periods.

---

### Post by K.Mandla on 2006-04-01
Cool, thanks. I was worried I had hosed something already. This is pretty cool stuff. I'm looking forward to it.

---

