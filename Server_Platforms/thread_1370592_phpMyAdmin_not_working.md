---
title: "phpMyAdmin not working"
date: 2010-01-02
forum: Server Platforms
---

### Post by Gadgetmo on 2010-01-02
I installed phpMyAdmin by using ```
sudo apt-get install phpmyadmin

``` and then ```
  sudo ln -s /usr/share/phpmyadmin/ /var/www/phpmyadmin
``` and it worked. But when I type in my username and password, or even a random username and password, the page just reloads and nothing happens. :confused:

---

### Post by zey on 2010-01-02
Have you try to use user nobody and no password?

[http://z-computer-z.blogspot.com]("http://z-computer-z.blogspot.com/")

---

### Post by Gadgetmo on 2010-01-02
The page reloaded and it stayed blank.

---

### Post by lightsabersetc on 2010-01-02
maybe a stupid question, but have u cleared the cookies and cache on ur browser and tried again?

---

### Post by Gadgetmo on 2010-01-02
Nothing happened.

---

### Post by Charlietje on 2010-01-02
what username and password did you use?

you must provide a mysql username and password.

Also, check the owner and rights of the phpmyadmin folder


regards

---

### Post by Gadgetmo on 2010-01-03
For the user I use root, and for the password I use my root password. I've also tested my own username and password. I changed the privileges for the phpmyadmin folder to 777 (rwxrwxrwx). Whenever I type the username + password, the page just reloads - it doesn't even display "Incorrect Username and Password". :confused:

---

### Post by zemon_ on 2010-01-03
Did you reboot after the install of phpmyadmin?

---

### Post by Charlietje on 2010-01-03
can you enter the mysql server?

```
mysql -uroot -ppassword
```

---

### Post by Gadgetmo on 2010-01-03
I've rebooted the server. When I typed the command into terminal it said: ```
Access denied for user 'root'@'localhost' (using password: YES)
```
But I did try logging in using Adminer as a test and it worked.

---

### Post by Charlietje on 2010-01-04
> **Gadgetmo said:**
> I've rebooted the server. When I typed the command into terminal it said: ```
Access denied for user 'root'@'localhost' (using password: YES)
```
But I did try logging in using Adminer as a test and it worked.

Did you try to login with **Adminer ** in phpMyAdmin?

---

### Post by Charlietje on 2010-01-04
Have you also looked in the log-file?

---

### Post by Gadgetmo on 2010-01-04
I used the same username and password on Adminer ([http://www.adminer.org/](http://www.adminer.org/)) as I did with phpMyAdmin.

Where are the log files located?

---

### Post by Charlietje on 2010-01-04
> **Gadgetmo said:**
> I used the same username and password on Adminer ([http://www.adminer.org/](http://www.adminer.org/)) as I did with phpMyAdmin.

Where are the log files located?

log files are located at /var/log

try the following
open a terminal and execute

```
tail -f /var/log/syslog
```

with that you will be able to follow the syslog live.

With that running, try to log on with phpmyadmin

If error occurs you'll be able to see them.

---

### Post by Gadgetmo on 2010-01-05
nothing's happening :(

---

### Post by Charlietje on 2010-01-05
How do you go to the website?
[http://.](http://.)..

---

### Post by Gadgetmo on 2010-01-06
[http://192.168.0.6/](http://192.168.0.6/)

---

### Post by Charlietje on 2010-01-06
I would advise you to uninstall phpmyadmin
```
apt-get remove phpmyadmin
```

and install in manually.
You can download it at
```
http://www.phpmyadmin.net/home_page/downloads.php
```

extract it and move it to /var/www/phpmyadmin

Make sure that phpmodule is loaded in apache2 and that the mysql server is running

If that is the case, then you can go to your site
```
http:\\...\phpmyadmin
```

---

### Post by Gadgetmo on 2010-01-06
I did that, created the config directory and set it to 777, made a duplicate of config.sample.inc.php and renamed it to config.inc.php, changed it slightly so it said:
```
<?php
/* vim: set expandtab sw=4 ts=4 sts=4: */
/**
 * phpMyAdmin sample configuration, you can use it as base for
 * manual configuration. For easier setup you can use setup/
 *
 * All directives are explained in Documentation.html and on phpMyAdmin
 * wiki <http://wiki.phpmyadmin.net>.
 *
 * @version $Id: config.sample.inc.php 13111 2009-11-09 15:02:21Z lem9 $
 * @package phpMyAdmin
 */

/*
 * This is needed for cookie based authentication to encrypt password in
 * cookie
 */
$cfg['blowfish_secret'] = ''; /* YOU MUST FILL IN THIS FOR COOKIE AUTH! */

/*
 * Servers configuration
 */
$i = 0;

/*
 * First server
 */
$i++;
/* Authentication type */
$cfg['Servers'][$i]['auth_type'] = 'cookie';
/* Server parameters */
$cfg['Servers'][$i]['host'] = 'localhost';
$cfg['Servers'][$i]['connect_type'] = 'tcp';
$cfg['Servers'][$i]['compress'] = false;
/* Select mysqli if your server has it */
$cfg['Servers'][$i]['extension'] = 'mysqli';
$cfg['Servers'][$i]['AllowNoPassword'] = false;

/* rajk - for blobstreaming */
$cfg['Servers'][$i]['bs_garbage_threshold'] = 50;
$cfg['Servers'][$i]['bs_repository_threshold'] = '32M';
$cfg['Servers'][$i]['bs_temp_blob_timeout'] = 600;
$cfg['Servers'][$i]['bs_temp_log_threshold'] = '32M';

/* User for advanced features */
$cfg['Servers'][$i]['controluser'] = 'pma';
$cfg['Servers'][$i]['controlpass'] = 'pmapass';
/* Advanced phpMyAdmin features */
$cfg['Servers'][$i]['pmadb'] = 'phpmyadmin';
// $cfg['Servers'][$i]['bookmarktable'] = 'pma_bookmark';
// $cfg['Servers'][$i]['relation'] = 'pma_relation';
// $cfg['Servers'][$i]['table_info'] = 'pma_table_info';
// $cfg['Servers'][$i]['table_coords'] = 'pma_table_coords';
// $cfg['Servers'][$i]['pdf_pages'] = 'pma_pdf_pages';
// $cfg['Servers'][$i]['column_info'] = 'pma_column_info';
// $cfg['Servers'][$i]['history'] = 'pma_history';
// $cfg['Servers'][$i]['designer_coords'] = 'pma_designer_coords';
/* Contrib / Swekey authentication */
// $cfg['Servers'][$i]['auth_swekey_config'] = '/etc/swekey-pma.conf';

/*
 * End of servers configuration
 */

/*
 * Directories for saving/loading files from server
 */
$cfg['UploadDir'] = '';
$cfg['SaveDir'] = '';

?>
```, and then finally logged in with the username pma and the password pmapass. Finally, nothing happened.   ](*,)

---

### Post by Charlietje on 2010-01-06
try

[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

---

### Post by Gadgetmo on 2010-01-06
nothing happened :(

---

### Post by Charlietje on 2010-01-06
is your apache and php running correctly?

pls, give the output of

```
dpkg -l | grep apache2
```

---

### Post by Gadgetmo on 2010-01-06
```
arthur@Linux-G4:~$ dpkg -l | grep apache2
ii  apache2                               2.2.12-1ubuntu2.1                          Apache HTTP Server metapackage
ii  apache2-mpm-prefork                   2.2.12-1ubuntu2.1                          Apache HTTP Server - traditional non-threaded model
ii  apache2-utils                         2.2.12-1ubuntu2.1                          utility programs for webservers
ii  apache2.2-bin                         2.2.12-1ubuntu2.1                          Apache HTTP Server common binary files
ii  apache2.2-common                      2.2.12-1ubuntu2.1                          Apache HTTP Server common files
ii  libapache2-mod-php5                   5.2.10.dfsg.1-2ubuntu6.3                   server-side, HTML-embedded scripting language (Apache 2 module)
```

---

### Post by Charlietje on 2010-01-06
That seems good.

What is the output of
```
netstat -nat
```

you should have **tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN** in the list, so we are sure that your mysql server is listening

did you change to 777 recursive, or just the folder phpmyadmin?

---

