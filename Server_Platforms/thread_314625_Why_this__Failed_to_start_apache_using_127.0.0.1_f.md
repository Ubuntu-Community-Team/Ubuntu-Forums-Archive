---
title: "Why this : Failed to start apache using 127.0.0.1 for ServerName"
date: 2006-12-07
forum: Server Platforms
---

### Post by Bill007 on 2006-12-07
How to solve this warning

Where to look ??

Failed to start apache :

 * Starting apache 2.0 web server...
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

Regards Bill007

---

### Post by chrisfay on 2006-12-08
In a terminal type:

```
sudo vi /etc/apache2/apche2.conf
```

Find the line that looks like this:

```
ServerName "127.0.0.1"
```

And either change it to your fqdn if you have one, or localhost.

```
:wq
```

Then restart apache:

```
sudo apache2ctl restart
```

If that doesn't work, try removing the ServerName altogether and try it. The error will show up in your logs but shouldn't stop Apache from working.

---

### Post by tturrisi on 2006-12-08
The error message means that apache failed to find a fully qualified domain name and that it IS starting and is using the localhost ip instead of an absent fqdn.

---

### Post by phplion on 2008-05-31
> **chrisfay said:**
> In a terminal type:

```
sudo vi /etc/apache2/apche2.conf
```

Find the line that looks like this:

```
ServerName "127.0.0.1"
```

And either change it to your fqdn if you have one, or localhost.

```
:wq
```

Then restart apache:

```
sudo apache2ctl restart
```

If that doesn't work, try removing the ServerName altogether and try it. The error will show up in your logs but shouldn't stop Apache from working.

Thanks

---

