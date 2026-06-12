---
title: "PHP on Ubuntu Server"
date: 2008-04-12
forum: Server Platforms
---

### Post by guitarman on 2008-04-12
Note that I already posted this under the general Installation Forum, but got no replies, so I thought about posting it here.:confused:


Hi all, I have been trying to add a page on my site that runs on my Ubuntu server that will allow users to text me on my cell phone. However page runs in PHP so I installed it but when I load that page, the page loads, but the security code that is suppose to generate a security code with the monofont.ttf never seems to come up. So I created another small file to run the following so I can see what php is running:

<?php
print_r (phpinfo());
?>


but get the following:
Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Warning: Unknown: Failed opening '/var/www/test2.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

Can anyone explain if I did not install PHP properly?

To understand the page that I was trying to create, go to : [www.easykiss123.com](www.easykiss123.com) and look at the SMS Texting video. I have been having problem with the security code appearing on the page when you run it, so when you hit the submit button, I get an response that the security code is incorrect, so I take it that the PHP file does generate the code, but does not display it. I emailed the webmaster of easykiss123, but got no response. I guess that they are not as responsive as the Ubuntu Forums.


Any help would be greatly appreciated.

thanks

---

### Post by songshu on 2008-04-12
did you install php-pear?

---

### Post by guitarman on 2008-04-12
I guess this did not install with the PHP5.  Do I simply do:

sudo apt-get install php-pear  

thanks,

---

### Post by andguent on 2008-04-13
There should be absolutely no harm in trying your sudo line there. Definitely give it a try and go from there.

FYI - your phpinfo() page can be slimmed down even more. I've never done a phpinfo() within a print_r.

```

<?php
  phpinfo();
?>
```

Either way, definitely let us know how it goes and mark this thread as solved when the time is right. Thanks and good luck.

---

### Post by guitarman on 2008-04-13
I'm starting to get a little discouraged.  I create a simple file with the code you provided to test php, uploaded it to my server and ran opened the file with my browser.  I still get:

Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Warning: Unknown: Failed opening '/var/www/phptest.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

Not sure what I'm doing wrong, I know that php and pear have been installed.  Do I need to reinstall them again?

:(

---

### Post by conjur3r on 2008-04-13
Do you have the CGI version of PHP installed?  If so, you need to allow execute priviledges to all PHP files.  Try it on one of those test php files you've already created:

# chmod 755 /var/www/phptest.php

Also, can you do a file listing to see if the www folder is traversible
# ls -l /var/

---

### Post by guitarman on 2008-04-14
ok I will try that later today, however I am almost sure that I did a chmod 777 (in fact) on those test.php files I created.  To install the CGI version of PHP what would be the apt-get command?  I think I may have just installed the regular php.

cheers,

---

### Post by ikonia on 2008-04-14
have you looked at the file it's complaining about 

/usr/share/php:/usr/share/pear

it's trying to include that and complaining about the contents at line 0 

have you even looked at this file yet ?

---

### Post by guitarman on 2008-04-14
Folks,

Here is the first couple of lines of the pear.php file that it is complaining about.  Does anything jump out at you that is wrong:

<?php
/**
 * PEAR, the PHP Extension and Application Repository
 *
 * PEAR class and PEAR_Error class
 *
 * PHP versions 4 and 5
 *
 * LICENSE: This source file is subject to version 3.0 of the PHP license
 * that is available through the world-wide-web at the following URI:
 * [http://www.php.net/license/3_0.txt](http://www.php.net/license/3_0.txt).  If you did not receive a copy of
 * the PHP License and are unable to obtain it through the web, please
 * send a note to [email]license@php.net[/email] so we can mail you a copy immediately.
 *
 * @category   pear
 * @package    PEAR
 * @author     Sterling Hughes <sterling@php.net>
 * @author     Stig Bakken <ssb@php.net>
 * @author     Tomas V.V.Cox <cox@idecnet.com>
 * @author     Greg Beaver <cellog@php.net>
 * @copyright  1997-2006 The PHP Group
 * @license    [http://www.php.net/license/3_0.txt](http://www.php.net/license/3_0.txt)  PHP License 3.0
 * @version    CVS: $Id: PEAR.php,v 1.97 2006/01/06 04:47:36 cellog Exp $
 * @link       [http://pear.php.net/package/PEAR](http://pear.php.net/package/PEAR)
 * @since      File available since Release 0.1
 */

/**#@+
 * ERROR constants
 */
define('PEAR_ERROR_RETURN',     1);
define('PEAR_ERROR_PRINT',      2);
define('PEAR_ERROR_TRIGGER',    4);
define('PEAR_ERROR_DIE',        8);
define('PEAR_ERROR_CALLBACK',  16);
/**
 * WARNING: obsolete
 * @deprecated
 */
define('PEAR_ERROR_EXCEPTION', 32);
/**#@-*/
define('PEAR_ZE2', (function_exists('version_compare') &&
                    version_compare(zend_version(), "2-dev", "ge")));

if (substr(PHP_OS, 0, 3) == 'WIN') {
    define('OS_WINDOWS', true);
    define('OS_UNIX',    false);
    define('PEAR_OS',    'Windows');
} else {
    define('OS_WINDOWS', false);
    define('OS_UNIX',    true);
    define('PEAR_OS',    'Unix'); // blatant assumption
}

// instant backwards compatibility
if (!defined('PATH_SEPARATOR')) {
    if (OS_WINDOWS) {
        define('PATH_SEPARATOR', ';');
    } else {
        define('PATH_SEPARATOR', ':');
    }
}

$GLOBALS['_PEAR_default_error_mode']     = PEAR_ERROR_RETURN;
$GLOBALS['_PEAR_default_error_options']  = E_USER_NOTICE;
$GLOBALS['_PEAR_destructor_object_list'] = array();
$GLOBALS['_PEAR_shutdown_funcs']         = array();
$GLOBALS['_PEAR_error_handler_stack']    = array();

@ini_set('track_errors', true);

---

### Post by riceriot on 2008-04-24
Hi,

I got the same error, and fixed it with some permission changes.  Make sure that your php file is readable by the server:

$chmod 744 /var/www/test2.php

Confirm that it's readable by everyone:

$ls -al
-rwxr--r-- /var/www/test2.php

---

### Post by guitarman on 2008-04-25
Thanks all,
after all this, I simply did a reset of the server and everything came up fine.  The PHP info is now coming up.

Maybe I can ask another piece of advice?? I am trying to get a page that has a security code to work but for some reason the code never comes up.  I followed the directions from this site: [www.easykiss123.com](www.easykiss123.com) (under creating an SMS TEXT form) and created a web site for a client, but as you can see, the security code never comes up. To check it out, you can go to [www.pinatano.com](www.pinatano.com) and click on the bold "send SMS TEXT" on the left (wording on the site is in both English and French).

My PHP info is at: [www.pinatano.com/test2.php](www.pinatano.com/test2.php)

Any ideas?  As per the video on [www.easykiss123.com](www.easykiss123.com) I copied my smstext form in the same directory as all the other files I downloaded from them, but the security code never comes up.

Thanks
:confused:

---

