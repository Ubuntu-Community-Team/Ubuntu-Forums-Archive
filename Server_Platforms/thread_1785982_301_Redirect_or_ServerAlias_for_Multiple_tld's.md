---
title: "301 Redirect or ServerAlias for Multiple tld's?"
date: 2011-06-19
forum: Server Platforms
---

### Post by rainleader on 2011-06-19
Our company owns multiple tld's for our corporate  domain (e.g. company.com, company.net, etc.). Currently, we operate the  main website at "company.com".
  To have "company.net" et al forward/redirect to "company.com", should  we use a 301 redirect or setup a ServerAlias in Apache's virtual host  directive (we use name-based virtual hosting on Ubuntu Server).
  Are there any SEO penalties from one approach vs. the other (e.g.  Google thinking you have multiple sites with the same contact + flagging  it as spam)? 
  Thanks for the help.

---

### Post by craigcrawford114 on 2011-06-19
ServerAlias would be the proper way of doing this.

---

### Post by rainleader on 2011-06-19
> **craigcrawford114 said:**
> ServerAlias would be the proper way of doing this.

That's what I thought! Thanks.

---

### Post by laughing-boy on 2011-11-23
Hi

I think that if SEO is a priority, 301 is preferred, since it forces  the use of a single domain name. Using one domain instead of several, search engines don't split their efforts indexing content across different URLs.

I use the config below in my Virtual Hosts -  from the Apache website - to make sure only one domain name is actually  used. Other domain names can be set as ServerAlias items, and are redirected to the preferred one. 

It also  forces the use of 'www' before the domain name (good for SEO rankings to be consistent in this, too):-

RewriteEngine on
RewriteCond %{HTTP_HOST}   !^www\.example\.co\.uk [NC]
RewriteCond %{HTTP_HOST}   !^$
RewriteRule ^/(.*)         http://www.example.co.uk/$1 [L,R=301,QSA]

Hope it helps.

---

