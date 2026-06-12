---
title: "Percona and PHPMyAdmin"
date: 2012-12-21
forum: Server Platforms
---

### Post by alex2agent on 2012-12-21
Hi everyone, 

I'm very new to Linux.  Always been a Win user.  Just installed Ubuntu Server 12.04, so I can run a web server.  I've installed Nginx and Percona rather than Apache, since I've read that it's the better way to go... however, I'm used to running Apache with PHPMyAdmin.  Can PHPMyAdmin be used with NGinx and Percona?  I've just tried installing PHPMyAdmin with sudo apt-get install phpmyadmin... however, it's giving me a choice of Apache2, and Lighttpd.  I take it I'm doing something wrong, or will choosing one of these options work?

I have my MYSQL Server from my windows server that I wanted to merge with the new database (Ubuntu) in the long run. 

Thanks in advance.

---

### Post by rubylaser on 2012-12-21
Yes, this can be configured to work.  Here are some instructions for a LEMP stack with PHPMyAdmin.

[http://maketecheasier.com/install-lemp-server-in-ubuntu/2012/05/29]("http://maketecheasier.com/install-lemp-server-in-ubuntu/2012/05/29")

---

### Post by alex2agent on 2012-12-21
Oh, perfect!  Thanks so much.  I'll give that a try.  

I was working remotely last night, and had it sitting at the screen with the Apache2, Lighttpd option... must have accidentally hit the return key when switching back and forth from host to client because I accidentally chose "yes" to "configuring my database with phpmyadmin." ](*,)  I'll need to figure out what it did, because my site will no longer load other than with localhost.

---

