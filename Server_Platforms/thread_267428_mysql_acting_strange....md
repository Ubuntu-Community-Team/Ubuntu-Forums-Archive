---
title: "mysql acting strange..."
date: 2006-09-28
forum: Server Platforms
---

### Post by chipyoung on 2006-09-28
I am trying to update the root password at the local host level on a new install.  I was able to complete the command;

sudo mysqladmin -u root password ******

but when I do the following as stated in the Ubuntu server manual
 
sudo mysqladmin -u root -h localhost password newrootsqlpassword

I get the following message;

mysqladmin: connect to server at 'localhost' failed
error: 'Lost connection to MySQL server during query' 

I am using the correct localhost which I checked in the database.

It's very strange because I just went through this on another PC with Ubuntu installed (version 6.06 i386 iso desktop) and had no problems.  I am running ubuntu  6.06 alternate i386 iso with a server install.

Thank you in advance,
Chip

---

