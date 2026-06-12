---
title: "Unable to start Apache"
date: 2011-12-07
forum: Server Platforms
---

### Post by jbru on 2011-12-07
Hi,

So I've recently inherited an Ubuntu server (10.10) that was set up by someone else and I don't have access to any notes or documentation on it, though from what I've seen so far, very little was done to it.

I'm in the early stages of setting it up with Nagios.  I knew that apache was already loaded on the server but I wanted to start it with fresh default settings so I ran

```

sudo apt-get purge apache2
sudo apt-get install apache2

```

It installed but when I attempt to start it. I receive the following error.

```

username@linux:/$ sudo /etc/init.d/apache2 start
 * Starting web server apache2                                                                                                                                                                                                               apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
Action 'start' failed.
The Apache error log may have more information.
```

I'm very noobish when it comes to apache so I'm not quite sure how to go about finding out what is already using the address.  

I've searched through the forums and employed some of the common solutions: (yes, I'm running as sudo. no, there are no other instances of apache running).  The logs stored in /var/logs/apache2/ are empty.

I'm at a bit of a loss as to what else I should be looking at.  Any ideas?

---

### Post by jbru on 2011-12-07
Alright, so I've determined that httpd is listening on port 80 and that is most likely why Apache can't start.

```
username@linux:/var/www$ sudo netstat -ltnup
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN      898/mysqld.bin
tcp        0      0 127.0.0.1:21            0.0.0.0:*               LISTEN      14287/vsftpd
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      13342/sshd
tcp6       0      0 :::80                   :::*                    LISTEN      1388/httpd
tcp6       0      0 :::22                   :::*                    LISTEN      13342/sshd
```

now my problem is that when I kill the httpd process, it instantly starts listening on the port again...

---

### Post by dapperdanny77 on 2011-12-07
try
apachectl stop
apachectl start

---

### Post by jbru on 2011-12-07
> try
apachectl stop
apachectl start

Command not found.

A new development, though, after removing apache2 (sudo apt-get purge apache2)  I've discovered that the server is serving up a website when browsing localhost. o_O

httpd process is still listening on port 80.

Now I'm really lost.  I'm not much of a webserver guy...

---

### Post by Lars Noodén on 2011-12-07
If Apache2, rather than 1.3.x, is installed then it should be:

```

apache2ctl stop
apache2ctl start

```

It might also be that either lighttpd or nginx is installed instead of Apache.

---

### Post by jbru on 2011-12-07
> **Lars Noodén said:**
> If Apache2, rather than 1.3.x, is installed then it should be:

```

apache2ctl stop
apache2ctl start

```

It might also be that either lighttpd or nginx is installed instead of Apache.

Thanks!  Apache2ctl helped me figure out that another instance of apache is still installed.  Apparently the AMP part of this LAMP server is entirely stored in /opt/

It's a Wordpress installation as well if that clue's anyone in.

It's not listed as an installed package with dpkg or apt-get.  I'm still trying to figure out how to remove it safely...

---

