---
title: "Help in System()"
date: 2010-03-16
forum: Ubuntu Dev Link Forum
---

### Post by Baraa Mahrouka on 2010-03-16
hey,

as we all know the system command in C returns and integer,
I'm just trying to get the result of the system command as a string,
i.e.
this command: 
system("ifconfig -s | grep eth | awk {'$12'});
gives me the status of eth0 if its BMRU or BMU so I want to take this result (BMRU or BMU)
as a string ...

any help ?

---

### Post by n0dix on 2010-03-16
Instead of use system() try with popen().
See [this]("http://www-user.tu-chemnitz.de/~anhe/DOCU/C/C/////////FUNCTIONS/popen.html").

---

### Post by roccivic on 2010-03-20
or even:
```
system("ifconfig -s | grep eth | awk {'$12'} > /tmp/nettest.tmp");
```
then read /tmp/nettest.tmp

---

