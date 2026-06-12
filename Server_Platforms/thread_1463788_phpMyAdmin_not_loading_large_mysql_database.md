---
title: "phpMyAdmin not loading large mysql database"
date: 2010-04-27
forum: Server Platforms
---

### Post by b89.smith on 2010-04-27
I am running Ubuntu 9.10 with Apache, phpMyAdmin and MySQL. Normally phpMyAdmin loads properly, but the other day I created a large database of 6,000+ tables and 1.3 GB of data in the entire database. Now phpMyAdmin loads and shows my different databases, but if I try to open the new large database, it just loads a white page with no content. Does anyone know if I can reconfigure my server so it will be able to show parts of the database? 

Thanks

---

### Post by b89.smith on 2010-04-27
I actually found a fix for it. I went into php.ini and changed the following settings:

max_execution_time = 600 
max_input_time = 120 
memory_limit = 64M

---

### Post by domzz on 2010-04-27
ignore this

---

