---
title: "mysql doesn't want to start for me HELP!"
date: 2007-01-20
forum: Server Platforms
---

### Post by rickc on 2007-01-20
Hello. 

Does anyone have any ideas why mysqld doesn't want to start for me? I was trying to launch /etc/init.d/mysqld start, but it ended with 'failed' status. So i tried to launch it manually by entering 'mysqld' command, and it gave me an error.

> 
070120 17:58:29  InnoDB: Started; log sequence number 0 43655
070120 17:58:29 [Note] Recovering after a crash using /var/log/mysql/mysql-bin
070120 17:58:29 [Note] Starting crash recovery...
070120 17:58:29 [Note] Crash recovery finished.
070120 17:58:29 [ERROR] Fatal error: Can't open and lock privilege tables: Incorrect file format 'host'


I did a search here before posting. The closest thing I found was [_this pos_t]("http://http://www.ubuntuforums.org/showthread.php?t=340663&highlight=mysql") And tried everything on it.


'pgrep mysql' shows nothing, the same with 
'tail /var/log/mysql.log'
'tail /var/log/mysql.err'
ps aux | grep mysqld returns 
> 
rickc    28429  0.0  0.0   2796   744 pts/0    R+   18:06   0:00 grep mysqld

and sudo netstat -tap returns
 > 
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      0 localhost:2208          *:*                     LISTEN     4140/hpiod          
tcp        0      0 localhost:49729         *:*                     LISTEN     4143/python         
tcp        0      0 localhost:ipp           *:*                     LISTEN     4105/cupsd          
tcp        0      0 localhost:52684         mc-in-f104.google.c:www ESTABLISHED4906/opera          
tcp6       0      0 *:www                   *:*                     LISTEN     28062/apache2       
tcp6       0      0 *:ssh                   *:*                     LISTEN     4741/sshd    

I have 'bind-address' in my.cnf commented out with an '#' for now. 
I currently run edgy on an AMD 2800xp with 1gig of ram 250 SATA HD. I'm runing mythTV and all has worked thus far. The only changes I've made in the last fe days in I installed Opera, and another capture card. But my system worked for about 2 days after the install, soI don' t think it was that....
If anywan has any ideas for me to try I'd greatly apreciate it. Thanks in advance rickC

---

### Post by transactionlogfiller on 2007-01-20
If you're not too bothered about losing the settings that are in there, you could remove the mysql database and run mysql_install_db to put it back with the defaults.

I believe you can also start the server with --skip-grants.

---

### Post by rickc on 2007-01-20
> **transactionlogfiller said:**
> If you're not too bothered about losing the settings that are in there, you could remove the mysql database and run mysql_install_db to put it back with the defaults.

I believe you can also start the server with --skip-grants.

I don't care about the setting... I need to get a DB out before I do it. I'll read up on how to do it & post back here ... thanks for the quick reply.

---

### Post by SeanHodges on 2007-06-18
This has just happened to me as well, did you have any luck fixing it rickc?

---

