---
title: "Can't browse to my Apache server"
date: 2013-08-14
forum: Server Platforms
---

### Post by neil3 on 2013-08-14
Hi Guys,

First time setting up Apache, using Ubuntu server 12.04.02

I am using this guide:[https://www.digitalocean.com/community/articles/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu](https://www.digitalocean.com/community/articles/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu)

Seems pretty straight forward, except I can't navigate to the webserver with my browser. I tried IE and Chrome.

---

### Post by sandyd on 2013-08-14
> **neil3 said:**
> Hi Guys,

First time setting up Apache, using Ubuntu server 12.04.02

I am using this guide:[https://www.digitalocean.com/community/articles/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu](https://www.digitalocean.com/community/articles/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu)

Seems pretty straight forward, except I can't navigate to the webserver with my browser. I tried IE and Chrome.

Please post the result of
```

lsof -i :80
```

Thanks

---

