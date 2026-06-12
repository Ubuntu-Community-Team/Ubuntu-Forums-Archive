---
title: "trouble with mysql replication"
date: 2010-01-13
forum: Server Platforms
---

### Post by kylegio on 2010-01-13
i am trying to set up mysql replication.

i have followed 
[http://www.howtoforge.com/how-to-set-up-database-replication-in-mysql-on-ubuntu-9.10](http://www.howtoforge.com/how-to-set-up-database-replication-in-mysql-on-ubuntu-9.10) 
closely, when it did not work i tried another walkthrough, and eventually the more intensive how-to from the mysql website. 

i have configured both the master and slave my.cnf files, all changes were made under the [mysqld] section, mysql on the master is reachable from the slave (checked it manually using the slaves user and password for the master). 


my trouble starts when it comes time to start the slave
i have replaced personal information with XXX such as the last octet of the masters ip address, and the password for user slave on the master.
```

mysql> CHANGE MASTER TO MASTER_HOST='192.168.1.XXX', MASTER_USER='slave', MASTER_PASSWORD='XXX', MASTER_LOG_FILE='mysql-bin.000001', MASTER_LOG_POS=5232;
Query OK, 0 rows affected (0.08 sec)

mysql> slave start;                                                             ERROR 1200 (HY000): The server is not configured as slave; fix in config file or with CHANGE MASTER TO
mysql> 

```

i am fairly sure the master is operating properly, i have checked its log files for changes made since i started telling it to log and it seems that its writing out the changes to the log properly. the master is reachable from the slave. the slave writes a proper master.info file:
```

15
mysql-bin.000001
5232
192.168.1.XXX
slave
XXX
3306
60
0





0

```
the master.info file is exactly 15 lines, as is specified it should be by the first line in the file. i am at a total loss for why this is not working, it is telling me to use the CHANGE MASTER TO, immediately after i issued the CHANGE MASTER TO command. 
 


any help appreciated,
thanks
kyle

---

