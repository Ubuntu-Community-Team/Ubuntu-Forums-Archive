---
title: "Problem on installing Wordpress"
date: 2013-01-31
forum: Server Platforms
---

### Post by satimis on 2013-01-31
Hi all,

Ubuntu 12.04 desktop 64bit
Wordpress

I was following;
How to Install Wordpress on Ubuntu 12.04 LTS
[http://linuxmoz.com/how-to-install-wordpress-on-ubuntu-12-04-lts/](http://linuxmoz.com/how-to-install-wordpress-on-ubuntu-12-04-lts/)

to install Wordpress.  Installation went through without much problem except on browser running;
[http://localhost/wordpress](http://localhost/wordpress)
unable to ope PHTML file.

Then I followed
Cannot open php PHTML file
[http://www.unixmen.com/cannot-open-php-phtml-file/](http://www.unixmen.com/cannot-open-php-phtml-file/)

install libapache2-mod-php5

Now on browser running;
[http://localhost/wordpress/](http://localhost/wordpress/)```

Error establishing a database connection

```

I haven't setup mysql yet.

Please help.  TIA

B.R.
satimis

---

### Post by lisati on 2013-01-31
Wordpress needs a database system (e.g. MySQL) to be installed in order to work, which is why Wordpress was unable to establish a connection.

Instructions for installing MySql on 12.04 can be found here: [https://help.ubuntu.com/12.04/serverguide/mysql.html](https://help.ubuntu.com/12.04/serverguide/mysql.html)

---

### Post by satimis on 2013-01-31
> **lisati said:**
> Wordpress needs a database system (e.g. MySQL) to be installed in order to work, which is why Wordpress was unable to establish a connection.

Instructions for installing MySql on 12.04 can be found here: [https://help.ubuntu.com/12.04/serverguide/mysql.html](https://help.ubuntu.com/12.04/serverguide/mysql.html)
Thanks for your advice.

mysql is now running;
$ sudo netstat -tap | grep mysql```

tcp        0      0 localhost:mysql         *:*                     LISTEN      1097/mysqld     

```

But still Wordpress could'nt be connected;
[http://localhost/wordpress/](http://localhost/wordpress/)
```

Error establishing a database connection

```

---

### Post by Habitual on 2013-01-31
[http://codex.wordpress.org/Installing_WordPress#Famous_5-Minute_Install](http://codex.wordpress.org/Installing_WordPress#Famous_5-Minute_Install)

...wp-config.php...

---

### Post by satimis on 2013-02-01
> **Habitual said:**
> [http://codex.wordpress.org/Installing_WordPress#Famous_5-Minute_Install](http://codex.wordpress.org/Installing_WordPress#Famous_5-Minute_Install)

...wp-config.php...
Hi,

Thanks for your advice and link

$ ls -al /usr/share/wordpress/wp-config.php ```

lrwxrwxrwx 1 www-data root 28 Jan 16  2012 /usr/share/wordpress/wp-config.php -> /etc/wordpress/wp-config.php

```

$ cat /etc/wordpress/wp-config.php ```

<?php
/***
 * WordPress's Debianised default master config file
 * Please do NOT edit and learn how the configuration works in
 * /usr/share/doc/wordpress/README.Debian
 ***/

/* Look up a host-specific config file in
 * /etc/wordpress/config-<host>.php or /etc/wordpress/config-<domain>.php
 */
$debian_server = preg_replace('/:.*/', "", $_SERVER['HTTP_HOST']);
$debian_server = preg_replace("/[^a-zA-Z0-9.\-]/", "", $debian_server);
$debian_file = '/etc/wordpress/config-'.strtolower($debian_server).'.php';
/* Main site in case of multisite with subdomains */
$debian_main_server = preg_replace("/^[^.]*\./", "", $debian_server);
$debian_main_file = '/etc/wordpress/config-'.strtolower($debian_main_server).'.php';

if (file_exists($debian_file)) {
    require_once($debian_file);
    define('DEBIAN_FILE', $debian_file);
} elseif (file_exists($debian_main_file)) {
    require_once($debian_main_file);
    define('DEBIAN_FILE', $debian_main_file);
} elseif (file_exists("/etc/wordpress/config-default.php")) {
    require_once("/etc/wordpress/config-default.php");
    define('DEBIAN_FILE', "/etc/wordpress/config-default.php");
} else {
    header("HTTP/1.0 404 Not Found");
    echo "Neither <b>$debian_file</b> nor <b>$debian_main_file</b> could be foun
founhp';

if (file_exists($debian_file)) {
    require_once($debian_file);
    define('DEBIAN_FILE', $debian_file);
} elseif (file_exists($debian_main_file)) {
    require_once($debian_main_file);
    define('DEBIAN_FILE', $debian_main_file);
} elseif (file_exists("/etc/wordpress/config-default.php")) {
    require_once("/etc/wordpress/config-default.php");
    define('DEBIAN_FILE', "/etc/wordpress/config-default.php");
} else {
    header("HTTP/1.0 404 Not Found");
    echo "Neither <b>$debian_file</b> nor <b>$debian_main_file</b> could be found. <br/> Ensure one of them exists, is readable by the webserver and contains the right password/username.";
    exit(1);
}

/* Default value for some constants if they have not yet been set
   by the host-specific config files */
define('ABSPATH', '/usr/share/wordpress/');
define('WP_CORE_UPDATE', false);
define('WP_ALLOW_MULTISITE', true);
define('DB_NAME', 'wordpress');
define('DB_USER', 'wordpress');
define('DB_HOST', 'localhost');

/* Default value for the table_prefix variable so that it doesn't need to
   be put in every host-specific config file */
if (!isset($table_prefix)) {
    $table_prefix = 'wp_';
}

    $table_prefix = 'wp_';
}

require_once(ABSPATH . 'wp-settings.php');
?>

```

Whether only change;```

define('DB_NAME', 'wordpress');
define('DB_USER', 'wordpress');

```
as;
```

define('DB_NAME', 'mysql');
define('DB_USER', 'root');

```
???

Where to add password?


Do I need to change following file as well?
$ cat /usr/share/wordpress/wp-config-sample.php
```

<?php
/**
 * The base configurations of the WordPress.
 *
 * This file has the following configurations: MySQL settings, Table Prefix,
 * Secret Keys, WordPress Language, and ABSPATH. You can find more information
 * by visiting {@link [http://codex.wordpress.org/Editing_wp-config.php](http://codex.wordpress.org/Editing_wp-config.php) Editing
 * wp-config.php} Codex page. You can get the MySQL settings from your web host.
 *
 * This file is used by the wp-config.php creation script during the
 * installation. You don't have to use the web site, you can just copy this file
 * to "wp-config.php" and fill in the values.
 *
 * @package WordPress
 */

// ** MySQL settings - You can get this info from your web host ** //
/** The name of the database for WordPress */
define('DB_NAME', 'database_name_here');

/** MySQL database username */
define('DB_USER', 'username_here');

/** MySQL database password */
define('DB_PASSWORD', 'password_here');

/** MySQL hostname */
define('DB_HOST', 'localhost');

/** Database Charset to use in creating database tables. */
define('DB_CHARSET', 'utf8');

/** The Database Collate type. Don't change this if in doubt. */
define('DB_COLLATE', '');

/**#@+
 * Authentication Unique Keys and Salts.
 *
 * Change these to different unique phrases!
 * You can generate these using the {@link [https://api.wordpress.org/secret-key/1.1/salt/](https://api.wordpress.org/secret-key/1.1/salt/) WordPress.org secret-key *********
 * You can change these at any point in time to invalidate all existing cookies. This will force all users to have to log in again.
 *
 * @since 2.6.0
 */
define('AUTH_KEY',         'put your unique phrase here');
define('SECURE_AUTH_KEY',  'put your unique phrase here');
define('LOGGED_IN_KEY',    'put your unique phrase here');
define('NONCE_KEY',        'put your unique phrase here');
define('AUTH_SALT',        'put your unique phrase here');
define('SECURE_AUTH_SALT', 'put your unique phrase here');
define('LOGGED_IN_SALT',   'put your unique phrase here');
define('NONCE_SALT',       'put your unique phrase here');

/**#@-*/

/**
 * WordPress Database Table prefix.
 *
 * You can have multiple installations in one database if you give each a unique
 * prefix. Only numbers, letters, and underscores please!
 */
$table_prefix  = 'wp_';

/**
 * WordPress Localized Language, defaults to English.
 *
 * Change this to localize WordPress. A corresponding MO file for the chosen
 * language must be installed to wp-content/languages. For example, install
 * de_DE.mo to wp-content/languages and set WPLANG to 'de_DE' to enable German
 * language support.
 */
define('WPLANG', '');

/**
 * For developers: WordPress debugging mode.
 *
 * Change this to true to enable the display of notices during development.
 * It is strongly recommended that plugin and theme developers use WP_DEBUG
 * in their development environments.
 */
define('WP_DEBUG', false);

/* That's all, stop editing! Happy blogging. */

/** Absolute path to the WordPress directory. */
if ( !defined('ABSPATH') )
	define('ABSPATH', dirname(__FILE__) . '/');

/** Sets up WordPress vars and included files. */
require_once(ABSPATH . 'wp-settings.php');

```

On the captioned file I found;```

/** MySQL database password */
define('DB_PASSWORD', 'password_here');

```

TIA

satimis

---

### Post by oygle on 2013-02-02
All you have to do to get the WP insall going is to modify wp-config.php with the following

```

define('DB_NAME', 'the name of the database');

/** MySQL database username */
define('DB_USER', 'the username to connect to the db');

/** MySQL database password */
define('DB_PASSWORD', 'the username password');

```

use wp-config-sample.php as your template for this. I.e Take a copy of 'sample', modify it to contain db name, username and pwd, and save it as wp-config.php

Then you should be right for the WP install.

---

### Post by satimis on 2013-02-02
> **oygle said:**
> All you have to do to get the WP insall going is to modify wp-config.php with the following

```

define('DB_NAME', 'the name of the database');

/** MySQL database username */
define('DB_USER', 'the username to connect to the db');

/** MySQL database password */
define('DB_PASSWORD', 'the username password');

```

use wp-config-sample.php as your template for this. I.e Take a copy of 'sample', modify it to contain db name, username and pwd, and save it as wp-config.php

Then you should be right for the WP install.
Hi,

Thanks for your advice.

Performed following steps;

.satimis@localhost:~$ ls -al /usr/share/wordpress/wp-config.php ```

lrwxrwxrwx 1 www-data root 28 Jan 16  2012 /usr/share/wordpress/wp-config.php -> /etc/wordpress/wp-config.php

```
/usr/share/wordpress/wp-config.php 
is sym-link to 
/etc/wordpress/wp-config.php

$ sudo cp /etc/wordpress/wp-config.php /etc/wordpress/wp-config.php.OLD

$ sudo cp /usr/share/wordpress/wp-config-sample.php /usr/share/wordpress/wp-config-sample.php.OLD

$ sudo gedit /usr/share/wordpress/wp-config-sample.php
change as;```

define('DB_NAME', 'mysql);

/** MySQL database username */
define('DB_USER', 'root');

define('DB_PASSWORD', 'mysq-root password');

```

and save the file;
wp-config-sample.php.NEW

Remark; There in only one user in MySQL

$ sudo cp /usr/share/wordpress/wp-config-sample.php.NEW /etc/wordpress/wp-config.php

On browser;
[http://localhost/wordpress/](http://localhost/wordpress/)
popup
/localhost/workpress/wp-admin/install.php

What shall I fill in on;
Site Title ?

Thanks

satimis

---

### Post by oygle on 2013-02-02
> **satimis said:**
> 
On browser;
[http://localhost/wordpress/](http://localhost/wordpress/)
popup
/localhost/workpress/wp-admin/install.php

What shall I fill in on;
Site Title ?


Whatever you want it to be, the name of your site. You can change it later if you don't like it.

[http://codex.wordpress.org/Installing_WordPress](http://codex.wordpress.org/Installing_WordPress)

---

### Post by satimis on 2013-02-02
> **oygle said:**
> Whatever you want it to be, the name of your site. You can change it later if you don't like it.

[http://codex.wordpress.org/Installing_WordPress](http://codex.wordpress.org/Installing_WordPress)

I got it done.  Thanks

satimis

---

