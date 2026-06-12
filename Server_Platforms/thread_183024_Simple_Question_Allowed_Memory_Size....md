---
title: "Simple Question: Allowed Memory Size..."
date: 2006-05-27
forum: Server Platforms
---

### Post by romUdog on 2006-05-27
Hey guys im trying to install some stuff on my website (php frameworks) and im getting the allowed memory error thing and i can change that using .htaccess files but id ratehr do it globally so i dont have to put it in every directory...i heard i could do this with the PHP.ini file but i cant find it and i dont know how to create one/where can someone help me with this i think about 20MB should do the trick for the memory thing...

---

### Post by fdoving on 2006-05-28
Hi.
php.ini for PHP4 is at /etc/php4/apache2/php.ini

At line 232 you find this:
```

memory_limit = 8M      ; Maximum amount of memory a script may consume (8MB)

```

Hope this helps.


- Frode

---

