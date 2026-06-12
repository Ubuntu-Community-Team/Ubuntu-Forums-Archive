---
title: "MySQL 5.5 on Ubuntu 10.10"
date: 2011-01-03
forum: Server Platforms
---

### Post by madeby.hm on 2011-01-03
Hi all,

I would love to run MySQL 5.5.X on Ubuntu 10.10 server. Do you know if this will be part of the default "sudo apt-get install mysql-server" command? Possible when?

I read this guide on how to do it manually:
[http://www.geeksww.com/tutorials/database_management_systems/mysql/installation/download_configure_compile_and_install_mysql_558_on_linux.php](http://www.geeksww.com/tutorials/database_management_systems/mysql/installation/download_configure_compile_and_install_mysql_558_on_linux.php)

Is that valid and will it be a good way to install it on Ubuntu? What about future updates?

Thanks!

---

### Post by R.Bucky on 2011-01-03
As 5.5 is a recent release, I suspect that it may be a little bit before it is available in the repos. Hopefully, you aren't going production with it? The real gains from 5.5 are for multi-core systems (over 4 cores) and in Windows environments.

---

### Post by madeby.hm on 2011-01-03
Well, I'm setting up a new environment with new websites and I wanted create a database server that I can scale in the cloud.

I figured that the latest version of MySQL would be the way to go.

Also, all the performance enhancements I can get is a plus.

---

### Post by rainefan on 2011-01-06
No PPA for MySQL 5.5 yet ??

---

### Post by rededit on 2011-01-25
I personally would love to see a mysql 5.5 package sooner then later. I am running a production server with Ubuntu 10.04. I recently discovered this problem with the new crm software we will be using. Currently we have been adding our inventory and customers into the database which came to a sudden halt when I discovered that I was unable to add any new items. Upon further research I have discovered this bug. 

[auto increment bug mysql 5.1]("http://bugs.mysql.com/bug.php?id=31956")

I have no choice but to install 5.5 on a production server. 

> **madeby.hm said:**
> Hi all,

I would love to run MySQL 5.5.X on Ubuntu 10.10 server. Do you know if  this will be part of the default "sudo apt-get install mysql-server"  command? Possible when?

I read this guide on how to do it manually:
[http://www.geeksww.com/tutorials/database_management_systems/mysql/installation/download_configure_compile_and_install_mysql_558_on_linux.php](http://www.geeksww.com/tutorials/database_management_systems/mysql/installation/download_configure_compile_and_install_mysql_558_on_linux.php)

Is that valid and will it be a good way to install it on Ubuntu? What about future updates?

Thanks!

Was this a good install tutorial? I currently am backing up my database and hoping to get information on the the process to install 5.5 smoothly.

---

### Post by sh1ny on 2011-01-25
That bug has been pushed in upstream and fixed back in 2007 ?

---

### Post by rededit on 2011-01-25
Are you sure? I am using Nolapro for a family run business and I am receiving an error when I try to add a new inventory item. Well the admin posted about the bug and posted a query I could do to verify the problem. Check out this [link]("http://www.nolapro.com/forum/viewtopic.php?f=6&t=1159&p=4439&hilit=error+adding+item#p4439"). I ran the query and my auto increment value was less then my rows. The queries matched the description of the bug. I assumed this was the problem. I am in the process of installing mysql 5.5 now. Do you have an idea of something else that could cause the issue? If the bug is fixed then I wonder why I am having this problem because believe me I would rather not have to go to 5.5 yet. This was not a permissions problem as the program checks before it installs. My permissions are correct. So ya if you got some info that could help me that would be greatly appreciated.

---

### Post by sh1ny on 2011-01-27
Are you using a cluster ?
This bug is in cluster mysql mode.

P.S. In our office we use otrs + mysql for a somewhat large database. Running on 10.04 ( upgraded from 9.10 ). It's our support ticket system and we get more than a bunch new tickets every day. Never had a problem with the mysql + autoincrement ( we got tables with more than 400k rows in them with autoinc ).

P.P.S. I don't think 5.5 will ever make it to Lucid. You'll be on your own for that, but again i don't think the solution is to upgrade to 5.5 . Non the less i have no idea where the problem might be.

---

### Post by rededit on 2011-02-02
Thank you for the reply. I did manage to install 5.5 but I am cautious to run it on a production server still. So I did some reading about MySQL and auto increment. I found the problem I think. Nola Pro still refers to it as a bug but I think that is the way it is suppost to be. InnoDB resets the variable when mysql gets reset if the value is above 1. I read about MyISAM and it does not reset. I tested the program using InnoDB added 2 items then reset mysql and it  reset the auto increment which made the program not take any new items.  Then I changed to MyISAM and corrected the variable to be 1 number above  my table rows. I was able to add items again. Then I reset MySQL and it maintained a peristant variable just like what I read. Problem is now I gotta do that for every function in the program that uses auto increment. I don't know that much about MySQL so I was wondering do you think there will be any serious problems from doing this?

---

### Post by sh1ny on 2011-02-03
You're definitely doing something wrong. See InnoDB does keep the autoincrement in memory yes, but :

[http://dev.mysql.com/doc/refman/5.1/en/innodb-auto-increment-handling.html](http://dev.mysql.com/doc/refman/5.1/en/innodb-auto-increment-handling.html)


states that :

> InnoDB uses the following algorithm to initialize the auto-increment counter for a table t that contains an AUTO_INCREMENT column named ai_col: After a server startup, for the first insert into a table t, InnoDB executes the equivalent of this statement:

[QUOTE]SELECT MAX(ai_col) FROM t FOR UPDATE;

InnoDB increments the value retrieved by the statement and assigns it to the column and to the auto-increment counter for the table. By default, the value is incremented by one. This default can be overridden by the auto_increment_increment configuration setting.[/QUOTE]

Which infact states that :

You insert a bunch o records, the autoincrements gets to 8 ( for example ).
You shutdown mysql.
You start mysql.
Upon trying to insert a new record, mysql does **SELECT MAX(ai_col) FROM t FOR UPDATE;** and finds out it's 8, and inserts the new records as value from above + 1 ( i.e. 9 ).

I just looked at one of my installations of magento. It uses InnoDB exclusively. I got a table like this :

```
CREATE TABLE IF NOT EXISTS `catalog_product_entity_varchar` (
  `value_id` int(11) NOT NULL AUTO_INCREMENT,
  `entity_type_id` mediumint(8) unsigned NOT NULL DEFAULT '0',
  `attribute_id` smallint(5) unsigned NOT NULL DEFAULT '0',
  `store_id` smallint(5) unsigned NOT NULL DEFAULT '0',
  `entity_id` int(10) unsigned NOT NULL DEFAULT '0',
  `value` varchar(255) NOT NULL DEFAULT '',
  PRIMARY KEY (`value_id`),
  UNIQUE KEY `IDX_ATTRIBUTE_VALUE` (`entity_id`,`attribute_id`,`store_id`),
  KEY `FK_CATALOG_PRODUCT_ENTITY_VARCHAR_ATTRIBUTE` (`attribute_id`),
  KEY `FK_CATALOG_PRODUCT_ENTITY_VARCHAR_STORE` (`store_id`),
  KEY `FK_CATALOG_PRODUCT_ENTITY_VARCHAR_PRODUCT_ENTITY` (`entity_id`)
) ENGINE=InnoDB  DEFAULT CHARSET=utf8 AUTO_INCREMENT=24595 ;

--
-- Constraints for dumped tables
--

--
-- Constraints for table `catalog_product_entity_varchar`
--
ALTER TABLE `catalog_product_entity_varchar`
  ADD CONSTRAINT `FK_CATALOG_PRODUCT_ENTITY_VARCHAR_ATTRIBUTE` FOREIGN KEY (`attribute_id`) REFERENCES `eav_attribute` (`attribute_id`) ON DELETE CASCADE ON UPDATE CASCADE,
  ADD CONSTRAINT `FK_CATALOG_PRODUCT_ENTITY_VARCHAR_PRODUCT_ENTITY` FOREIGN KEY (`entity_id`) REFERENCES `catalog_product_entity` (`entity_id`) ON DELETE CASCADE ON UPDATE CASCADE,
  ADD CONSTRAINT `FK_CATALOG_PRODUCT_ENTITY_VARCHAR_STORE` FOREIGN KEY (`store_id`) REFERENCES `core_store` (`store_id`) ON DELETE CASCADE ON UPDATE CASCADE;
```

As you can see the table is InnoDB, the field value_id is autoincrement and the autoincrement value on export is correctly set ( 24595 ). This magento shop has been running for a few months already ( since 10.04 :P ) and it has survived several server/mysql reboots. 

As much as i don't like to say it, i'm almost sure that the software you're using is buggy and not mysql itself. Handling InnoDB autoincrement is something that IS working correctly, or a lot of people would've been screaming to hell right now.

---

