---
title: "How to add subdomain to DNS if hosting myself?"
date: 2009-11-17
forum: Server Platforms
---

### Post by arhar on 2009-11-17
Hi all,
 
I'm trying to add a subdomain to Ubuntu 9.04 server, which I'm using as a dev server, and hosting myself (under the desk :)). I've used free DynDNS service to give it a nice name, so I can connect to it as [name.dynalias.com]("http://www.name.dynalias.com"), instead of the IP address.
 
My question is - I need to add a subdomain to it. Is it possible to do it for free, and if yes, what do I need to do? It seems an obvious solution would be to buy a domain name, and have it forwarded to [name.com]("http://www.name.com"), instead of [name.dynalias.com]("http://www.name.dynalias.com"), and then setup [subdomain.name.com]("http://www.subdomain.name.com") but that would require $$$. 
 
Is there a way to do that for free, while hosting everything myself? I'm trying to see if I can set up something like subdomain.name.dynalias.com... would that be possible?
 
Thank you!

---

### Post by shred_eng on 2009-11-17
hi, im not too savvy with domain - subdomain and exactly how it works but....

i have a host name with dyndns and i decided to get another one as you can have many for free, so i used joomla and made a page for my 2nd hostname and took note of the url of the page which my 2nd host name used on my 1st hosts website and did a redirect using htaccess so if i type in my 1st hosts url i go to its pages - menus and if i type my 2nd hosts url i go to its pages - i dont know if this is the kind of thing you require but it kinda works .

---

### Post by uberamd on 2009-11-17
I used everydns.com for mine (free also) but basically you create a new CNAME on your existing domain, set the HOST to *something*.yourdomain.com and the VALUE to yourdomain.com. Then in apache you configure it accordingly.

```
<VirtualHost *>
ServerName something.yourdomain.com
DocumentRoot /home/httpd/htdocs/subdomain/
</VirtualHost>
```

Here is a screen. Notice my type A record points to my IP, my CNAME record for [www.uberamd.org](www.uberamd.org) points to uberamd.org, then each CNAME for my subdomains just has the value uberamd.org
[IMG]http://steve.blogme.us/wp-content/uploads/2009/11/screenshot.png[/IMG]

---

### Post by BQAggie2006 on 2009-11-17
It looks like subdomains/CNAMEs are only available with a Dynamic DNS Pro account ($15/yr): [https://www.dyndns.com/services/upgrades/](https://www.dyndns.com/services/upgrades/)

---

