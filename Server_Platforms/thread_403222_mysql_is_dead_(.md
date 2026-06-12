---
title: "mysql is dead :("
date: 2007-04-06
forum: Server Platforms
---

### Post by lennartack on 2007-04-06
Hello, today I noticed my mysql server couldn't start anymore, and I can't live without it :P
> lennart@lennart:~$ sudo /etc/init.d/mysql start
 * Starting MySQL database server mysqld                                                                     [fail]
An aptitude upgrade mysql-server and a dpkg-reconfigure didn't work..

---

### Post by Frosty Cold Drink on 2007-04-06
You need to see *why* its failing to start. Check your mysql, daemon, and message logs in /var/log to see what is going on.

---

### Post by lennartack on 2007-04-06
this is the first time it didn't start:
> **daemon.log]Apr  6 21:42:08 LENNART mysqld_safe[4282]: started
Apr  6 21:42:09 LENNART mysqld[4285]: 070406 21:42:09  InnoDB: Started said:**
> : 070406 21:42:09 [ERROR] Can't start server: Bind on TCP/IP port: Cannot assign requested address
Apr  6 21:42:09 LENNART mysqld[4285]: 070406 21:42:09 [ERROR] Do you already have another mysqld server running on port: 3306 ?
Apr  6 21:42:09 LENNART mysqld[4285]: 070406 21:42:09 [ERROR] Aborting
Apr  6 21:42:09 LENNART mysqld[4285]: 
Apr  6 21:42:09 LENNART mysqld[4285]: 070406 21:42:09  InnoDB: Starting shutdown...
Apr  6 21:42:11 LENNART mysqld[4285]: 070406 21:42:11  InnoDB: Shutdown completed; log sequence number 0 43665
Apr  6 21:42:11 LENNART mysqld[4285]: 070406 21:42:11 [Note] /usr/sbin/mysqld: Shutdown complete
Apr  6 21:42:11 LENNART mysqld[4285]: 
Apr  6 21:42:11 LENNART mysqld_safe[4324]: ended
I'll try to find some more info in other logs later (if needed) but I need to go now.

---

### Post by Frosty Cold Drink on 2007-04-06
Try this
```
sudo netstat --inet -ltpn | grep 3306
```

It should tell you if anything is using that port or not.

---

### Post by lennartack on 2007-04-07
> **Frosty Cold Drink said:**
> Try this
```
sudo netstat --inet -ltpn | grep 3306
```

It should tell you if anything is using that port or not.
nothing..

The only log file with information about mysql is deamon.log, and the mysql log files are all empty.

---

### Post by lennartack on 2007-04-07
Everytime I try to apt-get upgrade I get this:
> Setting up mysql-server-5.0 (5.0.24a-9ubuntu2) ...
 * Stopping MySQL database server mysqld                                                                                             [ ok ]
 * Starting MySQL database server mysqld                                                                                             [fail]
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by jaheds on 2007-04-07
The code mentioned by Frosty Cold Drink returned nothing?  Just to be sure, can you try it again?

If it returns nothing again, it might be the case that mysqld is trying to bind to an IP/interface that you no longer have.

While you are at it, please provide us with the value of the "bind_address" setting in the /etc/mysql/my.cnf file... That's the IP address MySQL will try to bind to when it's starting.  It's usually "127.0.0.1"

---

### Post by lennartack on 2007-04-07
> **jaheds said:**
> While you are at it, please provide us with the value of the "bind_address" setting in the /etc/mysql/my.cnf file... That's the IP address MySQL will try to bind to when it's starting.  It's usually "127.0.0.1"
Actually, there is no bind_address in that file. Adding it manually doesn't change anything.

I forgot to post this error, which came before the error I posted earlier in this thread:
[quote=daemon.log]Apr  7 13:05:26 LENNART /etc/init.d/mysql[5788]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Apr  7 13:05:26 LENNART /etc/init.d/mysql[5788]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Apr  7 13:05:26 LENNART /etc/init.d/mysql[5788]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Apr  7 13:05:26 LENNART /etc/init.d/mysql[5788]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Apr  7 13:05:26 LENNART /etc/init.d/mysql[5788]: [/quote]

---

### Post by jaheds on 2007-04-07
Which Ubuntu are you running?

Can you paste the contents of your /etc/mysql/my.cnf for us

It shouldn't have anything secret (like passwords) in it, but just in case, make sure to scan through it and take anything private out

Have you modified /etc/mysql/my.cnf before?

---

### Post by lennartack on 2007-04-07
> **jaheds said:**
> Which Ubuntu are you running?
Ubuntu/Kubuntu Edgt Eft

> **jaheds said:**
> Can you paste the contents of your /etc/mysql/my.cnf for us
I removed all commented lines to make it more compact:
> **my.cnf][client]
port		= 3306
socket		= /var/run/mysqld/mysqld.sock

[mysqld_safe]
socket		= /var/run/mysqld/mysqld.sock
nice		= 0

[mysqld]

user		= mysql
pid-file	= /var/run/mysqld/mysqld.pid
socket		= /var/run/mysqld/mysqld.sock
port		= 3306
basedir		= /usr
datadir		= /var/lib/mysql
tmpdir		= /tmp
language	= /usr/share/mysql/english
skip-external-locking

old_passwords	= 1

bind-address		= 192.168.1.6

key_buffer		= 16M
max_allowed_packet	= 16M
thread_stack		= 128K
thread_cache_size	= 8

query_cache_limit	= 1048576
query_cache_size        = 16777216
query_cache_type        = 1

log_bin			= /var/log/mysql/mysql-bin.log

expire_logs_days	= 10
max_binlog_size         = 100M

skip-bdb

[mysqldump]
quick
quote-names
max_allowed_packet	= 16M

[mysql]

[isamchk]
key_buffer		= 16M[/quote]

[QUOTE=jaheds said:**
> Have you modified /etc/mysql/my.cnf before?
No...

---

### Post by jaheds on 2007-04-07
I originally said "bind_address", but I should have said "bind-address", and I see that it's value is 192.168.1.6

Is that your current IP?

Can you change it to 127.0.0.1 and try again?

---

### Post by Frosty Cold Drink on 2007-04-07
> **jaheds said:**
> I originally said "bind_address", but I should have said "bind-address", and I see that it's value is 192.168.1.6

Is that your current IP?

Can you change it to 127.0.0.1 and try again?

Its best to just remove it and listen on all addresses. If one were to do local host only, the mysqld socket would be a better choice.

---

### Post by lennartack on 2007-04-07
> **jaheds said:**
> Can you change it to 127.0.0.1 and try again?
Thanks! That did the trick.

---

### Post by [S2] on 2007-04-08
I have your same problem, but in my case binding mysqld to 127.0.0.1 is not an option, because I need to access it from other computers on my lan. I set the bind-address to 0.0.0.0 for now, but that is not really what I want.
I filed a bug report:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/104466](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/104466)

---

### Post by jaheds on 2007-04-08
I think that might just be a mysqld package installation issue.  It should probably be set to only start after the network has initialized.

---

### Post by [S2] on 2007-04-09
> **jaheds said:**
> I think that might just be a mysqld package installation issue.  It should probably be set to only start after the network has initialized.

Yes. I did not find the mysql package when submitting the bug, and it worked when there was no NetworkManager, so I selected NM.

---

### Post by thejart on 2007-05-17
first off it's bind-address, not bind_address in the my.cnf file.

making sure that this value was consistent with my ip address solved the problem of mysql not loading on my machine.  it also explains why some people found that a reboot solved their problem.  in my situation i'm running a lamp server, so i've setup a static ip.  after configuring the machine at my house and then moving the server to its permanent location, i had to reassign the ip to be consistent with the working subnet.  this is what broke mysql for me and re-binding the address solved it.  

it seems like a lot of people tend to reinstall for fixing a problem, but it's been my experience that that's hardly ever the most elegant solution.  this mentality has taught me a lot about linux...and i have a LOT to learn.

conversely, reinstalling is probably the best solution in windows :)

---

### Post by NeGrusti on 2007-12-06
My machine where I have a mysql server is getting a static DHCP lease, and mysql was working fine with previous Ubuntu version, with the bind-address set to this static lease. After an upgrade the NetworkManager came with the annoying bug in the log files:
nm_dhcp_manager_begin_transaction(): dhcdbd not running
And I think it's getting the IP much later than normal, and of course in this case mysql cannot bind to that address on startup.

---

