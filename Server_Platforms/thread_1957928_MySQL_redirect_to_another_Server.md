---
title: "MySQL redirect to another Server"
date: 2012-04-13
forum: Server Platforms
---

### Post by FCarlo on 2012-04-13
Hi!

I need some help. Is it possible to run two MySQL servers on the same network and port, but make them listen on different domain names. If not, can one make one Server redirect all traffic from one domain to another server?

Thanks in advance!

FCarlo

---

### Post by volkswagner on 2012-04-13
You may need to provide more specific info about your setup.  

What is "calling" MySQL?  Can't you point the requests at the ip address for each server?

You should have no problem running multiple MySQL servers on the network.

---

### Post by SeijiSensei on 2012-04-13
I think the OP means have two MySQL servers on the same box with multiple IP addresses both listening to port 3306.  You'd set the A record in DNS for each domain to the different addresses.  So mysql.example.com might point to 10.10.10.10:3306 while mysql.somewhere.com points to 10.10.10.11:3306.

There's nothing equivalent to "name-based virtual hosting" like there is for HTTP, though.  That's because the HTTP/1.1 protocol was written explicitly to support name-based hosting.  It quickly became clear in the early days of the World Wide Web that the HTTP/1.0 requirement of a separate IP for every domain would exhaust the IP space.

I think it would be possible to run two instances on a single server both listening to port 3306 if you specify different IP addresses in the "bind-address" field in my.cnf.  You'll need to configure the startup scripts to use different versions of my.cnf for the two instances, of course.

---

### Post by rubylaser on 2012-04-13
This should be possible, but I don't see the point.  If it's just to keep databases separate, just make different databases and grant privileges like normal.  OP, why do you think you need this, or what's the use case?

---

### Post by Jonathan L on 2012-04-14
Hi FCarlo

If you did mean you want to run two whole MySQL servers on the same computer, I'd start along the lines of giving yourself two IP addresses and confinue from there to separate the configuration, data, and startup files.

I took a look at a system with MySQL 5.1.37 and made some notes which perhaps will helpt:

The file /etc/init.d/mysql contains the warning:

```
# NOTE: Copying this script and changing the CONF variable here isn't
# enough to run multiple instances of mysqld. Debian/Ubuntu doesn't 
# currently support such a configuration out of the box.
CONF=/etc/mysql/my.cnf
```You can either make two config files or probably just two startup files, the second of which starts your second mysqld with enough command line flags to separate it from the first.  I'd experiment by having one run from the standard /etc/init.d/mysql.conf, and try starting a second by hand with extra command line arguments to separate it from the first.  Then I'd make a new /etc/init.d/mysqld2 based on the first one, but with the appropriate flags.

IP Addresses: imagining you already have your server on 192.168.0.32, you get another IP address alias:
```
ifconfig eth0:33 192.168.0.33
```I'm guessing you'll have two domain names set up, either
```
db1.example.com. A 192.168.0.32
db2.example.com. A 192.168.0.33
or
db.example1.com. A 192.168.0.32
db.example2.com. A 192.168.0.33
```And then one mysqld is started bound to 192.168.0.32, the second to 192.168.0.33.  Note that normally mysql binds to all addresses, including 127.0.0.1.  If it's only bound to 192.168.0.32, you'll no longer be able to reach it as localhost and will have to use its name or IP address.

You'll need a second data directory
```
 mkdir /var/lib/mysql2
 chmod 755 /var/lib/mysqld2
 chown mysql:mysql /var/lib/mysqld
```Getting it working will 'simply' be a question of finding all the file paths which might clash. Reading through the configs, I notice these things which need to change:

```
pid-file = /var/run/mysqld/mysqld.pid
socket = /var/run/mysqld/mysqld.sock
datadir = /var/lib/mysql
```Their matching command line versions are
```
--pid-file=/var/run/mysqld/mysqld2.pid
--socket=/var/run/mysqld/mysqld2.sock
--datadir=/var/lib/mysql2
```You'll need to read the details in [http://dev.mysql.com/doc/refman/4.1/en/server-options.html](http://dev.mysql.com/doc/refman/4.1/en/server-options.html)

Hope this is helpful.  Let us know how you get on.

Kind regards,
Jonathan.

---

