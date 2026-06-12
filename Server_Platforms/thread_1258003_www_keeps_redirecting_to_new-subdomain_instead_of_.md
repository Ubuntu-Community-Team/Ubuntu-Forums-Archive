---
title: "www keeps redirecting to new-subdomain instead of www.domain"
date: 2009-09-04
forum: Server Platforms
---

### Post by MechaMechanism on 2009-09-04
[SOLVED]

I recently added a subdomain and as a result the subdomain [www.domain.tld]("http://www.domain.tld") now points to the new-subdomain.domain.tld instead of the domain.tld.  The domain.tld however continues to work as expected.  This is my first subdomain.  I tried all kinds of DNS stuff to no avail.

My DNS. @ means domain.tld.

A record.
@ 1.2.3.4

CNAME records.
www @
new-subdomain @

I apt-get apache2 and enable mod_rewrite via a2enmod rewrite and make no other changes to /etc/apache2.  Except in /etc/apache2/conf.d.  In /etc/apache2/conf.d I create the subdomain file called new-subdomain.  I made no other changes at all to the rest of the apache2 dir.  So what gives with www going to the new-subdomain?

<Directory /some/directory>
  Options FollowSymLinks
  AllowOverride Limit Options FileInfo
</Directory>

<VirtualHost *:80>
  DocumentRoot /some/directory
  ServerName new-subdomain.domain.tld
</VirtualHost>

---

### Post by windependence on 2009-09-05
Can you post your configuration files here? I have an idea what it might be.

-Tim

---

### Post by hessiess on 2009-09-05
you need to create a vhost for the `www' subdomain which is first and a second vhost for your own subdomain. Virtual hoats are resolved `bottom up', apache checks the last vhost to see if it matches the dommain, if it doesnt it checks the second-last one and so on. if none match the first gets displayed.

---

### Post by MechaMechanism on 2009-09-05
> **hessiess said:**
> you need to create a vhost for the `www' subdomain which is first and a second vhost for your own subdomain. Virtual hoats are resolved `bottom up', apache checks the last vhost to see if it matches the dommain, if it doesnt it checks the second-last one and so on. if none match the first gets displayed.Yeah that's what I did.  I made my www subdomain file and then it worked.

---

