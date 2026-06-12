---
title: "How to install NextCloud 12 on Ubuntu Server 16.04 LTS"
date: 2018-01-13
forum: Tutorials
---

### Post by LHammonds on 2018-01-13
Greetings and salutations,

I hope this thread will be helpful to those who follow in my foot steps as well as getting any advice based on what I have done / documented.

Link to original post: [HammondsLegacy Forums]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=239&p=568") (best when viewed at original location due to custom formatting)

[SIZE=4]High-level overview[/SIZE]

NextCloud is a web application that can store and serve content from a centralized location, much like Dropbox. The difference is that NextCloud allows you to host the serving software on your own machines, taking the trust issues out of putting your personal data someone else's server.
 
This tutorial will cover how to manually setup an NextCloud server which will use a separate dedicated database server and SSL encryption.

Advantages of manually installing NextCloud:

[LIST]
[*]Can use the latest version of NextCloud currently available (Repository rarely contains latest version) 
[*]Are not forced to install MySQL locally (handy if you have a dedicated database server) 
[*]Can install where you want (such as standard / well-known locations) 
[/LIST]

Disadvantages of manually installing NextCloud:

[LIST]
[*]Will not automatically update the system via "apt-get update" (although you are not guaranteed you get the latest this way either...just the latest in the repository) 
[*]Not as easy to install (thus this step-by-step guide) 
[/LIST]

The server will be installed inside a virtual machine in vSphere running on ESXi servers. Notes will also be supplied for doing the same thing for VirtualBox on a Windows 10 PC.  Although there are some VMware-specific and VirtualBox-specific steps, they are very few and the majority of this documentation will work for other Virtual Machines or even directly installed onto a physical machine (e.g. bare-metal install). If you have any advice on doing things better, please let me know by replying to the Ubuntu forums thread above.
 
[SIZE=4]Tools utilized in this process[/SIZE]

[LIST]
[*][Ubuntu Server]("http://www.ubuntu.com/download/ubuntu/download") 16.04 LTS, 64-bit 
[*][NextClould]("https://nextcloud.com/install/") 12.0.4 
[*][Portable PuTTY]("http://portableapps.com/apps/internet/putty_portable") 0.70 
[*][VMware vSphere]("http://www.vmware.com/products/vsphere/overview.html") 6.0.0 
[*][VirtualBox]("http://www.virtualbox.org/") 5.1.30 
[/LIST]

[SIZE=4]Helpful links[/SIZE]

The list below are sources of information that was helpful in the creation of this document.

[LIST]
[*][Ubuntu Documentation]("https://help.ubuntu.com") 
[*][Ubuntu Firewall Basics]("https://help.ubuntu.com/community/IptablesHowTo#Disabling%20the%20firewall") 
[*][Ubuntu AppArmor Basics]("https://help.ubuntu.com/community/AppArmor#Disable%20AppArmor%20framework") 
[*][NextCloud Server Documentation]("https://docs.nextcloud.com/server/12/admin_manual/") 
[/LIST]

[SIZE=4]Assumptions[/SIZE]
 
This documentation will need to make use of some very-specific information that will most-likely be different for each person / location. And as such, this information will be noted in this section. They will be highlighted in red throughout the document as a reminder that you should plug-in your own value rather than actually using these "place-holder" values.

Under no circumstance should you use the actual values listed below. They are place-holders for the real thing. This is just a checklist template you need to have answered before you start the install process.

The [COLOR=red]RED[/COLOR] below are the values you need to substitute throughout this tutorial for use in your environment.

[LIST]
[*]Internet domain: [COLOR=red]nextcloud.mydomain.com[/COLOR] 
[*]Ubuntu Server name: [COLOR=red]srv-nextcloud[/COLOR] 
[*]Ubuntu Server IP address: [COLOR=red]192.168.107.9[/COLOR] 
[*]Ubuntu Admin ID: [COLOR=red]administrator[/COLOR] 
[*]Ubuntu Admin Password: [COLOR=red]myadminpass[/COLOR] 
[*]Database Server Name (remote): [COLOR=red]srv-mysql[/COLOR] 
[*]Database Server IP (remote): [COLOR=red]192.168.107.20[/COLOR] 
[*]Database Admin ID: [COLOR=red]root[/COLOR] 
[*]Database Admin Password: [COLOR=red]rootpass[/COLOR] 
[*]Database ID: [COLOR=red]nextclouduser[/COLOR] 
[*]Database Password: [COLOR=red]nextclouduserpass[/COLOR] 
[*]Email Server Name (remote): [COLOR=red]srv-mail[/COLOR] 
[*]Email Server IP (remote): [COLOR=red]192.168.107.25[/COLOR] 
[*]NextCloud Admin ID: [COLOR=red]NextCloudAdmin[/COLOR] 
[*]NextCloud Admin Password: [COLOR=red]nextcloudadminpass[/COLOR] 
[/LIST]

NextCloud Ubuntu Server - Setup an Ubuntu server for use as the NextCloud server.  This tutorial assumes the server was configured according to this tutorial: [How to install and configure Ubuntu Server]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=220")

MySQL/MariaDB server - Setup a separate and dedicated database server.  This tutorial assumes the server was configured according to this tutorial: [How to install and configure MariaDB]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=225")

It is also assumed the reader knows how to use the VI editor. If not, you will need to [beef up your skill set]("http://www.washington.edu/computing/unix/vi.html") or use a different editor in place of it.

---

### Post by LHammonds on 2018-01-13
[SIZE=4]Name Resolution[/SIZE]

Add your NextCloud domain(s) so they point to the local loopback (127.0.0.1)
Add your other remote servers such as your mail and database server IPs so you can reference them by name.

```
vi /etc/hosts
```
```

127.0.0.1       localhost
127.0.1.1       srv-nextcloud
127.0.0.1    nextcloud.mydomain.com
192.168.107.25  srv-mail
192.168.107.20  srv-mysql

```

[SIZE=4]Prerequisites[/SIZE]

Install Apache web server:
```
apt-get -y install apache2
```

Install PHP for Apache with MySQL/MariaDB support
```
apt-get -y install php7.0 libapache2-mod-php7.0 php7.0-mysql
```

TIP: You can search available PHP packages names by typing this:
```
apt-cache search php7.0
```

TIP: You can see which PHP modules are installed by typing this:
```
php -m
```

There are various required, recommended, app-specific modules listed on the requirements section of the manual.

The below will show what is already installed by default and what will be needed as a complete list.  You can customize to your needs.

PHP modules:
```

bz2
ctype
curl - Missing (contained in php7.0-curl)
dom - Missing (contained in php7.0-xml)
exif
fileinfo
ftp
gd - Missing (contained in php7.0-gd)
iconv
imagick - Missing (contained in php-imagick)
intl - Missing (contained in php7.0-intl)
gmp - Missing (contained in php7.0-gmp)
json
libxml
mbstring - Missing (contained in php7.0-mbstring)
mcrypt - Missing (contained in php7.0-mcrypt)
openssl
pdo_mysql
posix
simplexml - Missing (contained in php7.0-xml)
smbclient - Missing (contained in php-smbclient)
xmlreader - Missing (contained in php7.0-xml)
xmlwriter - Missing (contained in php7.0-xml)
zip - Missing (contained in php7.0-zip)
zlib

```

Install the missing PHP modules with these packages:
```

apt-get -y install php7.0-gd php7.0-zip php7.0-xml php7.0-mbstring php7.0-curl php7.0-intl php7.0-mcrypt php7.0-gmp php-imagick php-smbclient

```

NOTE: Need to research how to install / configure / enable LibreOffice and video previews.

Enable various options in Apache:
```

a2enmod rewrite
a2enmod headers
a2enmod env (probably already enabled)
a2enmod dir (probably already enabled)
a2enmod mime (probably already enabled)

```

Modify PHP to allow uploading of larger files and correct OPcache settings.  In the below example, it allows 2GB uploads.  

```
vi /etc/php/7.0/apache2/php.ini
```
```

default_charset = "UTF-8"
post_max_size = 2058M
upload_max_filesize = 2048M
opcache.enable=1
opcache.enable_cli=1
opcache.memory_consumption=128
opcache.interned_strings_buffer=8
opcache.max_accelerated_files=10000
opcache.revalidate_freq=1
opcache.save_comments=1

```

Reload Apache for changes to the config to take affect:
```
service apache2 reload
```

[SIZE=4]PHP Information[/SIZE]

To verify Apache, PHP and modules are installed and enabled, lets create the famous phpinfo page.
```
touch /var/www/html/phpinfo.php
chown www-data:www-data /var/www/html/phpinfo.php
chmod 0644 /var/www/html/phpinfo.php
echo "<?php phpinfo(); ?>" >> /var/www/html/phpinfo.php

```

Open a browser and load up the phpinfo page: [http://192.168.107.9/phpinfo.php](http://192.168.107.9/phpinfo.php)

You should be able to scroll down and see sections for each module we wanted enabled.  If you don't see a dedicated section, then that module is not installed/enabled.

When done, do not forget to remove the info file:
```
rm /var/www/html/phpinfo.php
```

---

### Post by LHammonds on 2018-01-13
[SIZE=4]Database Configuration[/SIZE]

```
mysql -u root -p
Enter password: rootpass
```

At the mysql> prompt, enter these commands:
```
CREATE DATABASE nextcloud CHARACTER SET utf8 COLLATE utf8_bin;
CREATE USER 'nextclouduser'@'%' IDENTIFIED BY 'nextclouduserpass';
GRANT ALL ON nextcloud.* TO 'nextclouduser'@'%';
FLUSH PRIVILEGES;
exit
```

NOTE: The above will allow the user to connect from any machine.  You can limit it by specifying your NextCloud server but the database server needs to recognize the server name (via hosts file):

```
CREATE USER 'nextclouduser'@'srv-nextcloud' IDENTIFIED BY 'nextclouduserpass';
GRANT ALL ON nextcloud.* TO 'nextclouduser'@'srv-nextcloud';
```
or
```
CREATE USER 'nextclouduser'@'192.168.107.9' IDENTIFIED BY 'nextclouduserpass';
GRANT ALL ON nextcloud.* TO 'nextclouduser'@'192.168.107.9';
```

NOTE: If you are using a local database (on the same machine), create the user like this:
```
CREATE USER 'nextclouduser'@'localhost' IDENTIFIED BY 'nextclouduserpass';
GRANT ALL ON nextcloud.* TO 'nextclouduser'@'localhost';
```

If you mess anything up, you can remove the database and user by issuing these commands:
```
DROP USER nextclouduser;
FLUSH PRIVILEGES;
DROP DATABASE nextcloud;
```

To avoid the "impossible to write to binary log since BINLOG_FORMAT = STATEMENT" error message when accessing the NextCloud page the 1st time which creates the database tables/data, you need to edit the "my.cnf" on the MySQL/MariaDB server to include the following setting:
```
binlog-format=MIXED
```
Then restart the database service:
```
service mysql restart
```

---

### Post by LHammonds on 2018-01-13
[SIZE=4]NextCloud[/SIZE]

We are installing manually instead of using the package manager for the following reasons:

[LIST]
[*]Can obtain the newer version straight from NextCloud's website 
[*]Don't want MySQL installed on the same server since I have a dedicate DB server (and also would rather use MariaDB) 
[*]Want to use my own paths rather than the path Ubuntu uses which is different than everyone else.
[/LIST]
 
Multiple web sites - This documentation assumes NextCloud will be an additional web site running on this server and as such will configure its own .conf files and manage each site separately.

```
cd /tmp
wget https://download.nextcloud.com/server/releases/nextcloud-12.0.4.zip.md5
wget https://download.nextcloud.com/server/releases/nextcloud-12.0.4.zip
```

Verify the file integrity of the download.  Compare both numbers and insure they are identical:

```
md5sum /tmp/nextcloud-12.0.4.zip
d29aa3fd0a57bcc6fbf2af5a21d70c47  /tmp/nextcloud-12.0.4.zip

cat /tmp/nextcloud-12.0.4.zip.md5
d29aa3fd0a57bcc6fbf2af5a21d70c47  nextcloud-12.0.4.zip
```

Extract the archive:
```
cd /tmp
unzip /tmp/nextcloud-12.0.4.zip
chown www-data:www-data -R /tmp/nextcloud/
mv /tmp/nextcloud /var/www/nextcloud
rm /tmp/nextcloud*.zip
rm /tmp/nextcloud*.md5

```

Create the data repository location.  It is recommended to keep this "Data" folder from being anywhere inside the web root folder to ensure users cannot simply browse it.

```

mkdir -p /var/www/nextcloud-data
chown www-data:www-data -R /var/www/nextcloud-data

```

Install NextCloud (create database)
```

cd /var/www/nextcloud/
sudo -u www-data php occ  maintenance:install --database "mysql" --database-host="srv-mysql" --database-name "nextcloud" --database-table-prefix "nc_" --database-user "nextclouduser" --database-pass "nextclouduserpass" --data-dir "/var/www/nextcloud-data" --admin-user "nextcloudadmin" --admin-pass "nextcloudadminpass"

```

[SIZE=4]NextCloud Configuration File[/SIZE]

Make sure your config looks similar to this but substituting your actual values and adding any missing lines:

```
vi /var/www/nextcloud/config/config.php
```

```

<?php
$CONFIG = array (
  'instanceid' => 'ocndnnro5l72',
  'passwordsalt' => 'bhiABCw6D7Ed3IF+mHpIzJF06vKLMN',
  'secret' => 'abcdefghijklmnopqrstuvwxyz123456790',
  'trusted_domains' =>
  array (
    0 => 'nextcloud.mydomain.com',
    1 => '192.168.107.10',
    2 => 'localhost',
  ),
  'datadirectory' => '/var/www/nextcloud-data',
  'overwrite.cli.url' => 'http://nextcloud.mydomain.com',
  'htaccess.RewriteBase' => '/',
  'dbtype' => 'mysql',
  'version' => '12.0.4.3',
  'dbname' => 'nextcloud',
  'dbhost' => 'srv-mysql',
  'dbport' => '',
  'dbtableprefix' => 'nc_',
  'dbuser' => 'nextclouduser',
  'dbpassword' => 'nextclouduserpass!',
  'auth.bruteforce.protection.enabled' => true,
  'installed' => true,
);

```

[SIZE=4]Create Apache Config for NextCloud[/SIZE]

```
vi /etc/apache2/sites-available/nextcloud.conf
```

```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName nextcloud.mydomain.com
        DocumentRoot /var/www/nextcloud
        ErrorLog ${APACHE_LOG_DIR}/nc-error.log
        CustomLog ${APACHE_LOG_DIR}/nc-access.log combined
        <Directory /var/www/nextcloud/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
                <IfModule mod_dav.c>
                  Dav off
                 </IfModule>
                SetEnv HOME /var/www/nextcloud
                SetEnv HTTP_HOME /var/www/nextcloud
        </Directory>
</VirtualHost>

```

Enable the site configuration:
```
a2ensite nextcloud
```

If you need to disable the site in the future:

```
a2dissite nextcloud
```

Reload the Apache config so it is aware of the modified virtual host
```
service apache2 reload
```

[SIZE=4]NextCloud Login[/SIZE]

Now, go to your IP address or domain name in your browser:
Example: [http://[COLOR=red]192.168.107.9[/COLOR]/]("http://192.168.107.9/") or [http://[COLOR=red]nextcloud.mydomain.com[/COLOR]/]("http://nextcloud.mydomain.com/")
Make sure you can login with your admin account.

---

### Post by LHammonds on 2018-01-13
[SIZE=4]Directory Security[/SIZE]

During install, you should have set the user/group ownership to match your web server (www-data for Apache on Ubuntu).

These are the default permissions for your NextCloud directories and files:

[LIST]
[*]All files should be read-write for the file owner, read-only for the group owner, and zero for the world (640) 
[*]All directories should be executable (because directories always need the executable bit set), read-write for the directory owner, and read-only for the group owner (750) 
[*]The .htaccess files are read-write for the file owner, read-only group and world (644) 
[*]The .htaccess files should be owned by root:www-data 
[/LIST]

Let's create the script that will enforce the recommended permissions/ownership.
```
mkdir -p /var/scripts
touch /var/scripts/nextcloud-secure.sh
chown root:root /var/scripts/nextcloud-secure.sh
chmod 0755 /var/scripts/nextcloud-secure.sh
vi /var/scripts/nextcloud-secure.sh
```

```

#!/bin/bash
## Name: nextcloud-secure.sh
## Compatibility: Tested on Ubuntu Server 16.04 for NextCloud 12.0.4
## Purpose: Ensures ownership and permissions are tightly set.
## NOTE: These settings will prevent the updater from working.
## The only thing needed to change in order for the updater to
## work is to change the rootuser to be the same as htuser.
ncwww='/var/www/nextcloud'
ncdata='/var/nextcloud-data'
htuser='www-data'
rootuser='root'
echo "Making folders if they are missing..."
if [ ! -d ${ncwww}/apps ]; then
  mkdir -p ${ncwww}/apps
fi
if [ ! -d ${ncwww}/config ]; then
  mkdir -p ${ncwww}/config
fi
if [ ! -d ${ncwww}/themes ]; then
  mkdir -p ${ncwww}/themes
fi
if [ ! -d ${ncdata} ]; then
  mkdir -p ${ncdata}
fi
echo "Setting Ownership..."
chown -R ${rootuser}:${htuser} ${ncwww}/
chown -R ${htuser}:${htuser} ${ncwww}/apps/
chown -R ${htuser}:${htuser} ${ncwww}/config/
chown -R ${htuser}:${htuser} ${ncwww}/themes/
find ${ncwww} -name .htaccess -exec chown ${rootuser}:${htuser} {} \;
chown ${rootuser}:${htuser} ${ncdata}/.htaccess
echo "Setting Folder Permissions..."
find ${ncwww}/ -type d -print0 | xargs -0 chmod 0750
find ${ncdata}/ -type d -print0 | xargs -0 chmod 0750
echo "Setting File Permissions..."
find ${ncwww}/ -type f -print0 | xargs -0 chmod 0640
find ${ncdata}/ -type f -print0 | xargs -0 chmod 0640
find ${ncwww}/ -name .htaccess | xargs -0 chmod 0644
chmod 0644 ${ncdata}/.htaccess
echo "Permission change complete."

```

Now just run the script
```
/var/scripts/nextcloud-secure.sh
```
You can also schedule the script via crontab to run on a regular basis to make sure the permissions never stay out of whack for long.

If you want to enable the updater to work, simply change the value of "rootuser" from "root" to "www-data"

[SIZE=4]Configure for secure (SSL) access[/SIZE]

This will create a self-signed certificate that will expire 1,095 days (3 years) from the date it was created.  Web browsers will balk about it being untrusted.   It will still work but end-users will have to allow this exception unless you pay > $200 for an official SSL certificate issued by a trusted/known authority.
```
a2enmod ssl
mkdir -p /etc/apache2/ssl/certs
mkdir -p /etc/apache2/ssl/private
openssl req -x509 -nodes -days 1095 -newkey rsa:2048 -keyout /etc/apache2/ssl/private/nextcloud.key -out /etc/apache2/ssl/certs/nextcloud.crt
  Country Name: US
  State: MyState
  Locality Name: MyCity
  Organication Name: MyCompany
  Organizational Unit Name: MyDepartment
  Common Name: nextcloud.mycompany.com
  Email Address: webmaster@mycompany.com
```

Create the SSL config
```
vi /etc/apache2/sites-available/nextcloud-ssl.conf
```
Set these values:

```

<IfModule mod_ssl.c>
        <VirtualHost _default_:443>
                ServerName nextcloud.mydomain.com:443
                ServerAdmin webmaster@localhost
                DocumentRoot /var/www/nextcloud
                ErrorLog ${APACHE_LOG_DIR}/nc-error.log
                CustomLog ${APACHE_LOG_DIR}/nc-access.log combined
                SSLEngine on
                SSLCertificateFile /etc/apache2/ssl/certs/nextcloud.crt
                SSLCertificateKeyFile /etc/apache2/ssl/private/nextcloud.key
                <FilesMatch "\.(cgi|shtml|phtml|php)$">
                                SSLOptions +StdEnvVars
                </FilesMatch>
                <Directory /usr/lib/cgi-bin>
                                SSLOptions +StdEnvVars
                </Directory>
                <IfModule mod_headers.c>
                                Header always set Strict-Transport-Security "max-age=15768000; includeSubDomains; preload"
                </IfModule>
                BrowserMatch "MSIE [2-6]" \
                                nokeepalive ssl-unclean-shutdown \
                                downgrade-1.0 force-response-1.0
                BrowserMatch "MSIE [17-9]" ssl-unclean-shutdown
        </VirtualHost>
</IfModule>

```

Now we need to enable the SSL site configuration:
```
a2ensite nextcloud-ssl
service apache2 reload
```

[SIZE=4]Force users to use SSL for enhanced security[/SIZE]

```
a2enmod rewrite
```

```
vi /etc/apache2/sites-available/nextcloud.conf
```
```

<VirtualHost *:80>
        #### Redirect to port 443 ###
        RewriteEngine on
        ReWriteCond %{SERVER_PORT} !^443$
        RewriteRule ^/(.*) https://%{HTTP_HOST}/$1 [NC,R,L]
        #### End of Redirection configuration ###

        ServerAdmin webmaster@localhost
        ServerName nextcloud.mydomain.com
        DocumentRoot /var/www/nextcloud
        ErrorLog ${APACHE_LOG_DIR}/nc-error.log
        CustomLog ${APACHE_LOG_DIR}/nc-access.log combined
        <Directory /var/www/nextcloud/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
                <IfModule mod_dav.c>
                  Dav off
                 </IfModule>
                SetEnv HOME /var/www/nextcloud
                SetEnv HTTP_HOME /var/www/nextcloud
        </Directory>
</VirtualHost>

```
Reload the updated configuration for Apache:
```
service apache2 reload
```

[SIZE=4]Configure NextCloud Settings[/SIZE]

Now, go to your IP address or domain name in your browser:
Example: [http://[COLOR=red]192.168.107.9[/COLOR]/]("http://192.168.107.9/") or [http://[COLOR=red]nextcloud.mydomain.com[/COLOR]/]("http://nextcloud.mydomain.com/")

It should automatically re-direct to https:// for secured SSL connection.

Login with your admin account and click the gear icon on top-right side, then click Admin

When the configuration check is complete, it should say "No problems found" if you did everything right (e.g. using SSL, .htaccess, etc.)

Email Server - Setup your mail sending capability here (choices vary depending on your mail server):
```
Send mode: smtp
  Encryption: SSL
  From address: nextcloud@mydomain.com
  Authentication method: Login
  Check: Authentication required
  Server address: mail.mydomain.com : 25
  Credentials: smtpuser
  Password: smtppassword
```

On top-right side, click on the gear icon, then +Apps and then find and enable the following:


[LIST]
[*]Office and Text -> Calendar 
[*]Office and Text -> Contacts
[/LIST]
 
[SIZE=4]Add Users[/SIZE]

While logged in with your admin user, click gear icon on top-right side and then Users
Click the "gear" icon on the lower-left corner to display settings.
Note the default space quota is set to Unlimited. You can configure the default here.
It would also be a good idea to place checkmarks beside "Send email to new user" and "Show email address"
In the empty "Username" "Password" and "Email" fields, add a user account and click "Create"
Repeat for each user you want added.

NextCloud comes with one default group: admin.  When you create users, they will not belong to any group.  If you need to create other groups, click the "+ Add group" link on the top-left and type in a name.

You can assign space limitations by setting the quota for each individual or just let it use the system-wide default quota.

[SIZE=4]Configure New User Folder Skeleton[/SIZE]

When a new user is created, the following folder/files are copied to the new user's folder:

/var/www/nextcloud/core/skeleton/*

You can remove the example files and/or create new folders/files so it looks a certain way when a new person logs in.

[SIZE=4]Install New Apps[/SIZE]

You can install other apps not listed with the default installation.
Visit this site: [https://apps.nextcloud.com/?xsortmode=high](https://apps.nextcloud.com/?xsortmode=high)

---

### Post by LHammonds on 2018-01-13
[SIZE=4]Upgrades[/SIZE]

Do not skip the major releases when upgrading.  So going from 9.0.54 to 12.0.4 means you need to upgrade in this order:

9.0.54 -> [9.0.58]("https://download.nextcloud.com/server/releases/nextcloud-9.0.58.zip") (Upgrade to the latest minor release of the current major version you are on)
9.0.58 -> [10.0.6]("https://download.nextcloud.com/server/releases/nextcloud-10.0.6.zip") (Upgrade to the latest next major release)
10.0.6 -> [11.0.6]("https://download.nextcloud.com/server/releases/nextcloud-11.0.6.zip") (Upgrade to the latest next major release)
11.0.6 -> [12.0.4]("https://download.nextcloud.com/server/releases/nextcloud-12.0.4.zip") (Upgrade to the latest next major release)

General steps of the upgrade are as follows:

[LIST=1]
[*]Disable any 3rd-party applications 
[*]Place system into maintenance mode.
```
cd /var/www/nextcloud
sudo -u www-data php occ maintenance:mode --on
```
or
```
vi /var/www/nextcloud/config/config.php
```
```
'maintenance' => true,
``` 
[*]Backup the NextCloud site (and uploads)
```
tar -czf /tmp/html-before.tar.gz /var/www/nextcloud
``` 
[*]Backup the database
```
mysql --databases nextcloud > /tmp/nextcloud-before.sql
``` 
[*]Download next release to install and extract into a temp folder
```

cd /tmp
wget *** INSERT URL HERE ***
unzip /tmp/nextcloud*.zip
rm /tmp/nextcloud*.zip
``` 
[*]Stop web server
```
service apache2 stop
``` 
[*]Push the folders around such as the following:
```
mv /var/www/nextcloud /var/www/nextcloud.old
mv /tmp/nextcloud /var/www/nextcloud
cp /var/www/nextcloud.old/config/config.php /var/www/nextcloud/config/.
mv /var/www/nextcloud.old/data /var/www/nextcloud/.
```
NOTE: If you have a custom theme, be sure to move it too.  Example:
```
mv /var/www/nextcloud.old/themes/mytheme /var/www/nextcloud/themes/.
``` 
[*]Start web server
```
service apache2 start
``` 
[*]Run the upgrade script:
```
cd /var/www/nextcloud
sudo -u www-data php occ upgrade
``` 
[*]Turn off maintenance mode.
```
sudo -u www-data php occ maintenance:mode --off
```
or
```
vi /var/www/nextcloud/config/config.php
```
```
'maintenance' => false,
``` 
[*]If the upgrade was successful, verify by logging into the site as admin an verify the version number. 
[*]Re-enable the 3rd party applications 
[*]Re-run the script to correct ownership and permissions.
```
/var/scripts/nextcloud-secure.sh
``` 
[*]Remove old code:
```
rm -rf /var/www/nextcloud.old
``` 
[*]Backup the NextCloud site (and uploads)
```
tar -czf /tmp/html-after.tar.gz /var/www/nextcloud
``` 
[*]Backup the database
```
mysql --databases nextcloud > /tmp/nextcloud-after.sql
``` 
[/LIST]

---

### Post by LHammonds on 2018-01-13
[SIZE=4]External Storage[/SIZE]

These are the steps to enable and configure external storage to mount an existing share on another server...Windows 2012 in this case.

Step #1 Gather Share Information

[LIST=1]
[*]Make sure you have valid connection information such as the following: 
[*]IP Address of the server hosting the share.  Example: [COLOR=red]192.168.107.55[/COLOR] 
[*]Exact spelling of the share.  Example: [COLOR=red]Share[/COLOR] 
[*]UserID that has access to the share.  Example: [COLOR=red]MyDomain\JDoe[/COLOR] 
[*]Password for the UserID.  Example: [COLOR=red]abcd123![/COLOR] 
[/LIST]

Step #2 Enable External Storage support

[LIST=1]
[*]Login to your NextCloud web interface with an administrator account 
[*]On the top-right corner, click the gear icon -> +Apps -> Not enabled 
[*]Find "External storage support" and click the Enable button 
[*]Click the Enabled section on the left to show all enabled plugins and make sure you see External storage support. 
[/LIST]

Step #3 - Configure NextCloud to utilize the external storage

[LIST=1]
[*]On the top-right corner, click the gear icon -> Admin -> External Storages 
[*]Type in a folder name that will show up in the user's account.  Example: [COLOR=red]Policies[/COLOR] 
[*]Click the "Add storage" drop-down beside it and select "SMB/CIFS" 
[*]Fill out the Host, Share, Username and Password. 
[*]In the "Available for" section to the right, add the NextCloud users/groups that will get this link. 
[*]WARNING: Be careful adding it to anyone that syncs their account to their PC because they will immediately start sync'ing this new location. 
[/LIST]

---

### Post by LHammonds on 2018-01-13
[SIZE=4]Fail2Ban[/SIZE]

If you have Fail2Ban installed and protecting SSH as part of the base install.  You can add these few changes to also watch for NextCloud login failures.

NextCloud as a basic brute force denial system but this one is much, much better and configurable to your needs.

If you use fail2ban option, be sure to edit NextCloud's config.php file and set auth.bruteforce.protection.enabled to false

```
vi /etc/fail2ban/filter.d/nextcloud.conf
```

```

## Author: LHammonds
## Date:   2017-01-11

[INCLUDES]

before = common.conf

[Definition]

## NextCloud 12.0.4
failregex=Login failed.*Remote IP.*'<HOST>'

ignoreregex =

```

```
vi /etc/fail2ban/jail.local
```

Add the following to the bottom.  If your data path is different, be sure to update "logpath"

```

[nextcloud]
enabled = true
filter  = nextcloud
# select http, https or both, depending on which you use:
port    =  http,https
# edit the logpath to your needs:
logpath = /var/www/nextcloud-data/nextcloud.log
## "bantime" is the number of seconds that a host is banned.
##  300 =  5 minutes
##  600 = 10 minutes
##  900 = 15 minutes
## 1800 = 30 minutes
## 3600 = 60 minutes
bantime = 1800
## "findtime" is the length of time between login attempts before a ban is set.
findtime = 600
## "maxretry" is how many attempts can be made to access the server from a single IP before a ban is imposed.
maxretry = 7

```

---

### Post by LHammonds on 2018-01-15
[SIZE=4]How to Install NextCloud Client[/SIZE]

Reference: [User Manual]("https://docs.nextcloud.com/server/12/user_manual/")

[SIZE=4]Client Installation[/SIZE]

[LIST=1]
[*]Visit [NextCloud]("https://nextcloud.com/install/") and download the Desktop Client that matches your operating system (e.g. Windows) 
[*]Install the client you just downloaded using the default settings 
[/LIST]

[SIZE=4]Account Configuration[/SIZE]

[LIST=1]
[*]Add Account 
[*]Address: [https://[COLOR=red]nextcloud.mydomain.com[/COLOR]]("https://<font color=&quot;red&quot;>nextcloud.mydomain.com</font>") 
[*]Untrusted Certificate - Click "Trust this certificate anyway" and click **OK** 
[*]Credentials - Type in your ID and password and click **Next** 
[*]Local folder options - Pick a folder on your PC to synchronize to the server and click **Connect** 
[*]Everything Setup - Click **Finish** 
[/LIST]

NOTE #1: It says Untrusted Certificate because we use a self-signed certificate during installation which is perfectly OK. If we needed to purchase an SSL certificate from Verisign, we would need to pay hundreds of dollars every couple of years to keep that warning message from displaying which is not that important.

NOTE #2: You might need to specify which folders in your account to sync if you can also access network shares (you do not want to sync the entire network file server to your PC)

[SIZE=4]Migration from ownCloud[/SIZE]

This information was documented with the following:

[LIST]
[*]ownCloud Desktop app version 2.4.0 
[*]Windows 10 
[*]NextCloud Desktop app version 2.3.3 
[/LIST]

[SIZE=4]Migration Option #1 - Re-use old configuration[/SIZE]

If you are unsure of the settings or are doing this for somebody else, you can just copy over the configuration and you do not have to worry about missing anything. This is the safest option to pick.

[LIST=1]
[*]Right-click on the ownCloud icon in taskbar, select **Quit ownCloud** 
[*]Open Control Panel, Programs and Features, uninstall ownCloud 
[*]Close Control Panel 
[*]Open a browser and login to [https://[COLOR=red]nextcloud.mydomain.com[/COLOR]]("https://<font color=&quot;red&quot;>nextcloud.mydomain.com</font>") 
[*]In the top-right corner, click the gear icon and select **Personal** 
[*]Under the Get the apps to sync your files click **Desktop app** 
[*]Click **Windows 7,8.x and 10** to download **Nextcloud-2.3.3.1-setup.exe** 
[*]Install NextCloud 
[*]Start NextCloud client but close it once the wizard asks for the Server Address 
[*]Right-click on the NextCloud icon in taskbar, select **Quit NextCloud** 
[*]Click Start, Run (or Search if Run is not visible), type %localappdata% and press **ENTER** 
[*]Edit ownCloud\owncloud.cfg and select all the contents (**CTRL+A**) and copy (**CTRL+C**) 
[*]Close owncloud.cfg 
[*]Edit NextCloud\nextcloud.cfg and select all the contents (**CTRL+A**) and paste (**CTRL+V**) to overwrite all the data 
[*]Save and close nextcloud.cfg 
[*]Start NextCloud client 
[*]Enter your password and the client should start without having to re-sync any files. 
[/LIST]

[SIZE=4]Migration Option #2 - Re-key configuration[/SIZE]

If you are confident in knowing all your settings, you can just re-configure the new client like the old client. This can be considered the riskier option.

[LIST=1]
[*]Right-click on the ownCloud icon in taskbar, select Quit ownCloud 
[*]Open Control Panel, Programs and Features, uninstall ownCloud 
[*]Close Control Panel 
[*]Follow the steps above in the Client Installation and Account Configuration sections. 
[/LIST]

[SIZE=4]Video Tutorials[/SIZE]

NOTE: NextCloud is just a new version of ownCloud so information about ownCloud applies.

[LIST]
[*][ownCloud Demonstration]("https://www.youtube.com/watch?v=l0oa_YtVLOc") 
[*][Introduction to ownCloud 8.1]("https://www.youtube.com/watch?v=RrAhClhrRAc") 
[*][Creating a public upload folder]("https://www.youtube.com/watch?v=3GSppxEhmZY") 
[*][Multi-user Document Editing]("https://www.youtube.com/watch?v=597gjnBB2JM") 
[*][Sorting Files]("https://www.youtube.com/watch?v=qXWZs07Y7jU") 
[*][Managing Users in ownCloud 8.1]("https://www.youtube.com/watch?v=teelHVdXD4k") 
[/LIST]

---

### Post by moboatgva on 2018-01-29
Thanks for all your amazing tutorials, I´m following them since a long time !

Can you plan to create an tutorial using Let´s Encrypt and certbot as SSL solution (letsencrypt.org and certbot.eff.org) ?
This will solve the [COLOR=#000000]self-signed certificate[/COLOR] limitation for not cost!

Thanks

---

### Post by LHammonds on 2018-01-29
> **moboatgva said:**
> Can you plan to create an tutorial using Let´s Encrypt and certbot as SSL solution (letsencrypt.org and certbot.eff.org) ?
Looks interesting.  I'll give it a try on my next SSL project.  If it works out and isn't a security issue, I'll update my dox with it.

Thanks,
LHammonds

---

