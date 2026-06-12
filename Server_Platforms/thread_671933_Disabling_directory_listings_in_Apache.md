---
title: "Disabling directory listings in Apache"
date: 2008-01-19
forum: Server Platforms
---

### Post by numberboy on 2008-01-19
I'm trying to disable directory listing in Apache2, but I can't seem to get it to work. I've got my server configured so that in /var/www I have subdirectories for each domain, with a subdirectory of /public under that which contains the pages people see when they access a domain name.
For scripting reasons I still need people browsing to be able to read from the whole of /var/www, but I don't want them to be able to get a list of the contents of directories. Is there a way to turn off directory listings for everything?

Failing that, I can't even get it to work for /var/www
I tried putting
```

<Directory "/var/www">
   Option -Indexes
</Directory>

```
in apache2.conf and then httpd.conf and neither worked. I also tried <Directory /> and <Directory *>, both of which failed (though in all cases Apache reloaded just fine.

Any help'd be appreciated

---

