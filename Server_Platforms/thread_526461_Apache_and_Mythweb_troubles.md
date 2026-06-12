---
title: "Apache and Mythweb troubles"
date: 2007-08-15
forum: Server Platforms
---

### Post by cobaltcopy on 2007-08-15
Hello all.

I'm having a somewhat intriguing problem with apache, by virtue of installing mythweb.

Now, when I install mythweb with ```
sudo apt-get install mythweb
``` it installs without errors. However, apache is missing several key files including /etc/init.d/apache2 and the following

A directory listing of /etc/apache2 gives the following
```
/etc/apache2# ls
conf.d  mods-available  mods-enabled  ports.conf  sites-available  sites-enabled

```

There's no httpd.conf, or apache2.conf. I reverted to an old apache2.conf and simply added a blank httpd.conf file to no avail.

I ran /usr/sbin/apache2 (there's no /etc/init.d/apache2) and it fails on the following:

```
<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
</Files>

TypesConfig /etc/mime.types

```

I commented that out and it ran, but it doesn't serve any pages.

So, three things:

1) Apache does not seem to be fully installed. It fails on a tried and true apache2.conf file.
2) Mythweb did not install itself into virtual site like it did before
3)/etc/init.d/apache2 does not exist.

I tried uninstalling and reinstalling apache2 and mythweb, but that didn't work.

---

### Post by moodog on 2007-12-08
Did you get anywhere with this? I'm having the same problem.

---

### Post by radmofo on 2008-06-05
Ditto!! I'm stressed out here. Why are things some dam difficult?

---

