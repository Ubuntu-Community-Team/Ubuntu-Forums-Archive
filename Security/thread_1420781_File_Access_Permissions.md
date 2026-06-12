---
title: "File Access Permissions"
date: 2010-03-03
forum: Security
---

### Post by theprocrastinater on 2010-03-03
I am setting up a new ubuntu server, and I am quite new to linux.
This server will be used as code repository for a project I am going to be working on.
I plan to setup 3 groups for users: dev, test, doc
 - for various developers, testers and documentation users.
I would like to setup the following permissions on the main code repository directory:

dev - write permission
test - execute permission
doc - read permission
public (anyone outside these groups) - deny all access

I am unsure what chmod setting to use, or if this is even possible in ubuntu.

Thanks,

Nick

---

### Post by bodhi.zazen on 2010-03-03
For an over view of "basic" linux permissions see :

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

please take note: permissions on files and directories are different, in particular the execute bit is needed to access the files within the directory.

Basic permissions give you 3 general groups 

user (the person who owns the file) - a group - everyone else

So as you have 4 groups (dev, test, doc , and public) you can not do it with basic permissions.

You would need to go to what is caleld acl, or access control lists. acl will allow you to set more then one set of group permissions 9so you can set permissions for each of your 4 groups).

[http://www.cs.unc.edu/cgi-bin/howto?howto=linux-posix-acls](http://www.cs.unc.edu/cgi-bin/howto?howto=linux-posix-acls)

There is a graphical too if you wish, although it does not have all the options available on the command line:

[http://www.linux.com/archive/feature/138169](http://www.linux.com/archive/feature/138169)

Eiciel is in the repositories.

How to activate acl is somewhat dependent on the file system, for ext4 (the default) you need to add acl in the options for fstab.

---

### Post by webtechquery on 2010-03-03
Hi.
Well I'm not sure if I can help ya, but for try, at least you can visit the following site:
[http://www.webtechquery.com/index.php/2010/02/you-dont-have-permission-to-access-httplocalhost-files-or-folders-on-this-server-in-ubuntu-linux/](http://www.webtechquery.com/index.php/2010/02/you-dont-have-permission-to-access-httplocalhost-files-or-folders-on-this-server-in-ubuntu-linux/)

Though it is a post related to a problem, but there are also some chmod explanation defined.

Thanx.

---

