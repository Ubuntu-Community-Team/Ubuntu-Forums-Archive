---
title: "Not parsing php - blank screen"
date: 2011-04-22
forum: Server Platforms
---

### Post by Guenhwyvar on 2011-04-22
[FONT=Arial]I have recently installed ubuntu 11.04, and I have installed[/FONT][FONT=Arial] apache2, php5-mysql, libapache2-mod-php5 and mysql-server.[/FONT][FONT=Arial]

Everytime I try to run a page in firefox the php is just blank. I get the' it works!' page, but no php files display. Some of the pages I have used fine before. I have also used these packages fine before. 

Any ideas? Please help asap. 

Have tried re-installing and php.load etc are in the right place. [/FONT]

---

### Post by bmathis on 2011-04-22
remove the index.html file in /var/www (index.html will be displayed before anyother index.whatever file) and make sure your php files are in the proper location.

---

### Post by Mosabama on 2011-04-22
add index.php to directory index files or what ever the name of the file that you want it to start first. cause index.php is not included by default I think

---

### Post by Guenhwyvar on 2011-04-22
I have deleted index.html, but I have no files called index anyway. 

I get a blank screen, not an error so the files are in the right place - (and i have checked)

Have been going directly to files ie localhost/home.php

---

### Post by Mosabama on 2011-04-22
are you sure that home.php actually generates an output? can you post the file code here?

---

### Post by Guenhwyvar on 2011-04-22
I am using files that work fine on my other computers and my uni server.

---

### Post by usatonycuba on 2011-04-22
Open your terminal and type:
```
sudo su
```
It will prompt for password (enter pass, and then type):

```
 gedit /var/www/php_test.php
```
Copy/Paste the following into your php_test.php

```

<?php phpinfo(); ?>

```

```
sudo /etc/init.d/apache2 restart 
```

Save and close.. Go to your Browser and type: [http://localhost/php_test.php](http://localhost/php_test.php)

**PD**: The best command that I have found, installing LAMP is
```
sudo apt-get install lamp-server^
``` .. that install everything..

---

