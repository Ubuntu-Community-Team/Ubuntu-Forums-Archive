---
title: "mysql ERROR 1045"
date: 2011-01-14
forum: Server Platforms
---

### Post by skipi-gz on 2011-01-14
hi
i was trying to allow remote access to mysql by following [http://www.cyberciti.biz/tips/how-do-i-enable-remote-access-to-mysql-database-server.html](http://www.cyberciti.biz/tips/how-do-i-enable-remote-access-to-mysql-database-server.html). mysql was running perfectly until i got here :
```
/sbin/iptables -A INPUT -i eth0 -s 192.168.1.0/24 -p tcp --destination-port 3306 -j ACCEPT
```i changed my.cnf bind-address line to : "bind-address        = 127.0.0.1" and nothing else.
i have tried removing (with --perge) mysql, phpmyadmin and iptables (with mysql i used : ```
sudo apt-get remove --perge mysql*
```) and installing them again. 

when i try connect with terminal on the local machine, it gives me the error > ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)any help would be greatly appreciated. thanx in advanced :)

---

### Post by chrislynch8 on 2011-01-14
Hi,

Maybe your Host file is pointing localhost to something other then 127.0.0.1. As you are also creating a rule to allow connections from your LAN 192.168.1.0/24 thes ewill all fail as far as I recall as your bind_address will only listen on 127.0.0.1 you will also have to add you LAN address on the server.

You will also have to allow access in your hosts.allow
```
mysqld: 127.0.0.1 192.168.1.0/24
```

Rgds
Chris

---

### Post by skipi-gz on 2011-01-14
no luck

i tried ```
mysqld 127.0.0.1 10.0.0.0/24
```
which gave me
> 110114 13:58:07 [Warning] Can't create test file /var/lib/mysql/skipiserv.lower-test
110114 13:58:07 [Warning] Can't create test file /var/lib/mysql/skipiserv.lower-test
mysqld: Can't change dir to '/var/lib/mysql/' (Errcode: 13)
110114 13:58:07 [ERROR] Aborting

110114 13:58:07 [Note] mysqld: Shutdown complete

sorry, i have no clue what the iptables are for (if that is what is causing this). if i did, i would know what to ask for.

---

### Post by chrislynch8 on 2011-01-14
Ok

you should have a colon after mysqld in the hosts file. You IP table command I beleive is opening up port 3360 for connections from the 192.168.1.0/24 network.

As you have 10.0.0.0/24 in the Hosts file try running the iptables command again, exchanging 192.168.1.0/24 for 10.0.0.0/24

See will that help.

Also can you access the directory /var/lib/mysql? What are the permissions/user/group on that folder?

Rgds
Chris

---

### Post by skipi-gz on 2011-01-14
ah :b clumsy me. i misread what u said. Its all working perfectly now. thanx a million :p

---

