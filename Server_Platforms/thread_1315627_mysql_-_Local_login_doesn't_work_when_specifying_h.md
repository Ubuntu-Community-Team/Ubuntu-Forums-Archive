---
title: "mysql - Local login doesn't work when specifying host"
date: 2009-11-05
forum: Server Platforms
---

### Post by awclemen on 2009-11-05
Hello,

I've tried this over at the MySQL forums, but no one responded.  So I though it might be a server issue (resolving from /etc/hosts or something like that?) and threw it up here.  Any and all ideas are welcome.

I have a mysql 5.0.75 server running on Ubuntu 9.0.4. I added my 'sa' user as shown:

```
GRANT SELECT,UPDATE,INSERT,DELETE ON quartz.* TO 'sa' IDENTIFIED BY '********';
```

Which, to my understanding, should allow all hosts for sa. When I login in like this:

```
>mysql -u sa -p quartz
```

everything works fine. When I specify a host:

```
>mysql -u sa -p -h 10.2.0.102 quartz
```

I get the following error message:

```
ERROR 1045 (28000): Access denied for user 'sa'@'tucpmptest01.******.com' (using password: YES)
```

When I log into the server from a remote host:

```
REMOTEHOST>mysql -u sa -p -h 10.2.0.102 quartz
```

it works fine.....

Reading the documentation ([http://dev.mysql.com/doc/refman/5.1/en/access-denied.html](http://dev.mysql.com/doc/refman/5.1/en/access-denied.html)) and tried mysqladmin flush-hosts - but still no love.

my user and db tables in the mysql database seem to be in order:

```
mysql> select user, host from user where user='sa';
+------+------+
| user | host |
+------+------+
| sa | % |
+------+------+
1 row in set (0.01 sec)

mysql> select user,db,host from db where user='sa';
+------+--------+------+
| user | db | host |
+------+--------+------+
| sa | quartz | % |
+------+--------+------+
1 row in set (0.01 sec)

```

Since I'm using the IP address, I would assume that DNS does not play an issue - but it shouldn't matter since ALL hosts are allowed.

Now if I add these permissions:
```
GRANT SELECT,UPDATE,INSERT,DELETE ON quartz.* TO 'sa'@'tucpmptest%' IDENTIFIED BY '********';
```
the login works.... I'm trying to avoid specifying the host in the database however...


Any ideas?

Thanks a plenty in advance!

--Andy

---

### Post by koenn on 2009-11-05
You could try some additional / alternative GRANT statements eg

```
GRANT SELECT,UPDATE,INSERT,DELETE ON quartz.* TO 'sa'@'%' IDENTIFIED BY '********';
```
or

```
GRANT SELECT,UPDATE,INSERT,DELETE ON quartz.* TO 'sa'@'localhost' IDENTIFIED BY '********';
```

but it looks to me you got everything covered already :
  * you can access the db from localhost as sa (without specifying a host)
  * you can access the db remotely by specifying the db host 

what else do you need ? 

You may want to run 
```
FLUSH PRIVILEGES;

```
after updating privileges

and read some more here : 
[http://dev.mysql.com/doc/refman/5.1/en/adding-users.html](http://dev.mysql.com/doc/refman/5.1/en/adding-users.html)
[http://dev.mysql.com/doc/refman/5.1/en/grant.html](http://dev.mysql.com/doc/refman/5.1/en/grant.html)

---

### Post by Ilalmi on 2009-11-05
Hi,

could you state the other entries of the user-table as well?
```
select user, host from user;
```
Although your user 'sa' seems fine, there could be other entries interfering. 

Thanks

---

### Post by awclemen on 2009-11-05
FLUSH Privileges worked! :p  Yea!  Thanks Koenn!  Thanks Ilalmi!

koenn:

The reason for the need to specify a host while connecting locally is that I am trying to connect to mysql via jdbc and when it connects it acts like a local login the specifies a host.

---

