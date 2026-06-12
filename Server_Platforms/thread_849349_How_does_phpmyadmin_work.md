---
title: "How does phpmyadmin work?"
date: 2008-07-04
forum: Server Platforms
---

### Post by skunkbad on 2008-07-04
Ubuntu Server Edition 8.04

I've successful installed phpmyadmin, and it works with mysql, and everything else is good. I'm just wondering how phpmyadmin works. Even though it is accessible from [http://localhost/phpmyadmin](http://localhost/phpmyadmin), there is no phpmyadmin directory in /www. I'm using name based virtual hosts, but don't see it in the apache2 sites-available directory. I'd just like to know how it is working.

---

### Post by marshal on 2008-07-04
when installing with apt-get the phpmyadmin files are located in /usr/share/phpmyadmin.

during the installation some apache-configs are changed to point to the right directory, or there are soft links im not sure how its done with apache

---

### Post by skunkbad on 2008-07-04
That is the type of info I am wondering about. Perhaps somebody else will elaborate.

---

### Post by nanog on 2008-07-04
its a symbolic link.

XXX@XXX:/var/www$ ls -lt 

phpmyadmin -> /usr/share/phpmyadmin

---

### Post by cariboo on 2008-07-04
if you do a directory listing in /var/www you will see where phpmyadmin is linked to.

Jim

---

### Post by skunkbad on 2008-07-04
> **nanog said:**
> its a symbolic link.

XXX@XXX:/var/www$ ls -lt 

phpmyadmin -> /usr/share/phpmyadmin

When I do this I only see the folders that my websites are in. Even if I do:

ls -alt , I still don't see the symbolic link.

What i did find out is this. I have an Include in my apache2.conf file:
Include /etc/phpmyadmin/apache.conf

Taking a look at /etc/phpmyadmin/apache.conf shows an Alias:
Alias /phpmyadmin /usr/share/phpmyadmin

and apparently this Alias is a symbolic link.

---

