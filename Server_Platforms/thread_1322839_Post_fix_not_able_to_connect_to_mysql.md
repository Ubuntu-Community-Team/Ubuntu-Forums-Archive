---
title: "Post fix not able to connect to mysql"
date: 2009-11-11
forum: Server Platforms
---

### Post by ninnypants on 2009-11-11
I am configuring postfix and courier on 8.4 following the instructions here [http://www.howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10](http://www.howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10) but I keep getting this error in my mail.log file
```
Nov 10 21:43:08 Directories postfix/trivial-rewrite[12406]: warning: connect to  mysql server localhost: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
```

I'm not sure why postfix can't connect to mysql when handling mail; because if I use postmap I can get results back.

---

