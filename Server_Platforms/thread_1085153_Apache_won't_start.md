---
title: "Apache won't start"
date: 2009-03-02
forum: Server Platforms
---

### Post by PreciousBodilyFluids on 2009-03-02
Hello - I'm fairly new to Linux and Ubuntu, and I'm trying to run a webserver using Apache.

I updated some virtual host files, and did a sudo /etc/init.d/apache2 reload in order to try out my changes, but found that nothing came up at all when I tried to visit my site.

Then I did a sudo /etc/init.d/apache2 restart and got:
 * Restarting web server apache2                                                httpd (pid 23569?) not running
                                                          [fail]

After searching a bit, I decided to stop apache, delete /var/run/apache2.pid and start it up again. So, that went:

sudo /etc/init.d/apache2 stop
 * Stopping web server apache2                                                  httpd (pid 23569?) not running
                                                                         [ OK ]

sudo rm /var/run/apache2.pid

sudo /etc/init.d/apache2 start
 * Starting web server apache2                                           [fail]

Just a fail, no error message or anything. I tried it without the sudo, to see what kind of error message I'd get, and I got:

/etc/init.d/apache2 start
 * Starting web server apache2                                                  (13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
                                                                         [fail]

And since then, nothing I've tried is working:

sudo /etc/init.d/apache2 start
 * Starting web server apache2                                           [fail]

sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                httpd (no pid file) not running
                                                                         [fail]


I don't know what I'm supposed to do if I don't even get an error message. Can anyone tell me what I should do next?

Thanks

---

### Post by volkswagner on 2009-03-02
Check logs.  

```
cat /var/log/apache2/error.log
```

If the problem occurred after modify of vhosts, I would disable all sites, except the default.  Then try to start apache.

---

### Post by MountainX on 2009-04-01
I'm having the same issue. Regarding the proposed solution:

> cat /var/log/apache2/error.log

Checking the logs doesn't work. Part of the error message is "Unable to open logs"

---

### Post by justislav on 2010-12-14
> **MountainX said:**
> I'm having the same issue. Regarding the proposed solution:



Checking the logs doesn't work. Part of the error message is "Unable to open logs"

No, apache can't open log specified for host.

Try to craete dirs specified in
```

    ErrorLog logs/baikal.error_log
    TransferLog logs/baikal.access_log

```

apache started after I created dir
```
/etc/apache2/logs
```
with my virtualhost
```

<VirtualHost *:80>

    ServerName baikal

    DocumentRoot /var/www/baikal

    ErrorLog logs/baikal.error_log
    TransferLog logs/baikal.access_log
    LogLevel warn

    <Directory "/var/www/baikal">
      Order allow,deny
      Allow from all
    </Directory>

</VirtualHost>

```

---

