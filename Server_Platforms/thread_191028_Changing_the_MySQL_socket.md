---
title: "Changing the MySQL socket"
date: 2006-06-07
forum: Server Platforms
---

### Post by bertilow on 2006-06-07
In case someone runs into the same problem I did, I'll post the solution here:

I needed to change the location of the MySQL socket (to be the same as in the production server). The default location for the MySQL packages in Dapper is "/var/run/mysqld/mysqld.sock", but I needed it to be "/tmp/mysql.sock".

I Breezy all I had to do was edit the file "/etc/mysql/my.cnf" changing the address for "socket" there (in three places!). In Dapper that didn't work. The server started all right at first, but after a reboot everything fell apart.

**As it turns out, in Dapper you need to change the address for the pid-file as well. That's also in "/etc/mysql/my.cnf" but just in one place. The pid-file for some reason has to be in the same directory as the socket, in my case "/tmp/mysql.pid".**

You also have to change the address for the socket in "/etc/mysql/debian.cnf" (in two places!). I don't remember anymore if that was needed in Breezy too.

(Why can't there be just one place to configure all this?!)

BTW, I didn't figure all this out by myself. The honor goes to Akkana:

[http://www.shallowsky.com/blog/index.cgi/programming/mysqldirs.html](http://www.shallowsky.com/blog/index.cgi/programming/mysqldirs.html)

---

### Post by LordHunter317 on 2006-06-07
[QUOTE=bertilow](Why can't there be just one place to configure all this?!)[/quote]Because the people writing MySQL's configuration system are beyond incompetent.

---

### Post by adamkane on 2006-06-07
Ouch!  Great thread!

---

