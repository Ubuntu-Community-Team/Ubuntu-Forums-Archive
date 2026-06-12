---
title: "UNIX mysql socket?"
date: 2007-12-08
forum: Server Platforms
---

### Post by whitenight639 on 2007-12-08
Hey, 

I'm trying to connect to my webhosts mysql database to install joomla, 

they said that I need to use the UNIX socket rather than TCP/IP 

Now i havnt got a clue how to figure out what the unix socket is, or what username / pass to use with it (they say in the knowlage base to  use my regular username /pass but it dosnt seem to work) 

also I am using a virtual private servers so have full controll over my php.ini which makes things more complicated, iv usedthe default one. 

my webhosts phpinfo.php is here [http://digital-crocus.com/phpinfo.php](http://digital-crocus.com/phpinfo.php)

so how do i work out what to put in the configuration.php file of joomla, iv tried loads of different ways its really confusing, 



	/* Database Settings */

var $dbtype = 'mysql';			// Normally mysql

var $host = '/tmp/mysql.sock'; // This is normally set to localhos

var $user = '';			// MySQL username

var $password = '';		// MySQL password

var $db = 'healthfreedom';			// MySQL database name

var $dbprefix = 'jos_';	  // Do not change unless you need to!



please help!!

---

### Post by Dryw Paulic on 2007-12-10
From your webhosts phpinfo page it looks like the configuration below is correct. Their mysql socket is indeed in /tmp/mysql.sock (default place) so the below should be good.

I did, however, find this on their website:

[http://digital-crocus.com/kb/13_I_can%27t_login_to_MySQL.html](http://digital-crocus.com/kb/13_I_can%27t_login_to_MySQL.html)

Looks like you can create a database from the control panel, then use that database name/your user credentials to login.

---

