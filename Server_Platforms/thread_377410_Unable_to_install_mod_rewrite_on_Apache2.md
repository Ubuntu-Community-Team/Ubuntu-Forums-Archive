---
title: "Unable to install mod_rewrite on Apache2"
date: 2007-03-06
forum: Server Platforms
---

### Post by marcus16 on 2007-03-06
I've installed Apache 2 via Synaptic, but I can't figure out how to get it to install mod_rewrite with it.
Can anyone help me?

---

### Post by Mr. C. on 2007-03-06
Unless I'm mistaken, it should be installed.  Check:

/usr/lib/apache2/modules/mod_rewrite.so

MrC

---

### Post by MJN on 2007-03-06
Whilst it's compiled it's not enabled by default.
 
Try **sudo** **a2enmod rewrite **(running **sudo a2enmod** by itself will give you a list of modules available to load)
 
Mathew

---

### Post by kbuel on 2007-03-06
I enabled it by creating a symlink from mods enabled to mods available:

cd /etc/apache2/mods-enabled
sudo ln -s ../mods-available/rewrite.load rewrite.load


Then here:

cd /etc/apache2/sites-available
sudo vi default


under the virtual host tag, turn on the rewrite engine:

<VirtualHost *>

  RewriteEngine on 

..
..
..


Hope this helps,

-K

---

### Post by hlynur on 2007-03-06
1

---

