---
title: "Read only sql user for dumps"
date: 2019-04-10
forum: Server Platforms
---

### Post by Tadaen_Sylvermane on 2019-04-10
For backing up my mariadb with mysqldump I am trying to create a read only user to help with security a bit. Been using root for this, laziness I guess.

Did this.

```
grant select on *.* to 'backup'@'localhost' identified by 'backup';
```

on my mysql command line. However I get this error or problem when running my script as that user.

```
mysqldump: Couldn't execute 'show create table `episode_view`': SHOW VIEW command denied to user 'backup'@'localhost' for table 'episode_view' (1142)
```

I have all permissions in the backup directory. Dumps are being created but they are much smaller than previous backups from the root user so something is amiss. I am at a loss as sql is not my strong point. I only have it working because I've found guides that told me step by step.

Script for good measure. It's been working fine until now as root

```
#!/bin/bash# tadaen sylvermane | jason gibson
# mysql backup script


## main sources file ##


. /usr/local/bin/mainsources


## initialization ##


bin_link_controller


## main variables ##


MYSQLPATH="$POOLLOC"/backups/mysqldump


## begin script ##


#if [[ "$USER" == root ]] ; then
        if [[ $(systemctl is-active mysql) == active ]] ; then
                if [[ "$MYSQLPATH" ]] ; then
                        mysqldump --user=backup --password=backup --quick --single-transaction --all-databases | gzip > "$MYSQLPATH"/mydatabases."$NOW".sql.gz
                        find "$MYSQLPATH"/ -type f -mtime +10 -exec rm -f {} \;
                fi
        fi
#fi


## end script ##
```

---

### Post by #&amp;thj^% on 2019-04-10
I've seen this also, this error also arises for a syntax error occurred due to aliasing tablename.

For instance, when executed below query,```


    select * from a.table1, b.table2 where a.table1= b.table2
```

below error occurs:

```
 MySQL Error: #1142. Response form the database. [B]SELECT command denied to user "username@ip" for table "table1"
```
[/B]
My Solution : Syntax to alias tablename should be used proper, syntax solution for above instance >select * from table1 a, table2 b where a.table1= b.table2

---

### Post by SeijiSensei on 2019-04-10
```
SHOW VIEW command denied to user
```
Wouldn't granting the backup user the VIEW privilege solve this?

---

### Post by Tadaen_Sylvermane on 2019-04-10
That solved it.

```
grant show view on *.* to 'backup'@'localhost';
```

Working fine now. Thank you much.

---

