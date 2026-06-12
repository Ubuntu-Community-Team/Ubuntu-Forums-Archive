---
title: "lighttpd phpmyadmin"
date: 2009-03-24
forum: Server Platforms
---

### Post by slamjam on 2009-03-24
HELP!!!!

I'm trying to setup phpmyadmin on ubuntu (Hardy), i'm using the latest version of php, lihttpd and MYSQL.

I've used this to setup the server: [http://nanotux.com/blog/the-ultimate-server/](http://nanotux.com/blog/the-ultimate-server/).

Then I tried to install phpmyadmin using sudo apt-get install phpmyadmin but I'm getting the errors below when I restart lighttpd:
 * Stopping web server lighttpd
   ...done.
 * Starting web server lighttpd
2009-03-24 10:11:09: (configfile.c.901) opening configfile  /etc/lighttpd/conf-enabled/50-phpmyadmin.conf failed: No such file or directory 
2009-03-24 10:11:09: (configfile.c.855) source: /usr/share/lighttpd/include-conf-enabled.pl line: 3 pos: 1 parser failed somehow near here: (EOL) 
2009-03-24 10:11:09: (configfile.c.855) source: /etc/lighttpd/lighttpd.conf line: 157 pos: 1 parser failed somehow near here: (EOL) 
   ...fail!

I believe this is because this directory is empty /etc/phpmyadmin and I think this file should be there??? /etc/phpmyadmin/lighttpd.conf.

But i'm not sure([https://bugs.launchpad.net/debian/+source/lighttpd/+bug/179484](https://bugs.launchpad.net/debian/+source/lighttpd/+bug/179484)).

I have 2 symbolic links here: /etc/lighttpd/conf-avaiable/50-phpmyadmin.conf and /etc/lighttpd/conf-enabled/50-phpmyadmin.conf.

If I removed the 2 symbolic links lighttpd restarts and works but no phpmyadmin.

Please help.

---

### Post by BkkBonanza on 2009-03-24
From what I recall there is no need for a conf file for phpmyadmin. It just needs to sit somewhere in your web accessible files and then edit the config file in the phpmyadmin directory (in the web files). So if you installed phpmyadmin into /var/www/mysite/phpmyadmin then in that directory there is a config file that needs to have it's root path set to work.

Also - I thought people were moving in droves from lighttpd to nginx... a better solution that is still actively worked on. Funny to see that linked page pushing lighttpd nowadays.

---

### Post by slamjam on 2009-03-24
Hi

thank you for your response.

I didn't know regarding lighttpd???

I have removed the SLs and now I can access phpmyadmin and log but I get the below warnings on each page:

Warning: include(/etc/phpmyadmin/config.header.inc.php) [function.include]: failed to open stream: No such file or directory in /usr/share/phpmyadmin/config.header.inc.php on line 6

Warning: include() [function.include]: Failed opening '/etc/phpmyadmin/config.header.inc.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /usr/share/phpmyadmin/config.header.inc.php on line 6


Warning: include(/etc/phpmyadmin/config.footer.inc.php) [function.include]: failed to open stream: No such file or directory in /usr/share/phpmyadmin/config.footer.inc.php on line 6

Warning: include() [function.include]: Failed opening '/etc/phpmyadmin/config.footer.inc.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /usr/share/phpmyadmin/config.footer.inc.php on line 6

On line 6 the php file is trying to include another php file from /etc/phpmyadmin but this directory is empty to the files do not exist.

Is this correct?

---

### Post by BkkBonanza on 2009-03-24
Hmmm. sounds a bit odd. Generally we don't install php scripts under /etc so it shouldn't be trying to find them there. I expect it was installed in the wrong place or an incorrect path was typed during install.

If /var/www is your root web dir, for example (yours may be different) then all the php files should be located somewhere down from there. If the config files are trying to get them from under /etc then most likely the include directives in the various config.*.inc.php files should be altered to point to where the real php files are located.

---

### Post by maxkool on 2009-04-13
I'm having the exact same problem, except I'm using Apache2 instead of lighttpd. So this problem has nothing to do with lighttpd but rather with phpmyadmin.

I've installed (using apt-get):
- apache2, works fine
- mysql, works fine
- php, works fine (tested with a php file in /var/www/ )

PHPMyAdmin just doesn't work. Trying to access [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) Firefox pops up the "Open With" dialog for an unspecified PHTML file (???).

Did: ln -s /usr/share/phpmyadmin/ /var/www/

Same result, except now I can access [http://localhost/phpmyadmin/main.php](http://localhost/phpmyadmin/main.php)  -- which results in the exact warnings mentioned by slamjam earlier:

Warning: include(/etc/phpmyadmin/config.header.inc.php) [function.include]: failed to open stream: No such file or directory in /usr/share/phpmyadmin/config.header.inc.php on line 6 

While the /etc/phpmyadmin/ directory does exist, it's empty.

This is extremely frustrating since I have absolutely no idea what to do about it.

LE: it gets weirder. I've just removed phpmyadmin completely and deleted all the files related to it that I could find and STILL when trying to go to [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) it still says it wants to open a PHTML file. But get this. I can download it. The name of the file is KoiWhp1e.phtml.part. Here are its contents: 
```

<?php
/* vim: set expandtab sw=4 ts=4 sts=4: */
/**
 * forms frameset
 *
 * @version $Id: index.php 11402 2008-07-15 18:42:50Z lem9 $
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
 */

/**
 * Gets core libraries and defines some variables
 */
require_once './libraries/common.inc.php';

/**
 * Includes the ThemeManager if it hasn't been included yet
 */
require_once './libraries/relation.lib.php';

// free the session file, for the other frames to be loaded
session_write_close();

// Gets the host name
// loic1 - 2001/25/11: use the new globals arrays defined with php 4.1+
if (empty($HTTP_HOST)) {
    if (PMA_getenv('HTTP_HOST')) {
        $HTTP_HOST = PMA_getenv('HTTP_HOST');
    } else {
        $HTTP_HOST = '';
    }
}


// purge querywindow history
$cfgRelation = PMA_getRelationsParam();
if ($GLOBALS['cfg']['QueryHistoryDB'] && $cfgRelation['historywork']) {
    PMA_purgeHistory($GLOBALS['cfg']['Server']['user']);
}
unset($cfgRelation);


/**
 * pass variables to child pages
 */
$drops = array('lang', 'server', 'convcharset', 'collation_connection',
    'db', 'table');

foreach ($drops as $each_drop) {
    if (! array_key_exists($each_drop, $_GET)) {
        unset($_GET[$each_drop]);
    }
}
unset($drops, $each_drop);

if (! strlen($GLOBALS['db'])) {
    $main_target = $GLOBALS['cfg']['DefaultTabServer'];
} elseif (! strlen($GLOBALS['table'])) {
    $_GET['db'] = $GLOBALS['db'];
    $main_target = $GLOBALS['cfg']['DefaultTabDatabase'];
} else {
    $_GET['db'] = $GLOBALS['db'];
    $_GET['table'] = $GLOBALS['table'];
    $main_target = $GLOBALS['cfg']['DefaultTabTable'];
}

$url_query = PMA_generate_common_url($_GET);

if (isset($GLOBALS['target']) && is_string($GLOBALS['target']) && !empty($GLOBALS['target']) && in_array($GLOBALS['target'], $goto_whitelist)) {
    $main_target = $GLOBALS['target'];
}

$main_target .= $url_query;

$lang_iso_code = $GLOBALS['available_languages'][$GLOBALS['lang']][2];


// start output
header('Content-Type: text/html; charset=' . $GLOBALS['charset']);
?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Frameset//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-frameset.dtd">
<html xmlns="http://www.w3.org/1999/xhtml"
    xml:lang="<?php echo $lang_iso_code; ?>"
    lang="<?php echo $lang_iso_code; ?>"
    dir="<?php echo $GLOBALS['text_dir']; ?>">
<head>
<link rel="icon" href="./favicon.ico" type="image/x-icon" />
<link rel="shortcut icon" href="./favicon.ico" type="image/x-icon" />
<title>phpMyAdmin <?php echo PMA_VERSION; ?> -
    <?php echo htmlspecialchars($HTTP_HOST); ?></title>
<meta http-equiv="Content-Type"
    content="text/html; charset=<?php echo $GLOBALS['charset']; ?>" />
<script type="text/javascript">
// <![CDATA[
    // definitions used in querywindow.js
    var common_query = '<?php echo PMA_escapeJsString(PMA_generate_common_url('', '', '&'));?>';
    var opendb_url = '<?php echo PMA_escapeJsString($GLOBALS['cfg']['DefaultTabDatabase']); ?>';
    var safari_browser = <?php echo PMA_USR_BROWSER_AGENT == 'SAFARI' ? 'true' : 'false' ?>;
    var querywindow_height = <?php echo PMA_escapeJsString($GLOBALS['cfg']['QueryWindowHeight']); ?>;
    var querywindow_width = <?php echo PMA_escapeJsString($GLOBALS['cfg']['QueryWindowWidth']); ?>;
    var collation_connection = '<?php echo PMA_escapeJsString($GLOBALS['collation_connection']); ?>';
    var lang = '<?php echo PMA_escapeJsString($GLOBALS['lang']); ?>';
    var server = '<?php echo PMA_escapeJsString($GLOBALS['server']); ?>';
    var table = '<?php echo PMA_escapeJsString($GLOBALS['table']); ?>';
    var db    = '<?php echo PMA_escapeJsString($GLOBALS['db']); ?>';
    var token = '<?php echo PMA_escapeJsString($_SESSION[' PMA_token ']); ?>';
    var text_dir = '<?php echo PMA_escapeJsString($GLOBALS['text_dir']); ?>';
    var pma_absolute_uri = '<?php echo PMA_escapeJsString($GLOBALS['cfg']['PmaAbsoluteUri']); ?>';

    // for content and navigation frames

    var frame_content = 0;
    var frame_navigation = 0;
    function getFrames() {
<?php if ($GLOBALS['text_dir'] === 'ltr') { ?>
        frame_content = window.frames[1];
        frame_navigation = window.frames[0];
<?php } else { ?>
        frame_content = window.frames[0];
        frame_navigation = window.frames[1];
<?php } ?>
    }
    var onloadCnt = 0; 
    var onLoadHandler = window.onload;
    window.onload = function() {
        if (onloadCnt == 0) {
            if (typeof(onLoadHandler) == "function") { 
                onLoadHandler(); 
            }
            if (typeof(getFrames) != 'undefined' && typeof(getFrames) == 'function') { 
                getFrames(); 
            }
            onloadCnt++;
        }
    };
// ]]>
</script>
<script src="./js/querywindow.js" type="text/javascript"></script>
</head>
<frameset cols="<?php
if ($GLOBALS['text_dir'] === 'rtl') {
    echo '*,';
}
echo $GLOBALS['cfg']['NaviWidth'];
if ($GLOBALS['text_dir'] === 'ltr') {
    echo ',*';
}
?>" rows="*" id="mainFrameset">
    <?php if ($GLOBALS['text_dir'] === 'ltr') { ?>
    <frame frameborder="0" id="frame_navigation"
        src="navigation.php<?php echo $url_query; ?>"
        name="frame_navigation" />
    <?php } ?>
    <frame frameborder="0" id="frame_content"
        src="<?php echo $main_target; ?>"
        name="frame_content" />
    <?php if ($GLOBALS['text_dir'] === 'rtl') { ?>
    <frame frameborder="0" id="frame_navigation"
        src="navigation.php<?php echo $url_query; ?>"
        name="frame_navigation" />
    <?php } ?>
    <noframes>
        <body>
            <p><?php echo $GLOBALS['strNoFrames']; ?></p>
        </body>
    </noframes>
</frameset>
</html>

```

---

### Post by BkkBonanza on 2009-04-13
You don't have apache/lighttpd configured correctly for handling php files. Any time your browser pops up and asks you what to do with a php file it's because your web server software is not interpreting the php file and instead is trying to send it to the browser. Read the manual on how to setup apache for php files correctly. Or search here, seems this question gets asked 3 times a day nowadays and is answered over and over.

---

### Post by maxkool on 2009-04-13
Thanks for the response. But Apache is interpreting PHP files correctly. Firefox opens any PHP file as it should. Phpinfo(); works properly. What doesn't work is PHPMyAdmin.

---

### Post by BkkBonanza on 2009-04-13
Hmm. Well, can't help you. I've installed phpmyadmin many times and never had any issues like this.

---

### Post by maxkool on 2009-04-16
I finally got it to work. In case anyone else experiences this problem, here's how I did it.

First, I found the following page:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

..i.e. the official docs (which, as a Ubuntu noob, I should have been looking at to begin with, instead of trying to install everything by myself) extremely helpful.

So, I removed the entire LAMP stack (not all of which was installed, but who cares) by doing:

> sudo apt-get remove apache2 apache2-mpm-prefork apache2-utils apache2.2-common libapache2-mod-php5 libapr1 libaprutil1 libdbd-mysql-perl libdbi-perl libmysqlclient15off libnet-daemon-perl libplrpc-perl libpq5 mysql-client-5.0 mysql-common mysql-server mysql-server-5.0 php5-common php5-mysql

Then I installed LAMP again by doing:

> sudo tasksel install lamp-server

Now I had to install PHPMyAdmin. Here's the trick. When I first installed PHPMyAdmin through Aptitude, the text-based installer popped up a blue-background dialog, asking me what server to automatically configure PHPMyAdmin for. I quickly selected Apache2 and pressed Enter. Wrong! As it turns out, you need to press SPACE first to place a check mark for that option, and only then hit Enter. So PHPMyAdmin hadn't configured itself for Apache. 

To add to the problem, whenever I removed and reinstalled PHPMyAdmin, for some reason, the configuration window didn't appear again! It only came up on the first installation.

Solution? I installed PHPMyAdmin through Synaptic. Configuration popped up again (this time in a nice graphical window :)) and I checked Apache2. Bingo, it works.
 
Maybe this saves someone else the trouble I went through! (not to mention the hair :))

---

### Post by MonochromeNight on 2009-05-12
Referring to maxkool's last post: you can also type in your terminal:

> sudo apt-get --purge remove phpmyadmin

This will remove phpmyadmin package as well as its config files. In this way, the next time you try to reinstall phpmyadmin using:

> sudo apt-get install phpmyadmin

the server configuration screen will pop-up and you can select your web server (don't forget to use the Space key to select your item before you press Enter).

---

### Post by F4RR3LL on 2009-05-22
@ maxkool > all i did was cleaned the browser's cache and restarted apache...works fine!

---

### Post by elect on 2012-05-29
> **maxkool said:**
> 
Now I had to install PHPMyAdmin. Here's the trick. When I first installed PHPMyAdmin through Aptitude, the text-based installer popped up a blue-background dialog, asking me what server to automatically configure PHPMyAdmin for. I quickly selected Apache2 and pressed Enter. Wrong! As it turns out, you need to press SPACE first to place a check mark for that option, and only then hit Enter. So PHPMyAdmin hadn't configured itself for Apache. 

[IMG]http://www1.picturepush.com/photo/a/7160094/1024/Poze/mother-of-god-meme-240x180.jpg[/IMG]

I didnt notice it, useful, thanks man

---

