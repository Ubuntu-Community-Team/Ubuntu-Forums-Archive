---
title: "phpmyadmin error"
date: 2015-05-09
forum: Server Platforms
---

### Post by adrin6 on 2015-05-09
[IMG]http://1.bp.blogspot.com/-cMns4g-fhh8/Tb5b4fiiD8I/AAAAAAAABQI/yGnDYVHXlJI/s1600/phpmyadmin+error.png[/IMG]

Hello i'm Adrian and it's a pleasure be in this great community :)

the problem is that phpmyadmin works well but if i add this code(down) phpmyadmin print this error, i don't know what do. :/

/usr/shared/phpmyadmin/index.php

[PHP]<?php
session_start();
if (!isset($_SESSION['user'])) {
   header("Location: /index.php");
   exit();
}
else
{
and the normal code of the index.php of phpmyadmin...

/* vim: set expandtab sw=4 ts=4 sts=4: */
/**
 *
 * @package PhpMyAdmin
 */

/**
 * Gets some core libraries and displays a top message if required
 */
require_once 'libraries/common.inc.php';

/**
 * display Git revision if requested
 */
require_once 'libraries/display_git_revision.lib.php';

/**
 * pass variables to child pages
 */

$drops = array(
    'lang',
    'server',
    'collation_connection',
    'db',
    'table'
);
 [/PHP]


My idea is that if the client is not login this cannot enter to the page. I do not know if I express myself well. :-? ](*,).

---

### Post by nerdtron on 2015-05-11
What does the /var/log/apache2/error.log (or wherever you configured the logs) shows when you encounter this error on the browser?

---

### Post by adrin6 on 2015-05-11
Apache does not throw any errors. :(:-(

---

