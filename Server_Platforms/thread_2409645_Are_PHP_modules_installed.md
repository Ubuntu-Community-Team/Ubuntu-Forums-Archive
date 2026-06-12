---
title: "Are PHP modules installed?"
date: 2019-01-04
forum: Server Platforms
---

### Post by philip18 on 2019-01-04
Hi, I've just installed the latest Ubuntu Server (Ubuntu Server 18.04.1 LTS) and PHP/Apache and mySQL. I need the following PHP modules:

PHP BCMath Arbitrary Precision Mathematics
PHP Internationalization extension
PHP Curl
PHP Zip
PHP GD
PHP XML
PHP MBString
PHP LDAP

Do these need to be installed, or are they already there and just need to be enabled? Eg I can run curl from the terminal but PHP says there is no Curl which makes me think it's just disabled in PHP.

What do I need to do to get these modules available to my PHP applications?

---

### Post by volkswagner on 2019-01-05
You can check to see if php packages are installed:
```
sudo dpkg --get-selections | grep  php
```


Ubuntu 18.04 has php7. You can search for available packages:
```
apt-cache search php7
```


You can check apache for modules that are available:
```
ls /etc/apache2/mods-available
```

You can check apache2 for enabled modules:
```
s /etc/apache2/mods-enabled
```

---

### Post by philip18 on 2019-01-05
So this did the trick:

sudo apt install php7.2-bcmath php7.2-curl php7.2-gd php7.2-intl php7.2-xml php7.2-ldap php7.2-zip php7.2-mbstring

---

### Post by philip18 on 2019-01-05
> **volkswagner said:**
> You can check to see if php packages are installed:
```
sudo dpkg --get-selections | grep  php
```


Ubuntu 18.04 has php7. You can search for available packages:
```
apt-cache search php7
```


You can check apache for modules that are available:
```
ls /etc/apache2/mods-available
```

You can check apache2 for enabled modules:
```
s /etc/apache2/mods-enabled
```

Hi, sorry I posted before I saw your reply. Thanks for those tips, I'll jot them down for next time.

---

