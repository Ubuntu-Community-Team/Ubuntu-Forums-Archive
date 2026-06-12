---
title: "Mod_rewrite"
date: 2007-06-04
forum: Server Platforms
---

### Post by mevets on 2007-06-04
I don't know the right way to enable mod_rewrite on feisty and apache2. I see /etc/apache2/mods-enabled but dont know the how I should go about telling it to load the module in the right way. Im sure i could have it tacked onto another .load, but wouldnt the be a poor way of achiving this?

So, how is it done?

---

### Post by jtc on 2007-06-05
```
a2enmod rewrite
```

[https://help.ubuntu.com/7.04/server/C/httpd.html](https://help.ubuntu.com/7.04/server/C/httpd.html)

---

### Post by mevets on 2007-06-05
thanks! The install was successful

I get this output from  apache2ctl -l:
```

Compiled in modules:
  core.c
  mod_log_config.c
  mod_logio.c
  prefork.c
  http_core.c
  mod_so.c

```
shouldnt mod_rewrite be included?

---

### Post by jtc on 2007-06-05
No.

In case mod_rewrite already was compiled into Apache you wouldn't have to load it separate, would you? :-P

---

### Post by mevets on 2007-06-05
guess not

---

### Post by CK0y0TE on 2007-06-08
Hmm that was exactly what me too needed. Yet another happy person today! :D

---

