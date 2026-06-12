---
title: "understanding webserver permissions"
date: 2005-06-04
forum: Server Platforms
---

### Post by drspin on 2005-06-04
Hello -

I have configured vsFTPd, Apache2, PHP, MySQL, SSL and it's all functioning beautifully. I have chown /var/www to wwwuser and chgrp to wwwuser. current fle permissions are rwx r-x r-x. I'm also using virtualhosts for the SSL and http sites so those work as well :)

wwwuser is configured with $home as /var/www

Is this an ideal scenario??

Here's my goal:
[http://blah.whateva.com](http://blah.whateva.com) REDIRECTS TO [https://blah.whateva.com](https://blah.whateva.com) thereby allowing no non-ssl connections. not sure the best way to do this.

I want to be able to FTP into the web folder to put files but I don't want to allow access outside of the $home (chroot maybe??) as I use the system on a daily basis and don't want people looking around on anything but the webserver.

I would like it if there was some kind of security for mysql connections from the webserver as there will be sensitive data kept in the database. 

Is there a way to encrpt the data stored in the database?

FINALLY, this may be for the howto section but... How can I set all of this to function in an environment where it would be as though it were running on a dedicated machine [chroot??] - while maintaing complete desktop functionality?

Thanks in advance!!

Cole

---

### Post by soce_32 on 2005-06-04
[QUOTE=drspin]Hello -

I have configured vsFTPd, Apache2, PHP, MySQL, SSL and it's all functioning beautifully. I have chown /var/www to wwwuser and chgrp to wwwuser. current fle permissions are rwx r-x r-x. I'm also using virtualhosts for the SSL and http sites so those work as well :)

wwwuser is configured with $home as /var/www

Is this an ideal scenario??

Here's my goal:
[http://blah.whateva.com](http://blah.whateva.com) REDIRECTS TO [https://blah.whateva.com](https://blah.whateva.com) thereby allowing no non-ssl connections. not sure the best way to do this.

I want to be able to FTP into the web folder to put files but I don't want to allow access outside of the $home (chroot maybe??) as I use the system on a daily basis and don't want people looking around on anything but the webserver.

I would like it if there was some kind of security for mysql connections from the webserver as there will be sensitive data kept in the database. 

Is there a way to encrpt the data stored in the database?

FINALLY, this may be for the howto section but... How can I set all of this to function in an environment where it would be as though it were running on a dedicated machine [chroot??] - while maintaing complete desktop functionality?

Thanks in advance!!

Cole[/QUOTE]
 You can run an instance of apache that redirects all of your http connections to your ssl server with something like Redirect Permanent [http://blah](http://blah) [https://blah](https://blah).  Check the manuals on that one though.

Generally don't run ftpd unless there you need anonymous access.  It doesn't sound like you need anon access, so you should consider scp/sftp for file transfers to beef up security.  There is a program in the repositories called scponly that allows users with accounts to transfer files, but not execute shell commands.

For your mysql server:  If it will only be accessed by web apps, it should only listen on localhost and not on external interfaces.  If other computers need to access the db directly, then mysql has allow/deny lists so that access can be somewhat restricted.  Conceivably, you could run things through an ssh tunnel since I don't think mysql does ssl yet.  Mysql does md5 hashes for things like passwords stored in the db, but performance would suffer is you encrypted everything.

Running servers from a desktop machine is not ideal, especially if security and availability are a concern.  Even if you chroot your services, you are still sharing the kernel, memory, i/o, etc, and your services will suffer as you do desktop tasks.  If you can afford it, put the servers on separate hardware.

---

### Post by LordHunter317 on 2005-06-04
[QUOTE=drspin] have chown /var/www to wwwuser and chgrp to wwwuser. current fle permissions are rwx r-x r-x.[/quote]This is generally a bad idea.  In the event of a compromise, now an attacker can modify the files you host on the web.

You want to have /var/www owned by whoever will edit the files in the web root.  If that's user drspin, then drspin should own the files in the webroot.  They should probably be group-owned by drspin as well.  Apache should generally get access under the permissions given to others.

The exception being configuration files, which should be group-owned www-data and have permissions no higher than 640.

> I want to be able to FTP into the web folder to put files but I don't want to allow access outside of the $home (chroot maybe??)VSFTP can do chroot'd FTP, but you don't want to use FTP anyway.  Using SFTP and proper permissions is probably a better solution anyway, given the fact SFTP is encrypted. SFTP doesn't support chroot but proper permissions avoids this from being an issue.

> I would like it if there was some kind of security for mysql connections from the webserver as there will be sensitive data kept in the database. Assuming the MySQL DB is local, then leaving networking support disabled is probably the best thing you can do.  Make sure the permissions on the database files themselves are sane, and don't use weak passwords on DB accounts.

> Is there a way to encrpt the data stored in the database?Nope, not without application-level support for it.

> FINALLY, this may be for the howto section but... How can I set all of this to function in an environment where it would be as though it were running on a dedicated machine [chroot??] - while maintaing complete desktop functionality?I'm not sure what you mean here -- Ubuntu as shipped in a desktop install can do this just fine.

---

### Post by LordHunter317 on 2005-06-04
[QUOTE=soce_32]For your mysql server:  If it will only be accessed by web apps, it should only listen on localhost and not on external interfaces.[/quote]No, it shouldn't listen on a TCP/IP interface **at all**, unless you're using JDBC or some other connectivity system that requires it (PHP does not).  In which case then you are correct.

>  Conceivably, you could run things through an ssh tunnel since I don't think mysql does ssl yet.It's done SSL for sometime.  Which is what you should do if you need secure access over the network since SSH would be terribly slow for that.  

> but performance would suffer is you encrypted everything.You can't trivally so it's a moot point.

---

