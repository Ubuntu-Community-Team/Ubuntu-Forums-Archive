---
title: "Apache Help"
date: 2008-08-16
forum: Server Platforms
---

### Post by jamelb on 2008-08-16
I am having major issues i just reinstalled ubuntu server and i am trying to restore my wordpress. I put the folder where it belongs and restored  the sql database but the screen shot is all i get. thank you
[ATTACH]81697[/ATTACH]

---

### Post by windependence on 2008-08-16
You need to re-enable the php module in Apache.

Why did you reinstall?

-Tim

---

### Post by jamelb on 2008-08-16
i needed to reinstall for a school project tim....also how do i re-enable the php module in Apache?

---

### Post by windependence on 2008-08-16
OK like this:

```
sudo libapache2-mod-php5

sudo a2enmod php5 

sudo /etc/init.d/apache2 restart
```

Make sure you clear your browser's cache before testing it again.

If sudo a2enmod php5 returns "$ This module does not exist!", you should purge (not just remove) the libapache2-mod-php5 package and reinstall it. 

-Tim

---

