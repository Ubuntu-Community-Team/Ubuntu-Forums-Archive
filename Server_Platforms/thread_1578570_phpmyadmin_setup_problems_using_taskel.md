---
title: "phpmyadmin setup problems using taskel"
date: 2010-09-20
forum: Server Platforms
---

### Post by quadrantids on 2010-09-20
I have just installed the amp of lamp using tasksel on my portable (lucid lynx) simply because I wanted to use MySQL.

Everything seems to work except that I get the warning messages "Connection for controluser as defined in your configuration failed" plus the following:"The additional features for working with linked tables have been deactivated. To find out why click here".

Can anyone tell please tell me why I get these messages? I suspect it's to do with the config.php file.

Version of phpmyadmin is 3.3.2deb1

---

### Post by Bachstelze on 2010-09-20
You have some work to do if you want to enable those features, apparently the package doesn't do it for you. Depending on what you want to do, you might not need them, though.

---

### Post by windependence on 2010-09-20
You probably don't need linked tables. To fix the error:
 
1. Type nano /etc/phpmyadmin/config.inc.php in the Linux terminal. You can substitute nano for vi or your favorite text editor.
2. Find the two blocks of text that read:

```
$cfg['Servers'][$i]['controluser'] = $dbuser;
$cfg['Servers'][$i]['controlpass'] = $dbpass;

```
one is near the top embedded in an if statement, and the other is towards the bottom. The text is not exactly the same for each block, but $cfg['Servers'][$i]['controluser'] is what matters. The block that is actually used by phpMyAdmin depends on your setup, but just for simplicity we will apply the change to both.
3. Just comment out those four lines by adding a // in front of each one.
4. Save, and the error should disappear next time you access phpMyAdmin. 
 
-Tim

---

### Post by quadrantids on 2010-09-22
Tim,

Thx for your help. I use Geany but although I can open the file I don't have the permission to change it. I guess I need to use sudo but where in step 1 of your recommendation should I add this?

Rob

---

