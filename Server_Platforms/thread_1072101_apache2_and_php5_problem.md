---
title: "apache2 and php5 problem"
date: 2009-02-17
forum: Server Platforms
---

### Post by ahsanghalib on 2009-02-17
Hi, I have install the apache2 and php5 on the ubuntu 8.04. It is working. I have checked the php working by creating the file of phpinfo.php in the /var/www folder and it's work. but now when i create any sort of index.php file it don't work. i says that you don't have the permission of viewing this file. or that you don't have any sort of index file in it. because i have replaced the index.html file the index.php file but it don't work as it should be. i am new to ubuntu. i am web developer i have checked all the configurations too. i have also made the /var/www folder permission to rwxrwxrwx. but now to it don't work. please help me in this regard.

another thing is that i have fat32 partitions on my hard disk. i have my web project folder on that. i want to make link of my default //localhost/ to that folder it's path is /media/disk-1/yoreca/ i have edit the virtual host file but not work what should i do. i has all the files including the index.php file to. that same folder i have copies to /var/www folder but don't work.

thankx.

---

### Post by cdtech on 2009-02-17
Be sure you have the php enabled within the default configuration file:
```
AddOutputFilter INCLUDES .html .php
```

---

### Post by ahsanghalib on 2009-02-18
There is another thing for the clearity:

I have made the phpinfo.php file it works. But all other .php & .html files are not working. It returns somthing following that:

arning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Fatal error: Unknown: Failed opening required '/home/ghalib/yoreca/index.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0) 

Where should i please that code. 

AddOutputFilter INCLUDES .html .php

---

### Post by catinthehat on 2010-07-21
I had to change the permissions (chmod 644) on all files to get them to be able to be read and displayed through apache. You could try this :D

---

