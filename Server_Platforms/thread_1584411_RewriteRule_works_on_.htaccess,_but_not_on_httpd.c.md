---
title: "RewriteRule works on .htaccess, but not on httpd.conf"
date: 2010-09-29
forum: Server Platforms
---

### Post by shaitan on 2010-09-29
Hi all,

We are trying to migrate from a centos server to ubuntu server, but we have some problems with an application called Topincs ([http://www.cerny-online.com/topincs/](http://www.cerny-online.com/topincs/)).

The installation is quite simple and I did it several time (but with ubuntu it's the first time).

Probably there are some parameters to set that I don't know, but even if the installation works fine and I can see the home page, the application doesn't work because RewriteRules aren't applied.

First I tried to ensure that mod_rewrite works fine and I found a weird situation: rewriterules work if they are in .htaccess but don't work if they are directly in http.conf.

Any ideas?

---

### Post by Ryan Dwyer on 2010-09-29
I'm going to guess that they must be inside a VirtualHost block, so if you don't want to use .htaccess then you must write the rules in /etc/apache2/sites-available/default (or a different host if you set up a separate one).

---

### Post by shaitan on 2010-09-29
Thank you very much indeed!

Now it works.

I guess that using sites-available/sites-enabled it's a choice of ubuntu/debian. Is it?

---

### Post by Ryan Dwyer on 2010-09-29
Yes, though I'm not sure which. I find it's an easier setup than editing a single vhost config file. Being able to enable and disable sites with a2ensite/a2dissite is pretty sweet. There's also a similar system for Apache modules.

---

### Post by SeijiSensei on 2010-09-29
Personally I find it easier to create a directory like /etc/apache2/sites.d/ and put the configurations for all the VMs in separate files there with names like www.example.com.conf.  Then at the bottom of httpd.conf I use 

Include sites.d/*.conf

and Apache reads all the .conf files in the directory.  

(Actually all my web servers run CentOS so I use /etc/httpd/sites.d/, but the principle is the same.)

---

