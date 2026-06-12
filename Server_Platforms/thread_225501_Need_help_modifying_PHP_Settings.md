---
title: "Need help modifying PHP Settings"
date: 2006-07-29
forum: Server Platforms
---

### Post by afbase on 2006-07-29
I would like to know how to modify my PHP 'engine/modulator' to extend my max_execution_time.  I need to adjust this from what seems like only 30 seconds to something much longer temporarily so I can upload images faster.



PHP max_execution_time limit

---

### Post by laprice on 2006-07-29
the file to alter is 
/etc/apache2/php4/php.ini

remember to put into version control before you start fiddling with it :)

---

### Post by afbase on 2006-07-30
> **laprice said:**
> the file to alter is 
/etc/apache2/php4/php.ini

remember to put into version control before you start fiddling with it :)

well i finally got it to work. I used /etc/php5/apache2/php.ini

---

