---
title: "mySql database wont start"
date: 2010-04-08
forum: Server Platforms
---

### Post by blakep2 on 2010-04-08
I have a mysql database and i use it with apache for my webpages.  And I guess it dosen't start when the computer starts so I have to manually start it with "sudo /etc/init.d/mysql start"  This returns fail so i went to '/var/run/mysqld/' and the folder was empty.  I don't know if this is the problem or not.  How can I fix this?

---

### Post by Ryan Dwyer on 2010-04-09
Does it give you an error message when you try to start it or does it just say "fail"?
What is in /var/log/mysql/error.log?

---

### Post by blakep2 on 2010-04-09
It does not give a error message it just says fail.  The /var/log/mysqld/ folder is empty

---

### Post by s_ø on 2010-04-09
By default mysql logs is in the syslog.
/var/log/syslog

---

### Post by blakep2 on 2010-04-09
> **s_ø said:**
> By default mysql logs is in the syslog.
/var/log/syslog

the mysql.err file is empty, mysql.log is empty as well, mysql.log.1.gz has a file but it us blank same for mysql.log.2.gz.

---

### Post by s_ø on 2010-04-09
You should open the syslog not the mysql.log, mysql.err etc
try to start mysql
then after you get the error open syslog and look for mysql errors
**grep -i 'mysql' /var/log/syslog**
will give you all entries with mysql.

---

### Post by blakep2 on 2010-04-09
> **s_ø said:**
> You should open the syslog not the mysql.log, mysql.err etc
try to start mysql
then after you get the error open syslog and look for mysql errors
**grep -i 'mysql' /var/log/syslog**
will give you all entries with mysql.

syslog had this in it about my sql

r  9 19:52:54 petermanserver mysqld[9211]: 100409 19:52:54  InnoDB: Started; log sequence number 0 43655
Apr  9 19:52:54 petermanserver mysqld[9211]: 100409 19:52:54 [ERROR] Can't start server: Bind on TCP/IP port: Cannot assign requested address
Apr  9 19:52:54 petermanserver mysqld[9211]: 100409 19:52:54 [ERROR] Do you already have another mysqld server running on port: 3306 ?
Apr  9 19:52:54 petermanserver mysqld[9211]: 100409 19:52:54 [ERROR] Aborting
Apr  9 19:52:54 petermanserver mysqld[9211]: 
Apr  9 19:52:54 Apr  9 19:52:53 petermanserver mysqld_safe[9207]: started
Appetermanserver mysqld[9211]: 100409 19:52:54  InnoDB: Starting shutdown...
Apr  9 19:52:55 petermanserver mysqld[9211]: 100409 19:52:55  InnoDB: Shutdown completed; log sequence number 0 43655
Apr  9 19:52:55 petermanserver mysqld[9211]: 100409 19:52:55 [Note] /usr/sbin/mysqld: Shutdown complete
Apr  9 19:52:55 petermanserver mysqld[9211]: 
Apr  9 19:52:55 petermanserver mysqld_safe[9242]: ended
Apr  9 19:53:08 petermanserver /etc/init.d/mysql[9380]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Apr  9 19:53:08 petermanserver /etc/init.d/mysql[9380]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Apr  9 19:53:08 petermanserver /etc/init.d/mysql[9380]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Apr  9 19:53:08 petermanserver /etc/init.d/mysql[9380]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Apr  9 19:53:08 petermanserver /etc/init.d/mysql[9380]:

---

### Post by blakep2 on 2010-04-09
also this when run the command

blake@petermanserver:~$ grep -i 'mysql' /var/log/syslog
Apr  9 19:52:53 petermanserver mysqld_safe[9207]: started
Apr  9 19:52:54 petermanserver mysqld[9211]: 100409 19:52:54  InnoDB: Started; log sequence number 0 43655
Apr  9 19:52:54 petermanserver mysqld[9211]: 100409 19:52:54 [ERROR] Can't start server: Bind on TCP/IP port: Cannot assign requested address
Apr  9 19:52:54 petermanserver mysqld[9211]: 100409 19:52:54 [ERROR] Do you already have another mysqld server running on port: 3306 ?
Apr  9 19:52:54 petermanserver mysqld[9211]: 100409 19:52:54 [ERROR] Aborting
Apr  9 19:52:54 petermanserver mysqld[9211]: 
Apr  9 19:52:54 petermanserver mysqld[9211]: 100409 19:52:54  InnoDB: Starting shutdown...
Apr  9 19:52:55 petermanserver mysqld[9211]: 100409 19:52:55  InnoDB: Shutdown completed; log sequence number 0 43655
Apr  9 19:52:55 petermanserver mysqld[9211]: 100409 19:52:55 [Note] /usr/sbin/mysqld: Shutdown complete
Apr  9 19:52:55 petermanserver mysqld[9211]: 
Apr  9 19:52:55 petermanserver mysqld_safe[9242]: ended
Apr  9 19:53:08 petermanserver /etc/init.d/mysql[9380]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Apr  9 19:53:08 petermanserver /etc/init.d/mysql[9380]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Apr  9 19:53:08 petermanserver /etc/init.d/mysql[9380]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Apr  9 19:53:08 petermanserver /etc/init.d/mysql[9380]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Apr  9 19:53:08 petermanserver /etc/init.d/mysql[9380]: 
blake@petermanserver:~$

---

### Post by blakep2 on 2010-04-09
Sorry one other thing i moved this machine to a different home.  Thus a different ip and etc.. would this be a problem.

---

### Post by s_ø on 2010-04-10
Moving shouldnt be a problem. By default MySQL only listens on localhost .
It looks like another service is using the 3306 that MySQL is trying to bind to.
You can scan localhost to see if another service is using the port.
Install nmap if you havent already.
```
 sudo apt-get install nmap
```
Then probe port 3306 on localhost
```
 nmap -p 3306 -sV localhost
```

---

### Post by blakep2 on 2010-04-10
returned this.


blake@petermanserver:~$ nmap -p 3306 -sV localhost

Starting Nmap 4.76 ( [http://nmap.org](http://nmap.org) ) at 2010-04-10 12:39 EDT
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
SCRIPT ENGINE: '/usr/share/nmap/scripts/skype_v2-version.nse' threw a run time error and could not be loaded.
SCRIPT ENGINE: '/usr/share/nmap/scripts/iax2Detect.nse' threw a run time error and could not be loaded.
SCRIPT ENGINE: '/usr/share/nmap/scripts/PPTPversion.nse' threw a run time error and could not be loaded.
Interesting ports on localhost (127.0.0.1):
PORT     STATE  SERVICE VERSION
3306/tcp closed mysql

Service detection performed. Please report any incorrect results at [http://nmap.org/submit/](http://nmap.org/submit/) .
Nmap done: 1 IP address (1 host up) scanned in 0.43 seconds
blake@petermanserver:~$

---

### Post by s_ø on 2010-04-10
To start with check the hosts file to see if there is any conflicts
[B]sudo nano /etc/hosts
[/B]Are there more than one localhost in there?

As I understand the three SCRIPT ENGINE errors the port is not scanned for those services.
If you have Skype installed you can set the port it uses under **Options > Advanced >Connection **
I dont know about the other 2, but you can look in the filesfor clues.

You should also check mysql config file **my.cnf**
**nano /etc/mysql/my.cnf **
look for this
[B]bind-address            = 127.0.0.1
[/B]If it is set to something different it could be the problem

Edit: Do you have any problems with your Apache server?

---

### Post by blakep2 on 2010-04-10
it was binding to the internal ip of the other home's ip the ip at the new house was taken by the router configuration site.

Thanks for the help it is working know.

---

### Post by s_ø on 2010-04-10
Great. MySQL should bind to localhost / 127.0.0.1. You dont need remote access to use it.
Could you please mark the thread as solved.

---

