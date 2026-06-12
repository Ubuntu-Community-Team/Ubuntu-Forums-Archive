---
title: "phpMyAdmin: WHERE does it install?"
date: 2009-09-10
forum: Server Platforms
---

### Post by Nokao on 2009-09-10
Hi ...

I saw that there is a cute phpmyadmin package in the repositories.

But WHERE does it installs?
I saw that it magically works after installation under:
[http://localdomain/phpmyadmin/](http://localdomain/phpmyadmin/)

But I don't find any reference in the apache2 configuration files...
... neither in the sites-enabled.

Thanks in advance ...

---

### Post by wojox on 2009-09-10
Check here:

[https://help.ubuntu.com/community/ApacheMySQLPHP#Phpmyadmin%20and%20mysql-admin](https://help.ubuntu.com/community/ApacheMySQLPHP#Phpmyadmin%20and%20mysql-admin)

---

### Post by Bachstelze on 2009-09-10
It installs in /usr/share/phpmyadmin. There's most likely an Alias for it somewhere in your Apache config.

---

### Post by Nokao on 2009-09-10
Oh I found it under:
/etc/apache2/conf.d/phpmyadmin (simbolic link).

Sorry and thank you.

I was just wandering how to change/remove it if needed.

---

