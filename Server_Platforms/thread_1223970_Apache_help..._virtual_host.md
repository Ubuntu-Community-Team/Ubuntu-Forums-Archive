---
title: "Apache help... virtual host?"
date: 2009-07-26
forum: Server Platforms
---

### Post by lionsnob on 2009-07-26
Hi all,

I purchased a domain with dyndns and am using it using their Custom DNS service.  It works great!  I have a web server up and I opened the appropriate ports on my router and all is well.

However, I'd like to set it up where I can type something like "site1.example.com" that takes the user to a certain directory instead of using "www.example.com/site1".  Is this done using virtual hosts?  If not, how does one do this?  If it is done using virtual hosts, is there a guide that shows how it's done?

Thanks!

---

### Post by LepeKaname on 2009-07-26
Yes is using virtual hosts.

For example: (/etc/apache2/sites-enabled/000-default)

```
<VirtualHost *>
    ServerName  site1.example.com
    ServerAlias www.site1.example.com
    DocumentRoot /var/www/example/site1
</VirtualHost>
```

Don't forget to setup your DNS to forward all subdomains to your IP (at your's domain registrar).

---

