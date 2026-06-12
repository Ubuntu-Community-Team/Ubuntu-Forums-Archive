---
title: "Securing mythweb - chown error"
date: 2007-08-26
forum: Server Platforms
---

### Post by Seantiago on 2007-08-26
Hi there. I'm trying to secure my mythweb setup by following these instructions here:

[http://mythtv.org/wiki/index.php/MythWeb#Apache_Configuration](http://mythtv.org/wiki/index.php/MythWeb#Apache_Configuration)

However, I've run into a probably very simple and silly snag, and it's got me stumped.

Basically, after I've created the httpd-passwords file and try to change the ownership with this command:

```
chown apache.apache /etc/httpd/conf/httpd-passwords
```

it tells me that apache.apache is an invalid user. That's all.

I'm running feisty if that makes any difference.

Thank you.

---

### Post by a9k on 2007-08-26
Ubuntu uses "www-data" not "apache" as the user and group for webservers.

---

### Post by Seantiago on 2007-08-26
So that command should look something more like this:

```
chown www-data:www-data /etc/apache2/httpd-passwords
```?

---

### Post by Seantiago on 2007-08-26
It must be, because that got it to work totally awesomely!

---

