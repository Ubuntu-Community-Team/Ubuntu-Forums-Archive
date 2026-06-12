---
title: "Unable To Run PHP Installer"
date: 2009-05-13
forum: Server Platforms
---

### Post by CarlosinFL on 2009-05-13
I am trying to install a PHP application on my Ubuntu machine called "Roundcube" which require the following:

- PHP 5.2
- Apache 2.x
- MySQL 5.x

I have all the following installed and modified the permissions...

Now I am told to point my browser to [http://localhost/roundcube/installer](http://localhost/roundcube/installer) & then a web based installation should come up. I tried this on CentOS and it works fine but on this Ubuntu machine I get the following that pops up. It's like it can't understand how to read the following:

---

### Post by a9k3d on 2009-05-14
sounds like php is not enabled in apache2. Type **ls /etc/apache2/mods-enabled/php5.conf**
If it does NOT reply */etc/apache2/mods-enabled/php5.conf* then run
**a2enmod php5**

In both cases try **/etc/init.d/apache2 restart** which should get php loaded with apache.

---

### Post by wojox on 2009-05-14
you may also want to try to check your dir.conf file in 
/etc/apache2/mods-enabled directory.
this is the module apache2 loads that holds the directory index of which files to parse to php. If you don't see index.phtml you'll need to add it.

---

### Post by mbeach on 2009-05-14
take a look at:
[https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20PHP%205](https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20PHP%205)

If that is followed, and you get the same result, make sure 
/etc/apache2/mods-available/php5.conf 
has a line like:
  AddType application/x-httpd-php .php .phtml .php3

---

