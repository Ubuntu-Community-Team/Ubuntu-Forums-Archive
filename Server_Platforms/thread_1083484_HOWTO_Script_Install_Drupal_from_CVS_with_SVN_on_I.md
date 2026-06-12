---
title: "HOWTO Script: Install Drupal from CVS with SVN on Intrepid (or Hardy)"
date: 2009-03-01
forum: Server Platforms
---

### Post by bioborg on 2009-03-01
This was done on EC2.
Taken from [http://groups.google.com/group/ec2drupal/web/wiki](http://groups.google.com/group/ec2drupal/web/wiki)
It works.  The bash scripting could be done in a more elegant way.  Feel free to share how.


```

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

```


Includes script to set up multisite instance: 

This should be able to be incorporated into a drupal module


```
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
```



CVS/SVN Info

To update, 

BACK UP YOUR DATABASE, then

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

### Post by jpeddicord on 2009-03-02
Moved to Server Platforms from Tutorials & Tips as it is an automated script. Looks nice, but to qualify as a tutorial you need to instruct a user how to do something, not do it for them. :)

---

