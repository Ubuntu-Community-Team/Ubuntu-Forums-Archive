---
title: "how do you enable server-info in apache2.conf"
date: 2006-11-08
forum: Server Platforms
---

### Post by don7777 on 2006-11-08
Hi all,

I'm running Ubuntu 6.06 with apache2. I've got server-status working
but I can't get server-info working. Here's what I have for it in
/etc/apache2/apache2.conf:

<Location /server-info>
    SetHandler server-info
#    Order deny,allow
#    Deny from all
#    Allow from .your_domain.com
</Location>

I have restarted apache2 and I go to [http://localhost/server-info](http://localhost/server-info) and I
get a "404 Not Found" response.
Do I have to enable anything else in order for server-info to show up?

Thanks for any help,
Don

---

### Post by Joe_CoT on 2006-11-08
mod_info installed?

```
sudo a2enmod info
sudo /etc/init.d/apach2 restart
```

---

### Post by don7777 on 2006-11-08
you da man!!

Thanks, that worked great.


> **Joe_CoT said:**
> mod_info installed?

```
sudo a2enmod info
sudo /etc/init.d/apach2 restart
```

---

### Post by Joe_CoT on 2006-11-08
Np. ubuntu has a large amount of apache modules compiled and ready to go, but they aren't installed any running by default, and for good reason ;)

---

