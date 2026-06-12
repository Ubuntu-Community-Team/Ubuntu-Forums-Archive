---
title: "Weird php and/or mysql bug"
date: 2010-08-20
forum: Server Platforms
---

### Post by gsx1022 on 2010-08-20
Hello,

I have probably found a bug in the Ubuntu php5 package. At first I thought it's a problem with Zend Framework, which I use, then I thought it's a php issue, but now it seems to be a problem with Ubuntu's php packages.

My problem is that under certain conditions, php is going to read records from the mysql database table infinite times. For a much more detailed description of the bug, please see: [http://framework.zend.com/issues/browse/ZF-9982](http://framework.zend.com/issues/browse/ZF-9982)

I've tried on an x86 Ubuntu Desktop edition, and an x64 Ubuntu Server edition, both 10.04, and both had this bug.

I have set up a test system (x86 Ubuntu Server edition 10.04), and compiled apache2 and php5 from source, but used the mysql-server package from the repository. And I couldn't reproduce the bug. However, after copying the self-compiled libphp5.so file from the test system to the desktop that produces the error, I could still reproduce the error on the desktop. This suggests me that the problem is either not in php, or - more probably - there are multiple php binaries used in the repository version, and therefore it doesn't matter that I've copied my libphp5.so because mysql functions are somewhere else. I've found a mysql.so file in /usr/lib/php5/20090626+lfs coming from the php5-mysql package. Does that have anything to do with this issue?

Thanks for your help in advance,
gsx1022

---

### Post by cdenley on 2010-08-20
Seems to work fine for me.
```

cdenley@vmware:/var/www$ mysqldump --compact -u root -p gal
Enter password: 
SET @saved_cs_client     = @@character_set_client;
SET character_set_client = utf8;
/*!50001 CREATE TABLE `allresources_view` (
  `name` varchar(30),
  `level` int(10) unsigned,
  `parent` varchar(30)
) ENGINE=MyISAM */;
SET character_set_client = @saved_cs_client;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!40101 SET character_set_client = utf8 */;
CREATE TABLE `resources` (
  `name` varchar(30) NOT NULL,
  `parent` int(10) unsigned NOT NULL,
  `id` int(10) unsigned NOT NULL AUTO_INCREMENT,
  `level` int(10) unsigned NOT NULL,
  PRIMARY KEY (`id`)
) ENGINE=MyISAM AUTO_INCREMENT=11 DEFAULT CHARSET=latin1;
/*!40101 SET character_set_client = @saved_cs_client */;
INSERT INTO `resources` VALUES ('root',0,1,0),('index_index',1,2,1),('error_error',10,3,2),('error',1,10,1),('error_denied',10,9,2);
/*!50001 DROP TABLE IF EXISTS `allresources_view`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = latin1 */;
/*!50001 SET character_set_results     = latin1 */;
/*!50001 SET collation_connection      = latin1_swedish_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`root`@`localhost` SQL SECURITY DEFINER */
/*!50001 VIEW `allresources_view` AS select `resources`.`name` AS `name`,`resources`.`level` AS `level`,(select `in`.`name` AS `pname` from `resources` `in` where (`in`.`id` = `resources`.`parent`)) AS `parent` from `resources` */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;
cdenley@vmware:/var/www$ cat bug.php
<?php
header('Content-type: text/plain');
$link = mysql_connect('localhost', 'test', 'fg95FS4jfF4')
    or die('Could not connect: ' . mysql_error());
mysql_select_db('gal') or die('Query failed: ' . mysql_error());
$raw = mysql_query('SELECT `name`, `level`, `parent` FROM `allresources_view` ORDER BY `level` ASC');
while ($r = mysql_fetch_assoc($raw)) {
	var_dump($r);
}
?>
cdenley@vmware:/var/www$ echo -e "GET /bug.php HTTP/1.0\n"|nc -q 1 127.0.0.1 80
HTTP/1.1 200 OK
Date: Fri, 20 Aug 2010 14:09:53 GMT
Server: Apache
X-Powered-By: PHP/5.3.2-1ubuntu4.2
Vary: Accept-Encoding
Content-Length: 561
Connection: close
Content-Type: text/plain

array(3) {
  ["name"]=>
  string(4) "root"
  ["level"]=>
  string(1) "0"
  ["parent"]=>
  NULL
}
array(3) {
  ["name"]=>
  string(11) "index_index"
  ["level"]=>
  string(1) "1"
  ["parent"]=>
  string(4) "root"
}
array(3) {
  ["name"]=>
  string(5) "error"
  ["level"]=>
  string(1) "1"
  ["parent"]=>
  string(4) "root"
}
array(3) {
  ["name"]=>
  string(12) "error_denied"
  ["level"]=>
  string(1) "2"
  ["parent"]=>
  string(5) "error"
}
array(3) {
  ["name"]=>
  string(11) "error_error"
  ["level"]=>
  string(1) "2"
  ["parent"]=>
  string(5) "error"
}
cdenley@vmware:/var/www$ php bug.php
array(3) {
  ["name"]=>
  string(4) "root"
  ["level"]=>
  string(1) "0"
  ["parent"]=>
  NULL
}
array(3) {
  ["name"]=>
  string(11) "index_index"
  ["level"]=>
  string(1) "1"
  ["parent"]=>
  string(4) "root"
}
array(3) {
  ["name"]=>
  string(5) "error"
  ["level"]=>
  string(1) "1"
  ["parent"]=>
  string(4) "root"
}
array(3) {
  ["name"]=>
  string(12) "error_denied"
  ["level"]=>
  string(1) "2"
  ["parent"]=>
  string(5) "error"
}
array(3) {
  ["name"]=>
  string(11) "error_error"
  ["level"]=>
  string(1) "2"
  ["parent"]=>
  string(5) "error"
}
cdenley@vmware:/var/www$

```

---

### Post by gsx1022 on 2010-08-20
Hi,

Strange. I have removed the php packages from the desktop for testing purposes, but I can still reproduce the bug on the server (x64). What version of (L)AMP are you using?
My versions:
ii  apache2                         2.2.14-5ubuntu8                                 
ii  apache2-mpm-prefork             2.2.14-5ubuntu8                                 
ii  apache2-utils                   2.2.14-5ubuntu8                                 
ii  apache2.2-bin                   2.2.14-5ubuntu8                                 
ii  apache2.2-common                2.2.14-5ubuntu8                                 
ii  libapache2-mod-php5             5.3.2-1ubuntu4.2                                                   
ii  php5                            5.3.2-1ubuntu4.2                                
ii  php5-common                     5.3.2-1ubuntu4.2                                
ii  php5-mysql                      5.3.2-1ubuntu4.2                               
ii  libmysqlclient-dev              5.1.41-3ubuntu12.3                              
ii  libmysqlclient16                5.1.41-3ubuntu12.3                              
ii  mysql-client-5.1                5.1.41-3ubuntu12.3                              
ii  mysql-client-core-5.1           5.1.41-3ubuntu12.3                              
ii  mysql-common                    5.1.41-3ubuntu12.3                              
ii  mysql-server                    5.1.41-3ubuntu12.3                              
ii  mysql-server-5.1                5.1.41-3ubuntu12.3                              
ii  mysql-server-core-5.1           5.1.41-3ubuntu12.3

gsx1022

---

### Post by cdenley on 2010-08-20
```

cdenley@vmware:~$ apt-cache policy php5 php5-mysql apache2 apache2-mpm-prefork mysql-server-5.1
php5:
  Installed: (none)
  Candidate: 5.3.2-1ubuntu4.2
  Version table:
     5.3.2-1ubuntu4.2 0
        500 http://mirror.anl.gov/pub/ubuntu/ lucid-updates/main Packages
     5.3.2-1ubuntu4 0
        500 http://mirror.anl.gov/pub/ubuntu/ lucid/main Packages
php5-mysql:
  Installed: 5.3.2-1ubuntu4.2
  Candidate: 5.3.2-1ubuntu4.2
  Version table:
 *** 5.3.2-1ubuntu4.2 0
        500 http://mirror.anl.gov/pub/ubuntu/ lucid-updates/main Packages
        100 /var/lib/dpkg/status
     5.3.2-1ubuntu4 0
        500 http://mirror.anl.gov/pub/ubuntu/ lucid/main Packages
apache2:
  Installed: 2.2.14-5ubuntu8
  Candidate: 2.2.14-5ubuntu8
  Version table:
 *** 2.2.14-5ubuntu8 0
        500 http://mirror.anl.gov/pub/ubuntu/ lucid/main Packages
        100 /var/lib/dpkg/status
apache2-mpm-prefork:
  Installed: 2.2.14-5ubuntu8
  Candidate: 2.2.14-5ubuntu8
  Version table:
 *** 2.2.14-5ubuntu8 0
        500 http://mirror.anl.gov/pub/ubuntu/ lucid/main Packages
        100 /var/lib/dpkg/status
mysql-server-5.1:
  Installed: 5.1.41-3ubuntu12.6
  Candidate: 5.1.41-3ubuntu12.6
  Version table:
 *** 5.1.41-3ubuntu12.6 0
        500 http://mirror.anl.gov/pub/ubuntu/ lucid-updates/main Packages
        100 /var/lib/dpkg/status
     5.1.41-3ubuntu12.3 0
        500 http://security.ubuntu.com/ubuntu/ lucid-security/main Packages
     5.1.41-3ubuntu12 0
        500 http://mirror.anl.gov/pub/ubuntu/ lucid/main Packages

```

Perhaps try using mysql-server-5.1 version 5.1.41-3ubuntu12.6 from lucid-updates.

---

### Post by gsx1022 on 2010-08-20
Hi,

I've upgraded, as you suggested, but nothing changed. Any other ideas?

gsx1022

---

### Post by cdenley on 2010-08-20
Post the FULL php script which you're having a problem with, except remove the password. Or just try mine I posted. Then maybe post the output for:
```

mysqldump gal -u root -p --compact

```

---

### Post by gsx1022 on 2010-08-20
Hi,

Here's the script. It's in a Zend Framework context, but that shouldn't matter to much.

[PHP]
<?php
    class CustomControllerAction extends Zend_Controller_Action
    {
        protected $db;
        protected $acl;
        
        public function init()
        {
            //alias db
        	$this->db = Zend_Registry::get('db');
        	
        	//generally useful stuff in templates
            $this->view->title = Zend_Registry::get('config')->getPageTitle();
            $this->view->pub_base = Zend_Registry::get('config')->getBasePublicPath();
            $this->view->logged_in_as = aget(Zend_Auth::getInstance()->getIdentity(), 'user');
            
            //acl
            $this->acl = new Zend_Acl();
            
            foreach ($this->db->query('SELECT `groups`.`id`, `groups`.`parent`, `groups`.`level` FROM `groups` ORDER BY `level` ASC')->fetchAll() as $g) {
            	$this->acl->addRole(new Zend_Acl_Role($g['id']), (($g['level'] > 0)?$g['parent']:null));
            }
            
            /*foreach ($this->db->query('SELECT `name`, `level`, `parent` FROM `allresources_view` ORDER BY `level` ASC')->fetchAll() as $r) {
            	var_dump($r);
            	echo '<br /><br />';
            	$this->acl->add(new Zend_Acl_Resource($r['name']), (($r['level'] > 0)?$r['parent']:null));
            }*/

            // TODO replace with Zend_Db as soon as Zend_Db bug is fixed
            
            $a = Zend_Registry::get('application');
            $c = mysqli_connect(aget($a->getOption('database'), 'hostname'), aget($a->getOption('database'), 'username'), aget($a->getOption('database'), 'password'), aget($a->getOption('database'), 'database'));
            $raw = mysqli_query($c, 'SELECT `name`, `level`, `parent` FROM `allresources_view` ORDER BY `level` ASC');
            
            
            while ($r = mysqli_fetch_assoc($raw)) {
            	var_dump($r);
            	echo '<br /><br />';
            	$this->acl->add(new Zend_Acl_Resource($r['name']), (($r['level'] > 0)?$r['parent']:null));
            }
            mysqli_close($c);
            
            
            foreach ($this->db->query('SELECT * FROM `allrules_view`')->fetchAll() as $r) {
            	$this->acl->allow($r['gid'], $r['resource'], array(($r['view'] == 1)?'view':null,($r['add'] == 1)?'add':null,($r['edit'] == 1)?'edit':null,($r['remove'] == 1)?'remove':null));
            }
            
        }
    }
?>

[/PHP]

And the output of mysqldump (I've omitted non-relevant INSERTs):
```

SET @saved_cs_client     = @@character_set_client;
SET character_set_client = utf8;
/*!50001 CREATE TABLE `allresources_view` (
  `name` varchar(30),
  `level` int(10) unsigned,
  `parent` varchar(30)
) ENGINE=MyISAM */;
SET character_set_client = @saved_cs_client;
SET @saved_cs_client     = @@character_set_client;
SET character_set_client = utf8;
/*!50001 CREATE TABLE `allrules_view` (
  `view` bit(1),
  `add` bit(1),
  `edit` bit(1),
  `remove` bit(1),
  `resource` varchar(30),
  `role` varchar(30),
  `gid` bigint(20) unsigned
) ENGINE=MyISAM */;
SET character_set_client = @saved_cs_client;
SET @saved_cs_client     = @@character_set_client;
SET character_set_client = utf8;
/*!50001 CREATE TABLE `allusers_view` (
  `user` varchar(12),
  `pass` varchar(64),
  `id` bigint(20) unsigned,
  `gid` int(10) unsigned,
  `group` varchar(30)
) ENGINE=MyISAM */;
SET character_set_client = @saved_cs_client;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!40101 SET character_set_client = utf8 */;
CREATE TABLE `config` (
  `key` varchar(20) CHARACTER SET latin1 NOT NULL,
  `value` varchar(120) CHARACTER SET latin1 NOT NULL,
  PRIMARY KEY (`key`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8 COLLATE=utf8_hungarian_ci;
/*!40101 SET character_set_client = @saved_cs_client */;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!40101 SET character_set_client = utf8 */;
CREATE TABLE `groups` (
  `id` int(10) unsigned NOT NULL AUTO_INCREMENT,
  `name` varchar(30) CHARACTER SET latin1 NOT NULL,
  `level` int(10) unsigned NOT NULL,
  `parent` int(10) unsigned NOT NULL,
  PRIMARY KEY (`id`)
) ENGINE=MyISAM AUTO_INCREMENT=4 DEFAULT CHARSET=utf8 COLLATE=utf8_hungarian_ci;
/*!40101 SET character_set_client = @saved_cs_client */;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!40101 SET character_set_client = utf8 */;
CREATE TABLE `resources` (
  `name` varchar(30) CHARACTER SET latin1 NOT NULL,
  `parent` int(10) unsigned NOT NULL,
  `id` int(10) unsigned NOT NULL AUTO_INCREMENT,
  `level` int(10) unsigned NOT NULL,
  PRIMARY KEY (`id`)
) ENGINE=MyISAM AUTO_INCREMENT=11 DEFAULT CHARSET=utf8 COLLATE=utf8_hungarian_ci;
/*!40101 SET character_set_client = @saved_cs_client */;
INSERT INTO `resources` VALUES ('root',0,1,0),('index_index',1,2,1),('error_error',10,3,2),('error',1,10,1),('error_denied',10,9,2);
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!40101 SET character_set_client = utf8 */;
CREATE TABLE `rules` (
  `resource` int(10) unsigned NOT NULL,
  `role` bigint(20) unsigned NOT NULL,
  `view` bit(1) NOT NULL DEFAULT b'0',
  `add` bit(1) NOT NULL DEFAULT b'0',
  `edit` bit(1) NOT NULL DEFAULT b'0',
  `remove` bit(1) NOT NULL DEFAULT b'0'
) ENGINE=MyISAM DEFAULT CHARSET=utf8 COLLATE=utf8_hungarian_ci;
/*!40101 SET character_set_client = @saved_cs_client */;
INSERT INTO `rules` VALUES (2,1,'\0','\0','\0','\0');
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!40101 SET character_set_client = utf8 */;
CREATE TABLE `users` (
  `user` varchar(12) CHARACTER SET latin1 NOT NULL,
  `pass` varchar(64) CHARACTER SET latin1 NOT NULL,
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  `gid` int(10) unsigned NOT NULL,
  PRIMARY KEY (`id`)
) ENGINE=MyISAM AUTO_INCREMENT=2 DEFAULT CHARSET=utf8 COLLATE=utf8_hungarian_ci;
/*!40101 SET character_set_client = @saved_cs_client */;
/*!50001 DROP TABLE IF EXISTS `allresources_view`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = utf8 */;
/*!50001 SET character_set_results     = utf8 */;
/*!50001 SET collation_connection      = utf8_general_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`root`@`localhost` SQL SECURITY DEFINER */
/*!50001 VIEW `allresources_view` AS select `resources`.`name` AS `name`,`resources`.`level` AS `level`,(select `in`.`name` AS `pname` from `resources` `in` where (`in`.`id` = `resources`.`parent`)) AS `parent` from `resources` */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;
/*!50001 DROP TABLE IF EXISTS `allrules_view`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = utf8 */;
/*!50001 SET character_set_results     = utf8 */;
/*!50001 SET collation_connection      = utf8_general_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`root`@`localhost` SQL SECURITY DEFINER */
/*!50001 VIEW `allrules_view` AS select `rules`.`view` AS `view`,`rules`.`add` AS `add`,`rules`.`edit` AS `edit`,`rules`.`remove` AS `remove`,`resources`.`name` AS `resource`,`groups`.`name` AS `role`,`rules`.`role` AS `gid` from ((`rules` join `resources` on((`rules`.`resource` = `resources`.`id`))) join `groups` on((`rules`.`role` = `groups`.`id`))) */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;
/*!50001 DROP TABLE IF EXISTS `allusers_view`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = utf8 */;
/*!50001 SET character_set_results     = utf8 */;
/*!50001 SET collation_connection      = utf8_general_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`root`@`localhost` SQL SECURITY DEFINER */
/*!50001 VIEW `allusers_view` AS select `users`.`user` AS `user`,`users`.`pass` AS `pass`,`users`.`id` AS `id`,`users`.`gid` AS `gid`,`groups`.`name` AS `group` from (`users` join `groups` on((`users`.`gid` = `groups`.`id`))) */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;

```

gsx1022

---

### Post by cdenley on 2010-08-20
Try a simpler use case, such as the one I posted. For all I know, your problem with that script is that the class is instantiated an infinite number of times.

---

### Post by gsx1022 on 2010-08-21
Hi,

First, thank you. Second, I don't know how could I be so dumb. I've been having this issue for months, and it didn't occur to me that I should test it in a non-zf context. Shame on me. For some reason I have not yet determined, the CustomControllerAction init() function is being called infinite times, as you have said.

Thanks again,
gsx1022

---

