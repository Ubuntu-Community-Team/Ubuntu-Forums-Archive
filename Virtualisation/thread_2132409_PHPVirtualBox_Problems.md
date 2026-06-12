---
title: "PHPVirtualBox Problems"
date: 2013-04-04
forum: Virtualisation
---

### Post by molnar20 on 2013-04-04
I'm able to get a log in screen but when I try logging in I get an error logging into vboxwebsrv.
  I tried user: admin pass: admin since that is the default. 

```

Exception Object
 (     
[message:protected] => Error logging in to vboxwebsrv.     
[string:Exception:private] => 
     [code:protected] => 64 
    [file:protected] => /var/www/phpvirtualbox/lib/ajax.php
     [line:protected] => 128     [trace:Exception:private] => Array
         (         
) 
       [previous:Exception:Private] => 
 )   

```

Here is my config.php file is the $password my actual password to log in...I covered it up with * because I didn't know. 
  
```

<?php
/**
 * phpVirtualBox example configuration. 
 * @version $Id: config.php-example 452 2012-10-17 12:22:12Z imooreyahoo@gmail.com $
 *
 * rename to config.php and edit as needed.
 *
 */
class phpVBoxConfig {

/* Username / Password for system user that runs VirtualBox */
var $username = 'vbox';
var $password = '****';

/* SOAP URL of vboxwebsrv (not phpVirtualBox's URL) */
var $location = 'http://127.0.0.1:18083/';

/* Default language. See languages folder for more language options.
 * Can also be changed in File -> Preferences -> Language in
 * phpVirtualBox.
 */
var $language = 'en';

/* Set the standard VRDE Port Number / Range, e.g. 1010-1020 or 1027 */
var $vrdeports = '9000-9100';

/*
 *
 * Not-so-common options / tweaking
 *
 */

// Max number of progress operations to keep in list
var $maxProgressList = 5;

/*
Allow to prompt deletion hard disk files on removal from Virtual Media Manager.
If this is not set, files are always kept. If this is set, you will be PROMPTED
to decide whether or not you would like to delete the hard disk file(s) when you
remove a hard disk from virtual media manager. You may still choose not to delete
the file when prompted.
*/
var $deleteOnRemove = true;

/*
 * File / Folder browser settings
 */

// Restrict file types
var $browserRestrictFiles = array('.iso','.vdi','.vmdk','.img','.bin','.vhd','.hdd','.ovf','.ova','.xml','.vbox','.cdr','.dmg','.ima','.dsk','.vfd');


/*
 * Misc
 */

/*
 * Auto-refresh interval in seconds for VirtualBox host memory usage information.
 * Any value below 3 will be ignored.
 */
var $hostMemInfoRefreshInterval = 5;

/* END SETTINGS  */

```

---

