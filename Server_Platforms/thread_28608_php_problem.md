---
title: "php problem"
date: 2005-04-20
forum: Server Platforms
---

### Post by dude2425 on 2005-04-20
I've got apache2 installed, I've got mysql setup, I KNOW I have php installed. I've got a file called test.php in /var/www, with <?php phpinfo(): ?> in it, and a whole slew of other php files, and every single one of them only show up as the source code in firefox when I goto [http://localhost/](http://localhost/)
I have no idea how to fix this one. Any ideas? I'm all ears, or eyes rather.

---

### Post by Vache on 2005-04-20
[QUOTE=dude2425]I've got apache2 installed, I've got mysql setup, I KNOW I have php installed. I've got a file called test.php in /var/www, with <?php phpinfo(): ?> in it, and a whole slew of other php files, and every single one of them only show up as the source code in firefox when I goto [http://localhost/](http://localhost/)
I have no idea how to fix this one. Any ideas? I'm all ears, or eyes rather.[/QUOTE]
 In your Apache config, you need...

```
LoadModule php4_module libexec/libphp4.so
```

and

```
AddType application/x-httpd-php .php .phtml
```

---

### Post by diebels on 2005-04-20
I only removed the # from line 274 in /etc/apache2/apache2.conf:
# AddType application/x-httpd-php .php
and restarted apache
Think the LoadModule thing is already set up. On Hoary that is.

---

### Post by mila80 on 2005-06-13
[QUOTE=dude2425]I've got apache2 installed, I've got mysql setup, I KNOW I have php installed. I've got a file called test.php in /var/www, with <?php phpinfo(): ?> in it, and a whole slew of other php files, and every single one of them only show up as the source code in firefox when I goto [http://localhost/](http://localhost/)
I have no idea how to fix this one. Any ideas? I'm all ears, or eyes rather.[/QUOTE]


Hi, 
  have you solve ypour problem???
I Install all with [COLOR=Red]sudo apt-get install apache2 mysql-server php4[/COLOR]
and all work fine.

<?php phpinfo(): ?>

You have an error here...


<?php phpinfo()[COLOR=Red];[/COLOR] ?>

Bye

---

### Post by LordHunter317 on 2005-06-13
Make sure php4.conf  and php4.load are in /etc/apache2/modules-enabled.  If you had to manually edit any files, you already did something wrong.

---

### Post by mila80 on 2005-06-13
I haven't modify any files...
I install all with apt and all work well!!!

---

### Post by pdf6161 on 2007-12-19
I'm having what seems to be the same problem.  I installed server 7.04 and selected to install a LAMP server.  When we browse to a sample page we created on the lamp server, the php doesn't work (sends the original code trough as text).  We have gone thru the various suggestions in the thread, but nothing seems to work.
In mods-enabled, I have the file php5.conf, containing
<IfModule mod_php5.c>
 AddType application/x-httpd-php .php .phtml .php3
 AddType application/x-httpd-php-source .phps
</IfModule>
We don't know where to look from here.

---

### Post by pdf6161 on 2008-01-21
Ok.  The book I was getting a php example from was using files with a .html extension.  I added .html to the first AddType line and all seems well.

---

