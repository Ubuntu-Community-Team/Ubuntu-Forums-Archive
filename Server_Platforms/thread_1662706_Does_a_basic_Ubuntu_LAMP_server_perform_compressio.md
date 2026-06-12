---
title: "Does a basic Ubuntu LAMP server perform compression by default?"
date: 2011-01-08
forum: Server Platforms
---

### Post by kpm on 2011-01-08
I have an Ubuntu 9.10 LAMP server that i do some Drupal development on.  In the performance settings, there is a selection to enable or disable compression, but it depends on whether the hosting server already does this or not:

> By default, Drupal compresses the pages it caches in order to save bandwidth and improve download times. This option should be disabled when using a webserver that performs compression.

How do I find out if the canned LAMP installation does perform compression or not?

Thanks

---

### Post by CharlesA on 2011-01-08
I think the default Apache config uses compression, however I am not 100% sure on that.

I did find deflate.conf in /etc/apache2/mods-enabled/

EDIT: I found [this page]("http://dtbaker.com.au/random-bits/howto-enable-compression-and-caching-on-apache2.html"), that tells you how you can you enable compression.

---

### Post by James78 on 2011-01-08
I believe it does do compression by default. I installed LAMP, and mod_defalte was already installed, so ya. You should be good, but try out "sudo a2enmod deflate" just to be sure.

---

### Post by kpm on 2011-01-15
> **CharlesA said:**
> I think the default Apache config uses compression, however I am not 100% sure on that.

I did find deflate.conf in /etc/apache2/mods-enabled/

EDIT: I found [this page]("http://dtbaker.com.au/random-bits/howto-enable-compression-and-caching-on-apache2.html"), that tells you how you can you enable compression.

Thanks!

---

