---
title: "asp.net ms-sql on ubuntu"
date: 2008-06-24
forum: Server Platforms
---

### Post by wenek18 on 2008-06-24
Hi 

I am running an ASP.Net website using an MS-SQL database on a windows hosting, I know have a problem as my server changed his hosting packages to medium trust and parts of my website are not working.

Was thinking, is it possible to run a windows based website on ubuntu (lamp installed) ? 

I heard about MONO but will it work ?

Thanks for your help guys

Thanks and regards
Justin

---

### Post by cdenley on 2008-06-24
I've run an asp.net site on FreeBSD before with mod_mono, so it will work on Linux. You could probably connect to a MS-SQL server, but I don't think you can run a MS-SQL server on Linux.

---

### Post by wenek18 on 2008-06-24
> **cdenley said:**
> I've run an asp.net site on FreeBSD before with mod_mono, so it will work on Linux. You could probably connect to a MS-SQL server, but I don't think you can run a MS-SQL server on Linux.
Hi thanks for your reply would i be able to use mysql instead ? would asp.net running in mono connect with mysql ?

Thanks for your help 
Justin

---

### Post by cdenley on 2008-06-24
Yes, that is what my site used.
[http://dev.mysql.com/downloads/connector/net/1.0.html](http://dev.mysql.com/downloads/connector/net/1.0.html)

---

### Post by wenek18 on 2008-06-24
Hi 
Good evening I managed to install mono on apache however I am having problems as am getting the following when I restart apache

apache2: Syntax error on line 186 of /etc/apache2/apache2.conf: Syntax error on line 3 of /etc/apache2/mods-enabled/mod_mono.conf: Could not open configuration file /usr/local/lib/mono/2.0/mono-server2-hosts.conf: No such file or directory
   ...fail!

I used the following guide 

[http://timanisblog.com/2007/07/22/install-mono-apache-mod-mono-applications-in-ubuntu/](http://timanisblog.com/2007/07/22/install-mono-apache-mod-mono-applications-in-ubuntu/)

Please help as I am getting crazy :(

Awaiting your replies

Thanks - Justin

---

