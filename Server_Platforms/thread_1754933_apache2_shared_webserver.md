---
title: "apache2 shared webserver"
date: 2011-05-10
forum: Server Platforms
---

### Post by maxougg on 2011-05-10
Hi all,

I need to setup a linux shared webserver on ubuntu that supports php5.

It's really simple to configure apache2 or nginx with a virtuelhost for each customer. But I thinks that not enough for security reasons...

Can anyone tell me if i need to use suexec, fast-cgi, php-fpm, create for each customer a local user,... and tell me how I will configure this?

If anyone knows a great tutorial, always welcome :)


Thanks for your replies...

---

### Post by volkswagner on 2011-05-10
Howtoforge.com has many tutorials.

This one may help with [fastCGI]("http://www.howtoforge.com/how-to-set-up-apache2-with-mod_fcgid-and-php5-on-ubuntu-10.10"), and these for [ispConfig]("http://www.howtoforge.com/perfect-server-ubuntu-10.10-maverick-meerkat-ispconfig-2") and [virtual hosting]("http://www.howtoforge.com/installing-ispcp-on-ubuntu-lucid-x86_64-and-implementing-chroot-per-virtual-host-in-apache2").

---

### Post by maxougg on 2011-05-11
> **volkswagner said:**
> Howtoforge.com has many tutorials.
 
This one may help with [fastCGI]("http://www.howtoforge.com/how-to-set-up-apache2-with-mod_fcgid-and-php5-on-ubuntu-10.10"), and these for [ispConfig]("http://www.howtoforge.com/perfect-server-ubuntu-10.10-maverick-meerkat-ispconfig-2") and [virtual hosting]("http://www.howtoforge.com/installing-ispcp-on-ubuntu-lucid-x86_64-and-implementing-chroot-per-virtual-host-in-apache2").
 
Hi volkswagner,
 
Thanks for the information. I will test this...
 
Another question:
Is using fastcgi and suexec together the best solution?

---

