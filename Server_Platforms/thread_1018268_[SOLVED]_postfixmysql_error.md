---
title: "[SOLVED] postfix/mysql error"
date: 2008-12-21
forum: Server Platforms
---

### Post by spiderbatdad on 2008-12-21
I can not seem to fix this alone:
postfix/smtpd[11256]: fatal: bad string length 0 < 1: etc/postfix/mysql_mailbox.cf_dbname = 

dbname has a value. there is no leading whitespace. This would be from my postfix/mysql_mailbox.cf

---

### Post by Drezard on 2008-12-21
So usually the database name is in there?

Have you tried it using no whitespace? such as:

> 
..db_name=mydatabase


Give that a go.

Daniel

---

### Post by spiderbatdad on 2008-12-22
```
user=XXXXX
password=XXXXXXXX
dbname=mymaildb
table=users
select_field=maildir
where_field=id
hosts=127.0.0.1
additional_conditions = and enabled = 1

```

---

### Post by spiderbatdad on 2008-12-22
the result appears to be that imapd-ssl dies...then following a successful authentication, imap drops the connection.
This seems like a fault in the smtpd


EDIT: finally...found a missing / in the path to file in the main.cf
```
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf

``` in the file /etc/postfix/main.cf

---

