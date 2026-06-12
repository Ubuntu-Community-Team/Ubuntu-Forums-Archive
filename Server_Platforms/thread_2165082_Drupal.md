---
title: "Drupal"
date: 2013-08-03
forum: Server Platforms
---

### Post by salmendar on 2013-08-03
hi, i have a new ubuntu server 12.04 installed and configured and the thing is that i installed drupal in my server but when i put my website on the server and access it . it gives me this error. 

*PDOException*[COLOR=#8C2E0B][FONT=Helvetica Neue]: SQLSTATE[28000] [1045] Access denied for user 'root'@'localhost' (using password: NO) in [/FONT][/COLOR]*lock_may_be_available()*[COLOR=#8C2E0B][FONT=Helvetica Neue] (line [/FONT][/COLOR]*167*[COLOR=#8C2E0B][FONT=Helvetica Neue] of [/FONT][/COLOR]*/var/www/civil/includes/lock.inc*[COLOR=#8C2E0B][FONT=Helvetica Neue]).

please help[/FONT][/COLOR]:(

---

### Post by tgalati4 on 2013-08-03
What version of Drupal?  In the Drupal installation instructions, there should be a section about setting up a proper mysql username and password.  Failure to do this will result in not being able to access the database and hence Drupal will not function.

Drupal 8 can create the database if you have installed with root privileges:  [https://drupal.org/documentation/install](https://drupal.org/documentation/install)

---

### Post by lisati on 2013-08-04
That looks like a MySQL error to me. Do you have a MySQL admin user and password set up? Having one can sometime make it easier for configuring things like Drupal.

Some basic instructions on setting up MySQL users can be found here: [https://help.ubuntu.com/community/ApacheMySQLPHP#Create_a_mysql_user](https://help.ubuntu.com/community/ApacheMySQLPHP#Create_a_mysql_user)

---

### Post by salmendar on 2013-08-04
i have both phpmyadmin and drupal installed and the phpmyadmin does allow me to log in as the separate user that i created for drupal and also to make changes in the drupal database ... ie to create the users and change passwords in phpmyadmin. but when i put my website on the server this error occurs... following are the links to my php my admin and drupal databases.
[drupal]("http://182.180.82.4/drupal")
[phpmyadmin]("http://182.180.82.4/phpmyadmin")

but even then i cant access my website.

---

### Post by Geoff_Butterfield on 2013-08-05
Drupal isn't connecting to your database because the MySQL username and/or password is incorrect, or the user doesn't have the right database permissions. Usually in Drupal 7+, the database gets connected the first time you run, but in your case you will need to make sure the MySQL connection information in this file --/drupal root/sites/default/settings.php -- matches what MySQL is expecting.

---

### Post by salmendar on 2013-08-06
well the problem was solved .... the problem was not the username and password... the problem was the host... :lolflag:

i was uploading user under  % host not localhost.

no body could have guessed that one ... pretty stupid mistake that i made.. rechecking that made it work .... 

Thank You all for your Support. I am very thankful to be a beginner of Ubuntu ... (Soon i hope that i can be of help to others)

---

