---
title: "Cannot get apache2 and cannot install mysql server?"
date: 2008-10-14
forum: Server Platforms
---

### Post by Wickd on 2008-10-14
Hi there

I do have a problem at the moment. I installed XAMPP, but decided to remove it, because I wanted to install Cacti, which required the use of various other php, sql and other programs. I uninstalled XAMPP successfully

I then proceeded to install the applications as indicated by the following tutorial: [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP"). I first started with the Apache 2 server, but when I tried to mount it, I get the following error:

ivan@Boomchiki:~$ sudo /etc/init.d/apache2 start
 * Starting web server apache2                                                  apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98 )Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

If someone could please help me. That would be fantastic

Thanks

---

### Post by bodhi.zazen on 2008-10-14
From the same page you referenced :

[https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20Apache]("https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20Apache")

If you have a FQDN (public IP and domain name) use that rather then localhost.

---

### Post by Wickd on 2008-10-14
> **bodhi.zazen said:**
> From the same page you referenced :

[https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20Apache]("https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20Apache")

If you have a FQDN (public IP and domain name) use that rather then localhost.

Haha, forgot to mention that I have already tried that, but for some reason I still get an error. So I reinstalled. The new error is as follows:

sudo /etc/init.d/apache2 start
 * Starting web server apache2                                                  (98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

Could this be that the localhost is in use by some file that might be related to XAMPP?

Thanks for the help so far

---

### Post by Wickd on 2008-10-14
Hey there. Thanks I seemed to have found the solution! I had to do 'n restart, because some of the processes were still running. Sorry for waisting your time

But thanks

---

### Post by bodhi.zazen on 2008-10-14
> **wickd said:**
> hey there. Thanks i seemed to have found the solution! I had to do 'n restart, because some of the processes were still running. Sorry for waisting your time

but thanks

lol

---

### Post by drubin on 2008-10-14
> **Wickd said:**
> Hey there. Thanks I seemed to have found the solution! I had to do 'n restart, because some of the processes were still running. Sorry for waisting your time

But thanks

> **Wickd said:**
> (98 )Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

when trying to start an application that needs to listen on a port number (mostly servers) and something says "socket already in use" it means that another instance of this server is running or you have a conflict another application is trying to litsen on the same port... 

You can always do a  This will tell you what application is listening on what port and you can see what is going on.
```
netstat  -l
```

---

