---
title: "MySQL Users and groups"
date: 2010-12-07
forum: Server Platforms
---

### Post by Johnley on 2010-12-07
hi guys,
    you've all been helpful before, and i just want to thank this great community! :p but i have a bit of a customizaton issue. i'm running a debian server with lighttpd, MySQL, PHP, and SSH. i want to set the server so that users are authenticated against a MySQL database instead of the /etc/shadow file. is there a guide on how to do this somewhere? i'm not too nooby, but this is my first foray into the unknown world of authentication :confused:

---

### Post by rubylaser on 2010-12-07
This is the type of thing that LDAP exists to do.  If you need to authenticate a bunch of users I'd look into setting up OpenLDAP. Otherwise, I'd stick with the /etc/shadow as there's less work to set it up for a few users.

---

### Post by SeijiSensei on 2010-12-07
[http://sourceforge.net/projects/modauthmysql/](http://sourceforge.net/projects/modauthmysql/)

I usually do authentication against a database using PHP scripts and session cookies.

---

### Post by rubylaser on 2010-12-07
This looks interesting, thanks for the link. I'm going to try this out in a virtual machine.

---

### Post by Johnley on 2010-12-07
my goal is to have a wordpress, DAV, SSH, and future modules all autheticate from the same file/database. can i do that with OpenLDAP?

---

### Post by Johnley on 2010-12-07
@rubylaser i did some googling, turns out there is a LDAP plugin for worpress mu. thanks so much :D

---

