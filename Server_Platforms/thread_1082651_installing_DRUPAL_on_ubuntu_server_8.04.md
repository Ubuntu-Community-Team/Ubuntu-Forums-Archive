---
title: "installing DRUPAL on ubuntu server 8.04"
date: 2009-02-28
forum: Server Platforms
---

### Post by max11 on 2009-02-28
I want to install **Drupal** content manager -CMS- 

Do I just follow all the steps here: 
[http://drupal.org/getting-started/5/install](http://drupal.org/getting-started/5/install) 
???

Is there anything special when installing on UBUNTU server 8.04???

Please advise...

---

### Post by leg on 2009-02-28
If starting fresh I would suggest installing Drupal 6 but have a good look at the modules available for it and that all you will need has been  updated for 6. It has been out a while now so most should be. Other than  that I would say yes just follow the install instructions from the site.

---

### Post by bioborg on 2009-03-01
I wrote these scripts to install Drupal, and make sure that clean urls and such work.  This works on 8.04 or 8.10 (8.04 doesn't actually need the part where the script writes to httpd.conf.  The command a2enmod rewrite is sufficient for enabling mod_rewrite for clean urls.)  This is the "developer way" to install Drupal.  It was written for the cloud, but will work anywhere.  Disregard the smiley, it should be (with no spaces inbetween) : p


(this script needs to be run as root.  I do a sudo su first then I chmod +x the script, then I execute it with a ./*SCRIPTNAME* )

#!/bin/bash
#Check for number of arguments
EXPECTED_ARGS=6
E_BADARGS=65

if [ $# -ne $EXPECTED_ARGS ]
then
  echo "Usage: `basename $0`  ROOTSQLPWD DBNAME DBUSER DBPASS site.domain.com DRUPAL-TAG (i.e. DRUPAL-6-10 )"
  exit $E_BADARGS
fi

#{ubuntu update}D
apt-get update && apt-get -y upgrade
apt-get -y install apache2 php5 mysql-server php5-mysql php5-gd cvs subversion sendmail vim
mysqladmin -u root password $1
 

#{install drupal from cvs}
mkdir -p /cvs/drupal-cvs/tags
mkdir /cvs/drupal-cvs/trunk
mkdir /cvs/drupal-cvs/branches
cd /cvs/drupal-cvs
cvs -d:pserver:anonymous:anonymous@cvs.drupal.org:/cvs/drupal checkout -d ./trunk -r $6 drupal
cd /
mkdir -p svn
svnadmin create svn/repos
svn import /cvs/drupal-cvs file:///svn/repos/drupal-cvs -m "Initial Import"

 

#{setting up multi-site drupal with symbolic links}

cd /var/www/html/
ln -s . $5

mv /var/www/html/sites/default/default.settings.php /var/www/html/sites/default/settings.php
cd sites
cp -r default/ _template

cp -r _template $5
chown -R www-data.www-data $5

cd /var/www
svn checkout file:///svn/repos/drupal-cvs/trunk html/
cp -r /var/www/html/sites/default /var/www/html/sites/_template
chown -R www-data.www-data /var/www/html/sites
 

#{change /var/www to /var/www/html in two spots }
sed 's/var\/www/var\/www\/html/' /etc/apache2/sites-available/default > /etc/apache2/sites-available/default.new

mv /etc/apache2/sites-available/default.new /etc/apache2/sites-available/default

a2enmod rewrite

echo "<Directory /var/www/html>" >> /etc/apache2/httpd.conf
echo "   RewriteEngine on" >> /etc/apache2/httpd.conf
echo "    RewriteBase /" >> /etc/apache2/httpd.conf
echo "    RewriteCond %{REQUEST_FILENAME} !-f" >> /etc/apache2/httpd.conf
echo "    RewriteCond %{REQUEST_FILENAME} !-d" >> /etc/apache2/httpd.conf
echo "    RewriteRule ^(.*)$ index.php?q=$1 [L,QSA]" >> /etc/apache2/httpd.conf
echo " </Directory>" >> /etc/apache2/httpd.conf

/etc/init.d/apache2 restart
 

#{install and make mysql databases - root mysql password PASSWORD}


mysql -uroot -p$1 -e"create database $2;"
mysql -uroot -p$1 -e"grant all on $2.* to $3@localhost identified by '$4';"
 

#{set permissions}
echo "now run install script at $5"



[B][U]Includes script to set up multisite instance: 

This should be able to be incorporated into a drupal module[/U][/B]


#!/bin/bash
EXPECTED_ARGS=2
E_BADARGS=65

if [ $# -ne $EXPECTED_ARGS ]
then
  echo "Usage: `basename $0` newsitename.com basesitename.com"
  exit $E_BADARGS
fi


cd /var/www/html/
cp -r sites/_template sites/$1
ln -s $1 sites/$2.$1
ln -s . $1
chown -R www-data.www-data /var/www/html/sites/$1




[B][U]CVS/SVN Info

To update, 

BACK UP YOUR DATABASE[/U][/B], then

from /var/www/html

type:

cvs update

then, run update.php by going to [http://[yoursitename]/update.php](http://[yoursitename]/update.php)

 

if everything works out ok, from /var/www/html

type:

svn commit

 

if everything doesn't work out ok,

check your logs, try to figure out what went wrong (detail forthcoming when I move some sites around in a little bit) , then if need be:

restore your database backup

and, from /var/www/html , type:

svn revert

---

### Post by bioborg on 2009-03-01
And, if you just want to use the instructions from the drupal site, and install from a tarball, be sure to execute these commands (taken from that script) first:

sudo apt-get update && sudo apt-get -y upgrade
sudo apt-get -y install apache2 php5 mysql-server php5-mysql php5-gd sendmail vim
sudo a2enmod rewrite
sudo /etc/init.d/apache2 force-reload

That will get you clean URLs and your gd libraries installed correctly.  And vim (vi annoys me, you can leave that part off if you use a different command-line text editor)

---

### Post by Thirtysixway on 2009-03-01
You can also check out turnkey linux

[http://www.turnkeylinux.org/appliances/drupal5](http://www.turnkeylinux.org/appliances/drupal5)

---

### Post by bioborg on 2009-03-01
Noticing that Turnkey linux installed its drupal from apt, makes me realize that's another, possibly easiest, way to do it:

sudo aptitude install apache2 php5 mysql-server php5-mysql php5-gd drupal5 sendmail
(one could probably use another MTA besides sendmail, I just haven't.  I am about to read this: [http://www.howtoforge.com/drupal-plus-postfix-integration-under-ubuntu-8.04](http://www.howtoforge.com/drupal-plus-postfix-integration-under-ubuntu-8.04)
it looks promising)

should do the job...
along with the 
a2enmod rewrite 
and 
/etc/init.d/apache2 force-reload

set up the database with 
mysql -uroot -p
CREATE DATABASE database_name;
GRANT ALL ON database_name.* TO database_user@localhost IDENTIFIED BY 'dbpasswd';
exit

then run the install script in the web browser 
Would have you running drupal in the shortest amount of time...

---

### Post by cybershan on 2009-09-25
I followed this thread to install my Drupal6,  I got this error:

###

Warning: fopen(./sites/default/settings.php) [function.fopen]: failed to open stream: Operation not permitted in /var/www/drupal613/includes/install.inc on line 236

Warning: Cannot modify header information - headers already sent by (output started at /var/www/drupal613/includes/install.inc:236) in /var/www/drupal613/includes/install.inc on line 618

Warning: Cannot modify header information - headers already sent by (output started at /var/www/drupal613/includes/install.inc:236) in /var/www/drupal613/includes/install.inc on line 619

###


Can anybody help out?

---

