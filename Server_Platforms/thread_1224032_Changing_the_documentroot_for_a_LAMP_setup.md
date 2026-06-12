---
title: "Changing the documentroot for a LAMP setup"
date: 2009-07-26
forum: Server Platforms
---

### Post by Delta62 on 2009-07-26
Hi guys, 

I have recently installed Ubuntu server 9.04 for use as a LAMP server. I've got everything configured right, except that I want to change the document root for my testing site from the default location (/var/www) to my ftp directory (/home/sam). when I do this by  modifying the apache2.conf, http pages work fine, but PHP pages get this error: 

Fatal error: Unknown: Failed opening required '/home/sam/index.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

Any ideas?

---

### Post by LepeKaname on 2009-07-26
check the permits of /home/sam. It should have 755 and its content 644. Unless you change the owner to www-data.

You are trying to include "index.php" from which file? If you are including several files, check that they are correctly referenced. 

Test adding this line: 

```
set_include_path(get_include_path() . PATH_SEPARATOR . "/home/sam/");
```

If it fails, and you have several includes (inside includes), try using getcwd() to check if you are at the correct directory.

---

### Post by Delta62 on 2009-07-27
Thanks for the suggestion. the directory is in fact already set to 755, but I am not sure what you mean by content. The file index.php is just a simple script that calls phpinfo() to ensure that PHP is functioning correctly.

---

### Post by LepeKaname on 2009-07-27
Check that the file index.php has "chmod 644".

If that doesn't fix it, did you make some special change in your php.ini?

---

### Post by Delta62 on 2009-07-27
Changing the index.php mode to 644 worked. Thanks a lot!

---

