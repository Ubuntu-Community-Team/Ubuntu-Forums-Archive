---
title: "mysql will not start"
date: 2011-03-14
forum: Server Platforms
---

### Post by pavel989 on 2011-03-14
ive been trying to fix this for a while. i dont have the original my.cnf, but i dont even know if thats the error:
```
pavel@pvl1:~$ sudo service mysql start
^C
pavel@pvl1:~$ cd /var/log/
pavel@pvl1:/var/log$ cat mysql.err
pavel@pvl1:/var/log$ cat mysql.log
pavel@pvl1:/var/log$ cd mysql
pavel@pvl1:/var/log/mysql$ ls
mysql.err  mysql.log.1.gz  mysql.log.3.gz  mysql.log.5.gz  mysql.log.7.gz
mysql.log  mysql.log.2.gz  mysql.log.4.gz  mysql.log.6.gz
pavel@pvl1:/var/log/mysql$ cat mysql.err
pavel@pvl1:/var/log/mysql$ cat mysql.log
pavel@pvl1:/var/log/mysql$

```

---

### Post by falko on 2011-03-15
Are there any MySQL errors in /var/log/syslog?

---

