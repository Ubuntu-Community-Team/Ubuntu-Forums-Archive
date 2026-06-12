---
title: "How to use lamp server"
date: 2011-06-02
forum: Server Platforms
---

### Post by baffodoro on 2011-06-02
Hello everybody

I have installed on my Ubuntu 11.04 a lamp server using this command:

sudo apt-get lamp-server^

and everything seems to be ok.

The question now is: how do I use this server? My intention is to upload Joomla! for trying out settings and applications, but how do I get apache, mysql and php running? How do I switch them off?

Is there any kinf of interface? must I use the command line?

Thank you for any help.

---

### Post by CharlesA on 2011-06-02
You can use the command line, or you can use something like webmin to configure apache.

You can use phpmyadmin to configure SQL databases too.

In order to use it, upload files to /var/www/ and access them from a web browser.

---

### Post by ruffEdgz on 2011-06-02
> **CharlesA said:**
> You can use the command line, or you can use something like webmin to configure apache.

You can use phpmyadmin to configure SQL databases too.

In order to use it, upload files to /var/www/ and access them from a web browser.

I agree with CharlesA on this.

I would also take a look on the command line the following directories that you will be most interested in:

Apache
/etc/apache2/...
/var/www/...

MySQL
/etc/mysql/...
/var/lib/mysql/... (don't touch anything in here)

Postfix
/etc/postfix/...

or

PHP
/etc/php5/...
/etc/phpmyadmin/... (if you download and use this webapp)

---

### Post by jramshu on 2011-06-02
Really read the Joomla guides carefully, understand the way it's structured, like categories, menus, and such.

You may want to look at Drupal also.

---

