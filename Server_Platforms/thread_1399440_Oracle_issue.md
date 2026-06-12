---
title: "Oracle issue"
date: 2010-02-05
forum: Server Platforms
---

### Post by AmirHp on 2010-02-05
I just installed the Ubuntu 9.10 and then installed Oracle 10 Express and all went fine. I can access oracle on 127.0.0.1:8080/apex address however when I try to access the server on it's external ip address (192.168.1.14) even when I'm on my Ubuntu machine it's failing.
I'm new to Linux so I'm sure this should be silly and simple issue but I can't find a way around it. I need this so I can access the oracle server from outside world (other nodes on the network)
Any help is appreciated.

Amir

---

### Post by Waappu on 2010-02-07
Hi,

Login to SQLplus as SYS and run
```

EXEC DBMS_XDB.SETLISTENERLOCALACCESS(FALSE);

```
[http://www.oracle.com/technology/software/products/database/xe/files/install.102/b25144/toc.htm#BABIJBHJ](http://www.oracle.com/technology/software/products/database/xe/files/install.102/b25144/toc.htm#BABIJBHJ)
[http://www.debian-administration.org/articles/430](http://www.debian-administration.org/articles/430)



Beware security risk if you expose your XE to internet
Good to read
[http://www.red-database-security.com/wp/hacking_and_hardening_oracle_XE.pdf](http://www.red-database-security.com/wp/hacking_and_hardening_oracle_XE.pdf)

---

