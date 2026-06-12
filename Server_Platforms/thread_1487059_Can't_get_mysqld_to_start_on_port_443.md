---
title: "Can't get mysqld to start on port 443"
date: 2010-05-18
forum: Server Platforms
---

### Post by B.Joudrey on 2010-05-18
MySQL 5.0, Ubuntu server 8.04

I changed the port in the my.cnf to port 443 to dodge a firewall configuration that would result in too much BS to get it changed.  Nothing else on the server is using port 443 (only ports 80(Tomcat) and 22(ssh).  If I change the port in the  my.cnf to 3306, the server will start.  If I change it to port 443, it fails.  Anyone have any idea why, or what can I check to find out what is going on here?  I've been unable to track down any useful information thus far.

Thanks,

Brian

---

### Post by cdenley on 2010-05-18
You need to connect to mysql through a firewall? Are you connecting over the internet? I think SSH tunneling would be safer. Are you sure port 443 isn't already in use? What errors did it give?
```

sudo lsof -n -i :443

```

---

### Post by jd65pl on 2010-05-19
Port 443 is usually used for https. Try using a higher range address which isn't reserved for a specific task. e.g. 6306. You can use [this]("http://en.wikipedia.org/wiki/list_of_TCP_and_UDP_port_numbers") to pick a more appropriate one.

---

### Post by B.Joudrey on 2010-05-19
I need to use 443 because it's the only port that I can come up with that is going to be open on the firewall that we need to get through, it's very restrictive.  I ran the lsof -n -i :443 and it returned nothing.  I'd already used netstat to try and find anything listening on that port and it also returned only listeners on ports 80 and 22.

We are connecting over the internet, yes.  I can't find any errors, I just try to start the mysqld and get a "fail."  I've looked for the error logs where they should be and there aren't any that I can find.  MySQL isn't my strong point at all, so thank you for your patience.  I'm a server guy that's gotten into this project because there is no one else here that can do it any better.

Is it just that those ports are reserved somehow (ie, port 443) ?

---

### Post by cdenley on 2010-05-19
I think mysql binds to the TCP port as the user mysql. However, only root can bind to ports 1-1024. I would not suggest running mysql as root. You can redirect traffic on port 443 to 3306.
```

sudo iptables -t nat -A PREROUTING -p tcp -d xxx.xxx.xxx.xxx --dport 443 -j REDIRECT --to-ports 3306

```
Replace "xxx.xxx.xxx.xxx" with your IP address.

---

### Post by cdenley on 2010-05-19
double post

---

### Post by jd65pl on 2010-05-19
It sounds like you are just trying to circumvent some business process for supplying data over a network. This doesn't sound like a good idea.

[http://www.iana.org/assignments/port-numbers](http://www.iana.org/assignments/port-numbers)

---

### Post by B.Joudrey on 2010-05-19
jd - I am the network admin for a small gov't funded non-profit org.  I've got a community college co-op student doing a development project for me.  He needs the database to work with.  It takes a week and a change order for the outsourced community college firewall to get changed.  I have direct contact with one of their network guys and we tried to work out a port that we could use that would work that was free for both of us.  So, all the stakeholders in this know what's going on and we're just trying to get something done sooner than later to get things moving.  That was an open port in their firewall that we figured we could use, because there aren't many.

cdenley - I ran the IPTABLES change through and then changed the my.cnf file back to port 3306 and now it still won't start.  Is Ubuntu somehow aware of the redirect and is now not allowing it to happen because mysqld is running as the non-privileged user mysql.  There were no errors when I ran the IPTABLES command.  I double checked to make sure that I correctly changed the my.cnf file back to port 3306.  Perhaps I should just quit while I'm behind?  Ugh ...

---

### Post by cdenley on 2010-05-19
> **B.Joudrey said:**
> 
Is Ubuntu somehow aware of the redirect and is now not allowing it to happen because mysqld is running as the non-privileged user mysql.


No. You must have screwed something else up.
```

sudo /etc/init.d/mysql stop
sudo ps -ef|grep '[m]ysql'
sudo killall -w mysqld
sudo /etc/init.d/mysql start
grep '^[^#]' /etc/mysql/my.cnf

```
I still think either tunneling through ssh or using the mysql client on the server in an ssh session is a better way to accomplish remote mysql access.

---

### Post by B.Joudrey on 2010-05-19
mysql.cnf:

```

[client]
port = 3306
socket = /var/run/mysqld/mysql.sock
[mysqld_safe]
socket = /var/run/mysqld/mysql.sock
nice = 0
[mysqld]
user = mysql
pid-file = /var/run/mysqld/mysql.pid
socket = /var/run/mysqld/mysqld.sock
port = 3306
basedir = /usr
datadir = /var/lib/mysql
tmpdir = /tmp
language = /usr/share/mysql/english
skip-external-locking
bind-address = <my IP address, removed>
key_buffer = 16M
max_allowed_packet = 16M
thread_stack = 128k
thread_cache_size = 8
query_cache_limit = 1M
query_cache_size = 16M
expire_logs_days = 10
max_binlog_size = 100M
skip-bdb
[mysqldump]
quick
quote-names
max_allowed_packet = 16M
[mysql]
[isamchk]
key_buffer = 16M
!includedir /etc/mysql/conf.d/

```

Is the service start/stop command for a newer version of Ubuntu than 8.04?
```

sudo: service: command not found

```

> 
I still think either tunneling through ssh or using the mysql client on  the server in an ssh session is a better way to accomplish remote mysql  access. 	

-not sure how to do that either.  My Linux experience is limited but growing, and it seems that I've bitten off more than I can chew at this present moment.  Thank you for your patience.

-Brian

---

### Post by jd65pl on 2010-05-19
I didn't mean to offend in what I said, I've spent enough time in the corporate world to realise hacking round something can result in big problems. 

I agree with the ssh tunnelling idea.

Both of these should be run on the machine you want to connect from i.e. the students comp.

To create the tunnel:
```
ssh -L 3307:mysqlserver.domain:3306 user@sshgateway.domain
```

To open the mysql client:
```
mysql -P 3307 -u mysqluser -h 127.0.0.1 -p
```

---

### Post by cdenley on 2010-05-19
> **B.Joudrey said:**
> 
Is the service start/stop command for a newer version of Ubuntu than 8.04?
```

sudo: service: command not found

```


Sorry, forgot you were using 8.04.

---

### Post by B.Joudrey on 2010-05-19
I just wanted to explain what I was doing so it didn't sound so much like I was trying to hack someone's network.  I understand what it looked like, so I wanted to clear that up.

I'll try the ssh tunnel tomorrow.  However, what we're trying to do is actually connect to the MySQL server with PyQT for an application that's in development.  Is this tunneling methodology something that could be easily coded into the communication between application and server (and yes, the application is going to be working over the internet because it's going to connect from a remote site back to our main site to maintain one set of records for both sites at the same time).  I'm just asking before I drive my developer nuts.  He's good, so I don't want him to want to kill me.  ;-)

Thanks!

Brian

---

### Post by jd65pl on 2010-05-19
Yes he would just connect to it as if the mysql server is running on his machine, through whatever application interface he chooses. Tell them to be careful with the host name though as I don't think mysql client will connect it the host isn't specified, can't comment on other connection methods though.

---

