---
title: "Apache Monitor"
date: 2006-05-27
forum: Server Platforms
---

### Post by amitroy5 on 2006-05-27
I run a server on Ubuntu using Apache2. I was wondering if it was possible to have a visual monitor. For example, where everyone on the website currently is, just so I can monitor the activities on the webserver. Thanks!

---

### Post by adamkane on 2006-05-27
ISP Setup:
[http://www.howtoforge.com/perfect_setup_ubuntu_5.10](http://www.howtoforge.com/perfect_setup_ubuntu_5.10)

See Webalizer section.

---

### Post by fdoving on 2006-05-28
I recommend using apache2s own server-status
With 'ExtendedStatus On' it does what you want.

This is how i configure it in /etc/apache/apache2.conf:
```

ExtendedStatus On
<Location /server-status>
    SetHandler server-status
    Order deny,allow
    Deny from all
    Allow from  192.168.0.100
</Location>

```

Now reload apache:
```

/etc/init.d/apache2 reload

```

And go to [http://yourwebsite.com/server-status](http://yourwebsite.com/server-status)

Make sure you've added your IP to 'Allow from' in the config.


- Frode

---

### Post by amitroy5 on 2006-05-28
When I try to use ExtendedStatus, I get the following error:

httpd not running, trying to start
(13)Permission denied: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs


How can I resolve this?

---

### Post by amitroy5 on 2006-05-28
I got it to work. But I was looking more for a visual monitor that I can keep running on the desktop.

---

