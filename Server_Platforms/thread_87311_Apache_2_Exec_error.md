---
title: "Apache 2 Exec error"
date: 2005-11-07
forum: Server Platforms
---

### Post by smgil on 2005-11-07
Hi everybody.


I'm trying to setup a apache 2 server in my ubuntu hoary but I get problems when aI try to execute php files which are outside of DocumentRoot.

I've just installed phpmyadmin and I'm not able to access it. I got same problem with a application that I bind using a Directory sentence in httpd.conf. The funny thing is that I copied my application inside /var/www/html everything works, and I'm running drupal in DocumentRoot and works well.

I the apache's logs I got this kind of messages.
```

[Mon Nov 07 17:40:21 2005] [error] [client 127.0.0.1] (13)Permission denied: exec of '/var/www/phpmyadmin/index.php' failed
[Mon Nov 07 17:40:21 2005] [error] [client 127.0.0.1] Premature end of script headers: index.php

```


I have next packages:

php4                4.3.10-10ubuntu4.2 
apache2             2.0.53-5ubuntu5.3
phpmyadmin          2.6.4-pl3-1 


Any help will be appreciated.

---

### Post by jaddison on 2005-11-07
[QUOTE=smgil]I'm trying to setup a apache 2 server in my ubuntu hoary but I get problems when aI try to execute php files which are outside of DocumentRoot.

I've just installed phpmyadmin and I'm not able to access it. I got same problem with a application that I bind using a Directory sentence in httpd.conf. The funny thing is that I copied my application inside /var/www/html everything works, and I'm running drupal in DocumentRoot and works well.

Any help will be appreciated.[/QUOTE]

Apache is a decently secure webserver; it is very specific about what web pages it will server - rather, it's specific about WHERE it will serve from.  **Directory** directives are intended to place permissions and control access to various functionality within the specified directory.  **DocumentRoot** is intended to specify where a web browser will be directed to upon accessing Apache.

You might want to take a look at the **VirtualHost** directive located [here at http://httpd.apache.org/docs/2.0/vhosts/]("http://httpd.apache.org/docs/2.0/vhosts/").  It's a way for you to specify subdomains.  For example, if you owned the domain name **[www.smgil.com](www.smgil.com)**, you could redirect **phpadmin.smgil.com** to a different directory, provided that all the Apache settings were correct.

It's a little complex at first, but once you get the hang of it, it's not that bad.

I hope this helps.  If you need more clarification, just respond, and myself or someone else will try to answer better.

---

### Post by smgil on 2005-11-08
> **jaddison]Apache is a decently secure webserver said:**
> here at http://httpd.apache.org/docs/2.0/vhosts/[/URL].  It's a way for you to specify subdomains.  For example, if you owned the domain name **[www.smgil.com](www.smgil.com)**, you could redirect **phpadmin.smgil.com** to a different directory, provided that all the Apache settings were correct.

It's a little complex at first, but once you get the hang of it, it's not that bad.

I hope this helps.  If you need more clarification, just respond, and myself or someone else will try to answer better.

That could be a solution for a production server but i have apache on my workstation just for development. I have configured this functionality other times on windows and fedora core and I had never got in troubles. It seems like a Ubuntu especial configuration.

---

### Post by jaddison on 2005-11-08
[QUOTE=smgil]That could be a solution for a production server but i have apache on my workstation just for development. I have configured this functionality other times on windows and fedora core and I had never got in troubles. It seems like a Ubuntu especial configuration.[/QUOTE]

Ubuntu no doubt sets up the Apache configuration files and directory layout as it sees fit, much as other distributions do the same.  I haven't played with Apache on an Ubuntu system as of yet - my experience is via Gentoo, for the most part.

I would suggest posting your pertinent Apache configuration files for others to examine - you might get some better feedback.

---

