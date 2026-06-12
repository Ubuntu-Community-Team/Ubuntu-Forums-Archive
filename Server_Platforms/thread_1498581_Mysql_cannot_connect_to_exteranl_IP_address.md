---
title: "Mysql cannot connect to exteranl IP address"
date: 2010-06-01
forum: Server Platforms
---

### Post by akester on 2010-06-01
I am running a server with Ubuntu 10.04 and mysql v.5.4.41-3ubuntu12.1

I am unable to connect to my mysql server remotely, (error 111).  I have added the port 3306 to iptables.  It is able to connect to the loopback address (127.0.0.1) but not through its external address.

For example, if I run
```
mysqladmin -u root -p -h 127.0.0.1 version
```

I recieve the output of the server's version saying that it connected via TCP/IP

But if I try
```
mysqladmin -u root -p -h 192.168.2.111 version
```

It gives a connection error 111, "Lost communication to MySQL server at 'reading initial communication packet'

Thank you for any help.

---

### Post by zhangr on 2010-06-01
On ubuntu distribution, mysql has been configured to listen loopback interface only, but you can modify the "bind-address" option in its configuration file /etc/mysql/my.cnf to enable mysql listen on other interface(s).

---

### Post by akester on 2010-06-04
Thanks, That got it solved!

---

