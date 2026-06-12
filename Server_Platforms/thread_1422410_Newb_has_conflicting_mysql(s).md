---
title: "Newb has conflicting mysql(s)"
date: 2010-03-05
forum: Server Platforms
---

### Post by woodsonoversoul on 2010-03-05
Hello all,
    I've been working with a database using xampp for a while now; until recently, when I had to take a break. During that break I began working with rails for the first time. I believe that during my rails setup I installed another version of mysql. When I run:
```
sudo /opt/lampp/lampp start
```
to begin working with my xampp database, I get:
```
Starting XAMPP for Linux 1.6.8a...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Another MySQL daemon is already running.
XAMPP: Starting ProFTPD...
XAMPP for Linux started.

```

How can I access my old database?

fwiw I setup rails using netbeans

---

### Post by woodsonoversoul on 2010-03-05
Solved.

sudo mysqladmin shutdown

then restart xampp

---

### Post by cdenley on 2010-03-05
I would suggest you stick to the ubuntu software repositories in the future to avoid these conflicts and to ensure your software is secure and stable.

---

