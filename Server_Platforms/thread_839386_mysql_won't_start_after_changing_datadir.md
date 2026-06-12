---
title: "mysql won't start after changing datadir"
date: 2008-06-24
forum: Server Platforms
---

### Post by Sjonny on 2008-06-24
Hi,

I have not enough room on my root partition for my mysql databases, so I changed the datadir config in /etc/mysql/my.cnf from /var/lib/mysql to /home/mysql.
Now I can't start mysql anymore. The following errors are in the log:
```

Jun 24 17:37:40 fratser mysqld_safe[32689]: started
Jun 24 17:37:40 fratser mysqld[32693]: 080624 17:37:40 [Warning] Can't create test file /home/mysql/fratser.lower-test
Jun 24 17:37:40 fratser mysqld[32693]: 080624 17:37:40 [Warning] Can't create test file /home/mysql/fratser.lower-test
Jun 24 17:37:40 fratser mysqld[32693]: 080624 17:37:40  InnoDB: Operating system error number 13 in a file operation.
Jun 24 17:37:40 fratser mysqld[32693]: InnoDB: The error means mysqld does not have the access rights to
Jun 24 17:37:40 fratser mysqld[32693]: InnoDB: the directory.
Jun 24 17:37:40 fratser mysqld[32693]: InnoDB: File name ./ibdata1
Jun 24 17:37:40 fratser mysqld[32693]: InnoDB: File operation call: 'open'.
Jun 24 17:37:40 fratser mysqld[32693]: InnoDB: Cannot continue operation.
Jun 24 17:37:40 fratser mysqld_safe[32699]: ended

```

I've tried other directories too. Even setting the mysql directory to 777 does not help. When I move the directory to /var/lib/my than it doesn't start also. Only when the directory is /var/lib/mysql, then mysql will start. Otherwise I get this weird permission denied error, which should not be true.

Any ideas why this is , and how to fix it?

---

### Post by Sjonny on 2008-06-24
ah, should have searched other keywords too ...
'apt-get --purge remove apparmor' fixed it

---

