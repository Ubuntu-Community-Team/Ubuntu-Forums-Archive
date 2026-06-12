---
title: "Mysql server cant be accessed?"
date: 2010-07-24
forum: Server Platforms
---

### Post by infofo on 2010-07-24
I have a xubuntu mysql server, and my winxp machine is unable to connect to the sql server using mysql ODBC.:( Is there any solution to my problem? Thanks.

---

### Post by minhnghivn on 2010-07-25
It is most likely that your MySQL is "bind" to a fixed IP address. For example:

# my.cf
bind-address        = 127.0.0.1

The implies that only connections from 127.0.0.1 are allowed. So, just comment the above directive, restart your MySQL and retry

Good luck

---

### Post by infofo on 2010-07-25
Thanks! I shall try that first thing tomorrow.

---

