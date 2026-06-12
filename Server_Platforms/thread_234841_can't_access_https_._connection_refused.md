---
title: "can't access https . connection refused"
date: 2006-08-12
forum: Server Platforms
---

### Post by careca on 2006-08-12
Hi,
I have apache-perl installed. I can access [http://localhost](http://localhost), but i get:

the connection was refused when attempting to contact localhost

when I try [https://localhost](https://localhost). (Note: httpS)

I'm new to apache, and I need to access trought https because I installed CMU NetReg, that access this way.

Thanks.

---

### Post by davham on 2006-08-12
I believe you have to open port 443 on your router to get https working

David

---

### Post by careca on 2006-08-12
My router?...

I don't have a router... i'm trying to access localhost.. on my computer

---

### Post by davham on 2006-08-12
Sorry
Then try opening port 443 in the firewall on that computer

---

### Post by davham on 2006-08-12
Have a look at this post. I think it covers what your looking for

[http://www.ubuntuforums.org/archive/index.php/t-4466.html](http://www.ubuntuforums.org/archive/index.php/t-4466.html)

---

