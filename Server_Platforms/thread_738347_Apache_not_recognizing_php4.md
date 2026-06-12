---
title: "Apache not recognizing php4"
date: 2008-03-28
forum: Server Platforms
---

### Post by gideon220 on 2008-03-28
apache2 not recognizing index.php or index.html.  Everytime I go to my site [http://www.txpod.org](http://www.txpod.org) it says that it is a application/x-httpd-php and what would you like to do with it.  I've uninstalled apache and php numerous times using

 sudo apt-get --purge remove apache apache2 apache2-common php4

sudo apt-get install apache2 php4 libapache2-mod-php4

Last time I had to format and start with the server disk in order to get this to work, but I can't do that again because I've got a customer who has set up mysql databases on it.  

This all started because I was trying to remove sasl for smtp and it ended up removing apache, php, phpmyadmin and everything.  I'm sorry I sound so frustrated I've just been fighting with this server from the get go.  Any help would be greatly appreciated.  Thanks

When I go to [http://www.txpod.org/index.php](http://www.txpod.org/index.php) it asks if I want to save it.  If I actually go to [http://www.txpod.org/index.html](http://www.txpod.org/index.html) it pulls it up, it's like the document root is messed up

---

### Post by gideon220 on 2008-03-28
it's working now.

---

