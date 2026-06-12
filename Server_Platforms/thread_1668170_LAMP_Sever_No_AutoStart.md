---
title: "LAMP Sever No AutoStart"
date: 2011-01-16
forum: Server Platforms
---

### Post by antonvrg on 2011-01-16
hi i want to run a LAMP server but dont want it to start when my computer starts. i want to start it via terminal. how do i do this?

---

### Post by James78 on 2011-01-16
I believe you can get the effect you want by editing the runlevel scripts startup.
```
sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf
*Find apache2, deselect all running instances*
```
Alternatively you could also use chkconfig..
```
sudo apt-get install chkconfig
sudo chkconfig --del apache2
```
I haven't tested these out, but they should work.

---

### Post by sj1410 on 2011-01-16
> **antonvrg said:**
> hi i want to run a LAMP server but dont want it to start when my computer starts. i want to start it via terminal. how do i do this?


LAMP is _L_inux _A_pache _M_ysql _P_hp

You know how to start Linux

Apache & Mysql starts automatically. If you think they are not starting you can start them manually

```
sudo /etc/init.d/apache2 start
sudo /etc/init.d/mysql start

``` 

apache listens by default on port 80 on all IPs
whereas mysql listens on 3306 only on 127.0.0.1 i.e. localhost

you can change it in /etc/mysql/my.cnf

more on

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by antonvrg on 2011-01-16
i know what LAMP stands for. linux is the only one i want to start. and James78 it worked. thanks

---

