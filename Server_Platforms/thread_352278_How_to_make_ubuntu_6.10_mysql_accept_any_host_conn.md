---
title: "How to make ubuntu 6.10 mysql accept any host connect?"
date: 2007-02-03
forum: Server Platforms
---

### Post by explorer1979 on 2007-02-03
Dear all,

I installed Ubuntu, but I am not good at command line, and I know how to using Windows's MySQL Administrator GUI tool to manage the MySQL ...

But the default of the Ubuntu MySQL is can not accept connect outside localhost ...

How to make the root can accept connect from any computer any host?

Thank for your time.

---

### Post by phossal on 2007-02-03
You have to grant permissions to the user and/or the host from which you would like to connect. Here is the main page for MySQL's documentation: [http://dev.mysql.com/doc/](http://dev.mysql.com/doc/) Check out the section on granting permissions: [http://dev.mysql.com/doc/refman/5.0/en/grant.html](http://dev.mysql.com/doc/refman/5.0/en/grant.html)

---

### Post by chrisfay on 2007-02-03
You need to comment out the portion of your my.cnf file that looks like:

```
bind-address = 127.0.0.1
```

.... to allow connections from outside localhost. You would also have to follow phossal's information after enabling remote connections in order to allow an actuall user/host to connect.

---

