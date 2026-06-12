---
title: "two domains with apache2"
date: 2010-09-11
forum: Server Platforms
---

### Post by marianolatorre on 2010-09-11
Hi, I have to host two domains in one server, I have done this before in other machines. I use to configure bind9 zones and apache, using servername. This time this does not work.

I have www.example1.com and www.example2.com

Their document root for each domain is /var/www/example1 and /var/www/example2

their public ip is 190.10.X.Y

When I enter www.example1.com all runs fine, but when I type www.example2.com in the web browser it redirects me to http://190.10.X.Y/example2...and obviously thats not what I want...

Please help!

---

### Post by johngreth on 2010-09-11
what is in your sites-enabled file? It should look something like this:
```

<VirtualHost *>
ServerName example1.com
ServerAdmin webmaster@host.foo.com
DocumentRoot /www/docs/example1.com
</VirtualHost>
<VirtualHost *>
ServerName example2.com
ServerAdmin webmaster@host.foo.com
DocumentRoot /www/docs/example2.com
</VirtualHost>

```

this may also help: [http://httpd.apache.org/docs/1.3/vhosts/name-based.html](http://httpd.apache.org/docs/1.3/vhosts/name-based.html)

---

