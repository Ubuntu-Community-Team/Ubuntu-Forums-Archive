---
title: "BIND restart"
date: 2009-08-14
forum: Server Platforms
---

### Post by dmalcomd on 2009-08-14
I was wondering about BIND daemon on production servers...
It needs to restart BIND daemon every time a line (some lines) is (are) added to a zone? Is it the only way or is there a "peaceful" restart? :confused:

---

### Post by alastair on 2009-08-14
Maybe : rndc reload

---

### Post by Bachstelze on 2009-08-14
Maybe:

```
firas@iori ~ % sudo /etc/init.d/bind9 reload
Reloading domain name service...: bind9.

```

---

### Post by dmalcomd on 2009-08-14
thank you so much!

---

