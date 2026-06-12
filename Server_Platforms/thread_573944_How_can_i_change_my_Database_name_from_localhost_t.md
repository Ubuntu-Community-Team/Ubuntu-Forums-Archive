---
title: "How can i change my Database name from localhost to mysql?"
date: 2007-10-12
forum: Server Platforms
---

### Post by alxbob on 2007-10-12
Hi,

I am trying to figure how can i change the DBserver from localhost,which is the default,to mysql cause i am migrating a web site from one server to another and they had a different DBserver name.That means tha the site dont work :) The message i get is Unknown MySQL server host 'mysql' (1).If anyone has any idea would be very helpful.

Tnx in advance for the help....

---

### Post by James79 on 2007-10-12
This is going to depend on what the website is.

If it's a forum, for example, then often they have configuration screens that allow you to change the hostname/ip of the DB.

Otherwise, the name of the DB is probably hardcoded in the script/text file somewhere.

Can you give us a little more info about the site?

---

### Post by Brazen on 2007-10-12
> **alxbob said:**
> Hi,

I am trying to figure how can i change the DBserver from localhost,which is the default,to mysql cause i am migrating a web site from one server to another and they had a different DBserver name.That means tha the site dont work :) The message i get is Unknown MySQL server host 'mysql' (1).If anyone has any idea would be very helpful.

Tnx in advance for the help....

The host is just the dns name or ip address of the server housing the mysql database and doesn't really have anything to do with mysql itself.  It sounds like you have two options here.  Either change the website to use 'localhost' as the database server, or make the name query for 'mysql' resolve to 127.0.0.1.  The latter would probably be the easiest, and the easiest way to do that would be to put an entry in your hosts file.

So, to put it simply, one way to solve this is to put this line:> 127.0.0.1       mysqladded to the /etc/hosts file on the server.

---

### Post by k_grdn on 2007-10-12
Hi alxbob,

Locate my.cnf usually /etc/mysql, edit the line:

bind-address            = localhost

note: this is usally hostname or ip so mysql db will need corresponding host/ip entry.

Regards,

k_grdn

---

### Post by alxbob on 2007-10-16
Hi again and tnx for your information...

I ve changed my /etc/hosts to 127.0.0.1 mysql and nothing changed.I ve also changed my.cnf bind-address 127.0.0.1 or mysql and again db server name didnt change.I did restart the mysql service and it is still locahost......


:confused:

---

### Post by alxbob on 2007-10-18
Still nothing....i dont know what to do....maybe i ll start changing all the lines to the web site....

---

