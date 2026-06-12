---
title: "MySQL Server not starting."
date: 2010-06-11
forum: Server Platforms
---

### Post by Promythyus on 2010-06-11
Hey all,      I've got a problem with mysql-server-5.1. The recent update (5.1.41-3ubuntu12.3) caused apt-get upgrade to hang (left it for at least 24hrs, after which I killed it with kill). This caused mysql-server-5.1 to be corrupted, thus I had to remove with apt-get remove --purge. I have now reinstalled with apt-get install mysql-server-5.1, which seems to have gone fine EXCEPT that I cannot actually start the server, sudo start mysql hangs, and running start with the verbose option doesn't say anything. If I then abort (ctrl-c) and try to start mysql again, it reports mysql is already running, but ps aux does not reflect this, and I cannot connect to the mysql server.    ANY help would be appreciated.

---

### Post by Promythyus on 2010-06-11
Problem solved. /etc/mysql/my.cnf was totally bare, so fixed it up, and the server started fine :)

---

