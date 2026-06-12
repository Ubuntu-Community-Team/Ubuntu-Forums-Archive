---
title: "PHP and Apache"
date: 2009-05-26
forum: Server Platforms
---

### Post by mikeym on 2009-05-26
Hi,

First off, sorry at this is such a daft question but I'm floundering trying to set up PHP, Apache and MySQL on my Ubuntu machine.

I have a website that I'm fed up paying for hosting for and I'm trying to move it to my machine. I've got MySQL, PHP and Apache (and phpmyadmin) installed and all seem to work fine. I've imported my database from a file and made a user to log on and checked that the user can access it for queries.

I've put all the PHP and HTML files in my Apache directory. When I try and access my local server I can see the HTML parts of the files but the PHP sections aren't being executed, and when I look at the source I can still see the calls to PHP like:

```

<?php
	require('include/main.php');
?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
	"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">

```

These should have been replaced (especially this one as it's the first line in the file).

What am I missing?

---

### Post by cdenley on 2009-05-26
Does the file have a .php extension? Did you enable the php5 module?
```

sudo a2enmod php5
sudo /etc/init.d/apache2 restart

```

---

### Post by mikeym on 2009-05-26
Files with the extension .php do seem to try and run (so I assume the module is loaded already), but I can't persuade .htm files to do the same. I've tried creating a .htaccess file in my /var/www directory where my site is:

```

AddType application/x-httpd-php .html .htm

```

Tis didn't change anything even with a restart of apache.

---

### Post by cdenley on 2009-05-26
By default, I don't think AddType can be used in .htaccess files. Try editing /etc/apache2/mods-available/php5.conf, then restarting.

---

### Post by mikeym on 2009-05-27
Thanks cdenley! That was spot on.

I've another wee question about my website and I suspect it may be a similar option. It's not working mostly how its supposed to but for some reason the php scripts are not getting global parameters which are passed in through the URL. So in a php function where the url is:

*index.htm?editbbcode=welcome#welcome*

I would expect to be able to access $editbbcode as a global but it is empty.

---

### Post by cdenley on 2009-05-27
> **mikeym said:**
> Thanks cdenley! That was spot on.

I've another wee question about my website and I suspect it may be a similar option. It's not working mostly how its supposed to but for some reason the php scripts are not getting global parameters which are passed in through the URL. So in a php function where the url is:

*index.htm?editbbcode=welcome#welcome*

I would expect to be able to access $editbbcode as a global but it is empty.

If you need globals to be registered, you need to edit the "register_globals" variable in /etc/php5/apache2/php.ini, then restart apache. This has been turned off by default for security reasons. I have seen firsthand how this can be exploited on a page which was coded carelessly, so be cautious if you use this option. The correct way to access variables such as that is
[PHP]
$editbbcode=$_REQUEST['editbbcode'];
[/PHP]

---

