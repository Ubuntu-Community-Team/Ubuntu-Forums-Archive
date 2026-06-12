---
title: "Contents of ports.conf"
date: 2009-09-25
forum: Server Platforms
---

### Post by Fliggerty on 2009-09-25
Hey all,

Would somebody mind posting the default contents of /etc/apache2/ports.conf after using tasksel to setup a LAMP server please?

Much appreciated!

--Fligg

---

### Post by cdenley on 2009-09-25
```

# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # SSL name based virtual hosts are not yet supported, therefore no
    # NameVirtualHost statement here
    Listen 443
</IfModule>

```

Older releases didn't have NameVirtualHost in ports.conf, but I think that was before 8.04.

---

### Post by Iowan on 2009-09-25
Mine is a Hardy LAMP server:```
Listen 80

<IfModule mod_ssl.c>
    Listen 443
</IfModule>
```

---

### Post by cdenley on 2009-09-25
I just checked, and 8.10 or newer use the one I posted. 8.04 and older use the one Iowan posted.

---

### Post by Fliggerty on 2009-09-26
The first one is exactly what I needed.  Suppose I should have mentioned my version.  :)

Thanks a bunch!

--Fligg

---

