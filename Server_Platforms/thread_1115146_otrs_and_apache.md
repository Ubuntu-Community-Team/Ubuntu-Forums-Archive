---
title: "otrs and apache"
date: 2009-04-03
forum: Server Platforms
---

### Post by daelious on 2009-04-03
Hello all,

I have just set up Ubuntu 8.10 server to test out using otrs.  I installed it and (naturally) apache.

It works great thusfar, but I was wanting to know if there is a way to change it so instead of having to go to [http://some.hostname.here/otrs](http://some.hostname.here/otrs) I could have it go to [http://some.hostname.here/](http://some.hostname.here/).

Thanks in advance for any help.
daelious

---

### Post by koenn on 2009-04-03
probably something along the lines of editing /etc/apache2/sites-enabled/000-default to include the contents of the apache conf for otrs (most likely to be found in /etc/apache/otrs.conf or so)

you'll want /etc/apache2/sites-enabled/000-default to look something like
```

NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost
        
        DocumentRoot /path/to/otrs

        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>

        <Directory /path/to/otrs>
               ## directory config from original otrs apache conf
               ## goes here
  
        </Directory>

[...]

```

keep copies of files you edit, you may have to roll back.

---

