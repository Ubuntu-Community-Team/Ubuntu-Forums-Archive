---
title: "How to find out Apache Username?"
date: 2009-10-17
forum: Server Platforms
---

### Post by dyingsun on 2009-10-17
Hi all
Is there a quick way of determining what my apache username is? Trying to chown a subfolder of /var/www/  and it doesn't like apache.apache   - not sure where to find the right name.

Thanks!
Damien

---

### Post by t3r0 on 2009-10-17
the default in ubuntu is www-data


- Tero

---

### Post by dyingsun on 2009-10-17
Bingo, thank you very much Tero, that's solved it.


Damien

---

### Post by Lars Noodén on 2009-10-18
> **t3r0 said:**
> the default in ubuntu is www-data


Yep.  That is the default.

To be sure what it is really set to, check the actual configuration files.
The umbrella file, apache2.conf will have something like the following, 

[INDENT][FONT="Courier New"]User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}[/FONT][/INDENT]

Thats is a reference to environment variables set in /etc/apache2/envvars
[mod_suexec](http://httpd.apache.org/docs/2.2/suexec.html) also allows scripts to be run as yet a different user and group.  

To find any virtual hosts which may use alternate users, groups or both, again, check the configurations.
```
$ egrep "^User|^Group|^SuexecUserGroup" /etc/apache2/apache2.conf /etc/apache2/sites-available/*.conf

```

---

