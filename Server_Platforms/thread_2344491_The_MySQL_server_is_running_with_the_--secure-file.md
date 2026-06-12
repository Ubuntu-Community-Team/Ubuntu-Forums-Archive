---
title: "The MySQL server is running with the --secure-file-priv option"
date: 2016-11-25
forum: Server Platforms
---

### Post by marchello_lippi2 on 2016-11-25
Hi all, 

I'm having troubles uploading my file into mysql. It happened like a week ago after software update (ran fine before). 

The code I run: 
```

sudo rm /var/lib/mysql/db_train/rejectlog.txt; sudo cp /var/log/exim4/rejectlog /var/lib/mysql/db_train/rejectlog.txt; sudo chown mysql:mysql /var/lib/mysql/db_train/rejectlog.txt; sudo mysql --user=root --password=mypassword < /home/user1/mysql/upload_rejectlog.sql; sudo rm /var/lib/mysql/db_train/rejectlog.csv; sudo mysql --user=root --password=mypassword < /home/user1/mysql/select_rejectlog.sql; sudo mpack -s "rejectlog.csv" /var/lib/mysql/db_train/rejectlog.csv user1@example.com

```

The error message: 
```

ERROR 1290 (HY000) at line 3: The MySQL server is running with the --secure-file-priv option so it cannot execute this statement
rm: cannot remove '/var/lib/mysql/db_train/rejectlog.csv': No such file or directory
ERROR 1290 (HY000) at line 2: The MySQL server is running with the --secure-file-priv option so it cannot execute this statement
/var/lib/mysql/db_train/rejectlog.csv: No such file or directory

```

/home/user1/mysql/upload_rejectlog.sql : 
```

USE db_train;
truncate table db_train.exim4_rejectlog;
LOAD DATA INFILE 'rejectlog.txt' INTO TABLE db_train.exim4_rejectlog;

```

/home/user1/mysql/select_rejectlog.sql
```

USE db_train;
select SUBSTRING_INDEX(SUBSTRING_INDEX(t.textmessage, '[', -1), ']', 1) as ip_address, t.* from db_train.exim4_rejectlog t where t.textmessage not like '%whatidonotwanttosee%'
INTO OUTFILE 'rejectlog.csv'
FIELDS TERMINATED BY ','
ENCLOSED BY '"'
LINES TERMINATED BY '\n';

```

Tried to put my file into /var/lib/mysql-files/ 
Tried to change mysql secure directory by putting **secure_file_priv=/var/lib/mysql/db_train/** into my /etc/mysql/my.cnf
Tried to disable secure_file_priv option by putting **secure_file_priv="" **into my /etc/mysql/my.cnf
Tried to stop and start mysql server again. 

Nothing worked for me. 
Actually, it is my personal server and the Earth is not in danger )) 
And yes, it is ugly way to do it under the root.
The purpose of this strange behavior is to filter rejectlog of my exim4 server and put needed strings into my email inbox. 
My workaround is just looking into exim4 rejectlog manually. 

But if someone can advise, please do it ) 
Thanks ahead.

> 
$ mysql -V
mysql  Ver 14.14 Distrib 5.5.53, for debian-linux-gnu (i686) using readline 6.3


> 
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:        14.04
Codename:       trusty


---

### Post by wildmanne39 on 2016-11-25
*Thread moved to **Server Platforms**.*

---

### Post by marchello_lippi2 on 2016-11-26
My another workaround: 
> 
sudo rm /tmp/rejectlog_filtered.txt; sudo less /var/log/exim4/rejectlog | grep -v "WhatIdoNotWantToSee" > /tmp/rejectlog_filtered.txt; sudo mpack -s "rejectlog_filtered.txt" /tmp/rejectlog_filtered.txt [email]user1@example.com[/email]


What is missing here is possibility to view it in columns using Excel..

---

