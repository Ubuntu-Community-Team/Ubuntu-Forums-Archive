---
title: "Tasksel Packages"
date: 2010-12-22
forum: Server Platforms
---

### Post by cc48510 on 2010-12-22
Is there a web page listing what packages each task installs ??? In particular, I wanted to know what lamp-server installs. I can safely assume Apache, MySQL, and PHP...but, does it install phpMyAdmin or anything else ???

---

### Post by clay7 on 2010-12-22
The only one i know of is: 
```
sudo tasksel install lamp-server 
```

This installs Apache2, MySQL, and PHP. It does NOT install phpMyadmin. Also, after running this and you need SSL, you will need to:

```
sudo a2enmod ssl
sudo a2ensite default-ssl
sudo /etc/init.d/apache2 restart
```

Yeah, I'd love to see more tasksel's too.

---

### Post by wojox on 2010-12-22
Try:

```
tasksel --task-packages dns-server
```

---

