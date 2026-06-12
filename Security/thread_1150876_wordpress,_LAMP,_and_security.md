---
title: "wordpress, LAMP, and security"
date: 2009-05-06
forum: Security
---

### Post by nbo10 on 2009-05-06
Hi all,
I would like to install wordpress on my laptop so I can play around with keeping a blog. But I don't want to open my system up to attacks by running LAMP. Can anyone give me a guide to using LAMP and still keeping my system secure? Thanks

---

### Post by cdenley on 2009-05-06
**EDIT:** I think I may have mis-read your post. If you want to set up a lamp server to "play around with" without making it available to others over the internet, then keep reading.

Edit /etc/apache2/ports.conf so it looks something like:
```

NameVirtualHost *:80
Listen **127.0.0.1:**80

<IfModule mod_ssl.c>
    # SSL name based virtual hosts are not yet supported, therefore no
    # NameVirtualHost statement here
    Listen **127.0.0.1:**443
</IfModule>

```
This will make apache bind to the local loopback interface so it isn't listening for remote connections
```

$ sudo netstat -tlnp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 **127.0.0.1**:3306          0.0.0.0:*               LISTEN      2546/mysqld     
tcp        0      0 **127.0.0.1**:80            0.0.0.0:*               LISTEN      30770/apache2   
tcp        0      0 **127.0.0.1**:443           0.0.0.0:*               LISTEN      30770/apache2

```

---

### Post by bodhi.zazen on 2009-05-06
> **nbo10 said:**
> Hi all,
I would like to install wordpress on my laptop so I can play around with keeping a blog. But I don't want to open my system up to attacks by running LAMP. Can anyone give me a guide to using LAMP and still keeping my system secure? Thanks

Security is a process and there are many ways to secure your server .

Start with the security thread at the top of these forums. Then look at apache security (apache is secure outof the box, IMO, but it can be hardened).

See also : 

[http://httpd.apache.org/docs/1.3/misc/security_tips.html](http://httpd.apache.org/docs/1.3/misc/security_tips.html)

Wordpress - keep it up to date ;)

You can also look at mod_security : 

[http://blog.bodhizazen.net/linux/how-to-mod_security-ubuntu-904/](http://blog.bodhizazen.net/linux/how-to-mod_security-ubuntu-904/)

---

### Post by nbo10 on 2009-05-06
Thanks. Do I need to do anything with mysql?

---

### Post by bodhi.zazen on 2009-05-06
no, should be fine.

---

