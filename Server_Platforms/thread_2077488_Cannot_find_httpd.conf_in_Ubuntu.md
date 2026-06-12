---
title: "Cannot find httpd.conf in Ubuntu"
date: 2012-10-28
forum: Server Platforms
---

### Post by FerasMoalla on 2012-10-28
Hello,

I have just installed Apache2 in my Ubuntu 12.10 desktop, the web server is working when I visit [http://localhost/](http://localhost/), the thing is I can't find the  file "httpd.conf", i looked every where, also used the command:

sudo find / -name "httpd.conf"

What is going on?

Thanks

---

### Post by Doug S on 2012-10-28
For a few releases now, the file /etc/apache2/httpd.conf file has been empty, and only present for legacy reasons. Now in 12.10, yes, it seems to be gone. Configurations are done in the subdirectories, sites-available, mods-available.

---

### Post by darkod on 2012-10-28
Also some configuration is in /etc/apache2/envvars

---

### Post by FerasMoalla on 2012-10-28
Thanks for the heads up guys, this I wasn't expecting!

---

### Post by rugbert on 2012-11-06
So like, in the httpd file you could set up system wide rules for things like url rewriting, which I need to get cakePHP up and running ie:
```

<Directory />
    Options FollowSymLinks
    AllowOverride All
#    Order deny,allow
#    Deny from all
</Directory>
```

where do we do that now?

---

### Post by CharlesA on 2012-11-06
/etc/apache2/sites-available/whateverthesitenameyouareworkingwith

The default site is here:
/etc/apache2/sites-available/default

---

