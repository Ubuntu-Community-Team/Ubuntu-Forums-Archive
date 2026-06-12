---
title: "[SOLVED] Apache httpd.conf Redirect Subdomain"
date: 2008-09-07
forum: The Cafe
---

### Post by firefly2442 on 2008-09-07
Hello all,

I'm trying to do this without using mod_rewrite in Apache.  Basically, I want to be able to redirect [http://www.mydomain.com/webmail/](http://www.mydomain.com/webmail/) to [https://www.mydomain.com/webmail/](https://www.mydomain.com/webmail/) as well as my subdomain [http://webmail.mydomain.com](http://webmail.mydomain.com) to [https://webmail.mydomain.com](https://webmail.mydomain.com)

Here is my httpd.conf file:

```
NameVirtualHost *:80
<VirtualHost *:80>
</VirtualHost>
<VirtualHost *:80>
    ServerName webmail.mydomain.com
    ServerAlias www.webmail.mydomain.com
    DocumentRoot /var/www/html/webmail
	Redirect permanent webmail.mydomain.com https://webmail.mydomain.com
</VirtualHost>

#This works ->
Redirect permanent /webmail https://webmail.mydomain.com

```

I'm not quite sure what I'm doing wrong, can anyone offer advice?

Thanks in advance! :)

---

### Post by firefly2442 on 2008-09-07
I was able to get it working with this:

```
Redirect permanent / https://webmail.mydomain.com
```

---

