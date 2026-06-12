---
title: "Mysql, Innodb free tablespace"
date: 2013-01-31
forum: Server Platforms
---

### Post by zeezam on 2013-01-31
I recently installed a new database server with Ubuntu 12.04 and mysql 5.5.

I have munin client installed on the server. After a while munin started to warn about Mysql InnoDB free tablespace.

How do I solve this?
I havn't found any good info about this...

---

### Post by slickymaster on 2013-01-31
Munin by default throws a warning at 2GB free tablespace and a critical alert at 1GB free tablespace and that's why you get a permanent Munin warning for MySQL InnoDB free tablespace. MySQL will by default create a 10MB autoexpanding tablespace, which autoextends as needed, thus this warning should be disregarded.

You can verify your table space, by executing:
```
mysql -e "SHOW VARIABLES LIKE 'innodb_data_file_path'"
```

---

### Post by zeezam on 2013-01-31
> **slickymaster said:**
> Munin by default throws a warning at 2GB free tablespace and a critical alert at 1GB free tablespace and that's why you get a permanent Munin warning for MySQL InnoDB free tablespace. MySQL will by default create a 10MB autoexpanding tablespace, which autoextends as needed, thus this warning should be disregarded.

You can verify your table space, by executing:
```
mysql -e "SHOW VARIABLES LIKE 'innodb_data_file_path'"
```

/var/lib/mysql/ibdata1 seems to be the file with tables stores.
If I run the command above I get no output.

Should I raise the warning level of free tablespace?

---

### Post by slickymaster on 2013-01-31
**/var/lib/mysql/ibdata1** is your MySQL databases of InnoDB format.
By default, MySQL stores all INNODB tables in a once, continuously growing, file in **/var/lib/mysql**.

Regarding whether you should raise the warning level of free tablespace or not, it's probably for the best if you read [this]("http://dev.mysql.com/doc/refman/5.0/en/innodb-configuration.html") in MySql documentation website.

---

