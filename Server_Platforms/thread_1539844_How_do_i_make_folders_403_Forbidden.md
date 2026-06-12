---
title: "How do i make folders 403 Forbidden?"
date: 2010-07-27
forum: Server Platforms
---

### Post by ubila on 2010-07-27
Hello,
Im running a webserver, and want to make certain folders forbidden to the public using webbrowser for example...
 
/public_html/javascript/
 
I would want them to be able to go to /public_html/ but not /javascript/ yet id need the javascript files in that folder to still work for them on the page that is in /public_html/
 
Any ideas on how to do this?
 
Thanks!

---

### Post by Bachstelze on 2010-07-27
```
Options -Indexes
```

In .htaccess.

---

### Post by dapperdanny77 on 2010-07-27
<Directory yourdirectory>

Order Allow,Deny
Allow from all
Deny from 10.10.10 192.168.1.1 

or

Order Deny,Allow
Deny from all
Allow from 10.10.10.10

</Directory>

[http://httpd.apache.org/docs/2.2/mod/core.html#directory](http://httpd.apache.org/docs/2.2/mod/core.html#directory)

---

### Post by Bachstelze on 2010-07-27
> **dapperdanny77 said:**
> <Directory yourdirectory>

Order Allow,Deny
Allow from all
Deny from 10.10.10 192.168.1.1 

or

Order Deny,Allow
Deny from all
Allow from 10.10.10.10

</Directory>

[http://httpd.apache.org/docs/2.2/mod/core.html#directory](http://httpd.apache.org/docs/2.2/mod/core.html#directory)

No, because if you do that, people will also be denied access to the contents of the directory.

---

### Post by ubila on 2010-07-27
> **dapperdanny77 said:**
> <Directory yourdirectory>
 
Order Allow,Deny
Allow from all
Deny from 10.10.10 192.168.1.1 
 
or
 
Order Deny,Allow
Deny from all
Allow from 10.10.10.10
 
</Directory>
 
[http://httpd.apache.org/docs/2.2/mod/core.html#directory](http://httpd.apache.org/docs/2.2/mod/core.html#directory)
 
Do i put this in htacces file or apache vhost config file. ie. mysite.com.conf?
Thanks

---

### Post by ubila on 2010-07-27
> **Bachstelze said:**
> ```
Options -Indexes
```
 
In .htaccess.
 
Thanks this worked :)

---

