---
title: "How To Hide Apache Information On Ubuntu 9 Server"
date: 2010-01-20
forum: Security
---

### Post by banyezdemah on 2010-01-20
Hi

I have an Ubuntu 9 server and i want to hide my apache information. I know what the code is. It is like following:

ServerTokens ProductOnly
ServerSignature Off


I did it on httpd.conf file in main config of http, but the Ubuntu 9 server had apache2.conf instead of httpd.con
The question is how can I user these codes on which file and which part of that file?


Thank You :)

---

### Post by cdenley on 2010-01-20
You should comment/uncomment the appropriate lines in /etc/apache2/conf.d/security.

---

### Post by bodhi.zazen on 2010-01-20
You can also look at mod_security ;)

---

### Post by banyezdemah on 2010-01-27
solved in /etc/apache2/conf.d/security


thank you so much :)

---

