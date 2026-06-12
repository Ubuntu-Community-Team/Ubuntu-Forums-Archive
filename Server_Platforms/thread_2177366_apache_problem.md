---
title: "apache problem"
date: 2013-09-28
forum: Server Platforms
---

### Post by remo2 on 2013-09-28
Where is defined in the Apache2 server default download an html file name and location, and the definition of what that is?

---

### Post by Iowan on 2013-09-28
Moved to Server Platforms.

---

### Post by Lars Noodén on 2013-09-28
The default location for HTML files in the default virtual host is /var/www  

You can change that by making a new directory and pointing to it with the [DocumentRoot](http://httpd.apache.org/docs/2.4/mod/core.html#documentroot) configuration directive.

---

### Post by remo2 on 2013-09-28
hi, i was searching in internet answer for that question. is it possible that Apache configuration is in / etc / httpd / conf / httpd.conf or / etc/apache2/httpd.conf configuration file?

---

### Post by Lars Noodén on 2013-09-28
Neither.  Most of the information you will find on the net is outdated.  It is largely written for Apache 1.3.x and you are running Apache2.x, which has a very different  configuration layout. In Apache2 httpd.conf should be left alone.

As I mentioned in the other thread, you have a default configuration for a default virtual host.  That default file is  /etc/apache2/sites-enabled/000-default.conf 
 You can change that file if you wish.  If you want more virtual hosts, add more configuration files in /etc/apache2/sites-available/ and then turn them on with [a2ensite](http://manpages.ubuntu.com/manpages/raring/en/man8/a2ensite.8.html).  It's a little fancier than it used to be with Apache 1.3 but it scales much better.  If you want something simpler to configure, you might try nginx instead of Apache2.

---

### Post by remo2 on 2013-09-28
ok, now i understand thanks a lot

---

### Post by Lars Noodén on 2013-09-28
One thing to add is that when you search for material online about Apache, make sure you are looking for Apache 2.  The configuration files changed quite a bit between 1.3 (the old version) and 2.x (the new version).  The [configuration directives](http://httpd.apache.org/docs/2.4/mod/quickreference.html) on the inside are about the same, but the files have been divided up to make it easier to manage multiple virtual hosts on the same machine, each with  different owners and adminsitrators.

---

### Post by monkeybrain20122 on 2013-09-30
> **Lars Noodén said:**
> One thing to add is that when you search for material online about Apache, make sure you are looking for Apache 2.  The configuration files changed quite a bit between 1.3 (the old version) and 2.x (the new version).  The [configuration directives]("http://httpd.apache.org/docs/2.4/mod/quickreference.html") on the inside are about the same, but the files have been divided up to make it easier to manage multiple virtual hosts on the same machine, each with  different owners and adminsitrators.

Is it? I think the dividing up is a Debian modification. Apache2 is Redhat/Fedora/CentOS still have the standard configuration layout.

---

