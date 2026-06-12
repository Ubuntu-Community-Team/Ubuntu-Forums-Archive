---
title: "I can't install phpmyadmin"
date: 2008-06-09
forum: Server Platforms
---

### Post by pcosta2007 on 2008-06-09
well,
i already tried to install but isnt working

i installed phpmyadmin by apget
when i try to go to [http://localhost/phpmyadmin](http://localhost/phpmyadmin) it says "page not found"

i gone to var/www and there is not phpmyadmin folder...

does anyone can help me?

i'm using ubuntu 8.04 64 bits:confused:

---

### Post by quelx on 2008-06-09
```
sudo ln -s /etc/phpmyadmin/apache.conf /etc/apache2/conf.d/phpmyadmin.conf
sudo /etc/init.d/apache2 reload
```

---

### Post by pcosta2007 on 2008-06-09
thank you alottt its working now! 

[IMG]http://img516.imageshack.us/img516/7025/capturadatelara1.png[/IMG]

---

### Post by molotov00 on 2008-06-09
Hmmm... and I bet he has no idea what those commands did.

Should have installed phpmyadmin manually. It's not like it needs to be compiled.

---

### Post by nix4me on 2008-06-09
It's amazing to me that the package was packaged and tested with disregard for the correct location of the apache config location.  How in the world can that pass testing?

---

### Post by hyper_ch on 2008-06-10
what is the correct location for apache configs? If I'm not mistaken it depends on whether you use apache 1.3 or apache 2

---

