---
title: "&quot;php_value session.auto_start on&quot; Not working in my .htaccess file"
date: 2017-08-24
forum: Server Platforms
---

### Post by do734 on 2017-08-24
So I'm fairly new to Ubuntu but I've worked with web hosts that have .htaccess files with the exact same php code.  I've created an .htaccess file in /var/www/html and added the line "php_value session.auto_start on",  then took out all the session_start(); lines in my code but the session is not starting?   Am I doing something wrong?  Is Ubuntu different than other servers with calling .htaccess configs?

It is a remote digital ocean virtual server.. Could that be the issue?

Thanks,

---

### Post by slickymaster on 2017-08-24
*Thread moved to **Server Platforms**.*

---

### Post by do734 on 2017-08-24
Ok will do.  Thanks.

---

### Post by Habitual on 2017-08-24
> **do734 said:**
> 
It is a remote digital ocean virtual server.. Could that be the issue?
Doubt it.

```

<Directory /var/www/html
AllowOverride All 
```

in /etc/apache2/sites-enabled/000-default.conf ?
**[COLOR="#FF0000"]AllowOverride None is[/COLOR] the default now.**
Either flip the bit on AllowOverride None to AllowOverride All 
for your DocumentRoot in /etc/apache2/sites-enabled/000-default.conf

or move the .htaccess code to /etc/apache2/sites-enabled/000-default.conf

---

