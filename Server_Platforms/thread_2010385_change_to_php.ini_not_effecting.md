---
title: "change to php.ini not effecting"
date: 2012-06-25
forum: Server Platforms
---

### Post by aleksi on 2012-06-25
Hi,

I run Apache on Ubuntu 12.04.


I wanted to change default settings for upload file size, and made changes to lines below(after I edited them)
File I made changes to was /etc/php5/apache2/php.ini

upload_max_filesize = 10M
post_max_size = 100M

After restarting apache phpinfo still says that:

 upload_max_filesize	2M

Any clue how is this possible?

---

### Post by stmiller on 2012-06-26
This can be over-written by a hidden .htaccess file in your web site's root directory.

Look for a file called dot htaccess (.htaccess) which can also set php limits. 

Cheers,

---

### Post by kennethconn on 2012-06-26
Does a reload of apache help?
Sometimes you read on guides to reload apache as opposed to restart it, but I don't really know if there is a difference.

---

### Post by LHammonds on 2012-06-27
Apache has to be restarted for changes to the php.ini to take affect.  Or a reload which "reloads" the configuration file if you have to keep the service online.

It might also be regulated by the application you are using.  Take a look at steps 15 and 16 on my post for [creating a mediawiki server]("http://ubuntuforums.org/showpost.php?p=11931601&postcount=7") for an example.

LHammonds

---

