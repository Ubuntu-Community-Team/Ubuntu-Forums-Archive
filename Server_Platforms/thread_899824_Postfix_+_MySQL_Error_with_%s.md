---
title: "Postfix + MySQL Error with %s"
date: 2008-08-24
forum: Server Platforms
---

### Post by iWarior on 2008-08-24
Hello, All!

I'm working in x64 Ubuntu Server 8.04, and have very strange problem with Postfix + MySQL. I'm install and config Postfix by this HowTo: **[http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.04]("http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.04")**

All seems like a works:

```
# netstat -tap 

[B]tcp        0      0 localhost:10024         *:*                     LISTEN      4908/amavisd (maste
tcp        0      0 localhost:10025         *:*                     LISTEN      13043/master[/B]
tcp        0      0 localhost:mysql         *:*                     LISTEN      10152/mysqld
tcp        0      0 *:www                   *:*                     LISTEN      5699/apache2
tcp        0      0 example.com:domain          *:*                     LISTEN      4849/named
tcp        0      0 localhost:domain        *:*                     LISTEN      4849/named
**tcp        0      0 *:smtp                  *:*                     LISTEN      13043/master**
tcp        0      0 localhost:953           *:*                     LISTEN      4849/named
tcp6       0      0 [::]:imaps              [::]:*                  LISTEN      5427/couriertcpd
tcp6       0      0 [::]:pop3s              [::]:*                  LISTEN      5461/couriertcpd
tcp6       0      0 [::]:pop3               [::]:*                  LISTEN      5441/couriertcpd
tcp6       0      0 [::]:imap2              [::]:*                  LISTEN      5407/couriertcpd
tcp6       0      0 [::]:domain             [::]:*                  LISTEN      4849/named
```

I'm put all info in to mysql tables, configure *.cf-files, clam, antispam etc

But postfix work very strange (not create mail folder, only receive mail's and so one). After long debug, i'm understand, that problem in mysql query from *.cf files &#8211; in **%s** variable ([http://www.postfix.org/mysql_table.5.html]("http://www.postfix.org/mysql_table.5.html")). In this variable, in this situation, must be e-mail address of e-mail recipient (eg: _admin@example.com_), But...

If I'm write in mysql-virtual_mailboxes.cf

```
query = SELECT CONCAT(SUBSTRING_INDEX(email,'@',-1),'/',SUBSTRING_INDEX(email,'@',1),'/') FROM users WHERE email = '%s'
```

in mysql log file I see, that %s = _example.com_ 

But, if I'm write (only for test of course :) ):

```
query = SELECT '%s'
```

I'm see in %s place my  _admin@example.com_

I'm really don't understand, whats happen, and why in the same place I have different results...:confused:

Any ideas?..

---

