---
title: "Enabling PHP Extensions"
date: 2011-04-07
forum: Server Platforms
---

### Post by cmnorton on 2011-04-07
I am installing Drupal 7.x (latest) and running on Ubuntu 10.04 LTS. 

Apache and PHP are installed, and PHP is properly configured thanks to this answer [http://ubuntuforums.org/showthread.php?t=1723656](http://ubuntuforums.org/showthread.php?t=1723656)

Drupal is now saying that PHP Extensions are disabled and I need to enable them for GD. I did not build PHP from source, but installed it using Synaptic.

How do I re-configure PHP to enable GD?
tnx
cmn

Found I needed to install php-gd. Problem solved.

---

