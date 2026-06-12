---
title: "Enable mod_rewrite module"
date: 2009-04-10
forum: Server Platforms
---

### Post by zemon_ on 2009-04-10
Im looking in the /etc/apache2/apache2.conf file for the LoadModule rewrite_module modules/mod_rewrite.so line but cannot locate it, I need to uncomment that line.
Running ubuntu 8.10 + apache2
Is this line in another location?

---

### Post by cdenley on 2009-04-10
You don't need to edit anything.
```

sudo a2enmod rewrite
sudo /etc/init.d/apache2 restart

```

---

### Post by zemon_ on 2009-04-11
Thanks :p

---

