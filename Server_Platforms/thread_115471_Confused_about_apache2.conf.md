---
title: "Confused about apache2.conf"
date: 2006-01-10
forum: Server Platforms
---

### Post by nordmann on 2006-01-10
I must be overlooking something.  Apache2 installs on Ubuntu with an /etc/apache2/httpd.conf file and a file called /etc/apache2/apache2.conf.  httpd.conf has nothing in it but some comments.  Apache2.conf has lots of information and would appear to be the file I'm interested in editing.  Others have posted in this forum that, yes, this is the file we're supposed to be editing to configure Apache.

The problem is, I can't see that this file actually gets referenced anywhere in the startup scripts.  Am I supposed to edit the /etc/init.d/apache2 and change the references to httpd.conf over to apache2.conf?  It seems a bit odd and un-Ubuntu-like to be tinkering with the init scripts like that.  I figure they're set up the way they are for a good reason.

Any ideas?

---

### Post by paddyg on 2006-01-11
I don't think you should bother /etc/init.d/apache2. I think you should take a look at /etc/apache2/README---if you haven't done it yet--- just to understand apache config in debian.

Everything depends on what you want to do. For example, the <VirtualHost>, <Directory> and Options directives can be edited in /etc/apache2/sites-available/default. That's just what I did when I had to set the Options directive to Includes. I just edited that file and restarted the server.

Unfortunately, I don't know why things work like that in this distro---but they do work fine...

---

### Post by i_am_socket on 2006-01-11
Yup, it works fine editing apache2.conf.  Definitely read the readme and any other documentation, though.

---

### Post by nordmann on 2006-01-13
Thanks, guys.  I just got ahead of myself and started making configuration changes based on assumptions from other Apache installations I've worked with.  The README file cleared everything up.

Thanks again.

---

### Post by MJN on 2006-01-13
The configuration for Apache2 on Debian, as you're likely read now, has been modularised.

However, you should find the following Include directive in /etc/apache2/apache2.conf by default:

```
Include /etc/apache2/httpd.conf
```

Hence anything you put into httpd.conf would've also been included.

Mathew

---

