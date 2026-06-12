---
title: "Apache2 Offers to Download and no Display"
date: 2006-06-28
forum: Server Platforms
---

### Post by Spudgun on 2006-06-28
I've recently installed Apache2 along with PHP5 and MySQL. How ever, when ever I view .php files, I get offered to download a PHTML file, instead of displaying the .php file as it should.

Does any one know how I could fix this?

Many thanks.

---

### Post by Maggot on 2006-06-28
is php5.conf in /etc/apache2/mods-enabled ?
Does the file contain the lines:

<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>

---

### Post by Spudgun on 2006-06-28
[QUOTE=Maggot]is php5.conf in /etc/apache2/mods-enabled ?
Does the file contain the lines:

<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>[/QUOTE]

The file wasn't there, so I created it pasting in the text you posted, but still no luck.

---

### Post by Maggot on 2006-06-28
Did you just install php? 

Check and ensure you have libapache2-mod-php5 installed.

You should delete that file you created..its just a symbolic link.

---

### Post by Spudgun on 2006-06-30
Ok, found something interesting. I can view PHP files that are in /var/www/,but if they're in another directory, such as /var/www/phpmyadmin, I get the download option.

---

