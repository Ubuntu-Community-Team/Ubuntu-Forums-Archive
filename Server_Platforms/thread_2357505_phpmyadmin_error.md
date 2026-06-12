---
title: "phpmyadmin error"
date: 2017-04-03
forum: Server Platforms
---

### Post by recharde on 2017-04-03
```
addJSON(         'list',         PMA_RecentFavoriteTable::getInstance('recent')->getHtmlList()     );     exit; }  if ($GLOBALS['PMA_Config']->isGitRevision()) {     if (isset($_REQUEST['git_revision']) && $GLOBALS['is_ajax_request'] == true) {         PMA_printGitRevision();         exit;     }     echo ''; }  // Handles some variables that may have been sent by the calling script $GLOBALS['db'] = ''; $GLOBALS['table'] = ''; $show_query = '1';  // Any message to display? if (! empty($message)) {     echo PMA_Util::getMessage($message);     unset($message); }  $common_url_query =  PMA_URL_getCommon(); $mysql_cur_user_and_host = '';  // when $server > 0, a server has been chosen so we can display // all MySQL-related information if ($server > 0) {     include 'libraries/server_common.inc.php';     include 'libraries/StorageEngine.class.php';      // Use the verbose name of the server instead of the hostname     // if a value is set     $server_info = '';     if (! empty($cfg['Server']['verbose'])) {         $server_info .= htmlspecialchars($cfg['Server']['verbose']);         if ($GLOBALS['cfg']['ShowServerInfo']) {             $server_info .= ' (';         }     }     if ($GLOBALS['cfg']['ShowServerInfo'] || empty($cfg['Server']['verbose'])) {         $server_info .= $GLOBALS['dbi']->getHostInfo();     }     if (! empty($cfg['Server']['verbose']) && $GLOBALS['cfg']['ShowServerInfo']) {         $server_info .= ')';     }     $mysql_cur_user_and_host = $GLOBALS['dbi']->fetchValue('SELECT USER();');      // should we add the port info here?     $short_server_info = (!empty($GLOBALS['cfg']['Server']['verbose'])                 ? $GLOBALS['cfg']['Server']['verbose']                 : $GLOBALS['cfg']['Server']['host']); }  echo '' . "\n"; // Anchor for favorite tables synchronization. echo PMA_RecentFavoriteTable::getInstance('favorite')->getHtmlSyncFavoriteTables(); echo ''; if ($server > 0 || count($cfg['Servers']) > 1 ) {     if ($cfg['DBG']['demo']) {         echo '';         echo '' . __('phpMyAdmin Demo Server') . '

';         echo '';         printf(             __(                 'You are using the demo server. You can do anything here, but '                 . 'please do not change root, debian-sys-maint and pma users. '                 . 'More information is available at %s.'             ),             '[demo.phpmyadmin.net]("http://demo.phpmyadmin.net/")'         );         echo '
';         echo '
';     }     echo '';     echo '' . __('General settings') . '

';     echo '
[LIST]
[*]';      /**      * Displays the MySQL servers choice form      */     if ($cfg['ServerDefault'] == 0         || (! $cfg['NavigationDisplayServers']         && (count($cfg['Servers']) > 1         || ($server == 0 && count($cfg['Servers']) == 1)))     ) {         echo ' 
[*]';         include_once 'libraries/select_server.lib.php';         echo PMA_Util::getImage('s_host.png') . " " . PMA_selectServer(true, true);         echo '';     }      /**      * Displays the mysql server related links      */     if ($server > 0 && ! PMA_DRIZZLE) {         include_once 'libraries/check_user_privileges.lib.php';          // Logout for advanced authentication         if ($cfg['Server']['auth_type'] != 'config') {             if ($cfg['ShowChgPassword']) {                 $conditional_class = 'ajax';                 PMA_printListItem(                     PMA_Util::getImage('s_passwd.png') . " " . __('Change password'),                     'li_change_password',                     'user_password.php' . $common_url_query,                     null,                     null,                     'change_password_anchor',                     "no_bullets",                     $conditional_class                 );             }         } // end if         echo ' 
[*]';         echo '        ' . "\n"            . PMA_URL_getHiddenInputs(null, null, 4, 'collation_connection')            . '            ' . "\n"            . '                ' . PMA_Util::getImage('s_asci.png') . " "                                . __('Server connection collation') . "\n"            // put the doc link in the form so that it appears on the same line            . PMA_Util::showMySQLDocu('Charset-connection')            . ': ' .  "\n"            . '            ' . "\n"             . PMA_generateCharsetDropdownBox(                PMA_CSDROPDOWN_COLLATION,                'collation_connection',                'select_collation_connection',                $collation_connection,                true,                true            )            . '        ' . "\n"            . '' . "\n";     } // end of if ($server > 0 && !PMA_DRIZZLE)     echo ' 
[/LIST]
';     echo '
'; }  echo ''; echo '' . __('Appearance settings') . '

'; echo '  
[LIST]
[*]';  // Displays language selection combo if (empty($cfg['Lang']) && count($GLOBALS['available_languages']) > 1) {     echo ' 
[*]';     include_once 'libraries/display_select_lang.lib.php';     echo PMA_Util::getImage('s_lang.png') . " " . PMA_getLanguageSelectorHtml();     echo ''; }  // ThemeManager if available  if ($GLOBALS['cfg']['ThemeManager']) {     echo ' 
[*]';     echo PMA_Util::getImage('s_theme.png') . " "             .  $_SESSION['PMA_Theme_Manager']->getHtmlSelectBox();     echo ''; } echo ' 
[*]'; echo PMA_Config::getFontsizeForm(); echo '';  echo ' 
[/LIST]
';  // User preferences  if ($server > 0) {     echo '
[LIST]
[*]';     PMA_printListItem(         PMA_Util::getImage('b_tblops.png') . " " . __('More settings'),         'li_user_preferences',         'prefs_manage.php' . $common_url_query,         null,         null,         null,         "no_bullets"     );     echo ' 
[/LIST]
'; }  echo '
';   echo '
'; echo '';   if ($server > 0 && $GLOBALS['cfg']['ShowServerInfo']) {      echo '';     echo '' . __('Database server') . '

';     echo '
[LIST]
[*]' . "\n";     PMA_printListItem(         __('Server:') . ' ' . $server_info,         'li_server_info'     );     PMA_printListItem(         __('Server type:') . ' ' . PMA_Util::getServerType(),         'li_server_type'     );     PMA_printListItem(         __('Server version:')         . ' '         . PMA_MYSQL_STR_VERSION . ' - ' . PMA_MYSQL_VERSION_COMMENT,         'li_server_version'     );     PMA_printListItem(         __('Protocol version:') . ' ' . $GLOBALS['dbi']->getProtoInfo(),         'li_mysql_proto'     );     PMA_printListItem(         __('User:') . ' ' . htmlspecialchars($mysql_cur_user_and_host),         'li_user_info'     );      echo ' 
[*]';     echo '        ' . __('Server charset:') . ' '        . '        ';     if (! PMA_DRIZZLE) {         echo '           '             . $mysql_charsets_descriptions[$mysql_charset_map['utf-8']];     }     echo '           (' . $mysql_charset_map['utf-8'] . ')'        . '        '        . ''        . ' 
[/LIST]
'        . ' 
'; }  if ($GLOBALS['cfg']['ShowServerInfo'] || $GLOBALS['cfg']['ShowPhpInfo']) {     echo '';     echo '' . __('Web server') . '
```

---

### Post by wildmanne39 on 2017-04-03
*Thread moved to **Server Platforms**.*

---

### Post by recharde on 2017-04-03
I don't know what wrong  i am doing, i just install phpmyadmin and check in browser.

---

### Post by darkod on 2017-04-03
Are you checking from the same server, or from another machine? Because linux servers usually don't have a GUI to have a browser.

On the server, can you post the output of:
```
sudo netstat -plunt
```

That will show us if apache and mysql are running or not.

---

### Post by izznogooood on 2017-04-03
Does your browser have Java script enabled?

---

