---
title: "mod_rewrite"
date: 2006-09-07
forum: Server Platforms
---

### Post by Compact on 2006-09-07
I have tryied to turn on mod_rewrite on apache, but when I run apache it display this error: 

Can't locate API module structure `mod_rewrite' in file /usr/lib/apache2/modules/mod_rewrite.so: /usr/lib/apache2/modules/mod_rewrite.so: undefined symbol: mod_rewrite

Any idea?

---

### Post by gnudownload on 2006-11-06
Hi
# cd /etc/apache2/mods-enabled
# ln -s /etc/apache2/mods-available/rewrite.load rewrite.load
# apache2ctl restart

---

### Post by Joe_CoT on 2006-11-06
The preferred method is to use **a2enmod**, not to symlink it yourself.

```
sudo a2enmod rewrite
```

---

