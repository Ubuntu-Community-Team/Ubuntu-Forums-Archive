---
title: "PHP error after installing apache2"
date: 2007-07-03
forum: Server Platforms
---

### Post by jayleesan on 2007-07-03
Hi all,

After installing apache2 under Feisty I recieve a PHP error I do not know:

Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Fatal error: Unknown: Failed opening required '/var/www/test/index.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

I figured this had something to do with permissions but after settging all to access and restarting apache the error remains.

Anyone any ideas?

Thanks!

---

### Post by Maxtorm on 2007-07-03
Which user owns /var/www/test/index.php?
```
ls -al /var/www/test/index.php
```
It should be owned by www-data.  Is it?

---

### Post by jayleesan on 2007-07-04
I had to mess around with the file- and folder-permissions to make it work. Wrong permissions is what coused the error.
Thanks anyways!!

---

