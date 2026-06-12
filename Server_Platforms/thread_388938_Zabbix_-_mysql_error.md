---
title: "Zabbix - mysql error"
date: 2007-03-20
forum: Server Platforms
---

### Post by dignus on 2007-03-20
Hey folks,

I'm trying to compile the latest beta of Zabbix. It gives me the following error after ./configure:
```

checking for mysql_config... no
no
configure: error: Not found MySQL library
```

This is strange, since I have mysql in place, including libraries:
```

root@bassie:~/zabbix-1.3.3# ldconfig -v | grep mysql
ldconfig: Can't stat /lib64: No such file or directory
ldconfig: Can't stat /usr/lib64: No such file or directory
        libmysqlclient_r.so.15 -> libmysqlclient_r.so.15.0.0
        libmysqlclient.so.15 -> libmysqlclient.so.15.0.0

```
Any suggestions?

---

### Post by NeonX on 2007-03-23
Install libmysqlclient15-dev via apt-get

---

