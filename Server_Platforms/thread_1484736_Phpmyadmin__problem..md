---
title: "Phpmyadmin  problem."
date: 2010-05-16
forum: Server Platforms
---

### Post by gurukatre on 2010-05-16
> **n0dix said:**
> Do you start the daemons of Apache2, Mysql, etc. ?


hi i got the solution:guitar: i was wondering from last 3 month to resolve this problem 

the problem is  :-


#2002 - The server is not responding (or the local MySQL server's socket  is not correctly configured)


Connection for controluser as defined in your configuration failed.

---

### Post by gurukatre on 2010-05-16
> **gurukatre said:**
> hi i got the solution:guitar: i was wondering from last 3 month to resolve this problem  :popcorn:

the problem is  :-


#2002 - The server is not responding (or the local MySQL server's socket  is not correctly configured)


Connection for controluser as defined in your configuration failed.


Solution is :-


go to the ubuntu terminal

Applications->accessories->Terminal

type the following command

**gksudo gedit /etc/mysql/my.cnf**

and comment the following line

bind-address        = your ip
like:-

bind-address        = 10.24.44.180

to

#bind-address        = 10.24.44.180


:)

---

### Post by cariboo on 2010-05-16
Moved to it's own thread.

---

