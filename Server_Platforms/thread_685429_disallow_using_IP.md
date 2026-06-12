---
title: "disallow using IP"
date: 2008-02-02
forum: Server Platforms
---

### Post by nuclearmaker on 2008-02-02
hye all.
how to disallow browse my home web server using IP ?
just allow user browser using [http://www.domain.com](http://www.domain.com) not using [http://151.98.0910](http://151.98.0910)


sorry for my english.

---

### Post by kirsche on 2008-02-06
Best choice is on layer 7 - virtual hosts in apache are your solution.
[http://httpd.apache.org/docs/2.0/vhosts/](http://httpd.apache.org/docs/2.0/vhosts/)

You need a way to control the content of the host header in a GET request - with the vhosts its pretty easy

---

### Post by nuclearmaker on 2008-02-13
kirsche ,thx for reply.
any tuts ?
im noob.:(

---

### Post by kirsche on 2008-02-14
Check the Virtual host section at the end of your httpd.conf (check the docs for apache).
For example:
```

<VirtualHost *:80>
   ServerName www.yourdomain.com
   ServerAlias www2.yourdomain.com
   ServerAdmin admin@yourdomain.com
   DocumentRoot /path/httpd/yourdomain
   ErrorLog /usr/local/apache2/logs/yourdomain/error_log
   CustomLog /usr/local/apache2/logs/yourdomain/acces_log common
</VirtualHost>

```

This will check the host header of an incoming http request for [www.yourdomain.com](www.yourdomain.com) or www2.yourdomain.com.
If it finds this, it uses the DocumentRoot defined in this section.

You can use your "normal" DocumentRoot as a cul-de-sac to tell people to use FQDN.

---

