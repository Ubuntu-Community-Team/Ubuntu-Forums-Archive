---
title: "apache 2.4 and a2ensite"
date: 2012-06-13
forum: Server Platforms
---

### Post by A2llex on 2012-06-13
hi,
i compiled Apache 2.4 from source but i can't enable any site through a2ensite, i get only:

ERROR: Site xyxy does not exist!

i added this line into httpd.conf: Include vhosts/*

and all my vhosts are stored in /usr/local/apache2/vhosts

for example there is xxy.vhost 

<VirtualHost *:80>
    DocumentRoot /var/www/xxy.tld/public

    ServerName xxy.tld 
...

if i try a2ensite xxy.vhost:
ERROR: ...

any idea? thank you.

---

### Post by volkswagner on 2012-06-13
I've never installed Apache from source, but your include directive likely needs a complete path.

Looking at my /etc/apache2/apache2.conf I have the following line:

```
# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/
```

---

### Post by A2llex on 2012-06-13
> **volkswagner said:**
> I've never installed Apache from source, but your include directive likely needs a complete path.

Looking at my /etc/apache2/apache2.conf I have the following line:

```
# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/
```

hi, i tried but no change.

---

### Post by A2llex on 2012-06-13
LOL!

this is very embarrassing but,

if forgot to copy www stuff to the directory :D:D

---

