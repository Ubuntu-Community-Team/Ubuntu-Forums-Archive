---
title: "Apache2 not starting anymore"
date: 2009-02-03
forum: Server Platforms
---

### Post by 2smooth on 2009-02-03
Apache does not start anymore, i did an upgrade of alle pakages, but i'm not sure if this is causing the problem.

When i try to start apache manually or automatically after reboot, not happens. No error, 

* Starting web server apache2                                                                                                                                   [ OK ]

There's no error message in error.log, neither in syslog...

I checked with

ps ax | grep -i apache

Nothing.

---

### Post by cdenley on 2009-02-03
Does this command work? What output does it give you?
```

sudo APACHE_RUN_USER=www-data APACHE_RUN_GROUP=www-data apache2 -X

```

---

### Post by 2smooth on 2009-02-03
This gives me nothing, also no error in the error.log or syslog

Only this notice in the error log each time i try to start apache

[notice] ModSecurity for Apache 2.1.5 configured - Apache/2.2.8 (Ubuntu) mod_defensible/1.2

---

### Post by 2smooth on 2009-02-04
```

# /usr/sbin/apache2 -X
apache2: bad user name ${APACHE_RUN_USER}

```

```

in the output of strace /usr/sbin/apache2 -X

i also see these lines:
access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
..cut..
access("/etc/ld.so.preload", R_OK) = -1 ENOENT (No such file or directory)
..cut..
access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
..cut..

```

---

### Post by cdenley on 2009-02-04
> **2smooth said:**
> ```

# /usr/sbin/apache2 -X
apache2: bad user name ${APACHE_RUN_USER}

```

That command won't work, which is why I posted the one which sets the variables needed by apache.

---

### Post by albinootje on 2009-02-04
> **2smooth said:**
> Apache does not start anymore
Can you post the output of the following :
```

dpkg -l|grep -i apache
sudo apache2ctl configtest
sudo apache2ctl restart
sudo apache2ctl status

```

---

### Post by 2smooth on 2009-02-04
> **cdenley said:**
> That command won't work, which is why I posted the one which sets the variables needed by apache.

As i said before i did run your command but that also didn't work..
It terminates quietly..

**No **message are added to errorlog, syslog, messages

---

### Post by 2smooth on 2009-02-04
> **albinootje said:**
> Can you post the output of the following :
```

dpkg -l|grep -i apache
sudo apache2ctl configtest
sudo apache2ctl restart
sudo apache2ctl status

```

```

**dpkg -l|grep -i apache**
ii  apache2                               2.2.8-1ubuntu0.3                      Next generation, scalable, extendable web se
ii  apache2-mpm-prefork                   2.2.8-1ubuntu0.3                      Traditional model for Apache HTTPD
ii  apache2-utils                         2.2.8-1ubuntu0.3                      utility programs for webservers
ii  apache2.2-common                      2.2.8-1ubuntu0.3                      Next generation, scalable, extendable web se
ii  libapache2-mod-php5                   5.2.4-2ubuntu5.4                      server-side, HTML-embedded scripting languag
ii  libapr1                               1.2.11-1                              The Apache Portable Runtime Library
ii  libaprutil1                           1.2.12+dfsg-3                         The Apache Portable Runtime Utility Library


**apache2ctl configtest**
Syntax OK
# apache2ctl restart
httpd not running, trying to start
# ps aux | grep -i apache
root      8353  0.0  0.0   5164   916 pts/0    S+   16:58   0:00 grep -i apache
# apache2ctl status

**apache2ctl restart**
httpd not running, trying to start


**apache2ctl status**

Looking up localhost
Making HTTP connection to localhost
Alert!: Unable to connect to remote host.

lynx: Can't access startfile http://localhost/server-status



```

I my system is broken, can i do a pretty fresh reinstall of all packages **remotely **over ssh?

---

### Post by albinootje on 2009-02-04
> **2smooth said:**
>  I my system is broken, can i do a pretty fresh reinstall of all packages **remotely **over ssh?

Thanks for the output.
I suggest you do the following :
```

sudo cp -arv /etc/apache2 /etc/apache2-backup
sudo apt-get remove --purge apache2 apache2-* apache2.*
--> make sure you take notice of what apt-get wants to remove with that!
sudo rm -rf /etc/apache2/*

```
After that install apache again.

---

### Post by 2smooth on 2009-02-04
Thanks a lot, i've reinstalled apache and it seems that it is working again. 

I hope that after reconfiguring apache everything works fine again.

---

