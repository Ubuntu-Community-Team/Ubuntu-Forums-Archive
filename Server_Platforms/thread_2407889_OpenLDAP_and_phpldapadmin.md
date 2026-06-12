---
title: "OpenLDAP and phpldapadmin"
date: 2018-12-10
forum: Server Platforms
---

### Post by nyren-amyra-dael on 2018-12-10
I am trying to set up a RADIUS server for WiFi authentication. I have successfully set up Freeradius, and am trying to create an OpenLDAP directory to add users via phpldapadmin, however, I can’t seem to get it working. I followed the directions at [https://www.techrepublic.com/article/how-to-install-phpldapadmin-on-ubuntu-18-04/](https://www.techrepublic.com/article/how-to-install-phpldapadmin-on-ubuntu-18-04/) to get phpadmin set up on Ubuntu 18.04 server edition. I installed slapd and reconfigured it. I installed apache2 as well and changed the port in ports.conf to 8080. When I navigate to /var/www/html/phpldapadmin/htdocs, this is the lovely message I am greeted with (see below). What can I do to resolve this issue?

```
[COLOR=#000000]<?php[/COLOR]/**
 * phpLDAPadmin Start Page
 *
 * @package phpLDAPadmin
 * @subpackage Page
 */

/**
 */

/*******************************************
<pre>

If you are seeing this in your browser,
PHP is not installed on your web server!!!

</pre>
*******************************************/

/**
 * We will perform some sanity checking here, since this file is normally loaded first when users
 * first access the application.
 */

# The index we will store our config in $_SESSION
define('APPCONFIG','plaConfig');

define('LIBDIR',sprintf('%s/',realpath('../lib/')));
ini_set('display_errors',1);
error_reporting(E_ALL);

# General functions needed to proceed.
ob_start();
if (! file_exists(LIBDIR.'functions.php')) {
    if (ob_get_level()) ob_end_clean();
    die(sprintf("Fatal error: Required file '<b>%sfunctions.php</b>' does not exist.",LIBDIR));
}

if (! is_readable(LIBDIR.'functions.php')) {
    if (ob_get_level()) ob_end_clean();
    die(sprintf("Cannot read the file '<b>%sfunctions.php</b>' its permissions may be too strict.",LIBDIR));
}

if (ob_get_level())
    ob_end_clean();

# Make sure this PHP install has pcre
if (! extension_loaded('pcre'))
    die('<p>Your install of PHP appears to be missing PCRE support.</p><p>Please install PCRE support before using phpLDAPadmin.<br /><small>(Dont forget to restart your web server afterwards)</small></p>');

require LIBDIR.'functions.php';

# Define the path to our configuration file.
if (defined('CONFDIR'))
    $app['config_file'] = CONFDIR.'config.php';
else
    $app['config_file'] = 'config.php';

# Make sure this PHP install has session support
if (! extension_loaded('session'))
    error('<p>Your install of PHP appears to be missing php-session support.</p><p>Please install php-session support before using phpLDAPadmin.<br /><small>(Dont forget to restart your web server afterwards)</small></p>','error',null,true);

# Make sure this PHP install has gettext, we use it for language translation
if (! extension_loaded('gettext'))
    system_message(array(
        'title'=>_('Missing required extension'),
        'body'=>'Your install of PHP appears to be missing GETTEXT support.</p><p>GETTEXT is used for language translation.</p><p>Please install GETTEXT support before using phpLDAPadmin.<br /><small>(Dont forget to restart your web server afterwards)</small>',
        'type'=>'error'));

# Make sure this PHP install has all our required extensions
if (! extension_loaded('ldap'))
    system_message(array(
        'title'=>_('Missing required extension'),
        'body'=>'Your install of PHP appears to be missing LDAP support.<br /><br />Please install LDAP support before using phpLDAPadmin.<br /><small>(Dont forget to restart your web server afterwards)</small>',
        'type'=>'error'));

# Make sure that we have php-xml loaded.
if (! function_exists('xml_parser_create'))
    system_message(array(
        'title'=>_('Missing required extension'),
        'body'=>'Your install of PHP appears to be missing XML support.<br /><br />Please install XML support before using phpLDAPadmin.<br /><small>(Dont forget to restart your web server afterwards)</small>',
        'type'=>'error'));

/**
 * Helper functions.
 * Our required helper functions are defined in functions.php
 */
if (isset($app['function_files']) && is_array($app['function_files']))
    foreach ($app['function_files'] as $file_name ) {
        if (! file_exists($file_name))
            error(sprintf('Fatal error: Required file "%s" does not exist.',$file_name),'error',null,true);

        if (! is_readable($file_name))
            error(sprintf('Fatal error: Cannot read the file "%s", its permissions may be too strict.',$file_name),'error',null,true);

        ob_start();
        require $file_name;
        if (ob_get_level()) ob_end_clean();
    }

# Configuration File check
if (! file_exists($app['config_file'])) {
    error(sprintf(_('You need to configure %s. Edit the file "%s" to do so. An example config file is provided in "%s.example".'),app_name(),$app['config_file'],$app['config_file']),'error',null,true);

} elseif (! is_readable($app['config_file'])) {
    error(sprintf('Fatal error: Cannot read your configuration file "%s", its permissions may be too strict.',$app['config_file']),'error',null,true);
}

# If our config file fails the sanity check, then stop now.
if (! $config = check_config($app['config_file'])) {
    $www['page'] = new page();
    $www['body'] = new block();
    $www['page']->block_add('body',$www['body']);
    $www['page']->display();
    exit;

} else {
    app_session_start();
    $_SESSION[APPCONFIG] = $config;
}

if ($uri = get_request('URI','GET'))
    header(sprintf('Location: cmd.php?%s',base64_decode($uri)));

if (! preg_match('/^([0-9]+\.?)+/',app_version())) {
    system_message(array(
        'title'=>_('This is a development version of phpLDAPadmin'),
        'body'=>'This is a development version of phpLDAPadmin! You should <b>NOT</b> use it in a production environment (although we dont think it should do any damage).',
        'type'=>'info','special'=>true));

    if (count($_SESSION[APPCONFIG]->untested()))
        system_message(array(
            'title'=>'Untested configuration paramaters',
            'body'=>sprintf('The following parameters have not been tested. If you have configured these parameters, and they are working as expected, please let the developers know, so that they can be removed from this message.<br/><small>%s</small>',implode(', ',$_SESSION[APPCONFIG]->untested())),
            'type'=>'info','special'=>true));

    $server = $_SESSION[APPCONFIG]->getServer(get_request('server_id','REQUEST'));
    if (count($server->untested()))
        system_message(array(
            'title'=>'Untested server configuration paramaters',
            'body'=>sprintf('The following parameters have not been tested. If you have configured these parameters, and they are working as expected, please let the developers know, so that they can be removed from this message.<br/><small>%s</small>',implode(', ',$server->untested())),
            'type'=>'info','special'=>true));
}

include './cmd.php'; [COLOR=#000000]?>[/COLOR]
```

---

### Post by wildmanne39 on 2018-12-10
*Thread moved to **Server Platforms for a more appropriate fit**.*

---

### Post by SeijiSensei on 2018-12-11
I quickly skimmed that article, and it didn't seem to include the steps for installing PHP.  It appeared to assume you already had it installed.

If you think you have PHP installed, you could be missing this package which tells Apache how to identify and parse PHP scripts:  libapache2-mod-php7.2

I find the easiest way to install Apache and PHP, and get the MySQL database server thrown in as well, is to use the "lamp-server" meta-package.

```
sudo apt install lamp-server^
```

Make sure to include the "^".

(Many online guides suggest using "tasksel" to install this package, but you don't need it.  Just enter the command above.)

---

