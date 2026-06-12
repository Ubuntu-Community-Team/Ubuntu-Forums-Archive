---
title: "[SOLVED] Where is phpmyadmin?"
date: 2009-01-06
forum: Server Platforms
---

### Post by wattaman on 2009-01-06
Hello!
This will sound dumb for the most of you, probably, but...anyway.
I've just installed phpmyadmin from within webmin. Installed fine, but can't access it from the browser
I know it should be here [http://IP/phpmyadmin](http://IP/phpmyadmin), however when I browse it I reeive only 404 errors.
Anyone has any sugestions?
I have Ubuntu 8.04 installed, php5, apache2, mysql5 on my server. 
Thanks!

Almost forgot the phpmyadmin config file:
> <?php
/**
 * Debian local configuration file
 *
 * This file overrides the settings made by phpMyAdmin interactive setup
 * utility.
 *
 * For example configuration see /usr/share/doc/phpmyadmin/examples/config.default.php.gz
 *
 * NOTE: do not add security sensitive data to this file (like passwords)
 * unless you really know what you're doing. If you do, any user that can
 * run PHP or CGI on your webserver will be able to read them. If you still
 * want to do this, make sure to properly secure the access to this file
 * (also on the filesystem level).
 */

/**
 * Server(s) configuration
 */
$i = 0;
// The $cfg['Servers'] array starts with $cfg['Servers'][1].  Do not use $cfg['Servers'][0].
// You can disable a server config entry by setting host to ''.
$i++;

/* Authentication type */
//$cfg['Servers'][$i]['auth_type'] = 'cookie';
/* Server parameters */
//$cfg['Servers'][$i]['host'] = 'localhost';
//$cfg['Servers'][$i]['connect_type'] = 'tcp';
//$cfg['Servers'][$i]['compress'] = false;
/* Select mysqli if your server has it */
//$cfg['Servers'][$i]['extension'] = 'mysql';
/* Optional: User for advanced features */
// $cfg['Servers'][$i]['controluser'] = 'pma';
// $cfg['Servers'][$i]['controlpass'] = 'pmapass';
/* Optional: Advanced phpMyAdmin features */
// $cfg['Servers'][$i]['pmadb'] = 'phpmyadmin';
// $cfg['Servers'][$i]['bookmarktable'] = 'pma_bookmark';
// $cfg['Servers'][$i]['relation'] = 'pma_relation';
// $cfg['Servers'][$i]['table_info'] = 'pma_table_info';
// $cfg['Servers'][$i]['table_coords'] = 'pma_table_coords';
// $cfg['Servers'][$i]['pdf_pages'] = 'pma_pdf_pages';
// $cfg['Servers'][$i]['column_info'] = 'pma_column_info';
// $cfg['Servers'][$i]['history'] = 'pma_history';
// $cfg['Servers'][$i]['designer_coords'] = 'pma_designer_coords';

/*
 * End of servers configuration
 */

/*
 * Directories for saving/loading files from server
 */
$cfg['UploadDir'] = '';
$cfg['SaveDir'] = '';

---

### Post by erwall on 2009-01-06
Easiest thing would be to remove it through webmin and install through the repos;
```
sudo aptitude install phpmyadmin
```
Then you should be able to access it as you attempted before.  Installing through the repos does all the work for you.

---

### Post by wattaman on 2009-01-06
Thank you very much... that did it.

---

### Post by Iowan on 2009-01-06
Is it fixed?  \\:D/ Mark the thread [SOLVED] (Under Thread Tools).

---

