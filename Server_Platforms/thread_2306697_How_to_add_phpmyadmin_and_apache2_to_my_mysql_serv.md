---
title: "How to add phpmyadmin and apache2 to my mysql server?"
date: 2015-12-17
forum: Server Platforms
---

### Post by Higgins909 on 2015-12-17
I've already got mysql installed on my server.  With some data already being stored on it.
But I'm trying to receive help on setting some stuff up, and they're using phpmyadmin.
From what I've read, phpmyadmin uses apache2?

Is it possible and safe to add these 2 to my server?
What parts will need to be configed?
Will phpmyadmin come with apache2?

Thanks,
Higgins909

---

### Post by deepakdeshp on 2015-12-17
You can install Ubuntu 14,04 LTS server which will have mysql , apache and php all installed. You can choose them at the time of installation. Server will not have any GUI . phpmyadmin can be installed and controlled from a client. Server will be very light on resources.

Absolutely you can install phpmyadmin and Apache
If you want to install on the existing set up please follw the following procedure


[https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-14-04)

[https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-ubuntu-14-04)

---

### Post by SeijiSensei on 2015-12-18
```
sudo apt-get install apache2 phpmyadmin
```

should be all you need.

---

### Post by Higgins909 on 2015-12-22
I ended up installing phpmyadmin at first and it ended up installing apache2 with it.

---

