---
title: "Where is phpmyadmin"
date: 2009-05-21
forum: Server Platforms
---

### Post by c-m on 2009-05-21
I installed phpmyadmin by using:

```
sudo apt-get install libapache2-mod-auth-mysql php5-mysql phpmyadmin
```

phpmyadmin successfully installed but where is it? How do i access it?

---

### Post by mbeach on 2009-05-21
I believe it installs to
/usr/share/phpmyadmin

and this part is a guess, but I suspect in your browser you goto
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

edit:
url should be correct, see [https://help.ubuntu.com/community/phpMyAdmin](https://help.ubuntu.com/community/phpMyAdmin)

---

### Post by _Purple_ on 2009-05-21
If you can't access using [http://localhost/phpmyadmin](http://localhost/phpmyadmin), link phpmyadmin by typing in terminal:
```
sudo ln -s /usr/share/phpmyadmin /var/www
```

Replace /usr/share/phpmyadmin with the actual location of phpmyadmin.

---

### Post by c-m on 2009-05-21
> **_Purple_ said:**
> If you can't access using [http://localhost/phpmyadmin](http://localhost/phpmyadmin), link phpmyadmin by typing in terminal:
```
sudo ln -s /usr/share/phpmyadmin /var/www
```

Replace /usr/share/phpmyadmin with the actual location of phpmyadmin.

This worked - there was no symlink

Many thanks

---

### Post by apel_2804 on 2009-05-21
Check if you have the config file /etc/apache2/conf.d/phpmyadmin.conf 

if so a simple /etc/init.d/apache2 reload will activate it.

---

