---
title: "snort mysql and base"
date: 2007-04-22
forum: Server Platforms
---

### Post by shahin on 2007-04-22
Greetings-
   I am having a lot ot trouble with starting snort.  When I look at 
the deamon logs seems snort@localhost can not access my database.  I 
checked to see if I can manually log into the database, mysql and yes 
I can do it.  Strange thing is when I try to start snort I see an 
error message about eth0.  Would you please help?
Here is the eth error message:
sansari@zamzam:/var/www/base$ sudo /etc/init.d/snort start
Starting Network Intrusion Detection System: snort(eth0)No 
/etc/snort/snort.eth0.conf, defaulting to snort.conf
Here is the result of logs and the manual login:
Apr 21 18:18:54 zamzam snort: FATAL ERROR: database: mysql_error: Access 
denied for user 'snort'@'localhost' (using password: YES) 
sansari@zamzam:~$ mysql -u snort -p -D snort
Enter password: 
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 15 to server version: 
5.0.24a-Debian_9ubuntu2-log

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> exit
Bye

**********************************
I have to add I am using base and I suspect I am not updating everything
in the base_conf.php.  Here is what I have done:
$BASE_urlpath = "/base";
$DBlib_path = "/usr/share/php/adodb/";
$DBtype = "mysql"
$alert_dbname   = "snort";
$alert_host     = "localhost";
$alert_port     = "3306";
$alert_user     = "snort";
$alert_password = "123"; // It is not really 123, but you get the idea
/* Archive DB connection parameters */
$archive_exists   = 0; # Set this to 1 if you have an archive DB
$archive_dbname   = "snort_archive";
$archive_host     = "localhost";
$archive_port     = "";
$archive_user     = "snort";
$archive_password = "123";

These are all the changes I have made.  Would you please help?

---

### Post by shahin on 2007-04-22
Ok let me just thanks everyone.  Although I did not receive a direct reply,
I could not do this w/o the posts in the online community such as this one 
and the snort community.  I was finally able to get snort, and base work
together.  My issue was that snort.conf file had the wrong password.  I 
foundout by looking through the /var/log/ directory.  Speciaffically, the 
daemon file and messages was helpful.  I am not sure how in detail the 
base_conf.php works with snort.conf.  My last issue was a bad password for
the snort user to access the mysql database.  And I saw it in the daemon 
file in the log directory.  ie /var/log/daemon.  Below is some of the other
issues I ran into and how I solved them.  Good luck.  The directions that
is posted in this community in the tutorials section rocks.  The issue I
ran into was my own fault.
I went to update snort.config file but 
I did not have the line for mysql database so I looked in README.database file
at: /usr/shar/doc/snort-mysql directory
output database: log, mysql, user=root password=test dbname=db host=localhost
I did make a mistake:
mysql> set password for root@localhost=password('*********');
Query OK, 0 rows affected (0.00 sec)

I should have had PICK_A_PASSWORD

No it should have been a password.  When I did the:
sansari@zamzam:/usr/share/doc/snort-mysql$ zcat create_mysql.gz | mysql -u root 
-h localhost -p snort
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: Y
ES)
sansari@zamzam:/usr/share/doc/snort-mysql$ zcat create_mysql.gz | mysql -u root 
-h localhost -p snort
Enter password: 

I got error messages until I used PICK_A_PASSWORD literally as the password.


In short I am confused what above line does, while we do:
set password for snort@localhost=password('*******************');

 WARNING: include path for php has changed!                                     
 &#9474;  
 &#9474;                                                                              
   &#9474;  
 &#9474; libphp-adodb is no longer installed in /usr/share/adodb. New installation pat
h  &#9474;  
 &#9474; is now /usr/share/php/adodb.                                                 
   &#9474;  
 &#9474;                                                                              
   &#9474;  
 &#9474; Please update your php.ini file. Maybe you must also change your web-server  
   &#9474;  
&#9474; configuraton.        


****************************************************
Ok I found the issue.  According to the procedures we should fireup the brawser
and go to [http://localhost.base](http://localhost.base) .  When I do that it says:
Error loading the DB Abstraction library:  from "/usr/share/adodb/adodb.inc.php"

Check the DB abstraction library variable $DBlib_path in base_conf.php 

And there is another line which is not important.  When I look at the path
variable it says:

/usr/share/adodb/

But it should really be:

/usr/share/php/adodb/
***********************************************************
wow base is working finally:-)
I got the following error messages when I run sudo apt-get install php5-gd php-p
ear
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libgd2-xpm libt1-5 php5-cli
Suggested packages:
  libgd-tools
The following NEW packages will be installed:
  libgd2-xpm libt1-5 php-pear php5-cli php5-gd
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
E: Could not open lock file /var/cache/apt/archives/lock - open (2 No such file 
or directory)
E: Unable to lock the download directory

---

