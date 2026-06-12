---
title: "Server MySQL Permission advice"
date: 2011-11-19
forum: Security
---

### Post by Lori700698 on 2011-11-19
I need to read up on MySQL permissions so I better understand and get them set correctly, the only two I'm 100% sure of is to not grant privileges and not to create users, I know you have to give access to the tables for programs to work but I could use a little education on the matter.  If anybody knows of any good solid articles, posts, or books would you mind sharing?
Thank you so much
Lori

---

### Post by Jonathan L on 2011-11-21
> **Lori700698 said:**
> I need to read up on MySQL permissions so I better understand and get them set correctly, the only two I'm 100% sure of is to not grant privileges and not to create users, I know you have to give access to the tables for programs to work but I could use a little education on the matter.  If anybody knows of any good solid articles, posts, or books would you mind sharing?
Thank you so much
Lori

Hi Lori

I would say the critical thing is you don't allow access from anywhere that's not essential.  For example, if you run your database on the same computer as your web server, then don't even allow connections except on the loopback interface.

You check this with netstat:
```
$ **netstat -an**
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 [COLOR=SeaGreen]127.0.0.1[/COLOR]:3306          0.0.0.0:*               LISTEN     
tcp        0      0 [COLOR=Red]192.168.0.64[/COLOR]:3306       0.0.0.0:*               LISTEN     
[...]

```MySQL port is 3306, and we're listening on 127.0.0.1: this is good.  Unless you need a different computer to talk to this DB server, then you don't want to listen on 192.168.0.64 (ie your ethernet's IP address), like the red one shown above.  You control this with [bind-address]("http://dev.mysql.com/doc/refman/5.0/en/server-options.html#option_mysqld_bind-address").

Regardless of where you're listening, check your user and db tables:
```
mysql> **select host, user, password from user;**
+------------------+------------------+-------------------------------------------+
| host             | user             | password                                  |
+------------------+------------------+-------------------------------------------+
| localhost        | root             | *1111111111111111111111111111111111111111 |
| [COLOR=Red]something-else[/COLOR]   | root             | *1111111111111111111111111111111111111111 |
| 127.0.0.1        | root             | *1111111111111111111111111111111111111111 |
| localhost        | debian-sys-maint | *2222222222222222222222222222222222222222 |
| localhost        | wikiuser         | *3333333333333333333333333333333333333333 |
+------------------+------------------+-------------------------------------------+
```Again, you shouldn't be able to connect to your sever from anywhere that isn't essential to deliver your service.

The principal thing I'm suggesting is make sure you look, not only at the configuration, but from the other side: ie, what ports is it *actually* listening on; what users are *actually* defined.

Hope that gives you some ideas.

Kind regards,
Jonathan.

---

