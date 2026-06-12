---
title: "Multiple user for a web server"
date: 2011-01-15
forum: Server Platforms
---

### Post by DanHorniblow on 2011-01-15
I need to create an Apache web server with multiple user accounts, for work.

Each user needs to be able to upload his/her files via SSH

Each user needs his/her own web directory, (preferably in their home directory for ease with permissions)

There web directories need to be password protected

Only one user account (mine) should be allowed remote SSH control.

It needs to be easy to add new users to the system.


Any suggestions?

---

### Post by Thirtysixway on 2011-01-15
> **DanHorniblow said:**
> I need to create an Apache web server with multiple user accounts, for work.

Each user needs to be able to upload his/her files via SSH

Each user needs his/her own web directory, (preferably in their home directory for ease with permissions)

There web directories need to be password protected

Only one user account (mine) should be allowed remote SSH control.

It needs to be easy to add new users to the system.


Any suggestions?

I would look at mod_userdir for apache.  It allows the user to have [www.mydomain.com/~username](www.mydomain.com/~username) website simply by having a folder called public_html in their home directory.

sudo a2enmod userdir
make public_html folder for each uer
give access to user:www-data

you may want to google around for a guide

---

