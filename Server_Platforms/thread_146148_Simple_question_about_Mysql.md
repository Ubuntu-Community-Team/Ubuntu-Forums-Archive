---
title: "Simple question about Mysql"
date: 2006-03-17
forum: Server Platforms
---

### Post by Tortanick on 2006-03-17
I think I may have used the wrong Fully Qualified domain name. I used adress.co.uk rather than server.adress.co.uk

Where can I find the config file that will let me fix this?

---

### Post by tkiesel on 2006-03-17
Hi Tortanick,

A quick 'man mysql' on the webserver I run tells me that the file you're looking for is /etc/mysql/my.cnf

Take care!
-T

---

### Post by Tortanick on 2006-03-18
Thanks but that file isn't it, I checked and their was no mention of any domain name. Perhaps it gets the results from some system config file?

---

### Post by Gallows on 2006-03-19
Have a look at /etc/hostname, have you got the correct servername set here?

---

