---
title: "How to set up sub-domains"
date: 2006-08-28
forum: Server Platforms
---

### Post by lugos on 2006-08-28
Hello,

I have successfully set up an Ubuntu 6.06 webserver, thanks in large part to this great Ubuntu community.  I would now like to know how I can set up sub domains (I think that's what they're called).  For instance, I have [www.mydomain.com](www.mydomain.com).  I would now like to know how to set up mysubdomain.mydomain.com.

Thanks in advance for the help.

lugos

---

### Post by chrisfay on 2006-08-28
If you're running your own DNS then just add an A record with that subdomain pointing to your IP. Then just create a new virtual host in Apache sites-enabled using that new subdomain. 

If you aren't running a DNS, then ask whoever you are using to add an A record for that subdomain. Most registrars have a web interface allowing you to do it; you obviously would have to be using there DNS for it to make a difference.

---

### Post by lugos on 2006-08-28
> **chrisfay said:**
> If you aren't running a DNS, then ask whoever you are using to add an A record for that subdomain. Most registrars have a web interface allowing you to do it; you obviously would have to be using there DNS for it to make a difference.

Yahoo is my domain name registrar, and zoneedit provides my DNS service.  So I have to add an A record at Yahoo and add one at zoneedit?  They both provide web interfaces.

Can you point me to a tutorial or something that provides instructions on how to create the virtual hosts?

Thanks again for the help,
lugos

---

### Post by chrisfay on 2006-08-29
Since you're using Zoneedit as your DNS you only have to add the A record there. If I remember correctly its a very straigtforward and simple task.

As far as adding a virtual host in apache, assuming you're using Apache2:

Locate the file ```
/etc/apache2/sites-enabled/000-default
```

Add something like this to the end:
```
<VirtualHost *>
DocumentRoot "/var/www/subdomain/"
ServerName sub.domain.tld
<Directory "/var/www/subdomain/">
allow from all
Options -Indexes
</Directory>
</VirtualHost>
```

Save and restart apache and it should route requests for sub.domain.tld to your new subdomain. You obviously need to replace "sub.domain.tld" with the subdomain you chose and "/var/www/subdomain" with the location of your subdomains document root.

---

