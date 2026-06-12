---
title: "rewrite question"
date: 2011-08-05
forum: Server Platforms
---

### Post by PaulNL on 2011-08-05
Hello all, 
I have a problem and i hope you all can help.

I have made a rewrite rule for a subdomain  
```

<VirtualHost *:80>
DocumentRoot "/var/www/subdomain/document"
ServerName subdomain.domain.nl
RewriteEngine on
RewriteCond %{HTTP_HOST} ^([^.]+)\.domain\.nl$
RewriteRule ^/(.*)$ http://domain.nl/document/%1.html [L,R]
<Directory "/var/www/domain/document">
allow from all
Options +Indexes
</Directory>
</VirtualHost>

```my problem is
when i go to [http://subdomain.domain.nl](http://subdomain.domain.nl) the new url becomes [http://domain.nl/document/subdomain.html](http://domain.nl/document/subdomain.html)

what i want is that when i go to [http://subdomain.domain.nl](http://subdomain.domain.nl) the page with the name like the subdomain is loaded without the long url.

What have i made wrong.

---

### Post by Beacon11 on 2011-08-05
Umm... I'm not quite sure what you're wanting. Are you saying you want [http://subdomain.domain.nl](http://subdomain.domain.nl) to TRANSPARENTLY rewrite to [http://domain.nl/documents/subdomain.html](http://domain.nl/documents/subdomain.html) rather than changing the URL in the address bar? Is that your problem right now? If so, try changing the R in your rewrite rule to PT.

---

### Post by PaulNL on 2011-08-05
Yes i want to make it dynamic so when a page is not in the folder he has to use the default and when the page exist he has to use it. So for sub1.domain.nl he has to use sub1.html as first page, and for sub2.domain.html he has to use sub2.html.

So i don't have to make a lot of subdomains :)

PAul

---

### Post by Beacon11 on 2011-08-05
Okay, did you try changing the R in your rewrite rule to PT?

---

### Post by Beacon11 on 2011-08-05
Also, I bet your question would get more eyes if you changed the subject to something involving Apache (e.g. Need Help With Apache Rewrite Module).

---

