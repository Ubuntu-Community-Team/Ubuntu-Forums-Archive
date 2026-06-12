---
title: "Subdomains w/ Apache"
date: 2011-05-05
forum: Server Platforms
---

### Post by rainleader on 2011-05-05
I've got a server running Ubuntu 10.10 and LAMP that I'd like to configure a subdomain in Apache for. I have two websites that I want to serve:

mydomain.com (which resides in /var/www/mydomain)

AND

clients.mydomain.com (which resides in /var/www/clients)

I'm trying to use name-based virtual hosts and can't get the subdomain (clients.mydomain.com) working but mydomain.com resolves just fine.

Here's my configuration:

**/etc/apache2/sites-available/mydomain.com.conf**

```
<VirtualHost *:80>
DocumentRoot "/var/www/domain"
ServerName mydomain.com
<Directory "/var/www/mydomain">
allow from all
Options +Indexes
</Directory>
</VirtualHost>
```


**/etc/apache2/sites-available/clients.mydomain.com.conf**

```
<VirtualHost *:80>
DocumentRoot "/var/www/clients"
ServerName clients.mydomain.com
<Directory "/var/www/clients">
allow from all
Options +Indexes
</Directory>
</VirtualHost>
```

I also have an A record pointing clients.mydomain.com to the Ip of my server. Any idea on what's wrong?

---

### Post by a2j on 2011-05-06
both of these config files included in your main apache config file? check permissions maybe. 
what error do you get for the "clients" subdomain?

---

