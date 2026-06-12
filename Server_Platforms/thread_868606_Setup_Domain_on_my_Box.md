---
title: "Setup Domain on my Box"
date: 2008-07-24
forum: Server Platforms
---

### Post by Initsil on 2008-07-24
Hey everyone :)

I have a domain that I bought. I also have a linux box running ubuntu server 8.04. Could someone tell me how I could setup my domain on this box, so if someone goes to my_domain.com it would goto my box's apache server.

Thanks
Initsil

---

### Post by pdwerryhouse on 2008-07-24
Your domain registrar should have a web-based tool that will let point your new domain name at your box's IP address.

If you want to go further than that and run a domain-name server yourself, then you'll have to read up about BIND (for example) and then install the bind9 package. But frankly, for one simple host, I'd just use your registrar's web tool, if I were you.

---

### Post by Initsil on 2008-07-24
> **pdwerryhouse said:**
> Your domain registrar should have a web-based tool that will let point your new domain name at your box's IP address.

If you want to go further than that and run a domain-name server yourself, then you'll have to read up about BIND (for example) and then install the bind9 package. But frankly, for one simple host, I'd just use your registrar's web tool, if I were you.

That's awesome! Thanks. But, if I wanted to give the domain a home directory instead of /var/www how would I do that? 

Also if I make multiple domains on the site how would I give them their own private directory?

---

### Post by pdwerryhouse on 2008-07-24
The /var/www directory is set by the DocumentRoot directive, under /etc/apache2/sites-available/default.

If you want to have multiple domains with different content, then look at the "VirtualHost" and "NameVirtualHost" directives.

---

