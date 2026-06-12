---
title: "#1045 Cannot log in to the MySQL server"
date: 2012-11-29
forum: Server Platforms
---

### Post by WASHAD on 2012-11-29
Looking to be taught to fish here, and I'd call myself an high-beginner / intermediate ubuntu user. 

**Problem:** When trying to run phpmyadmin, I get the following error "#1045 Cannot log in to the MySQL server"

**What I've done:** I have verified that the root password is correct in MySQL and that the service is started. I have veried that there is a phpmyadmin table created within mysql. I purged and re-installed phpmyadmin. I have restarted Ubuntu. I've tried to edit the conifg.ini file for phpmyadmin, adding the user of root and the password (in plain text), but I get a configuration error after doing that and still get the dabase connection error. 

**Question:** What steps should I take to troubleshoot this problem. Think less about giving me actual code, wrather psuedo code responses (unless I have to cry uncle and ask for more. 

Thank you.

---

### Post by dapperdanny77 on 2012-11-29
are you able to login from command line?
```

>mysql -u root -p 

```

---

### Post by WASHAD on 2012-11-29
> **dapperdanny77 said:**
> are you able to login from command line?


Yup, I can log in just fine from the command line. I should note that I ran the security script to remove blank users and such. 


```

steve@UB12VB:~$ mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 50
Server version: 5.5.28-0ubuntu0.12.04.2 (Ubuntu)

Copyright (c) 2000, 2012, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> 


```

---

### Post by sandyd on 2012-11-29
> **WASHAD said:**
> Looking to be taught to fish here, and I'd call myself an high-beginner / intermediate ubuntu user. 

**Problem:** When trying to run phpmyadmin, I get the following error "#1045 Cannot log in to the MySQL server"

**What I've done:** I have verified that the root password is correct in MySQL and that the service is started. I have veried that there is a phpmyadmin table created within mysql. I purged and re-installed phpmyadmin. I have restarted Ubuntu. I've tried to edit the conifg.ini file for phpmyadmin, adding the user of root and the password (in plain text), but I get a configuration error after doing that and still get the dabase connection error. 

**Question:** What steps should I take to troubleshoot this problem. Think less about giving me actual code, wrather psuedo code responses (unless I have to cry uncle and ask for more. 

Thank you.

can you post your config.ini? (just replace the username and password.)

---

### Post by WASHAD on 2012-11-29
> **sandyd said:**
> can you post your config.ini? (just replace the username and password.)

This is from config.inc.php



> 

<?php
/**
 * Debian local configuration file
 *
 * This file overrides the settings made by phpMyAdmin interactive setup
 * utility.
 *
 * For example configuration see
 *   /usr/share/doc/phpmyadmin/examples/config.sample.inc.php
 * or
 *   /usr/share/doc/phpmyadmin/examples/config.manyhosts.inc.php
 *
 * NOTE: do not add security sensitive data to this file (like passwords)
 * unless you really know what you're doing. If you do, any user that can
 * run PHP or CGI on your webserver will be able to read them. If you still
 * want to do this, make sure to properly secure the access to this file
 * (also on the filesystem level).
 */

// Load secret generated on postinst
include('/var/lib/phpmyadmin/blowfish_secret.inc.php');

// Load autoconf local config
include('/var/lib/phpmyadmin/config.inc.php');

/**
 * Server(s) configuration
 */
$i = 0;
// The $cfg['Servers'] array starts with $cfg['Servers'][1].  Do not use $cfg['Servers'][0].
// You can disable a server config entry by setting host to ''.
$i++;

/**
 * Read configuration from dbconfig-common
 * You can regenerate it using: dpkg-reconfigure -plow phpmyadmin
 */
if (is_readable('/etc/phpmyadmin/config-db.php')) {
    require('/etc/phpmyadmin/config-db.php');
} else {
    error_log('phpmyadmin: Failed to load /etc/phpmyadmin/config-db.php.'
        . ' Check group www-data has read access.');
}

/* Configure according to dbconfig-common if enabled */
if (!empty($dbname)) {
    /* Authentication type */
    $cfg['Servers'][$i]['auth_type'] = 'cookie';
    /* Server parameters */
    if (empty($dbserver)) $dbserver = 'localhost';
    $cfg['Servers'][$i]['host'] = $dbserver;

    if (!empty($dbport) || $dbserver != 'localhost') {
        $cfg['Servers'][$i]['connect_type'] = 'tcp';
        $cfg['Servers'][$i]['port'] = $dbport;
    }
    //$cfg['Servers'][$i]['compress'] = false;
    /* Select mysqli if your server has it */
    $cfg['Servers'][$i]['extension'] = 'mysqli';
    /* Optional: User for advanced features */
    $cfg['Servers'][$i]['controluser'] = $dbuser;
    $cfg['Servers'][$i]['controlpass'] = $dbpass;
    /* Optional: Advanced phpMyAdmin features */
    $cfg['Servers'][$i]['pmadb'] = $dbname;
    $cfg['Servers'][$i]['bookmarktable'] = 'pma_bookmark';
    $cfg['Servers'][$i]['relation'] = 'pma_relation';
    $cfg['Servers'][$i]['table_info'] = 'pma_table_info';
    $cfg['Servers'][$i]['table_coords'] = 'pma_table_coords';
    $cfg['Servers'][$i]['pdf_pages'] = 'pma_pdf_pages';
    $cfg['Servers'][$i]['column_info'] = 'pma_column_info';
    $cfg['Servers'][$i]['history'] = 'pma_history';
    $cfg['Servers'][$i]['designer_coords'] = 'pma_designer_coords';
    $cfg['Servers'][$i]['tracking'] = 'pma_tracking';
    $cfg['Servers'][$i]['userconfig'] = 'pma_userconfig';

    /* Uncomment the following to enable logging in to passwordless accounts,
     * after taking note of the associated security risks. */
    // $cfg['Servers'][$i]['AllowNoPassword'] = TRUE;

    /* Advance to next server for rest of config */
    $i++;
}

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
/* Uncomment the following to enable logging in to passwordless accounts,
 * after taking note of the associated security risks. */
// $cfg['Servers'][$i]['AllowNoPassword'] = TRUE;

/*
 * End of servers configuration
 */

/*
 * Directories for saving/loading files from server
 */
$cfg['UploadDir'] = '';
$cfg['SaveDir'] = '';




---

