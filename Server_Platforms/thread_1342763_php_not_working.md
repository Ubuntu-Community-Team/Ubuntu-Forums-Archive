---
title: "php not working"
date: 2009-12-01
forum: Server Platforms
---

### Post by cablejimmy on 2009-12-01
I am a complete noob at php, and I don't know what I am doing. I have an index.php file in the /var/www folder. when I try accessing it online, it just brings up the code. what am I doing wrong?

---

### Post by rudy.b on 2009-12-01
Is your PHP module enabled in Apache? 
```
$ sudo a2enmod php5
```
Be sure to restart your Apache server to apply the change, if it wasn't already enabled.

---

### Post by cablejimmy on 2009-12-01
It says it was already enabled.
Btw, what's the script to restart Apache?

---

### Post by cablejimmy on 2009-12-01
Btw, what's the script to restart Apache?

---

### Post by cablejimmy on 2009-12-01
Okay, I found the restart script. It's still not working.

---

### Post by rudy.b on 2009-12-01
To restart Apache: 'sudo /etc/init.d/apache2 restart'

Are you running PHP version 5?  Can you post the PHP code you're trying to execute?

---

### Post by cablejimmy on 2009-12-01
Yeah, it's php5.
```
< ?php phpinfo() ?>
```

---

### Post by weemadarthur on 2009-12-01
> **cablejimmy said:**
> Yeah, it's php5.
```
< ?php phpinfo() ?>
```
Remove the space between the first < and the ?.

---

