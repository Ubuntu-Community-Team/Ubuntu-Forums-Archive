---
title: "Server Isn't Responding To .htaccess!"
date: 2010-03-03
forum: Server Platforms
---

### Post by LeonBlade on 2010-03-03
Hey everyone,

For some reason my .htaccess file isn't doing ANYTHING what so ever.
Let me know what files I should post here to help you determine my problem.

Sorry I'm not posting much.
Leon Blade

---

### Post by ImperialXT on 2010-03-03
paste a copy of your .htaccess file please

---

### Post by AlexanderDGreat on 2010-03-04
It must be related to modules, my .htaccess rewrite engine didn't work also so I:

```
sudo a2enmod rewrite
``` - to enable modules for rewrites

```
sudo gedit /etc/apache2/sites-available/default
AllowOverride All
``` - not 100% sure if it applies to you sir.

---

