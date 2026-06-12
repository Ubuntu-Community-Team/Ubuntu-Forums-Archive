---
title: "Can I install LAMP on my Ibex workstation ?"
date: 2008-11-05
forum: Server Platforms
---

### Post by prepstyles on 2008-11-05
I seem to remember a few releases back that I could install a LAMP configuration with a single line. Has that changed?

I'd like to setup my desktop as a LAMP server so I can build and test server side projects.

I ran:

```
sudo tasksel install lamp-server
```

And got the blue screen installer ... which just hung at 0% until I killed it and reset the computer (something I needed to do to free the package management system).

Am I better off just installing all PHP MySQL and Apache individually ?

Any thoughts are appreciated ... thank in advance!

---

### Post by erwall on 2008-11-06
```
sudo aptitude install mysql-server mysql-client libmysqlclient15-dev pache2 apache2-doc apache2-mpm-prefork apache2-utils apache2-suexec libexpat1 ssl-cert libapache2-mod-php5 libapache2-mod-ruby libapache2-mod-python php5 php5-common php5-curl php5-dev php5-gd php5-idn php-pear php5-imagick php5-imap php5-mcrypt php5-memcache php5-mhash php5-ming php5-mysql php5-pspell php5-recode php5-snmp php5-sqlite php5-tidy php5-xmlrpc php5-xsl
```

---

