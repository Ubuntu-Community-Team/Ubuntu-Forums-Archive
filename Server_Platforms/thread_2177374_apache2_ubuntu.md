---
title: "apache2 ubuntu"
date: 2013-09-28
forum: Server Platforms
---

### Post by remo2 on 2013-09-28
how do you define your server to listen to your own IP adress and port 8080?
    where is defined ( the file location and name) on dedicated server by default allowed number of requests?
    where is defined (the file location and name) server TimeOut value and what does it mean?

---

### Post by pqwoerituytrueiwoq on 2013-09-28
/etc/apache2/ports.conf
you can run multiple ports for the same thing, if you want to
i think you are looking for line 96 of /etc/apache2/apache2.conf

---

### Post by Lars Noodén on 2013-09-28
All your settings are found in your default virtual host's configuration file.  Unless you've changed or added anything, that should be /etc/apache2/sites-enabled/000-default.conf

The ports your server listens on are set in /etc/apache2/ports.conf.  Just change the line or add another.  Your [VirtualHost](http://httpd.apache.org/docs/2.4/mod/core.html#virtualhost) directive in your vhost configuration file will have to match what you are listening on.  In other words, the setting must be made in two files.

The [TimeOut](http://httpd.apache.org/docs/2.4/mod/core.html#timeout) settings are something that you can change.

You'll have to have the server reload for any changes to take effect.

```

sudo service apache2 reload

```

---

### Post by remo2 on 2013-09-28
thanks

---

### Post by remo2 on 2013-09-28
what about first question, i thought i can define port by command? but im not sure is correct : Listen 8080 or just Listen 80

---

### Post by Lars Noodén on 2013-09-28
The port to listen to is set in ports.conf  If you want to serve data on port 8080 instead of port 80 then you need to remove the line that says "Listen 80" and replace it with a line that says "Listen 8080"  Then have the server reload your configuration for the changes to take effect.  

Another thing which might come in handy both now and later is testing the config file for correct syntax.

```

apache2ctl configtest

```

Doing that after major changes will help find any mistakes.  Of course it is possible to still make mistakes, but that will catch the obvious ones.

---

