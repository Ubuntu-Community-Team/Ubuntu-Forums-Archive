---
title: "MySQL problems"
date: 2008-10-02
forum: Server Platforms
---

### Post by gh0ti on 2008-10-02
I am having a problem trying to start mqsql

he in the log from /var/log/syslog

Oct  2 17:02:15 mdus mysqld_safe[14123]: started
Oct  2 17:02:15 mdus mysqld[14127]: 081002 17:02:15  InnoDB: Operating system error number 13 in a file operation.
Oct  2 17:02:15 mdus mysqld[14127]: InnoDB: The error means mysqld does not have the access rights to
Oct  2 17:02:15 mdus mysqld[14127]: InnoDB: the directory.
Oct  2 17:02:15 mdus mysqld[14127]: InnoDB: File name ./ibdata1
Oct  2 17:02:15 mdus mysqld[14127]: InnoDB: File operation call: 'open'.
Oct  2 17:02:15 mdus mysqld[14127]: InnoDB: Cannot continue operation.
Oct  2 17:02:15 mdus mysqld_safe[14133]: ended
Oct  2 17:02:30 mdus /etc/init.d/mysql[14283]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Oct  2 17:02:30 mdus /etc/init.d/mysql[14283]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Oct  2 17:02:30 mdus /etc/init.d/mysql[14283]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Oct  2 17:02:30 mdus /etc/init.d/mysql[14283]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Oct  2 17:02:30 mdus /etc/init.d/mysql[14283]:


can anyone help.

---

### Post by Idefix82 on 2008-10-02
What's the command with which you start mysql? It looks to me like you didn't grant it root privileges. I.e. try something like "sudo your command".

---

### Post by gh0ti on 2008-10-02
sudo /etc/init.d/mysql start

---

### Post by Idefix82 on 2008-10-02
In that case maybe the file it is talking about is not executable? You could try
```
sudo chmod 755 path_to_file/ibdata1
```

---

### Post by gh0ti on 2008-10-02
sweet now working, Thanks

---

