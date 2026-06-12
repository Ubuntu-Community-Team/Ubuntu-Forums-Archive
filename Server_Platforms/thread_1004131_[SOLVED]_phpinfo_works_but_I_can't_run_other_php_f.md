---
title: "[SOLVED] phpinfo works but I can't run other php files"
date: 2008-12-06
forum: Server Platforms
---

### Post by clay7 on 2008-12-06
Hello,

Variables [all 1 day old]:
--------------------------
Ubuntu 8.10
Apache2
PHP5
phpMyAdmin
i386 1G Ram, 40G SATA HD
No other OS on disk

I took the leap from XP to Ubuntu. I am used to developing PHP and MySql databases from XP. THere, I would put a folder with all website files in the **htdocs** folder under Apache. 

Now, I don't know where to put my websites. I have a folder called "fitness" and it has a index.php in it. Here is the path to it:
/var/www/fitness/index.php

When I open Firefox and type in "http://localhost/fitness/index.php", I get this error message:

[COLOR="Red"]Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Fatal error: Unknown: Failed opening required '/var/www/fitness/index.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0[/COLOR]

That's really odd. I have no line 0.

**If I do "http://localhost/index.php", which has phpinfo(), that works fine. **

Is my folder in the right place? What is wrong?

---

### Post by clay7 on 2008-12-06
got it...

I had to set the permissions of the folder and everything in it to allow **Others** to **Access Files** and apply permissions to enclosed files.

---

