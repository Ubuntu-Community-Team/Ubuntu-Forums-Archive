---
title: "Accessing phpmyadmin"
date: 2010-04-05
forum: Server Platforms
---

### Post by dtommy79 on 2010-04-05
Hi,

I've installed phpmyadmin on my VPS. How can i access it from browser?

thanks

---

### Post by jfmanamtr on 2010-04-05
The url is [http://computer-ip/phpmyadmin](http://computer-ip/phpmyadmin).
 
~John

---

### Post by dtommy79 on 2010-04-05
Thanks for the answer.

yeah, that was what I tried first, but I get a not found message
> The requested URL /phpmyadmin/ was not found on this server.

do I need to do some settings modification after install?

---

### Post by dtommy79 on 2010-04-05
OK,

I forgot to add

> Include /etc/phpmyadmin/apache.conf

to apache2.conf

---

