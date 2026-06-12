---
title: "Installing mysql-server on 18.04 fails to get root PW"
date: 2018-03-05
forum: Ubuntu Development Version
---

### Post by crcarson on 2018-03-05
After install 18.04 (daily build 3/5/18) the installation of mysql-server does not get the root PW from the user.  No way to access root to build local tables.  Tried several methods to reset mysql root PW but unsuccessful so far.

---

### Post by Doug S on 2018-03-07
yes, please see this [bug report]("https://bugs.launchpad.net/serverguide/+bug/1752215").

Summary: mysql now uses your main root password. where you used to do "mysql -u root -p" you now do "sudo mysql".

---

### Post by whshk on 2018-04-28
This is my temporary solution [https://whs-dot-hk.github.io/ubuntu-18.04/install-mysql.html](https://whs-dot-hk.github.io/ubuntu-18.04/install-mysql.html)

---

### Post by cariboo on 2018-04-28
Thread closed, as Bionic has been released.

---

