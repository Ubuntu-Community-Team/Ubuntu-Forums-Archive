---
title: "Configuring Apache/FTP"
date: 2010-04-29
forum: Server Platforms
---

### Post by imbty on 2010-04-29
Ubuntu Server 9.10 with Webmin.

So I managed to get Samba to work perfectly (users can only access certain folders).

Now, I had Apache and ProFTPD working, but it seems to have stopped.

I can't start ProFTPD anymore.

I "Stopped" Apache, but whenever I try to start it again, it gives me this:

* Starting web server apache2
apache2: Syntax error on line 235 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/sites-enabled/000-default: No such file or directory
...fail!

From what I remember, the only thing I did before it stopped working was when I tried to change the document root directory to /home/user/user_site from /var/www . Bad move?

edit: I also tried reinstalling apache2 and proftpd and deleting things from /etc/proftpd and stuff, but still wouldn't work.

PS: I lied. I managed to allow only user1 and user2 to see /path/here. I don't want user3 to access /path/here, which I can do. But it's visible. It's no biggie, but it would be nice if user3 can't even see it as an existing directory. Thanks, guys.

---

