---
title: "Mysqldump issue"
date: 2012-04-17
forum: Server Platforms
---

### Post by netizen99 on 2012-04-17
Dear all, 

I'm not sure it's ok to ask question about mysqldump here. I have installed a Ubuntu 11.10 server with MySQL 5.1.61 installed.

I try to backup a database with command 

mysqldump -u root -p openfire > openfire.dump

I get the below message:

Warning: mysqldump: ignoring option '--databases' due to invalid value 'openfire'

What's wrong with my command?

---

### Post by Dangertux on 2012-04-17
Nothing. That error is telling you the database doesn't exist, do you have the right database name?

btw...why couldn't you ask questions about the mysqldump tool?

---

### Post by sj1410 on 2012-04-18
> **netizen99 said:**
> 
mysqldump -u root -p openfire > openfire.dump

I get the below message:

Warning: mysqldump: ignoring option '--databases' due to invalid value 'openfire'




It should be

```


mysqldump -u root -p --databases openfire > openfire.dump


```

you can also dump multiple database using the same command.


```

Usage: mysqldump [OPTIONS] database [tables]
OR     mysqldump [OPTIONS] --databases [OPTIONS] DB1 [DB2 DB3...]
OR     mysqldump [OPTIONS] --all-databases [OPTIONS]

```

---

### Post by netizen99 on 2012-04-18
> **sj1410 said:**
> It should be

```


mysqldump -u root -p --databases openfire > openfire.dump


```you can also dump multiple database using the same command.


```

Usage: mysqldump [OPTIONS] database [tables]
OR     mysqldump [OPTIONS] --databases [OPTIONS] DB1 [DB2 DB3...]
OR     mysqldump [OPTIONS] --all-databases [OPTIONS]

```

It strange, the database openfire is exist, as I can select the database in mysql client with

use openfire;

I get the same message when issue 
mysqldump -u root -p --databases openfire > openfire.dump. 

with the warning,  It look like that I can still get the dump.

Any idea?

---

### Post by sj1410 on 2012-04-18
you can open the dump file in a text editor or just cat it and see if the sql statements exists. if you database does not exist than you should get a error something like this

```

mysqldump: Got error: 1049: Unknown database 'openfire' when selecting the database

```

---

### Post by netizen99 on 2012-04-18
I don't find the message, below is output form terminal.

xxxsa@ubuntuxxx:~$ mysqldump -u root -p --databases openfire > openfire.dump
Warning: mysqldump: ignoring option '--databases' due to invalid value 'openfire'
Enter password:
xxxsa@ubuntuxxx:~$ vi openfire.dump
-- MySQL dump 10.13  Distrib 5.1.61, for debian-linux-gnu (x86_64)
--
-- Host: localhost    Database: openfire
-- ------------------------------------------------------
-- Server version       5.1.61-0ubuntu0.11.10.1

/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8 */;
/*!40103 SET @OLD_TIME_ZONE=@@TIME_ZONE */;
/*!40103 SET TIME_ZONE='+00:00' */;
/*!40014 SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 */;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;
/*!40111 SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0 */;

--
-- Current Database: `openfire`
--


CREATE DATABASE /*!32312 IF NOT EXISTS*/ `openfire` /*!40100 DEFAULT CHARACTER SET utf8 */;

USE `openfire`;

--
-- Table structure for table `ofExtComponentConf`
--

DROP TABLE IF EXISTS `ofExtComponentConf`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!40101 SET character_set_client = utf8 */;
CREATE TABLE `ofExtComponentConf` (
  `subdomain` varchar(255) NOT NULL,
  `wildcard` tinyint(4) NOT NULL,
  `secret` varchar(255) DEFAULT NULL,
  `permission` varchar(10) NOT NULL,
  PRIMARY KEY (`subdomain`)

---

### Post by sj1410 on 2012-04-18
yup, the database exist and the dump was successful. ignore the error.

---

### Post by SeijiSensei on 2012-04-18
> xxxsa@ubuntuxxx:~$ mysqldump -u root -p --databases openfire > openfire.dump
Warning: mysqldump: ignoring option '--databases' due to invalid value 'openfire'

Just exclude the --databases option; it's only relevant if you're backing up multiple databases.

---

