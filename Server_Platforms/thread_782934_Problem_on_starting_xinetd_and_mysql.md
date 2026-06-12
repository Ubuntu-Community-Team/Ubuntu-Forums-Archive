---
title: "Problem on starting xinetd and mysql"
date: 2008-05-05
forum: Server Platforms
---

### Post by satimis on 2008-05-05
Hi folks,


Ubuntu 6.05.3 Drake amd64


On running;
$ sudo /etc/init.d/xinetd start```

Password:
Starting internet superserver: xinetd.

```

On googling I found;
Needs Ubuntu-style init script
[https://bugs.launchpad.net/ubuntu/+source/xinetd/+bug/43574](https://bugs.launchpad.net/ubuntu/+source/xinetd/+bug/43574)


It seems to be a bug.  I couldn't figure out how to fix the problem.  Please advise?  TIA


On running;
$ sudo /etc/init.d/mysql restart```

Stopping MySQL database server: mysqld.
Starting MySQL database server: mysqld.

```
Same problem.


B.R.
satimis

---

