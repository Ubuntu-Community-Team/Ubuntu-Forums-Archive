---
title: "msqly database default install for oscommerce"
date: 2007-09-14
forum: Server Platforms
---

### Post by gr3gg0r on 2007-09-14
Here's what I'm trying to do:

I want to use my Ubuntu desktop as a temporary web server with php and mysql etc, (LAMP).  I just want it so I can see what my webpage will look like when I go live.  I plan on using a different server, I just want to be able to run it all locally right now.  So I have all that stuff installed.  Now, I'm completely new at this stuff, and when I go through the oscommerce setup, It asks me some things, and I don't know the answer.  Here's what I need:

The address of the database server in the form of a hostname or ip address.
The username for said database server.
password
the name of the database to hold the data in.

Where can I configure/find out what that info is??  What's the defaults??  Thanks!

---

### Post by James79 on 2007-09-22
Hi. I'm not familiar with oscommerce, but I'll give your anwers a try.

> **gr3gg0r said:**
> 
The address of the database server in the form of a hostname or ip address.


If you're installing "oscommerce" on the same computer that is running MySQL, try simply putting "127.0.0.1" as the IP. That's a special IP address that simply means "myself".

> **gr3gg0r said:**
> 
The username for said database server.
password


If I remember correctly, the default user on MySQL is "root" and it has a blank password. If this is a closed system that isn't accessible to untrusted people (especially the internet) then you can simply leave it as such for simplicity's sake.

> **gr3gg0r said:**
> 
the name of the database to hold the data in.


Often programs will create their own database and fill them with the tables they need. Try simple typing in "oscommerce" and see if it'll proceed or complain. We'll work from there :)

---

