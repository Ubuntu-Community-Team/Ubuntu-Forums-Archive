---
title: "Apache &quot;htdocs&quot; path"
date: 2007-02-16
forum: Server Platforms
---

### Post by .Michael on 2007-02-16
What is the path to the apache htdocs folder?

(where I put stuff to be served)

---

### Post by darrenm on 2007-02-16
Depends on your vhosts. A base configuration will have it in /var/www

Have a look in /etc/apache2/sites-enabled/

---

### Post by highneko on 2007-02-16
It's:
```
/var/www
```
You can find more apache paths with:
```
man apache2
```
Or to find some documentation you could:
```
dpkg -L apache2
```

---

