---
title: "[SOLVED] how to parse php instead of downloading it (in firefox)"
date: 2008-06-17
forum: Server Platforms
---

### Post by jakonj on 2008-06-17
How can i parse php files on my pc?
You see i installed:
```
apache2 php5-mysql libapache2-mod-php5 mysql-server php5
```
After this i done this:
```
sudo echo "ServerName localhost" >> /etc/apache2/conf.d/fqdn
```
After this i restarted apache2 with
```
sudo /etc/init.d/apache2 restart
```
After this i restarted pc (it´s my first time to use php5, mysql and apache) and i tried to start offline joomla installation but there was no progress: firefox (3.0b5) is still downloading php files insted of parsing them. What to do?

i use desktop edition (8.04).

tnx for help


p.s. During installation i entered mysql password (if this matters)

---

### Post by windependence on 2008-06-17
First of all you have to download the Joomla packages to install it (they are php files).

Second, localhost is not your fqdn (fully qualified domain name). It should be in this format:

servername.domain.tld

Sooo, if your server name is localhost and your domain is gamer.nix, then your fqdn would be localhost.gamer.nix

I would suggest reading through the Joomla install instructions carefully before trying to install again. If this is like other packages like this, you just download the php files and put them in the correct directory and then navigate to the install folder and run the install php script.

-Tim

---

### Post by jakonj on 2008-06-17
> First of all you have to download the Joomla packages to install it (they are php files).

Second, localhost is not your fqdn (fully qualified domain name). It should be in this format:

servername.domain.tld

Sooo, if your server name is localhost and your domain is gamer.nix, then your fqdn would be localhost.gamer.nix

I would suggest reading through the Joomla install instructions carefully before trying to install again. If this is like other packages like this, you just download the php files and put them in the correct directory and then navigate to the install folder and run the install php script.

1. I downloaded joomla packages(v1.5.3 stable) to my pc.
2. This for fqdn is written on ubuntu wiki ( check out: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) ). So i have to choose another thing. I will try it
3. I read about 4 manuals for instalkling :>

Still there is problem since my pc wont open any php file localy ;)
Wnat can i do to fix that?

---

### Post by jakonj on 2008-09-16
stupid me... I just have to install:
```
apache2 php5-mysql libapache2-mod-php5 mysql-server php5
```
And to add this
```
sudo echo "ServerName localhost" >> /etc/apache2/conf.d/fqdn
```

After this i just have to put my files in /var/www/ ando voila...
Solved

---

