---
title: "mysql database limit"
date: 2013-07-31
forum: Server Platforms
---

### Post by salmendar on 2013-07-31
hi,
 i have a ubuntu server 12.04 running in my office . it's a small business and it usually is enough for our requirements but now i need to increase the database file upload limit as that is 2MB which is insufficient for our use . can someone please help me by telling me where to edit the limit ...
[RIGHT][INDENT]thank you
Salman Dar[/RIGHT][/INDENT]

---

### Post by LHammonds on 2013-07-31
MySQL upload limit?  Are you actually talking about PHP/Apache Web server upload limit?

If so, increase the php filesize limit of uploaded files by editing **/etc/php5/apache2/php.ini** and find **upload_max_filesize** and change it from 2M to **50M**, then find **post_max_size** and change it from 8M to **51M**

LHammonds

---

### Post by salmendar on 2013-07-31
this is to be done after changing the ownership of the file or as root user ??

i am going to change user ownership

---

### Post by salmendar on 2013-07-31
yep, that did the trick.

Thank you

---

