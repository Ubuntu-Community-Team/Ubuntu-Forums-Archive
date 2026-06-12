---
title: "Virtual host question"
date: 2006-07-28
forum: Server Platforms
---

### Post by shendric on 2006-07-28
If this has been discussed before, please feel free to send me to the thread.  I couldn't seem to find one that dealt with this exactly.

I'm setting up a virtual host on my Apache server on Drake.  I have added the following file to my /etc/apache2/sites-available directory:

NameVirtualHost 127.0.0.1
<VirtualHost 127.0.0.1:80>
  ServerName mysite.com
  ServerAlias [www.mysite.com](www.mysite.com)
  DocumentRoot /var/www/MySite/
  CustomLog /var/log/apache2/mysite.com-access.log combined
  ErrorLog /var/log/apache2/mysite.com-error.log
</VirtualHost>

And I've added the following line to /etc/hosts:

127.0.0.1	mysite.com

I restarted apache, and then typed in mysite.com into my browser.  I went directly to the /var/www directory, rather than the /var/www/MySite/ directory.  Can anyone tell me what I've done wrong?

Just wanted to add that I've kept the default file in /etc/apache2/sites-available.

---

### Post by vanilla on 2006-07-29
a2ensite is the command you looking for.

---

### Post by shendric on 2006-07-29
> **vanilla said:**
> a2ensite is the command you looking for.

Oh, right.  Got to enable the site.  Thanks.  That works fine now.

Sean

---

