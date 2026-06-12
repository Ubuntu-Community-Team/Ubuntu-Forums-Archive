---
title: "Noob MySql Remote Refused"
date: 2010-02-21
forum: Security
---

### Post by jk121960 on 2010-02-21
HI and thanks, I am building a drupal site on ubuntu 64bit server no desktop in VMware, ssh connects no problem but I can't connect to mysql with tools (MySQL Administrator) from my other vm. Iptables does not appear to be running, it is not in the list of services. I have nothing in hosts.allow or hosts.deny, can someone help me out? I only need local nat connectivity. The refusal specifically is: 
Could not connect to host '192.168.0.164' MySQL Error Nr. 1130
Host '192.168.0.157' is not allowed to connect to this MySQL server. 

any help would be appreciated.

thanks jerry

---

### Post by cdenley on 2010-02-22
[http://ubuntuforums.org/showthread.php?p=8848732](http://ubuntuforums.org/showthread.php?p=8848732)

---

### Post by cariboo on 2010-02-22
Do you have a user setup that is allowed to connect remotely?

You can do this by opening the mysql console and entering the following commands:

```
mysql> grant all privileges on *.* to <user>@'localhost'
    -> identified by '<password>' with grant option;
Query OK, 0 rows affected (0.09 sec)

mysql> grant all privileges on *.* to <user>@'%'
    -> identified by '<password>' with grant option;
Query OK, 0 rows affected (0.01 sec)

mysql> 
```

substitute your user name and password.

---

