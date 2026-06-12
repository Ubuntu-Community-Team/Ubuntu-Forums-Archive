---
title: "Apache2 start"
date: 2008-10-29
forum: Server Platforms
---

### Post by malatoforte on 2008-10-29
how the title says i'v got a problem with apache2
when i do the command /etc/init.d/apache2 start (and restart too) got the same error msg:

 * Restarting web server apache2
httpd (no pid file) not running
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
                                                                             [fail]

how can i do to resolve this problem ???
but the more strange thing is who until 2 days ago it work very good...but the current went down...and when i restart all begin to have all this problem...
(sorry for my bad english)
hope in a fast replie
Anticipate thx

---

### Post by lykwydchykyn on 2008-10-29
Well, it looks like something else is bound to port 80. Can you do:
```

sudo netstat -tunap

```

---

### Post by malatoforte on 2008-10-29
sorry guys...i've resolved this problem...

i do this command as root:
lsof -i :80

and see the service who take busy the port 80 
was nepenthes...i removed it and now apache begin to work again...

---

### Post by lykwydchykyn on 2008-10-29
What are you trying to accomplish with php5 restart?  php is not a service, it is called by apache when required.

---

### Post by malatoforte on 2008-10-29
and so why apache dont load php?
look
click here 
[http://blackserver.hopto.org/forum/index.php](http://blackserver.hopto.org/forum/index.php)

---

### Post by lykwydchykyn on 2008-10-29
Did you install libapache2-mod-php5?

---

### Post by malatoforte on 2008-10-29
yes

---

### Post by Coreigh on 2008-10-29
Sounds like a config error. Take a look at this:
[http://www.linuxquestions.org/questions/linux-newbie-8/could-not-bind-to-address-0.0.0.080-405377/]("http://www.linuxquestions.org/questions/linux-newbie-8/could-not-bind-to-address-0.0.0.080-405377/")

---

### Post by lykwydchykyn on 2008-10-29
alright, check for errors in /var/log/apache2/error_log.  Does apache2 restart now without errors?

Also, make sure the php module is loaded:
```

sudo a2enmod php5

```

---

### Post by Vegan on 2008-10-29
try 

sudo a2enable php5
sudo /etc/init.d/apache2 force-restart

---

### Post by malatoforte on 2008-10-29
Module php5 installed; run /etc/init.d/apache2 force-reload to enable.
root@paz-b63801870e4:~# /etc/init.d/apache2 force-reload
 * Reloading web server config apache2                                       [ OK ]

but still dont support php...

---

