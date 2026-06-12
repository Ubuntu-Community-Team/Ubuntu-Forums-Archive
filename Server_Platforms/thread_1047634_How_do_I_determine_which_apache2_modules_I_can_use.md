---
title: "How do I determine which apache2 modules I can use?"
date: 2009-01-22
forum: Server Platforms
---

### Post by nipar on 2009-01-22
Using Ubuntu Server 8.10

I need to know how to determine which apache2 modules are available through 'aptitude' or 'apt-get' and if I can install modules not available from Ubuntu repositories that I download from the Apache web site.

One module in particular is mod_security. There are others, but I'm concerned that I might break the Ubuntu release of Apache2.

Any help is much appreciated.

---

### Post by R.Bucky on 2009-01-22
simply type in "**apache2 mod**" in synaptic package manager. or, you can choose from mods-available by typing in terminal "**sudo a2enmod**"

---

