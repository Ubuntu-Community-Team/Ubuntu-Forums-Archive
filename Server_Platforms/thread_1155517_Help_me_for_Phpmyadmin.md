---
title: "Help me for Phpmyadmin"
date: 2009-05-10
forum: Server Platforms
---

### Post by sajid786 on 2009-05-10
I installed apache 2 and phpmyadmin on ubuntu 8.04.
i check my test page and its working fine. (using localhost)
But when i try to access from webbrowser localhost/phpmyadmin it not showing me anything.
i got "phpmyadmin" folder under /etc

what i need to so i can access phpmyadmin from webbrowser ?

---

### Post by unutbu on 2009-05-10
Please post the output of ```
grep "apache\|phpmyadmin" /var/log/dpkg.log
```

---

### Post by _Purple_ on 2009-05-10
You can link phpmyadmin using terminal command. If phpmyadmin is in /usr/share/phpmyadmin:
```
sudo ln -s /usr/share/phpmyadmin /var/www
```

Replace /usr/share/phpmyadmin with the actual location of phpmyadmin.

---

### Post by sajid786 on 2009-05-12
> **_Purple_ said:**
> You can link phpmyadmin using terminal command. If phpmyadmin is in /usr/share/phpmyadmin:
```
sudo ln -s /usr/share/phpmyadmin /var/www
```Replace /usr/share/phpmyadmin with the actual location of phpmyadmin.

Thanks Its works now :) :guitar:

---

