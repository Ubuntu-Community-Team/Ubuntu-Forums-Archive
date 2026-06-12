---
title: "phpmyadmin only php code"
date: 2011-08-23
forum: Server Platforms
---

### Post by frytoya on 2011-08-23
I've setup a lamb server on ubuntu 10.10 but the php5 seam's not to work : when i test it with the info.php file that i've create, i only get the php code. Same for phpmyadmin. 


Thks for your time

---

### Post by fdrake on 2011-08-23
> **frytoya said:**
> I've setup a lamb server on ubuntu 10.10 but the php5 seam's not to work : when i test it with the info.php file that i've create, i only get the php code. Same for phpmyadmin. 


Thks for your time

well both info.php an myPhpAdmin run with php . 

```

sudo apt-get purge php*
sudo apt-get install mysql-server libapache2-mod-auth-mysql php5-mysql libapache2-mod-php5 php5-common php5-cgi

```

to install the latest phpadmin

```

wget "http://sourceforge.net/projects/phpmyadmin/files%2FphpMyAdmin%2F3.4.3.2%2FphpMyAdmin-3.4.3.2-all-languages.7z/download
#!md5!0c9ddd37b1c539fed7a6eb3ffc65089b"
sudo cp download /var/www/phpMyAdmin.7z
rm download
sudo apt-get install p7zip #make sure that u have 7z installed
cd /var/www
sudo p7zip -d phpMyAdmin.7z
sudo mkdir phpMyAdmin
sudo mv phpMyAdmin-3.4.3.2-all-languages/* -t phpMyAdmin/
sudo rm -r phpMyAdmin-3.4.3.2-all-languages

```

---

### Post by jasonrisenburg on 2011-08-23
that seemed easy

---

### Post by frytoya on 2011-08-23
Ident ! Still getting the php code ! Holly .. you was fast on the reply : thks !

---

### Post by fdrake on 2011-08-23
> **frytoya said:**
> Ident ! Still getting the php code ! Holly .. you was fast on the reply : thks !

to run the php files you have to go with firefox at [http://localhost/phpMyAdmin](http://localhost/phpMyAdmin)

```

firefox http://localhost/phpMyAdmin

```

---

### Post by frytoya on 2011-08-23
Thks for the basic verifications but the bug it's i only get the php code. It's some sort of he can't read it. 
I enter [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) and i get : 

<?php
/* vim: set expandtab sw=4 ts=4 sts=4: */
/**
 * forms frameset
 *
 * @version $Id$
 * @uses    $GLOBALS['strNoFrames']
 * @uses    $GLOBALS['cfg']['QueryHistoryDB']
 * @uses    $GLOBALS['cfg']['Server']['user']
 * @uses    $GLOBALS['cfg']['DefaultTabServer']     as src for the mainframe
 * @uses    $GLOBALS['cfg']['DefaultTabDatabase']   as src for the mainframe
 * @uses    $GLOBALS['cfg']['NaviWidth']            for navi frame width
 * @uses    $GLOBALS['collation_connection']    from $_REQUEST (grab_globals.lib.php)
 *                                              or common.inc.php
 * @uses    $GLOBALS['available_languages'] from common.inc.php (select_lang.lib.php)
 * @uses    $GLOBALS['db']
 * @uses    $GLOBALS['charset']
 * @uses    $GLOBALS['lang']
 * @uses    $GLOBALS['text_dir']
 * @uses    $_ENV['HTTP_HOST']
 * @uses    PMA_getRelationsParam()
 * @uses    PMA_purgeHistory()
 * @uses    PMA_generate_common_url()
 * @uses    PMA_VERSION
 * @uses    session_write_close()
 * @uses    time()
 * @uses    PMA_getenv()
 * @uses    header()                to send charset
 * @package phpMyAdmin
 */

/**
 * Gets core libraries and defines some variables
 */
require_once './libraries/common.inc.php';

---

### Post by SeijiSensei on 2011-08-23
Are you sure you have libapache2-mod-php5 installed?  That's the package that installs the SetHandler directive in /etc/apache2/mods-enabled that tells Apache how to handle files with the .php extension.

---

### Post by levidurfee on 2011-08-23
I already have phpMyAdmin installed, but I'm running 3.3.1. Is this the only way to upgrade to 3.4.x?

---

### Post by frytoya on 2011-08-23
Be careful guys !!!!! I get hacked last night after i post on the forum !!! Be sure every things is secure !

---

### Post by fdrake on 2011-08-23
> **frytoya said:**
> Be careful guys !!!!! I get hacked last night after i post on the forum !!! Be sure every things is secure !

how do you know that? what exactly did you notice?

ps. I do believe you have problem with your apache/php server because you must have installed some other packages that to go in conflict with the regular installation. Beside LAMP what else did you install?

---

