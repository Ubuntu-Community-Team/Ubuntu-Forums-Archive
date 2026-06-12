---
title: "Mysql connect from Vista"
date: 2008-05-09
forum: Server Platforms
---

### Post by niqmk on 2008-05-09
Hi guys, I've installed lamp at my ubuntu-server and it runs correctly but i can't connect throught with mysql administrator GUI from Vista.
Ok, I've edited my.conf and insert # to bind-address

Restart mysql

mysql at vista pop the message error : 
MySQL error number 1103 host '192.168.1.130' isn't allowed  to connect the this mysql server.

Ubuntu IP Address is 192.168.1.201
Vista IP Address is 192.168.1.130

I Tried to update host use mysql query like:

use mysql;
update user set host='%' where user='root';

but the error message disturbs me :

duplicate entry '%-root' for key 1

Please help me how do i connect mysql at ubuntu via mysql administator at vista?

---

### Post by MaindotC on 2008-05-09
Could you connect to it from other Linux machines?  I think there's a configuration file that has to be edited to allow connections from sources other than "localhost".  I'll try and find it for you if you can't answer my first question.

Edit:  Try [these instructions]("http://dev.mysql.com/doc/refman/5.0/en/connection-access.html").

---

### Post by niqmk on 2008-05-09
> **strAlan said:**
> Could you connect to it from other Linux machines?  I think there's a configuration file that has to be edited to allow connections from sources other than "localhost".  I'll try and find it for you if you can't answer my first question.

Edit:  Try [these instructions]("http://dev.mysql.com/doc/refman/5.0/en/connection-access.html").

i've tried update user set root='%' where user='root'. but it still doesn't work at all (error message). Any conclusion?

---

### Post by MaindotC on 2008-05-09
Yeah I think I added the link in my post after you had tried and replied to mine.  Check out that link on the MySQL site I have in my previous post.

---

### Post by niqmk on 2008-05-09
Great Now I can access through ubuntu server via vista.

GRANT ALL PRIVILEGES ON db.* TO david@'192.58.197.0/255.255.255.0';

It's the solution for this problem. Thanks to you.

---

### Post by opus on 2008-05-09
your sql statement of "update user set root='%' where user='root'" doesn't work because by default there are multiple accounts called root, all of which have different domains. The domains are localhost, <machinename>, and 127.0.0.1.  

Personally, I remove all but the root@localhost user.  Make sure the password is changed to something very secure.  That way root can only login from the local machine, and only by you.  

Adding your own account and granting access is definately the way to go, but make sure your account has a really secure password too.

Aaron Throckmorton
[Admin Daily - Daily System Administration]("http://admindaily.blogspot.com/")

---

