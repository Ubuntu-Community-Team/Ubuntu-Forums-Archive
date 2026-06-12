---
title: "Drupal 5.1 site Segmentation Fault on Ubuntu 6.10"
date: 2007-04-17
forum: Server Platforms
---

### Post by elruy on 2007-04-17
I deployed a drupal-5.1 site using several contrib modules. It is giving me a segmentation fault under certain installations. I would like to determine what is causing this, but it's quite difficult since I get no information from the server.

The site works perfectly in a box with suse apache2, php4.4, mysql4.1).

But when I set up a copy of the site in a Ubuntu6.10, Apache breaks with a segmentation fault! In the same ubuntu machine if I excecute php-cli (`php index.php`) it responds correctly.
Never the less, a fresh drupal5.1 install on this ubuntu machine works without a problem. I also tried all of the modules by separate and they work fine in ubuntu.

The packages used in the Ubuntu machine are:
- apache2 2.0.55-4, apache2-common 2.0.55-4, apache2-mpm-prefork 2.0.55-4,
- php5 5.1.6-1, php5-common 5.1.6-1, php5-mysql 5.1.6-1, php5-gd 5.1.6-1,
- mysql 5.0.24a-9
I have updated my system.

Any suggestions on how to debug my installation/site?

Thanks
Ruy

---

