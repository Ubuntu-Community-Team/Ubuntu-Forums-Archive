---
title: "Need help configuring apache2 server"
date: 2007-02-14
forum: Server Platforms
---

### Post by kidcharles on 2007-02-14
Hi folks, for some reason I'm having an impossible time getting my apache2 server up and running.

Basically, I'm trying to tell apache2 where my document root is and the domain name, that's all. When I add the lines:

DocumentRoot "/document/root"
ServerName domain.name.com:80

to apache2.conf with appropriate values, the site will not load properly. Also 'localhost' only lists 'apache-default', which is the standard default apache page. Any ideas? Other than the document root and server name, I just want to use the apache defaults. Yes I restarted httpd with '/etc/init.d/apache2 restart' after making changes. Thanks in advance.

---

### Post by MJN on 2007-02-14
Try putting your config in /etc/apache2/sites-available/default - the config is modularised on Debian-based distros.

I'm pretty sure there's a Readme file describing what does what.

Mathew

---

### Post by Brazen on 2007-02-14
MJN is exactly right.  Your site config needs to go in /etc/apache2/sites-available/default.  If you changed anything else, put it back how you found it.  Also a good practice to to make a backup of any config files you change.  You can make a backup like this:```
sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/default.original
```

---

