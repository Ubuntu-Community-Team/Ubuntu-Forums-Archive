---
title: "Notes: FreePBX 2.10 on Ubuntu 12.04 Server"
date: 2012-05-24
forum: Tutorials
---

### Post by notanothersignup on 2012-05-24
Few notes about the install process and problems encountered
Sorry this is updated from memory after following the original script it looked too messy to let it just run so I ran it line by line on the console
From https://wiki.ubuntu.com/AsteriskOnUbuntu/Development

```
#installing FreePBX and Asterisk on Ubuntu 12.04 Server
#Revision 1.1
#updated 24th May 2012
#this is an untested script which I hope should be accurate
#it's best to read through this script before running it
#it's assumed that you're running from 'sudo -i' or su user
#better still, copy and paste each section in to your command line
#if any part of the install doesn't work for any reason, try 'apt-get update' and try again
#this doesn't include configuring any zaptel drivers, to install XP100P see https://wiki.ubuntu.com/AsteriskOnUbuntu/Current
# ensure package directory up to date and system upgraded

apt-get -y update
apt-get -y dist-upgrade
#probably should reboot here if linux-image was updated
#presumably any script that calls something like `uname -r` may cause problems otherwise
apt-get -y install asterisk sox asterisk-mysql asterisk-mp3

# you can test asterisk at this point by typing 'asterisk -vvvvr'
# if it's working you'll see a prompt '>'
# type in 'quit' to get back to the command line

# install mysql server
apt-get -y install mysql-server

# install packages needed beyond base install with openssh server
#apt-get -y install linux-headers-`uname -r`

apt-get -y install make bison flex g++ gcc apache2 php5
apt-get -y install php5-cli php5-mysql php-pear php-db php5-gd curl
apt-get -y install sox libncurses5-dev libssl-dev libmysqlclient15-dev
apt-get -y install php-pear

#the following should already be installed
#apt-get -y install apache2
#apt-get -y install php5
#apt-get -y install libapache2-mod-php5
#/etc/init.d/apache2 restart
#apt-get update

#what does this do?... suggests default db format is deprecated?? (can this be updated safely)
pear install DB

#run this line again
#apt-get install php5-mysql
#before configuring asterisk, save the current settings
#cd /etc mkdir backupasterisk
#cp -r asterisk backupasterisk
#cp -r /var/run/asterisk backupasterisk

#get freepbx
export FREEPBX_VERSION=2.10.0 
cd /usr/src
wget http://mirror.freepbx.org/freepbx-${FREEPBX_VERSION}.tar.gz
tar zxvf freepbx-${FREEPBX_VERSION}.tar.gz
cd freepbx-${FREEPBX_VERSION}

#remove the asterisk password so the rest of the script works more easily
#passwd --delete asterisk
#the following I got from https://wiki.ubuntu.com/AsteriskScriptOnHardy
# create asterisk user and group, adding to www-data group for apache server
#ignore any error on the following line
#adduser asterisk --disabled-password --gecos "asterisk PBX"
adduser www-data asterisk

# fix up apache configuration to run as asterisk user
#cp /etc/apache2/apache2.conf /etc/apache2/apache2.conf-orig
#this should actually now be altered in /etc/apache2/envvars
#however there seem to be some serious bugs in the FreePBX install script
#if the wrong sequence of events are chosen it can corrupt the install
#it didnt work for me unless initially run with the www-data user/group
#sed -i "s/\(^User *\)\(.*\)/\1asterisk/" /etc/apache2/apache2.conf
#sed -i "s/\(^Group *\)\(.*\)/\1asterisk/" /etc/apache2/apache2.conf

# patch safe_asterisk script to use bash
#sed -i "s|#!/bin/sh|#!/bin/bash|" /usr/sbin/safe_asterisk

# add dummy timing device for asterisk
#modprobe ztdummy
#ztdummy should already be included

# setup databases for freepbx use
#export MYSQL_ROOT_PW=
mysqladmin -u root -p${MYSQL_ROOT_PW} create asterisk
mysqladmin -u root -p${MYSQL_ROOT_PW} create asteriskcdrdb
mysql -u root -p${MYSQL_ROOT_PW} asterisk < SQL/newinstall.sql
mysql -u root -p${MYSQL_ROOT_PW} asteriskcdrdb < SQL/cdr_mysql_table.sql
mysql -u root -p${MYSQL_ROOT_PW} <<-END_PRIVS
    GRANT ALL PRIVILEGES ON asterisk.* TO asteriskuser@localhost IDENTIFIED BY "${ASTERISK_DB_PW}"; GRANT ALL PRIVILEGES ON asteriskcdrdb.* TO asteriskuser@localhost IDENTIFIED BY "${ASTERISK_DB_PW}"; flush privileges; 
END_PRIVS

# reconfigure php for freepbx

cp /etc/php5/apache2/php.ini /etc/php5/apache2/php.ini-orig
sed -i "s/\(upload_max_filesize *= *\)\(.*\)/\120M/" /etc/php5/apache2/php.ini
sed -i "s/\(memory_limit *= *\)\(.*\)/\1100M/" /etc/php5/apache2/php.ini
#was already set...
#sed -i "s/\(magic_quotes_gpc *= *\)\(.*\)/\1Off/" /etc/php5/apache2/php.ini

# restart apache web server
/etc/init.d/apache2 restart

# fix up directory use and permissions for asterisk
#mkdir /var/run/asterisk
#chown asterisk:asterisk /var/run/asterisk
#chown asterisk:asterisk -R /etc/asterisk
#chown asterisk:asterisk -R /var/lib/asterisk

# chmod a+x /var/lib/asterisk/bin/*
#chown asterisk:asterisk -R /var/log/asterisk
#chown asterisk:asterisk -R /var/spool/asterisk
#chown asterisk:asterisk -R /var/www

#not sure what the following does or if necessary...(possibly turn on and off defaults)
sed -i "s/\[directories\](!) .*/[directories]/" /etc/asterisk/asterisk.conf
#believe this was already set
#sed -i "s|astrundir *=> */var/run|astrundir => /var/run/asterisk|" /etc/asterisk/asterisk.conf

#this is from the FreePBX install instructions...
#you may need to update safe_asterisk to make the start_asterisk script work 
#(don't know if it is significantly different than running /etc/init.d/asterisk start)

#nano /usr/sbin/safe_asterisk
SAFE_AST_BACKGROUND=1

# start asterisk
./start_asterisk start

# install amp
#script should ask pertinent questions including db password and ip
#you should choose /var/www as the web root however please note
#the script did not work for me and failed whilst still referencing /var/www/html
#it appears until the config files are updated that this will not take the correct
#setting for webroot or finish installation correctly
#however please note if apache started as asterisk:asterisk the installer did not
#provide a working web page from which to update the config files
#therefore the script has to be run once under www-data:www-data then a 2nd time
#under asterisk:asterisk after logging on to the FreePBX console and updating the config
./install_amp
#logon to web page e.g. 'localhost/admin', username is admin, password is admin
#save / update config (presumably writes default config files)
#don't update modules yet
#i think if you update your modules then reinstall over the top you will break FreePBX

#update apache logon
#this should actually now be altered in /etc/apache2/envvars
#however there seem to be some serious bugs in the FreePBX install script
#if the wrong sequence of events are chosen it can corrupt the install
#it didnt work for me unless initially run with the www-data user/group
#not sure if following will work as I just used nano to do the udpates
#sed -i "s/\(^User *\)\(.*\)/\1asterisk/" /etc/apache2/envvars
#sed -i "s/\(^Group *\)\(.*\)/\1asterisk/" /etc/apache2/envvars

# restart apache web server
/etc/init.d/apache2 restart

# install amp (should complete this time)
./install_amp

# start amportal (problems with init script and conversion to upstart)
#amportal start

#current known bug 1 (with fix following): when I run 'grep -r sqlite /etc/asterisk/*' it shows I'm running sqlite, when I run 'asterisk -c' it reports 'Registered Config Engine sqlite' and '.PostgreSQL RealTime: Failed to connect database asterisk on 127.0.0.1: '. Obviously I want to configure for MySQL not Postgres.
#current known bug 2: (with fix following) the message log reports 'manager.c: 127.0.0.1 failed to authenticate as admin'. This may very well be related to known bug number 1.
#for the bug fixes a few edits to the config files should do the trick. Alternatively the Hardy install for Asterisk script works quite well. https://wiki.ubuntu.com/AsteriskScriptOnHardy
# to fix these bugs I did the following, uncomment the following lines if needed
#rm -r /etc/asterisk
#apt-get -y update
#apt-get upgrade
#apt-get -y remove asterisk
#apt-get -y install asterisk
#apt-get install --reinstall asterisk
#cd usr/src/freepbx-${FREEPBX_VERSION}
#./install_amp --username=root --password={MYSQL_ROOT_PW}
#amportal start

echo "you're done, go to your browser URL and type in 'localhost/admin', username is admin, password is admin"
echo ""
echo "** VERY IMPORTANT: IF YOU DON'T WANT A LOT OF GRIEF, MAKE SURE THE FIRST THING YOU DO IS TO UPGRADE YOUR MODULES IN FREEPBX SETUP"
echo "http://localhost/admin/config.php?type=setup&display=modules and click on 'check online' and then update the current modules"
echo "if you get an error that a field is missing (password_sha1) then read the end of the script for more notes"
#notes on how to fix password_sha1 error.
#add a field to ampuser in the table, using phpmyadmin, mysql or webmin.
#run the following php script to get the value to enter in password_sha1
#<?php
# $newpassword = 'admin';
# echo sha1($newpassword) ;
#?>
# for further info see http://wiki.opencsta.org/index.php/FreePBX_-_password_sha1_change_in_database_for_admin_to_reset_lost_password
```

---

### Post by notanothersignup on 2012-05-24
Sorry the original thread is still being approved but I don't have time to wait for it to be approved to finish the post.
Please could you tag this on the bottom of the original thread.

There were major issues getting the FreePBX startup script to work (amportal start). The suggested init script did not work and failed with an obscure error something like [FATAL] Error. After doing some debugging this turned out to be because MySql wasn't running as it appears the amportal script requires a database connection. The problem now being that currently (24th May 2012) MySql uses an upstart job and the relevant startup procedure appears to be asynchronous so even putting the required line in your rc.local may not always work correctly unless you introduce a suitable system dependent delay (or other more sophisticated synchronization mechanism). 

Initially I didn't think writing a new upstart job was going to be very difficult i.e. just wrap the amportal script. This assumption proved to be completely incorrect and it required modification of one of the FreePBX scripts to make it work correctly. Upstart also appeared to get confused very easily frequently resulting in the system hanging on reboot. I guess you could probably add the amportal start stop commands into the existing mysql upstart job but this would presumably not be upgrade proof. It appears the developers of upstart really dislike the use of pid files and that if I have understood correctly that the premise on which upstart is designed specifically relies on identifying the PID of the daemon. You could cheat and write a simple loop that checks for the PID in /var/run/asterisk/asterisk.pid but I didn't like that idea personally. The problem with the provided expect stanza is that neither the fork or daemon settings appear to be able to identify the correct PID and I believe that this is what causes the system to hang when rebooting. I would not recommend using asterisk -r for tracking the daemon as unless you allow it to connect to the console (which is messy and buggy) it will just sit and spin (you will also potentially have a copy of asterisk cli connected to asterisk running as root). Perhaps you could use /var/run/asterisk/asterisk.ctl somehow if you want to take the time to investigate the mechanism involved (or already know) or just wait for the files to disappear (not sure how that's better than waiting for the PID though unless you can come up with a way to do it without polling).

I believe the amportal script probably does all sorts of things that will make it hard for upstart to automatically determine the correct PID. I would suggest (if anyone cares :)) that perhaps a filter can be added where you could specify the name of the daemon you want along with some other specification to identify it correctly. As it appears upstart uses ptrace (I'm guessing this allows tracing of PIDs as they start and stop) providing a filter specification should allow the correct PID to be identified without resorting to trial / error or wading through long strace logs to figure out how many forks you need to wait for.

Anyway I will post what worked for me in case it is of use to someone...

Made sure I reset safe_asterisk back to its original state
```
sudo nano /usr/sbin/safe_asterisk 
SAFE_AST_BACKGROUND=0
```Added a new upstart job as (/etc/init/amportal.conf) perhaps this should be called freepbx to prevent confusion with the existing amportal script...
```
# amportal - FreePBX / Asterisk 
#
# Asterisk Phone System and FreePBX Web App

description    "FreePBX"

start on started mysql
stop on stopping mysql

pre-stop exec /usr/local/sbin/amportal stop

exec /usr/local/sbin/amportal start wait
```Modified /var/lib/asterisk/bin/freepbx_engine to wait for the asterisk daemon PID to terminate which should be compatible with upstart and also does not require any polling. Upstart will probably track the parent PID but I think that's still ok asterisk may be re-spawned by the script. Patch as follows...

```
--- orig/freepbx_engine    2012-05-22 21:05:07.176973905 +0100
+++ /var/lib/asterisk/bin/freepbx_engine    2012-05-22 21:25:37.556379280 +0100
@@ -10,6 +10,7 @@
 
 ROOT_UID=0     # root uid is 0
 E_NOTROOT=67 # Non-root exit error
+C_WAIT=$2
 
 echo
 # check to see if we are root
@@ -299,7 +300,8 @@
             # su - asterisk -c "export PATH=$PATH:/usr/sbin && export LD_LIBRARY_PATH=/usr/local/lib && /usr/sbin/safe_asterisk"
             export LD_LIBRARY_PATH=/usr/local/lib
             umask $AMPVMUMASK
-            /usr/sbin/safe_asterisk -U $AMPASTERISKUSER -G $AMPASTERISKGROUP
+            /usr/sbin/safe_asterisk -U $AMPASTERISKUSER -G $AMPASTERISKGROUP &
+                        pid_child=$!
             sleep 5
             check_asterisk
             sleep 1
@@ -307,6 +309,12 @@
             echo "Asterisk Started"
         fi
     call_hook run_asterisk
+
+    case $C_WAIT in
+            wait)
+                wait $pid_child
+        ;;
+    esac
 }
 
 stop_asterisk() {
```Remove original asterisk init script...
```
sudo rm /etc/rc*/*asterisk
```You can still call amportal start stop as normal with the modification above. I did this in case there is anywhere in FreePBX that calls that script. I guess upstart wouldn't be aware the daemon is running anymore though after the 1st time amportal stop is called.

As a side note I originally installed AsteriskNOW but this failed to work correctly. It hit a jQuery error every time I tried to apply the config and kept returning to the logon prompt after clicking on a link. I saw the same errors during my own install after trying to fix the install by running install_amp again after upgrading the modules. Some further notes about CentOS as used by AsteriskNOW... the boot time seemed very slow to me and it does not play well with virtualbox requiring the divider=10 option to be added to the kernel boot options (it still consumes more CPU at idle that ubuntu even after that).

---

### Post by Stu2 on 2012-10-17
Thanks - the instructions were very helpful. I haven't tried the upstart stuff, yet.

I also had to 'chmod 777 /var/lib/php5/*' Otherwise, every click returned me to the login screen.

---

