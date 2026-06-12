---
title: "ubuntu and apache 2 wont parse php"
date: 2017-08-05
forum: Server Platforms
---

### Post by Adrian_Padilla on 2017-08-05
i recently installed apache 2 on my ubunutu, and i can not get .php files to parse, for example 

<include header.php in one of the lines in my index.php files, 

well it wont display the header.php

it worked on my old server but i have a feeling i am missing a directive from my apache config somewhere, 

i am runing php5

here is my apache config for my virtual host on ubuntu

<VirtualHost *:80>
    ServerAdmin [EMAIL="admin@compumedik.com"]admin@compumedik.com[/EMAIL]
    ServerName [www.compumedik.com]("http://www.compumedik.com")
    ServerAlias compumedik.com
    DocumentRoot /var/www/html/compumedik.com/comp/
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

any help would be appreciated

---

### Post by cariboo on 2017-08-05
Depending on what php version you are using do you have:

[LIST]
[*]libapache2-mod-php
[*]libapache2-mod-php7.1
[/LIST]

---

### Post by Adrian_Padilla on 2017-08-05
This is what i have installed

---

### Post by Adrian_Padilla on 2017-08-05
[h=1]PHP Version 7.0.18-0ubuntu0.16.04.1[/h]

---

### Post by cariboo on 2017-08-05
Do you have the module installed? it should show this in /etc/apache2/mods-enabled:

```
lrwxrwxrwx 1 root root 29 Aug  4  2016 php7.0.conf -> ../mods-available/php7.0.conf
lrwxrwxrwx 1 root root 29 Aug  4  2016 php7.0.load -> ../mods-available/php7.0.load
```

If you don't have it installed you can use the following command to install it:

```
sudo apt install libapache2-mod-php
```

---

### Post by Adrian_Padilla on 2017-08-05
I have both of the mods enabled

  File: 'php7.0.load' -> '../mods-available/php7.0.load'
  Size: 29        	Blocks: 0          IO Block: 4096   symbolic link
Device: fc00h/64512d	Inode: 9307711     Links: 1

Access: (0777/lrwxrwxrwx)  Uid: (    0/    root)   Gid: (    0/    root)




  File: 'php7.0.conf' -> '../mods-available/php7.0.conf'
  Size: 29        	Blocks: 0          IO Block: 4096   symbolic link
Device: fc00h/64512d	Inode: 9307710     Links: 1
Access: (0777/lrwxrwxrwx)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2017-08-05 06:25:10.665539926 -0400
Modify: 2017-05-04 22:59:00.068166215 -0400

---

### Post by Adrian_Padilla on 2017-08-05
lrwxrwxrwx 1 root root 29 May  4 22:59 **php7.0.conf** -> **../mods-available/php7.0.conf**
lrwxrwxrwx 1 root root 29 May  4 22:59 **php7.0.load** -> **../mods-available/php7.0.load**

---

### Post by Adrian_Padilla on 2017-08-05
i dont know if this will be of any importance but i am using VHOSTS

---

### Post by cariboo on 2017-08-05
Using a vhost should make any difference. When I was setting up my server I installed libapache2_mod_ php just worked the way it should.

Does anything show up in /var/log/apache2/error.log?

---

### Post by Adrian_Padilla on 2017-08-05
the only error i am seeing is about the ICO file not being there, that is all that is in there

---

### Post by Adrian_Padilla on 2017-08-06
Maybe i need to clarify this a little better,  

i go to my index.php home page and there should be some arguments called per the page

<?
include 'header.php';
?>
<style type="text/css">
<!--
.style2 {
	font-size: 48px;
	color: #000000;
}
.style3 {font-size: 16px}
.style4 {font-size: medium; }
.style5 {font-size: medium; color: #0033CC; }
-->
</style>

the header is not being called, and i have a feeling it is something to do with the way either 

A) how my apache config is set up, for some reason i think it is not set up right, 
b) maybe there is a permission problem, but i have set all my php pages to 775 permission


any help would be greatly appreciated

---

### Post by SeijiSensei on 2017-08-06
You're using "short tags" ("<?") instead of the complete tag "<?php".  By default short tags are disabled.  You can edit /etc/php7/apache2/php.ini and set "short_open_tag = On".

---

### Post by Adrian_Padilla on 2017-08-06
DAG nabbitttt, i knew it was something simple, thank you so much that did the trick

---

### Post by SeijiSensei on 2017-08-07
Glad I could help.

Please marked this thread [SOLVED] using the Thread Tools link at the top of the page.

---

