---
title: "setting up LAMP on Feisty"
date: 2007-09-15
forum: Server Platforms
---

### Post by hobojjr on 2007-09-15
Hi,

I followed the instruction at [http://ubuntuguide.org/#installmysqldatabaseserver](http://ubuntuguide.org/#installmysqldatabaseserver) to install lamp and proftpd sever.

It appears that lamps is running ok. But, proftpd is not quite right.

The ftp server directory is the web server directory.

Here is the problem:

So I created a user for myself and allowed it all access. But when I connect to the ftp server it says

Response:	331 Password required for user1.
Command:	PASS ******
Response:	230 Anonymous access granted, restrictions apply.

I can upload and rename files, but I cannot overwrite or delete files.  

It is the same story for every user.

---

### Post by CLI-Linux on 2007-09-18
My first inkling would be to say look at /etc/proftpd/proftpd.conf.

A lot of what you are saying sounds like it could be solved by changing a few options in the config file.

And remember that anything with '#' before it is commented out.

---

