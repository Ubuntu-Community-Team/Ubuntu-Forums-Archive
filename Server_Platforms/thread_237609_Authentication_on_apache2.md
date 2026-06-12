---
title: "Authentication on apache2"
date: 2006-08-16
forum: Server Platforms
---

### Post by Icefox on 2006-08-16
How to protect folder/s in apache2 with user and password authentication?

---

### Post by crmanski on 2006-08-16
I would look at this...
[http://httpd.apache.org/docs/2.0/howto/auth.html](http://httpd.apache.org/docs/2.0/howto/auth.html)
and maybe this...
[http://httpd.apache.org/docs/2.0/howto/htaccess.html](http://httpd.apache.org/docs/2.0/howto/htaccess.html)

Just keep in mind that when you run the htpasswd command you should add sudo in front of it. So the first example that they show on the page would look like this...
```
sudo htpasswd -c /usr/local/apache/passwd/passwords rbowen
```

---

