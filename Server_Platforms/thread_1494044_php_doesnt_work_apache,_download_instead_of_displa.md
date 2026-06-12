---
title: "php doesnt work apache, download instead of display"
date: 2010-05-26
forum: Server Platforms
---

### Post by Marwelln on 2010-05-26
Hello, i just updated apache trough webmin and now everything is ****ed up.

All my php files is beeing download isntead of displayed. I searched around users with same error but none of  their solutions work.

What should I do??????????

The php5 module is enabled.

---

### Post by Vegan on 2010-05-26
Did you install the full LAMP stack.

```
sudo tasksel
```

and choose LAMP

and this should install everything you need.

---

### Post by bemenaker on 2010-06-01
Did you add:
Servername localhost

to your httpd.conf file?  That fixed that problem for me.

---

### Post by WorMzy on 2010-06-01
Do you have apache2-mod-php5 installed?

---

