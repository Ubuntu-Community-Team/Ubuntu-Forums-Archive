---
title: "ProFTPd permission denied?"
date: 2010-09-30
forum: Server Platforms
---

### Post by jawsykilla on 2010-09-30
Okay I have set up my Ubuntu Server 10 machine recently and I have got the XAMPP package installed. Now the web side of things was dead easy and straight forward. 

Now proftpd has been giving me trouble all day. I have basically created 2 users on my machine I have given their home directories the permission 755 so that only the owner can change their stuff. 

When I log in through ftp I get taken to the home directory no problem but I cannot do anything but read and execute, yet this user owns the directory? The only way I can get it to work is set the user as a member of the group "nogroup" which was specified in the proftpd.conf and then apply 775 permissions to the home directory. But then this means that all of my users can edit each others home directories?

Any ideas?

Cheers,
Jawsykilla

---

