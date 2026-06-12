---
title: "Webmin/Apache"
date: 2008-04-07
forum: Server Platforms
---

### Post by dewman0012 on 2008-04-07
I am having some issues with getting our eccomerce site to work correctly with apache. So far I have gotten the site to display, however, our navigation is controlled by mod_rewrite. Things I don't understand:

1) httpd.conf file is not being used. How can I make this happen?
2) .htaccess is obviously not working correctly because the URL rewrite command is not being used. What needs to be done for this to work?


As of right now, I want to start fresh again with Apache. However, I can seem to delete my already created virtual servers. Is there a ways to delete them inside webmin? I check the box and say delete, then on refresh it is still there. Ideas? 

Can I just reinstalled apache? If so, how can this be done? 

Thanks in advance!

---

### Post by hyperlobic on 2008-04-08
How are you starting apache?

Try running apachectl -V and see where it's looking for you httpd.conf file

It should output something like this:L

-D SERVER_CONFIG_FILE="conf/httpd.conf

---

### Post by dewman0012 on 2008-04-08
> **hyperlobic said:**
> How are you starting apache?

Try running apachectl -V and see where it's looking for you httpd.conf file

It should output something like this:L

-D SERVER_CONFIG_FILE="conf/httpd.conf

Apache is always running, the initial starting of apache was in Webmin.


I ran that command, however, I did not receive the output you described. All I received back was the server version and server built date. 

The httpd.conf file is in /etc/apache2/

---

