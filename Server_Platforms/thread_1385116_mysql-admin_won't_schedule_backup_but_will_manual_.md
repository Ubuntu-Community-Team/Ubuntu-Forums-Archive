---
title: "mysql-admin won't schedule backup but will manual backup"
date: 2010-01-19
forum: Server Platforms
---

### Post by sevenearths on 2010-01-19
I have a scheduled backup to run on our server at work and since the 7/12/09 it has be making 592k files instead of 10Mb files, and I have no idea why!?!

In mysql-admin (the GUI tool) I have a stored connection for the user 'backup', the user has select and lock rights on the databases being backed up. I have a backup profile  called 'backup_regular' and in the third tab along its scheduled to backup at 2 in the morning every week day.

If I look at one of the small backup files generated I see the following:

```
-- MySQL Administrator dump 1.4
--
-- ------------------------------------------------------
-- Server version	`


/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8 */;

/*!40014 SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 */;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;
```

If I run the backup profile manually I get the following:

```
-- MySQL Administrator dump 1.4
--
-- ------------------------------------------------------
-- Server version	5.0.75-0ubuntu10.2


/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8 */;

/*!40014 SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 */;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;


--
-- Create schema wordpress
--

CREATE DATABASE IF NOT EXISTS wordpress;
USE wordpress;

--
-- Definition of table `wordpress`.`wp_comments`
--

DROP TABLE IF EXISTS `wordpress`.`wp_comments`;
CREATE TABLE  `wordpress`.`wp_comments` (
  `comment_ID` bigint(20) unsigned NOT NULL auto_increment,
  `comment_post_ID` int(11) NOT NULL default '0',
  `comment_author` tinytext NOT NULL,
...
...

```

As you can see the only difference between the files in the headers is the fact that the failed backup one does not list the server version:

```
-- Server version	`
```

apposed to:

```
-- Server version	5.0.75-0ubuntu10.2
```

In the manual version

It seems that MySQL can open and write to the file fine, it just can't dump :confused:

Does anyone have any ideas why this would happen or how I could find out whats going on?

---

### Post by sevenearths on 2010-01-20
anyone?

---

### Post by sevenearths on 2010-01-21
I have tried changing the stored connection to:

127.0.0.1 - The IP under server information in mysql-admin
127.0.1.1 - The IP under client information in mysql-admin
192.168.2.5 - The IP of the machine on the network

all to no avail :(

---

### Post by sevenearths on 2010-01-21
\\:D/

[PROBLEM SOLVED!!!]("http://forums.mysql.com/read.php?28,154488,228775#msg-228775")

[I]Hi,

I solved this problem by activating the 'store connection password' option located in Tools - Preferences - General Options.

Don't forget to re-enter the connection password in Tools - Manage Connections.

Regards.

Gwen[/I]

---

