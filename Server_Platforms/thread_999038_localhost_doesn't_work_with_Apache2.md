---
title: "localhost doesn't work with Apache2"
date: 2008-12-01
forum: Server Platforms
---

### Post by Maya-PSK on 2008-12-01
Hi to all. 
I've just tried to install Apache on my Ubuntu Box but I can't run the server.
The problem is:

```

enrico@enrico-desktop:~/httpd-2.2.10$ sudo /usr/local/apache2/bin/apachectl start
httpd: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

```

What is wrong?

I've installed it with the 3 laws:
```
./configure
make
make install 
```

Thanks! :D


P.S: Is this the right categories? Sorry for my English ;)

---

### Post by Iowan on 2008-12-01
[This]("https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20Apache") help page discusses Apache.  The troubleshooting section even covers the "Could not reliably determine..." message you got.

BTW, Apache2 (maybe not the VERY latest/greatest) is available in the repositories via Synaptic, Aptitude, or apt-get.  Saves you having to compile.

---

### Post by Maya-PSK on 2008-12-01
Solved!
I've reboot and now it works! 
But the warning remains :-/

---

### Post by LordTiggy on 2008-12-01
I have that warning too ... must be because we run it locally ... so no real domain is used :)

---

### Post by K.Mandla on 2008-12-01
Moved to Server Platforms.

---

### Post by Iowan on 2008-12-01
The tips in the help page didn't work?
Another thing to try - edit */etc/hosts* file. Add a line so it looks similar to: ```
127.0.0.1 localhost
127.0.1.1 servername.domain servername
```

---

### Post by Maya-PSK on 2008-12-02
Thanks to all , now it works!

---

### Post by Maya-PSK on 2008-12-04
Excuse me,  i've got another problem. 
I've changed the DocumentRoot.
When I want to view a file an error occurs:

```
403 Forbidden

You don't have permission to access /NameofFile.html on this server.
```

What is the problem?

EDIT: Solved with sudo chmod -R a+rwx /home/enrico/www/NameofFile.html , but i must do this command for every file on my directory :-/

---

