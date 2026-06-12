---
title: "postmap: warning: connect to mysql server, acces denied for user  ."
date: 2011-04-09
forum: Server Platforms
---

### Post by venol on 2011-04-09
Hello all, I need help about postfix. I want to make mail server with virtual account for postfix and listed in mysql database. So I create file configuration postfix to mysql Database. The file is "mysql_virtual_mailbox_domains.cf" and contains like this :

> 
hosts = 127.0.0.1
user = postfix
pass = password
dbname = postfixdb
query = select 1 from virtual_mailbox where nama_domain='%s' 


Then, I create user postfix on mysql  with access to database "postfixdb". I test with command "
> mysql --user=postfix --password=password postfixdb
" and it works. But, when I test with "postmap -q example.com mysql:/etc/postfix/mysql_virtual_mailbox_domains.cf" the result is . . 

> 
postmap: warning: connect to mysql server 127.0.0.1: Access denied for  user 'postfix'@'localhost' (using password: YES)


what's problem?

---

### Post by elico on 2011-04-09
make sure you are allowing both 127.0.0.1 source and localhost.
you can change the allow user access from anywhere just to make sure that it's the problem(in most of the cases it is)

---

### Post by venol on 2011-04-10
> **elico said:**
> make sure you are allowing both 127.0.0.1 source and localhost.
you can change the allow user access from anywhere just to make sure that it's the problem(in most of the cases it is)

thanks for the reply elico. Yes, I make sure to give privileges to both(127.0.0.1 and localhost)
> 
mysql> grant all privileges on postfixdb.* to 'postfix'@'localhost' identified by 'password';
Query OK, 0 rows affected (0.00 sec)

mysql> grant all privileges on postfixdb.* to 'postfix'@'127.0.0.1' identified by 'password';
Query OK, 0 rows affected (0.00 sec)

mysql> flush privileges;
Query OK, 0 rows affected (0.00 sec)

mysql> quit


is correct ?

and then I test 
> 
mysql --user=postfix --password=password -h 127.0.0.1 postfixdb
     and
mysql --user=postfix --password=password -h localhost postfixdb


this is success..

I confused, where is the mistake?. is the configuration above true? 
I'm sure, I'm make mistake.But I dont know where is the mistake!

help..:(

---

