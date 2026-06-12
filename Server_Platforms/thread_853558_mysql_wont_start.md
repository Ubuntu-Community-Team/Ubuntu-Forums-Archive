---
title: "mysql wont start"
date: 2008-07-08
forum: Server Platforms
---

### Post by darkorical on 2008-07-08
alright I have searched and read [this thread](http://ubuntuforums.org/showthread.php?t=801607&highlight=mysql+start)
and a few others and I couldnt find any info that helped me.

much like the mentioned thread my mysql comes up starting then reports [ [COLOR="Red"]fail[/COLOR] ] and I tried looking at the logs but much like the thead listed above my logs were empty however unlike the the mentioned thread changing the ownership did not fix it. So can someone please tell me what other info is needed to allow someone here to help me 

System hostname 	Linux
Operating system 	Ubuntu Linux 7.10
Webmin version 	1.412
Time on system 	Tue Jul 8 16:25:08 2008
System uptime 	17 hours, 15 minutes
CPU load averages 	0.00 (1 min) 0.00 (5 mins) 0.00 (15 mins)
Real memory 	1.95 GB total, 76.48 MB used
	
Virtual memory 	5.71 GB total, 0 bytes used
	
Local disk space 	141.09 GB total, 8.01 GB used
	
Im having troubles tracking down exact system info right now.

what other info .. and how do I get it do I need to get help on my issue.

---

### Post by lamego on 2008-07-08
Please check /var/log/daemon.log for mysql related errors.

---

### Post by darkorical on 2008-07-09
Jul  9 08:02:44 Linux mysqld_safe[4296]: started
Jul  9 08:02:44 Linux mysqld[4299]: ^G/usr/sbin/mysqld: File '/var/log/mysql/mysql-bin.index' not found (Errcode: 13)
Jul  9 08:02:44 Linux mysqld[4299]: 080709  8:02:44 [ERROR] Aborting
Jul  9 08:02:44 Linux mysqld[4299]: 
Jul  9 08:02:44 Linux mysqld[4299]: 080709  8:02:44 [Note] /usr/sbin/mysqld: Shutdown complete
Jul  9 08:02:44 Linux mysqld[4299]: 
Jul  9 08:02:44 Linux mysqld_safe[4301]: ended
Jul  9 08:02:58 Linux /etc/init.d/mysql[4436]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Jul  9 08:02:58 Linux /etc/init.d/mysql[4436]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Jul  9 08:02:58 Linux /etc/init.d/mysql[4436]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Jul  9 08:02:58 Linux /etc/init.d/mysql[4436]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Jul  9 08:02:58 Linux /etc/init.d/mysql[4436]: 

I checked and /var/run/mysqld/mysqld.sock does not appear to exist 
in fact /var/run/mysqld/ appears to be completely empty 

how do I fix this?

---

### Post by windependence on 2008-07-09
Create the directory if it is not there:
```
sudo mkdir /var/run/mysqld/
```

touch the file to create it
```
sudo touch /var/run/mysqld/mysqld.sock
```

change the ownership of the folder and socket to the mysql user
```
sudo chown mysql /var/run/mysqld/
```
```
sudo chown mysql /var/run/mysqld/mysqld.sock
```


start the mysql server 
```
sudo mysqld
```

and see if it works

-Tim

---

### Post by darkorical on 2008-07-18
for the record I tried your suggestions and it still didnt work however I ran an upgrade and it seems to be working just fine now

---

