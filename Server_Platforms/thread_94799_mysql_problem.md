---
title: "mysql problem"
date: 2005-11-24
forum: Server Platforms
---

### Post by diebels on 2005-11-24
I'm trying to run```
mysql database < database_dump -p
```on my ubuntu machine, and getting```
ERROR 1064 at line 20: You have an error in your SQL syntax.  Check the manual that corresponds to your MySQL server version for the right syntax to use near 'collate latin1_danish_ci NOT NULL default '',
  PRIMARY KEY  (`
```
Some of the database_dump:```
-- MySQL dump 10.8
--
-- Host: xxxx    Database: database
-- ------------------------------------------------------
-- Server version       4.1.14-standard-log

/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8 */;
/*!40014 SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 */;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE="NO_AUTO_VALUE_ON_ZERO" */;

--
-- Table structure for table `hesk_categories`
--

DROP TABLE IF EXISTS `hesk_categories`;
CREATE TABLE `hesk_categories` (
  `id` smallint(5) unsigned NOT NULL auto_increment,
  `name` varchar(20) collate latin1_danish_ci NOT NULL default '',
  PRIMARY KEY  (`id`)
) ENGINE=MyISAM DEFAULT CHARSET=latin1 COLLATE=latin1_danish_ci;

--
-- Dumping data for table `hesk_categories`
--

```As you can see the database_dump is from a mysql 4.1.14 server, while on my ubuntu server mysql is 4.0.23 .

Can this version difference create syntax errors?

If so, how can I convert the database dump to mysql 4.0.23 syntax?

---

### Post by hoodwink on 2005-11-24
[QUOTE=diebels]I
DROP TABLE IF EXISTS `hesk_categories`;
CREATE TABLE `hesk_categories` (
  `id` smallint(5) unsigned NOT NULL auto_increment,
  `name` varchar(20) collate latin1_danish_ci NOT NULL default '',
  PRIMARY KEY  (`id`)
)


[/QUOTE]

I don't know whether this is your problem or not, but I've noticed that even on the same MySQL release (same system), MySQL dumps in a format that produces errors upon restore. I've never taken the time to check it out, just corrected the problem and moved on.

On my system (and others at different levels) MySQL does not like the specifics following the CREATE TABLE `hesk_categories` ( ... ) definition, ie the line 

) ENGINE=MyISAM DEFAULT CHARSET=latin1 COLLATE=latin1_danish_ci;

On my own system I have to change it to

);

and let the defaults for engine, charset, and collate apply.

HTH,

---

### Post by diebels on 2005-11-24
[QUOTE=hoodwink]I don't know whether this is your problem or not, but I've noticed that even on the same MySQL release (same system), MySQL dumps in a format that produces errors upon restore. I've never taken the time to check it out, just corrected the problem and moved on.

On my system (and others at different levels) MySQL does not like the specifics following the CREATE TABLE `hesk_categories` ( ... ) definition, ie the line 

) ENGINE=MyISAM DEFAULT CHARSET=latin1 COLLATE=latin1_danish_ci;

On my own system I have to change it to

);

and let the defaults for engine, charset, and collate apply.

HTH,[/QUOTE]Thanks. I also had to remove "collate latin1_danish_ci" inside the hesk_categories for mysql to accept it.

2578 lines... Time to make up a sed -i 's/ something command.

---

