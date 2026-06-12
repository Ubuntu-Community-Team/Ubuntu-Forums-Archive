---
title: "apache directories"
date: 2008-11-26
forum: Server Platforms
---

### Post by inter-m on 2008-11-26
im trying to learn PHP... and already installed apache2 to my laptop... thing is my course im taking is on windows... i was instructed to save a PHP file to htdocs... im really lost i dont know where to find that file... thanx in advance...

K.H.

---

### Post by Wayne_V on 2008-11-26
By htdocs they mean the document root of your web server.   On Intrepid this is defined in /etc/apache2/sites-enabled/000-default --- typically /var/www.

---

### Post by Dr Small on 2008-11-26
The "htdocs" directory, by default, is:
```
/var/www
```

---

### Post by inter-m on 2008-11-27
> **Dr Small said:**
> The "htdocs" directory, by default, is:
```
/var/www
```

i tried saving a file in that directory called firstcode.php... and when i went to my browser i typed [http://localhost/firstcode.php](http://localhost/firstcode.php) and then i got a message saying that the file dosent exsist...

---

### Post by MJN on 2008-11-28
You need to find out where *your* document root is (as the others have mentioned this defaults to /var/www/ but apparently not in your case).
 
Find it with **grep -ir documentroot /etc/apache2**
 
Mathew

---

