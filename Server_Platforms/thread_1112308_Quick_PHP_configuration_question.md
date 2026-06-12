---
title: "Quick PHP configuration question"
date: 2009-03-31
forum: Server Platforms
---

### Post by mwilhide on 2009-03-31
I just threw a copy of Ubuntu Server onto a VM and set LAMP up during install.

Where can I find the PHP config file?  I'd like to check and see what extensions are enabled by default, and I need to enable the ldap extension as well.

Thank you!

---

### Post by cdenley on 2009-03-31
```

cat /etc/php5/apache2/php.ini /etc/php5/apache2/conf.d/*|less

```

---

