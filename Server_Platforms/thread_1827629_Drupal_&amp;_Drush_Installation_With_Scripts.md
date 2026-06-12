---
title: "Drupal &amp; Drush Installation With Scripts"
date: 2011-08-18
forum: Server Platforms
---

### Post by histographik on 2011-08-18
[SIZE=1][FONT=Verdana, sans-serif]========================================
[SIZE=3]Drupal & Drush Installation With Scripts[/SIZE]
========================================

There are many ways of accomplishing this installation. What this tutorial attempts to do is to outline the most basic installation possible. It show you how to install Drupal from the command-line to speed up "development" of your website.

**[[EDIT]]** [COLOR="SandyBrown"]REMOVED LAMP SERVER INSTALL PART OF TUTORIAL AS THERE ARE MUCH BETTER (MORE SECURE) TUTORIALS ON THIS TOPIC.[/COLOR]

FOR A LIVE SITE DON'T USE ROOT AS DRUPAL'S DATABASE USER. FOR DEVELOPMENT PURPOSES WHERE SECURITY IS NOT A CONCERN GO AHEAD - IT MAKES SETUP AND RE-INSTALLATION FASTER. BUT I STRESS THIS IS ONLY FOR DEVELOPMENT PURPOSES WHERE RE-INSTALLATIONS MAY BE A COMMON THING. 

[COLOR=SlateGray]Here's the plan:
[/COLOR][/FONT][/SIZE][SIZE=1][COLOR=SlateGray][FONT=Verdana, sans-serif]==========[/FONT][/COLOR][/SIZE][COLOR=SlateGray]
[/COLOR][SIZE=1][FONT=Verdana, sans-serif][COLOR=SlateGray]Install drush for using the command line on Drupal. Create some management scripts to manage Drupal via the command-line. Create some installation scripts to install drupal via the command-line. Make the scripts executable and install them in /usr/local/bin. Open a terminal and install Drupal with one command.[/COLOR]

01. Assumptions
==========
[COLOR=Sienna]You have your LAMP server, Drupal MySQL database and databse user setup and ready to go! 
For development sites on my **local desktop machine** I use root as drupal's database user because it speeds up re-installation when necessary.[/COLOR]

02. Install drush (DRUSH 4.4 AVAILABLE IN NATTY WITHOUT PPA)
==========
#[COLOR=Sienna]apt-get install drush[/COLOR]
 
03. Create 3 folders to hold your drupal backups, scripts and libraries
==========
#[COLOR=Sienna]mkdir /home/user/drupal/backup[/COLOR]
#[COLOR=Sienna]mkdir /home/user/drupal/scripts[/COLOR]
#[COLOR=Sienna]mkdir /home/user/drupal/libraries[/COLOR]
#[COLOR=Sienna]cd /home/user/drupal/scripts[/COLOR]

04. Create a script to manage web server permissions
==========
#[COLOR=Sienna]gedit drupal-siteperms && [/COLOR][/FONT][/SIZE][SIZE=1][FONT=Verdana, sans-serif][COLOR=Sienna]chmod +x drupal-siteperms[/COLOR][/FONT][/SIZE][SIZE=1][FONT=Verdana, sans-serif]

---------cut-and-paste----------
[COLOR=SeaGreen]#! /bin/bash 

cd /var/www 
chown -R root:www-data . 
find . -type d -exec chmod u=rwx,g=rx,o= {} \; 
find . -type f -exec chmod u=rw,g=r,o= {} \; 
cd /var/www/sites 
find . -type d -name files -exec chmod ug=rwx,o= '{}' \; 
find . -name files -type d -exec find '{}' -type f \; | while read FILE; do chmod ug=rw,o= "$FILE"; done 
find . -name files -type d -exec find '{}' -type d \; | while read DIR; do chmod ug=rwx,o= "$DIR"; done 
echo 
echo "Permission rebuilding is complete!" 
echo[/COLOR]
----------cut-and-paste----------

05. Create a script to manage Drupal updates
==========
#[COLOR=Sienna]gedit drupal-siteup && [/COLOR][/FONT][/SIZE][SIZE=1][FONT=Verdana, sans-serif][COLOR=Sienna]chmod +x drupal-siteup[/COLOR][/FONT][/SIZE][SIZE=1][FONT=Verdana, sans-serif]

----------cut-and-paste----------
[COLOR=SeaGreen]#!/bin/bash 

drush --yes -r /var/www up && echo
drush --yes -r /var/www cc all && echo
drush --yes -r /var/www cron && echo
drupal-siteperms[/COLOR]
----------cut-and-paste----------

06. Create a script to manage Drupal backups
==========
#[COLOR=Sienna]gedit drupal-backup && [/COLOR][/FONT][/SIZE][SIZE=1][FONT=Verdana, sans-serif][COLOR=Sienna]chmod +x drupal-backup[/COLOR][/FONT][/SIZE][SIZE=1][FONT=Verdana, sans-serif]

----------cut-and-paste----------
[COLOR=SeaGreen]#!/bin/bash 

drush -r /var/www sql-dump &#8211;result-file=/home/user/drupal/backup/backup.sql[/COLOR]
----------cut-and-paste----------

07. Create a script to install drupal for the first time
==========
#[COLOR=Sienna]gedit install-drupal-first && [/COLOR][/FONT][/SIZE][SIZE=1][FONT=Verdana, sans-serif][COLOR=Sienna]chmod +x install-drupal-first[/COLOR][/FONT][/SIZE][SIZE=1][FONT=Verdana, sans-serif]

----------cut-and-paste----------
[COLOR=SeaGreen]#!/bin/bash 

clear 
echo 
echo " ... INSTALL DRUPAL CORE FOR THE FIRST TIME&#8221;
echo 

[COLOR=SeaGreen]# GOTO WEB ROOT 
cd /var/www 

[/COLOR][COLOR=SeaGreen]# CLEAR DATABASE (make sure it is clean!)[/COLOR]
drush --yes sql-drop 
echo 

# CLEAR WEB ROOT OF OLD SITE IF ANY (make sure it is clean!)
rm -Rf /var/www/* > /dev/null 2>&1 && rm /var/www/.htaccess > /dev/null 2>&1 

# DOWNLOAD DRUPAL CONTAINER INTO WEB ROOT 
drush --yes dl drupal --drupal-project-rename 
echo 

# RELOCATE DRUPAL FILES TO FROM CONTAINER TO WEBROOT 
mv /var/www/drupal/* /var/www && mv /var/www/drupal/.htaccess /var/www 

# REMOVE DRUPAL DOWNLOAD CONTAINER 
rm -r /var/www/drupal 

# CREATE DRUPAL INSTALL SETTINGS.PHP 
cp /var/www/sites/default/default.settings.php /var/www/sites/default/settings.php 

# COPY LIBRARY FILES TO WEB DRUPAL 
cp -Rf /home/user/drupal/libraries /var/www/sites/all/ 

# RESET WEB ROOT PERMISSIONS TO DEFAULT 
drupal-siteperms 
echo 

# SET TEMP INSTALL PERMISSIONS FOR DEFAULT FOLDER AND SETTINGS.PHP 
chmod 777 /var/www/sites/default && chmod 777 /var/www/sites/default/settings.php 

# INSTALL DRUPAL WITH OWNER AND DEFAULT DATABASE 
drush --yes site-install standard --site-name=mywebsite --site-mail=jim@gmail.com --account-name=jim --account-pass=12345 --db-url=mysql://root:a1B2c3@localhost/drupaldb
echo 

# RESET WEB ROOT PERMISSIONS TO DEFAULT AFTER INSTALL 
drupal-siteperms 
echo 

# UPDATE DRUPAL 
drupal-siteup 

echo 
echo " ... DRUPAL COMMERCE SITE : READY : BROWSE TO [http://localhost](http://localhost)  " 
echo [/COLOR]
----------cut-and-paste----------

08. Create a script to re-install drupal with existing database
==========
#[COLOR=Sienna]gedit install-drupal-existing && [/COLOR][/FONT][/SIZE][SIZE=1][FONT=Verdana, sans-serif][COLOR=Sienna]chmod +x install-drupal-existing[/COLOR][/FONT][/SIZE][SIZE=1][FONT=Verdana, sans-serif]

----------cut-and-paste----------
[COLOR=SeaGreen]#!/bin/bash 

clear 
echo 
echo " ... INSTALL DRUPAL CORE WITH EXISTING DATABASE&#8221;
echo 

# GOTO WEB ROOT 
cd /var/www 

# REMOVE OLD BACKUPS (make sure it is clean!)
rm -Rf /home/user/drupal/backup/backup.sql 

# BACKUP EXISTING SITE SQL (create up-to-date backup!)
drush -y sql-dump --result-file=/home/user/drupal/backup/backup/backup.sql 
echo 

# CLEAR DATABASE 
drush -y sql-drop 
echo 

# CLEAR WEB ROOT OF OLD SITE (make sure it is clean!)
rm -Rf /var/www/* > /dev/null 2>&1 && rm /var/www/.htaccess > /dev/null 2>&1 

# DOWNLOAD DRUPAL CONTAINER INTO WEB ROOT 
drush --yes dl drupal --drupal-project-rename 
echo 

# RELOCATE DRUPAL FILES TO FROM CONTAINER TO WEBROOT 
mv /var/www/drupal/* /var/www && mv /var/www/drupal/.htaccess /var/www 

# REMOVE DRUPAL DOWNLOAD CONTAINER 
rm -r /var/www/drupal 

# CREATE DRUPAL INSTALL SETTINGS.PHP 
cp /var/www/sites/default/default.settings.php /var/www/sites/default/settings.php 

# COPY LIBRARY FILES TO WEB DRUPAL 
cp -Rf /home/user/drupal/libraries /var/www/sites/all/ 

# RESET WEB ROOT PERMISSIONS TO DEFAULT 
drupal-siteperms 
echo 

# SET TEMP INSTALL PERMISSIONS FOR DEFAULT FOLDER AND SETTINGS.PHP 
chmod 777 /var/www/sites/default && chmod 777 /var/www/sites/default/settings.php 

# INSTALL DRUPAL WITH OWNER AND DEFAULT DATABASE 
drush --yes site-install standard --site-name=mywebsite --site-mail=jim@gmail.com --account-name=jim --account-pass=12345 --db-url=mysql://root:a1B2c3@localhost/drupaldb
echo 

# RESET WEB ROOT PERMISSIONS TO DEFAULT AFTER INSTALL 
drupal-siteperms 
echo 

# RESTORE PREVIOUS SQL 
drush -y sql-cli < /home/user/drupal/backup/backup.sql

# RESET PERMISSIONS 
drupal-siteperms 

# UPDATE DRUPAL 
drupal-siteup 

echo 
echo " ... DRUPAL COMMERCE SITE : REINSTALLED : BROWSE TO [http://localhost](http://localhost) " 
echo [/COLOR]
----------cut-and-paste----------

You should now have the following scripts located in /home/user/drupal/scripts
==========
[COLOR=Black][COLOR=DarkOrchid]drupal-siteperms[/COLOR], [/COLOR][COLOR=Black][COLOR=DarkOrchid]drupal-siteup[/COLOR], [/COLOR][COLOR=Black][COLOR=DarkOrchid]drupal-backup[/COLOR], [/COLOR][COLOR=Black][COLOR=DarkOrchid]install-drupal-first[/COLOR], [/COLOR][COLOR=DarkOrchid]install-drupal-existing[/COLOR]

Copy over your scripts from /home/user/drupal/scripts to /usr/local/bin
==========
#[COLOR=Sienna]sudo cp /home/user/drupal/scripts/* /usr/local/bin[/COLOR]

RUNNING THESE SCRIPTS!
==========

First time Drupal installation open a terminal and issue the installation command:
#[COLOR=Sienna]sudo install-drupal-first[/COLOR]

subsequent re-installations of Drupal with an existing database:
#[COLOR=Sienna]sudo install-drupal-existing[/COLOR]
 
Then open up your browser and go to [http://localhost](http://localhost) and you are all done.

Remember you can use the management scripts at any time independently
==========

To update Drupal and additionally reset site permissions run:
#[COLOR=Sienna]drush -r /var/www drupal-siteup[/COLOR]

To reset site permissions only run:
#[COLOR=Sienna]drush -r /var/www drupal-siteperms[/COLOR]

To backup the Drupal database run:
#[COLOR=Sienna]drush -r /var/www drupal-backup[/COLOR]

!! /home/[COLOR=Red]user[/COLOR]/drupal/scripts/&#8221;  &#8220;usr&#8221; = [COLOR=Red]user name[/COLOR] !!

==========
All done     :-))
==========[/FONT][/SIZE][FONT=Verdana, sans-serif][SIZE=1]
[/SIZE][/FONT]

---

### Post by rudelgurke on 2011-08-19
> **histographik said:**
> 
<Directory /> 
Options FollowSymLinks 
AllowOverride All 
</Directory>


This should - would even say it must be:

<Directory /> 
Options None
AllowOverride None
Order deny,allow
Deny from all
</Directory>

There is a reason this is the default configuration, a very good reason.

Another note - it's maybe a good idea to create a dedicated user for Drupal. Using the "root" user which has basically all rights on MySQL isn't a good idea.

And finally - Drush may install Drupal 7.x though Ubuntu - at the moment - doesn't official provides packages for MySQL 5.5.x so one gives up one of the advantages Drupal 7 provides over Drupal 6 :(
And some modules you install aren't required - except one needs them (e.g. the commerce modules).

But - yes - Drush is nice to rollout Drupal installations without the need to go through their web based installed :)

---

### Post by histographik on 2011-08-20
For anyone interested the scripts above work equally well for drupal 6 (i.e) "drush dl drupal-6". Just re-tune the modules for branch 6 which will differ for version 7, obviously.

Thanks for the feedback about security, good advice for a live site. (REMOVED INSECURE LAMP SERVER INSTALL PART OF TUTORIAL TO FOCUS ON THE SIMPLE BASHING OF DRUSH!)

---

