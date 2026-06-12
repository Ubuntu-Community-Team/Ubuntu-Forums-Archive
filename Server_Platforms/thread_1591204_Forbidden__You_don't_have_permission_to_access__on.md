---
title: "Forbidden  You don't have permission to access / on this server."
date: 2010-10-08
forum: Server Platforms
---

### Post by tomtetlaw on 2010-10-08
When I try to access the /var/www/ folder through apache, which is at [http://tom-server/](http://tom-server/) from my Windows Machine, I get this error, even though it was working before with no changes:
```
Forbidden  You don't have permission to access / on this server. Apache/2.2.14 (Ubuntu) Server at tom-server Port 80
```

 ```
<Directory "/var/www/">
Order Allow,Deny
Allow from all
</Directory>
```

What could I do to fix it?
The apache server is on my Ubuntu Server(10.04.01) box and the computer that it trying to connect to it is running Windows XP.

---

### Post by Ryan Dwyer on 2010-10-08
Look in /var/log/apache2/error.log to see why it's denying access.

---

### Post by tomtetlaw on 2010-10-09
When I do that, I get this output:

```
[Sat Oct 09 13:57:59 2010] [error] [client 10.0.0.33] (13)Permission denied: access to /index.xhtml denied
[Sat Oct 09 13:57:59 2010] [error] [client 10.0.0.33] (13)Permission denied: access to /index.htm denied
[Sat Oct 09 15:43:28 2010] [error] [client 10.0.0.33] (13)Permission denied: access to /favicon.ico denied
[Sat Oct 09 15:44:12 2010] [error] [client 10.0.0.33] (13)Permission denied: access to /favicon.ico denied
[Sat Oct 09 16:29:38 2010] [error] [client 10.0.0.33] (13)Permission denied: access to /index.html denied
[Sat Oct 09 16:29:38 2010] [error] [client 10.0.0.33] (13)Permission denied: access to /index.cgi denied
[Sat Oct 09 16:29:38 2010] [error] [client 10.0.0.33] (13)Permission denied: access to /index.pl denied
[Sat Oct 09 16:29:38 2010] [error] [client 10.0.0.33] (13)Permission denied: access to /index.php denied

```

I used this to get it: ```
tail -f /var/log/apache2/error.log
```

---

### Post by tomtetlaw on 2010-10-09
bump

---

### Post by luvshines on 2010-10-09
Though I am not sure but this could help:
[http://ubuntuforums.org/showthread.php?t=1245839&page=2](http://ubuntuforums.org/showthread.php?t=1245839&page=2)

---

### Post by SeijiSensei on 2010-10-09
There are two levels of permissions that come into play with Apache:  filesystem permissions and permissions within Apache itself.

The /var/www directory needs to be readable by the "www-data" user that Apache runs as.  Usually this should be correct by default, but a quick "ls -l /var" will display the permissions.  All the files Apache needs to send also need to be readable by www-data.  They can be owned by other users as long as they are either world-readable or assigned to the www-data group and readable by that group's members.  The default installation assigns ownership of /var/www to root with 0755 permissions and 0644 permissions for the sample files therein. That means the directory and the files it contains are readable by anyone.  What ownership and permissions does /var/www and its files have on your system?

The other set of controls are enforced by Apache itself.  You've already set the allow/deny controls, but you may need some other permissions as well.  Take a look at /etc/apache2/sites-enabled/000-default for details.  You might need to add the Indexes option, for instance.

When you first install Apache on Ubuntu, it should be using the 000-default configuration.  Accessing the server from a browser should bring up the "It works!" page.  Was that true for you?

---

### Post by Vegan on 2010-10-09
```
sudo chmod -R 777 /var/www
```

---

### Post by Ryan Dwyer on 2010-10-09
DON'T chmod /var/www to 777. That's bad practice. Whatever you do, don't give "other" write access.

---

### Post by tomtetlaw on 2010-10-09
ls -l /var/ gives:

```

drwxr-xr-x  2 root root  4096 2010-10-08 06:42 backups
drwxr-xr-x 11 root root  4096 2010-09-29 15:44 cache
drwxrwxrwt  2 root root  4096 2010-04-14 06:52 crash
drwxr-xr-x 40 root root  4096 2010-09-29 15:45 lib
drwxrwsr-x  2 root staff 4096 2010-07-29 17:31 local
drwxrwxrwt  3 root root    60 2010-10-10 12:29 lock
drwxr-xr-x 13 root root  4096 2010-10-10 12:29 log
drwxrwsr-x  2 root mail  4096 2010-09-26 21:13 mail
drwxr-xr-x  3 root root  4096 2010-10-10 12:29 ncalrpc
drwxr-xr-x  2 root root  4096 2010-09-26 21:13 opt
drwxr-xr-x 11 root root   440 2010-10-10 12:30 run
drwxr-xr-x  5 root root  4096 2010-09-26 21:28 spool
drwxrwxrwt  2 root root  4096 2010-10-09 13:33 tmp
drwxrwxr-x  4 tom  tom   4096 2010-10-08 20:56 www

```

When I first installed it, it did have the It Works! message.

What I did just then was copied the stuff from 000-default into httpd.conf and it lets me view the pages now :)

---

