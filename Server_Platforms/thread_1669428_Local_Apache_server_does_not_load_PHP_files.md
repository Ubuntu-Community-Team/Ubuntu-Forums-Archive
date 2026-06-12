---
title: "Local Apache server does not load PHP files"
date: 2011-01-17
forum: Server Platforms
---

### Post by pilotguy415 on 2011-01-17
I just installed apache2 and php on my local machine. HTML files load fine but I cannot get it to read php files it just has me download the file instead. I completely purged libapache2-mod-php5 and reinstalled. I've updated the apache2.conf and the httpd.conf files. Still will not read .php files. 

If I run "sudo apache2ctl -M" it shows php5_module (shared) syntax OK.

Any ideas what else I can try? I've been searching high and low online to see what I might be missing. Most just show the libapache2-mod-php5 is missing and to install it again. 

Thanks for any help!

---

### Post by SeijiSensei on 2011-01-17
What's in /etc/apache2/mods-enabled/php5.conf?

You should see 

```

<FilesMatch "\.ph(p3?|tml)$">
SetHandler application/x-httpd-php
</FilesMatch>

```

---

