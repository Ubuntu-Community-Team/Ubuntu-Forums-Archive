---
title: "MySQL server has gone away"
date: 2007-12-15
forum: Server Platforms
---

### Post by bnuytten on 2007-12-15
I have setup a simple Apache2 webserver that uses a MySQL database to store the users for the secure site. All works fine, except that, after a long time (several hours), I suddenly get an Internal Server Error in my browser.

When I look at the error log for the site, I see the following line each time I refresh the browser:
```
[error] Query call failed: MySQL server has gone away (2006)
```
Reloading, restarting MySQL does not change anything. When I reload apache, all works fine again... Untill a couple of hours later, when the problem re-appears.

I am not sure about this, but I guess the connection used by Apache to authenticate users against the MySQL database is closed by MySQL after a certain amount of time. If this is the case, how do I tell Apache to automatically reconnect? Reloading apache every 3 hours is merely a workaround, not a real solution...

Using:
```
apache2                               2.2.4-3build1
libapache2-mod-auth-mysql             4.3.9-4
mysql-server-5.0                      5.0.45-1ubuntu3

```

---

### Post by bnuytten on 2007-12-29
[http://dev.mysql.com/doc/refman/5.0/en/gone-away.html]("http://dev.mysql.com/doc/refman/5.0/en/gone-away.html")

---

### Post by echofire on 2008-04-03
Hello,

Did you ever get an answer to this question ?  I have the exact same problem.  Increasing wait_timeout does not help, nor does decreasing wait_timeout and increasing the number of connections from 100 to 300

Nick

---

### Post by bnuytten on 2008-04-05
Unfortunatly no. I think it has something todo with timing issues, but that's just a guess. Or maybe it's a bug?

I am using a htpasswd file for the time being. Altough I want to store my users a the mysql database. By the way, I am also using Courrier in combination with MySQL (also user authentication) and the problem never shows. So the cause is probably located somewhere in apache...

---

### Post by GrugFromAus on 2008-05-14
This would be due to the default action of the MySQL client to reconnect being changed to false. Because of that, applications need to explicitly set the flag when using the MySQL client and any that don't are now broken.

There is more info in this Debian bug report: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=420010]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=420010")

Now I'm just trying to work out when it is going to get moved into the Gutsy repository.

---

### Post by bnuytten on 2008-07-05
Based on the bugtraq information. I have now installed version 4.3.9-9 from the next version of Ubuntu (Intrepid) on my Hardy install. So far so good, time will tell if the bug has been fixed in this release.

[http://packages.ubuntu.com/intrepid/libapache2-mod-auth-mysql](http://packages.ubuntu.com/intrepid/libapache2-mod-auth-mysql)

---

