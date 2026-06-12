---
title: "apache2 restart error"
date: 2011-01-22
forum: Server Platforms
---

### Post by hoobjob23 on 2011-01-22
First time trying to create an apache2 server.  I have loaded/setup apache.  When I go to restart server, i recieve this error:

apache2: Syntax error on line 236 of /etc/apache2/apache2.conf: Syntax error on line 42 of /etc/apache2/sites-enabled/000-default: </VirtualHost> without matching <VirtualHost> section
   ...fail!

any ideas?

---

### Post by wongo888 on 2011-01-22
In "/etc/apache2/sites-enabled/000-default", search for something like this ahead of line 42 and uncomment it:

```

#<VirtualHost *:80>
```

You're probably closing a VirtualHost tag without opening it. Make it look like this:

```

<VirtualHost *:80>
```

Check with:

```
$ apache2ctl configtest

```

---

### Post by brtsos on 2011-01-23
Try this program :

[http://apache-switch.webuda.com/](http://apache-switch.webuda.com/)

It's very easy to use. You can turn on, turn off or restart apache server.

---

