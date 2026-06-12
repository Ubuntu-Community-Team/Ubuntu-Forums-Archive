---
title: "Mysql listening"
date: 2006-05-20
forum: Server Platforms
---

### Post by rensu on 2006-05-20
When Im grepping mysql port getting this:
netstat -an | grep 3306
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN

What does the 0.0.0.0 mean? Is it something wrong?:S

---

### Post by linuxone on 2006-05-20
[QUOTE=rensu]What does the 0.0.0.0 mean? Is it something wrong?:S[/QUOTE]

0.0.0.0 means "**all** addresses". Nothing is wrong. :)

Thomas

---

