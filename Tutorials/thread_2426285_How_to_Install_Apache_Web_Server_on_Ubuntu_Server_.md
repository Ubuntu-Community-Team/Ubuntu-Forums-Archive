---
title: "How to Install Apache Web Server on Ubuntu Server 18.04 LTS"
date: 2019-09-06
forum: Tutorials
---

### Post by LHammonds on 2019-09-06
Greetings and salutations,

I hope this thread will be helpful to those who follow in my foot steps as well as getting any advice based on what I have done / documented.

Link to original post: [HammondsLegacy Forums]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=261") (best when viewed at original location due to custom formatting)

[SIZE=4]High-level overview[/SIZE]

The Apache HTTP Server Project is an effort to develop and maintain an open-source HTTP server for modern operating systems including UNIX and Windows.

This tutorial will cover how to setup an Apache web server.

This is an overview image of a highly-available web server platform.
This article covers the web server install.
[img]https://hammondslegacy.com/images/linux/design-ha-lamp-service.jpg[/img]

[SIZE=4]Tools utilized in this process[/SIZE]


[LIST]
[*][Ubuntu Server]("https://www.ubuntu.com/download/alternative-downloads#alternate-ubuntu-server-installer") 18.04.2 LTS, 64-bit 
[*][Apache HTTP Server]("https://httpd.apache.org/") 2.4.29 
[*][PHP]("https://php.net/") 7.2.19 
[*][Let's Encrypt]("https://letsencrypt.org/") 0.31.0 
[*][Portable PuTTY]("http://portableapps.com/apps/internet/putty_portable") 0.71 
[*][VMware vSphere]("http://www.vmware.com/products/vsphere/overview.html") 6.0.0 
[*][VirtualBox]("http://www.virtualbox.org/") 6.0.10 
[/LIST]
 
[SIZE=4]Helpful links[/SIZE]

The list below are sources of information that was helpful in the creation of this document.


[LIST]
[*][Apache Documentation]("https://httpd.apache.org/docs/2.4/") 
[*][Let's Encrypt Documentation]("https://letsencrypt.org/docs/") 
[*][Uncomplicated Firewall]("https://help.ubuntu.com/community/UFW") (UFW) 
[*][SSL Configuration Generator]("https://ssl-config.mozilla.org/") 
[/LIST]
 
[SIZE=4]Assumptions[/SIZE]
 
This documentation will need to make use of some very-specific information that will most-likely be different for each person / location. And as such, this information will be noted in this section. They will be highlighted in red throughout the document as a reminder that you should plug-in your own value rather than actually using these "place-holder" values.

Under no circumstance should you use the actual values listed below. They are place-holders for the real thing. This is just a checklist template you need to have answered before you start the install process.

Wherever you see [COLOR=red]RED[/COLOR] in this document, you need to substitute it for you will use in your environment.


[LIST]
[*]Internet domain: [COLOR=red]mysite.mydomain.com[/COLOR] -> [COLOR=red]216.70.70.70[/COLOR] (Public IP) -> Firewall -> [COLOR=red]192.168.107.91[/COLOR] (Internal IP) 
[*]Ubuntu Admin ID: [COLOR=red]administrator[/COLOR] 
[*]Ubuntu Admin Password: [COLOR=red]myadminpass[/COLOR] 
[*]Email Server Name (remote): [COLOR=red]srv-mail[/COLOR] 
[*]Email Server Internal IP (remote): [COLOR=red]192.168.107.25[/COLOR] 
[/LIST]
 
Ubuntu Server - This tutorial assumes the server was configured according to this tutorial: [How to install and configure Ubuntu Server]("https://ubuntuforums.org/showthread.php?t=2389846")

It is also assumed the reader knows how to use the VI editor. If not, you will need to [beef up your skill set]("http://www.washington.edu/computing/unix/vi.html") or use a different editor in place of it.

---

### Post by LHammonds on 2019-09-06
[SIZE=4]Install Apache[/SIZE]

```
sudo apt install apache2
```

[SIZE=4]Install PHP for Apache with MySQL/MariaDB support[/SIZE]

```
sudo apt install php7.2 libapache2-mod-php7.2 php7.2-mysql
```

TIP: You can search available PHP packages names by typing this:

```
apt-cache search php7.2
```

[SIZE=4]Large File Upload Support[/SIZE]

If your site will allow uploading of files larger than 8 MB, you can increase this limit in PHP.  The below will modify the upload limit to allow files as large as 2,048 MB to be uploaded.

```
sudo vi /etc/php/7.2/apache2/php.ini
```

```

post_max_size = 2058M
upload_max_filesize = 2048M

```

Reload Apache for changes to the config to take affect:

```
systemctl reload apache2
```

[SIZE=4]Firewall Rules[/SIZE]

Edit the firewall script that was created during the initial setup of the server (if you [followed my instructions]("https://ubuntuforums.org/showthread.php?t=2389846&page=2&p=13758735#post13758735")):
```
vi /var/scripts/prod/en-firewall.sh
```

Add (or enable) the following:

```
echo "Adding Web Server rules"
ufw allow proto tcp to any port 80 comment 'HTTP Service' 1>/dev/null 2>&1
ufw allow proto tcp to any port 443 comment 'HTTPS Service' 1>/dev/null 2>&1

```

Run the updated rules:

```
/var/scripts/prod/en-firewall.sh
```

[SIZE=4]PHP Modules and Information[/SIZE]

To verify Apache, PHP and modules are installed and enabled, lets create the famous phpinfo page.

```

touch /var/www/html/phpinfo.php
chown www-data:www-data /var/www/html/phpinfo.php
chmod 0644 /var/www/html/phpinfo.php
echo "<?php phpinfo(); ?>" >> /var/www/html/phpinfo.php

```

Open a browser and load up the phpinfo page: [http://192.168.107.91/phpinfo.php](http://192.168.107.91/phpinfo.php)

You should be able to scroll down and see sections for each module we wanted enabled. If you don't see a dedicated section, then that module is not installed/enabled.

When done, do not forget to remove the info file:

```
rm /var/www/html/phpinfo.php
```

---

### Post by LHammonds on 2019-09-06
[SIZE=4]Disable the default sites[/SIZE]

It is best to disable and not use the default sites.
```

sudo a2dissite 000-default
sudo a2dissite default-ssl

```

[SIZE=4]Web Site Root Folder[/SIZE]

Create the web site root folder and default test page:

```

mkdir -p /var/www/mysite.mydomain.com
chown www-data:www-data /var/www/mysite.mydomain.com
chmod 0755 /var/www/mysite.mydomain.com
touch /var/www/mysite.mydomain.com/index.php
chown www-data:www-data /var/www/mysite.mydomain.com/index.php
chmod 0644 /var/www/mysite.mydomain.com/index.php
echo "<?php phpinfo(); ?>" >> /var/www/mysite.mydomain.com/index.php

```

[SIZE=4]DNS Resolution[/SIZE]

Typically, when you setup a web site, you will have a domain name and a public IP associated to it so people from anywhere on the Internet can access your server through the domain name.  But if you do not have that yet and want to setup the server as if you did, you can edit the local host file of your PC to "resolve" the friendly domain name to the correct IP (at least until you get it working at the DNS level).  Just be sure to undo these changes once the DNS server starts handling the name resolution.

On a Linux PC, you edit the following file:
```
sudo vi /etc/hosts
```
On a Windows PC, you edit the following file:
```
notepad C:\Windows\System32\Drivers\etc\hosts
```
And add an entry like this:
```
192.168.107.91   mysite.mydomain.com
```

You should be able to open a Command Prompt / Terminal and ping "mysite.mydomain.com" and your local host file should translate that to your IP address such as 192.168.107.91.

```
# ping -c3 mysite.mydomain.com
PING mysite.mydomain.com (192.168.107.91) 56(84) bytes of data.
64 bytes from mysite.mydomain.com (192.168.107.91): icmp_seq=1 ttl=64 time=0.028 ms
64 bytes from mysite.mydomain.com (192.168.107.91): icmp_seq=2 ttl=64 time=0.049 ms
64 bytes from mysite.mydomain.com (192.168.107.91): icmp_seq=3 ttl=64 time=0.053 ms

--- mysite.mydomain.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2049ms
rtt min/avg/max/mdev = 0.028/0.043/0.053/0.012 ms
```

[SIZE=4]Virtual Host Creation[/SIZE]

Create the virtual host configuration file for your domain / web site:

```

sudo touch /etc/apache2/sites-available/mysite.mydomain.com.conf
sudo chown root:root /etc/apache2/sites-available/mysite.mydomain.com.conf
sudo chmod 0644 /etc/apache2/sites-available/mysite.mydomain.com.conf

```

Edit the virtual host configuration file:
```
sudo vi /etc/apache2/sites-available/mysite.mydomain.com.conf
```

Set these values:

```

<VirtualHost *:80>
  ServerAdmin webmaster@localhost
  ServerName mydomain.com
  ServerAlias mysite.mydomain.com
  DocumentRoot /var/www/mysite.mydomain.com
  ErrorLog ${APACHE_LOG_DIR}/mysite.mydomain.com-error.log
  CustomLog ${APACHE_LOG_DIR}/mysite.mydomain.com-access.log combined
</VirtualHost>

```

[SIZE=4]Validate Virtual Host Syntax[/SIZE]

Validate the configuration file syntax and ensure it shows "Syntax OK"

```
sudo apache2ctl configtest
```

[SIZE=4]Enable Virtual Host[/SIZE]

To enable the site we just created, run this command (specific to your configuration filename):

```
a2ensite mysite.mydomain.com
```

[SIZE=4]Disable Virtual Host[/SIZE]

If you need to disable a site, run this command (specific to your configuration filename):

```
a2dissite mysite.mydomain.com
```

[SIZE=4]Reload Apache Configuration[/SIZE]

Whenever changes are made to the configuration files, modules or certificates, you will need to reload Apache for it to take affect.

```
systemctl reload apache2
```

---

### Post by LHammonds on 2019-09-06
[SIZE=4]Create Self-Signed SSL Certificate[/SIZE]

NOTE: This section is only here for historical reference.  For production SSL use, see the Let's Encrypt section for SSL certificates from a source web browsers trust.

This will create a self-signed certificate that will expire 1,095 days (3 years) from the date it was created. Web browsers will complain about it being untrusted. It will still work but end-users will have to allow this exception (unless it is on a LAN and you can add the site to all computers trusted sites via group policy)

```
a2enmod ssl
a2enmod rewrite
a2enmod headers
mkdir -p /etc/apache2/ssl/certs
mkdir -p /etc/apache2/ssl/private
openssl req -x509 -nodes -days 1095 -newkey rsa:2048 -keyout /etc/apache2/ssl/private/mysite.mydomain.com.key -out /etc/apache2/ssl/certs/mysite.mydomain.com.crt
  Country Name: US
  State: MyState
  Locality Name: MyCity
  Organication Name: MyCompany
  Organizational Unit Name: MyDepartment
  Common Name: mysite.mydomain.com
  Email Address: webmaster@mydomain.com

```

Ensure correct file ownership/permissions:

```

chown root:root /etc/apache2/ssl/private/mysite.mydomain.com.key
chown root:root /etc/apache2/ssl/certs/mysite.mydomain.com.crt
chmod 600 /etc/apache2/ssl/private/mysite.mydomain.com.key
chmod 600 /etc/apache2/ssl/certs/mysite.mydomain.com.crt

```

To verify the certificate:

```
openssl x509 -in /etc/apache2/ssl/certs/mysite.mydomain.com.crt -text -noout
```

To verify the private key:

```
openssl rsa -in /etc/apache2/ssl/private/mysite.mydomain.com.key -check
```

Create the virtual host SSL configuration file:

```

sudo touch /etc/apache2/sites-available/mysite.mydomain.com-ssl.conf
sudo chown root:root /etc/apache2/sites-available/mysite.mydomain.com-ssl.conf
sudo chmod 0644 /etc/apache2/sites-available/mysite.mydomain.com-ssl.conf

```

Edit the configuration file:
```
sudo vi /etc/apache2/sites-available/mysite.mydomain.com-ssl.conf
```

Set these values:

```

<IfModule mod_ssl.c>
  <VirtualHost _default_:443>
    ServerName mysite.mydomain.com
    ServerAlias mysite.mydomain.com
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/mysite.mydomain.com
    ErrorLog ${APACHE_LOG_DIR}/mysite.mydomain.com-error.log
    CustomLog ${APACHE_LOG_DIR}/mysite.mydomain.com-access.log combined
    SSLEngine on
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
    SSLCertificateFile /etc/apache2/ssl/certs/mysite.mydomain.com.crt
    SSLCertificateKeyFile /etc/apache2/ssl/private/mysite.mydomain.com.key
  </VirtualHost>
</IfModule>

```

Validate the configuration file syntax and ensure it shows "Syntax OK"

```
sudo apache2ctl configtest
```

Enable the site configuration:

```
a2ensite mysite.mydomain.com-ssl
```

Reload the Apache config so it is aware of the modified virtual host

```
systemctl reload apache2
```

Test the web page by visiting [https://mysite.mydomain.com/index.php](https://mysite.mydomain.com/index.php) and make sure the page displays and shows the SSL certificate is active.

---

### Post by LHammonds on 2019-09-06
[SIZE=4]Let's Encrypt SSL Certificate[/SIZE]

Let's Encrypt is a non-profit certificate authority run by Internet Security Research Group that provides X.509 certificates for Transport Layer Security encryption at no charge. The certificate is valid for 90 days, during which renewal can take place at any time.

This section will describe how to obtain a certificate and automate the renewal process.

[SIZE=4]Prerequisites[/SIZE]


[LIST]
[*]A registered domain name such as mydomain.com 
[*]Two Host A records on your authoritative DNS server for your domain such as:
```
Type A, mydomain.com, 216.70.70.70
Type A, mysite.mydomain.com, 216.70.70.70
``` 
[*]Web server (such as Apache) 
[*]A Virtual Host configuration file
[/LIST]
 
[SIZE=4]Install Certbot[/SIZE]

The Ubuntu package repository has Certbot available but tends to be several versions behind what is available by the Cerbot developers.  We can get the latest stable version of Certbot by adding the developers package repository.

```
sudo add-apt-repository ppa:certbot/certbot
sudo apt update
sudo apt install python-certbot-apache

```

[SIZE=4]LetsEncrypt Permission Fix[/SIZE]

While testing version 0.31.0, I found that I kept getting a "client lacks sufficient authorization" error message.  The problem is that during the authorization phase, it re-directs the Virtual Host configuration to /var/lib/letsencrypt/http_challenges but the parent folder of /var/lib/letsencrypt has too restrictive of permissions set.  The owner is set to root:root and permissions of 700 which means the web service (www-data) cannot view anything under that directory.  The solution is to fix the permission on that folder so "other" users (www-data) can see the contents.

```
chmod 755 /var/lib/letsencrypt
```

[SIZE=4]Obtain the SSL Certificate[/SIZE]

```
sudo certbot --apache -d mydomain.com -d mysite.mydomain.com
```

We use -d to specify each name we would like the certificate to be valid for.

Upon the first time creating the certificate, you will be prompted for various information.

Once the information gathering is complete, Certbot will ask how to configure the HTTPS settings such as not forcing a redirect of HTTP to HTTPS or letting it add a redirect to force all HTTP traffic to HTTPS.

You can answer however you like but I like to do my own redirection (especially if this is already handled on a load balancer).

The new files will be placed here by default:
```

/etc/letsencrypt/live/mydomain.com/fullchain.pem
/etc/letsencrypt/live/mydomain.com/privkey.pem

```

Look at the modified Virtual Host configuration file:
```
sudo vi /etc/apache2/sites-available/mysite.mydomain.com.conf
```

The modified file now looks something like this:

```

<IfModule mod_ssl.c>
  <VirtualHost _default_:443>
    ServerName mysite.mydomain.com
    ServerAlias mysite.mydomain.com
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/mysite.mydomain.com
    ErrorLog ${APACHE_LOG_DIR}/mysite.mydomain.com-error.log
    CustomLog ${APACHE_LOG_DIR}/mysite.mydomain.com-access.log combined
    SSLEngine on
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
    Include /etc/letsencrypt/options-ssl-apache.conf
    SSLCertificateFile /etc/letsencrypt/live/mysite.mydomain.com/fullchain.pem
    SSLCertificateKeyFile /etc/letsencrypt/live/mysite.mydomain.com/privkey.pem
  </VirtualHost>
</IfModule>

```

[SIZE=4]Crontab Schedule For SSL Certificate Auto-Renew[/SIZE]

Let's Encrypt certificates are only valid for 90 days. This encourages admins to automate their certificate renewal process.

The steps below will have the script run daily as the root user.  It will check all certificates and if any are within 30 days of expiring, it will initiate the automated renewal process.

You can force a simulated update to ensure the process will work using the dry-run option below.  If you see "success" messages, then you should be OK when it comes time for the renew to run for real:

```
sudo certbot renew --dry-run
```

Make a backup of the root crontab schedule (this file should exist if you [followed my instructions]("https://ubuntuforums.org/showthread.php?t=2389846&p=13758728#post13758728"))

```
cp /var/scripts/data/crontab.root /var/scripts/data/2019-07-23-crontab.root
```

Edit the root crontab schedule file:

```
sudo vi /var/scripts/data/crontab.root
```

Add the following line which will schedule Certbot to run at 7am every day:

```
0 7 * * * /usr/bin/certbot renew > /dev/null 2>&1
```

Replace the current root crontab schedule with the updated file:

```
crontab -u root /var/scripts/data/crontab.root
```

You can verify the update by listing the current schedule:

```
crontab -u root -l
```

---

### Post by LHammonds on 2019-09-06
[SIZE=4]Force SSL Usage[/SIZE]

This section will describe how to modify the site configuration to ensure anyone that hits an http (port 80) URL will be automatically re-directed to the https (port 443) location...thus ensuring all traffic on the site is encrypted using SSL.

Enable the rewrite mod:
```
sudo a2enmod rewrite
```

Restart Apache service for change to take affect:
```
sudo systemctl restart apache2
```

Edit the non-secure Virtual Host configuration file:
```
sudo vi /etc/apache2/sites-available/mysite.mydomain.com.conf
```

Add the following entries:
```

  RewriteEngine On
  RewriteRule ^(.*)$ https://%{HTTP_HOST}$1 [R=301,L]

```

Make sure the syntax is correct for the config file:
```
sudo apache2ctl configtest
```

Reload the Apache configuration for changes to take affect:
```
sudo systemctl reload apache2
```

Visit the non-ssl URL (http) and it should automatically swap it to the SSL URL (https).

[http://mysite.mydomain.com](http://mysite.mydomain.com)

---

### Post by LHammonds on 2019-09-06
[SIZE=4]Directory Security[/SIZE]

It is a good idea to have your site permission settings in a script that can be scheduled to run on a normal basis.  Each site/application will need to have specific permissions set so use the following script as an example of things you can do to customize a script for your site.

Create the file and set appropriate ownership / permissions.

```

touch /var/scripts/prod/mysite.mydomain.com-secure.sh
chown root:root /var/scripts/prod/mysite.mydomain.com-secure.sh
chmod 0755 /var/scripts/prod/mysite.mydomain.com-secure.sh

```

Edit the script:

```

vi /var/scripts/prod/mysite.mydomain.com-secure.sh

```

Add the following to the file and make changes that match your site:

```

#!/bin/bash
#############################################
## Name          : mysite.mydomain.com-secure.sh
## Version       : 1.1
## Date          : 2019-09-03
## Author        : LHammonds
## Compatibility : Ubuntu Server 18.04 LTS
## Requirements  : Run as root user
## Purpose       : Ensures ownership and permissions are set correctly.
## Run Frequency : Manual as needed or via crontab schedule.
################ CHANGE LOG #################
## DATE       WHO WHAT WAS CHANGED
## ---------- --- ----------------------------
## 2019-07-23 LTH Created script.
## 2019-09-03 LTH Added full path to executables.
#############################################
wwwdir='/var/www/mysite.mydomain.com'
webuser='www-data'
webgrp='www-data'
rootuser='root'

echo "Setting Ownership..."
/bin/chown -R ${webuser}:${webgrp} ${wwwdir}/
/bin/echo "Setting Folder Permissions..."
/usr/bin/find ${wwwdir}/ -type d -print0 | /usr/bin/xargs -0 /bin/chmod 0750
/bin/echo "Setting File Permissions..."
/usr/bin/find ${wwwdir}/ -type f -print0 | /usr/bin/xargs -0 /bin/chmod 0640
if [ -f ${wwwdir}/.htaccess ]; then
  /bin/chmod 0644 ${wwwdir}/.htaccess
fi
/bin/echo "Permission change complete."

```

Run the script and make sure there are no syntax errors:
```
/var/scripts/prod/mysite.mydomain.com-secure.sh
```

Verify that file and folder permissions were set correctly:
```
ls -l /var/www/mysite.mydomain.com
```

[SIZE=4]Crontab Schedule[/SIZE]

The script can now be schedule to run automatically.  The steps below will have the script run daily as the root user.

Make a backup of the root crontab schedule (this file should exist if you [followed my instructions]("https://ubuntuforums.org/showthread.php?t=2389846&p=13758728#post13758728"))

```
cp /var/scripts/data/crontab.root /var/scripts/data/2019-07-23-crontab.root
```

Edit the root crontab schedule file:

```
sudo vi /var/scripts/data/crontab.root
```

Add the following line which will schedule the script to run at 3am every day:

```
0 3 * * * /var/scripts/prod/mysite.mydomain.com-secure.sh > /dev/null 2>&1
```

Replace the current root crontab schedule with the updated file:

```
crontab -u root /var/scripts/data/crontab.root
```

You can verify the update by listing the current schedule:

```
crontab -u root -l
```

---

### Post by LHammonds on 2019-09-06
This section covers settings that can be modified to make it a bit more secure.

[SIZE=4]ServerSignature[/SIZE]

Turn off ServerSignature to prevent Apache from identifying itself and version number.

/etc/apache2/conf-available/security.conf
```
ServerSignature Off
```

[SIZE=4]ServerTokens[/SIZE]

Set ServerTokens to the least amount of information given.

This directive configures what you return as the Server HTTP response Header such as the the OS-Type and compiled in modules.

/etc/apache2/conf-available/security.conf
```
ServerTokens Prod
```

[SIZE=4]Fail2Ban - Standard Filters[/SIZE]

If you [followed my instructions]("https://ubuntuforums.org/showthread.php?t=2389846&page=2&p=13758736#post13758736") for setting up the Ubuntu Server, you should already have sshd being protected by Fail2Ban.  Now we are going to add some pre-defined Apache filters.

Edit the jail configuration file:
```
sudo vi /etc/fail2ban/jail.local
```

Add the following sections to the bottom:
```

[apache-auth]
# detect password authentication failures
enabled  = true
port     = http,https
filter   = apache-auth
action   = iptables-multiport[name=auth, port="http,https"]
logpath  = %(apache_error_log)s
bantime  = 3600
maxretry = 3

[apache-noscript]
# detect potential search for exploits
enabled  = true
port     = http,https
filter   = apache-noscript
action   = iptables-multiport[name=noscript, port="http,https"]
logpath  = %(apache_error_log)s
bantime  = 3600
maxretry = 6

[apache-overflows]
# detect Apache overflow attempts
enabled  = true
port     = http,https
filter   = apache-overflows
action   = iptables-multiport[name=overflows, port="http,https"]
logpath  = %(apache_error_log)s
bantime  = 3600
maxretry = 2

[apache-badbots]
# detect spammer robots crawling email addresses
enabled  = true
port     = http,https
filter   = apache-badbots
action   = iptables-multiport[name=badbots, port="http,https"]
logpath  = %(apache_access_log)s
bantime  = 48h
maxretry = 1

[php-url-fopen]
# detect PHP remote injection attacks
enabled  = true
port     = http,https
filter   = php-url-fopen
action   = iptables-multiport[name=phpfopen, port="http,https"]
logpath  = %(apache_access_log)s
maxretry = 1

```

Restart the Fail2Ban service:
```
sudo systemctl restart fail2ban
```

Check the status:
```
sudo fail2ban-client status
```

[SIZE=4]Fail2Ban - WordPress Login[/SIZE]

WordPress does not write login results to the web logs.  However, we can make an assumption that anyone trying to access the login page multiple times in a short period of time does not know their credentials or they are trying to brute-force crack accounts.  So let's create a filter that looks for anyone accessing the login page multiple time in a short timeframe.

Create a new filter:
```
sudo touch /etc/fail2ban/filter.d/wordpress-login.conf
sudo chown root:root /etc/fail2ban/filter.d/wordpress-login.conf
sudo chmod 644 /etc/fail2ban/filter.d/wordpress-login.conf

```

Edit the filter file:
```
sudo vi /etc/fail2ban/filter.d/wordpress-login.conf
```

Add this to the file:
```
[Definition]
failregex = <HOST> - - .*(POST|GET) .*/wp-login.php HTTP.*
```

Edit the jail configuration file:
```
sudo vi /etc/fail2ban/jail.local
```

Add the following sections to the bottom:
```

[wordpress-login]
# detect multiple attempts to login
enabled  = true
port     = http,https
action   = iptables-multiport[name=wordpress, port="http,https"]
filter   = wordpress-login
logpath  = %(apache_access_log)s
bantime  = 3600
findtime = 60
maxretry = 6

```

Restart the Fail2Ban service:
```
sudo systemctl restart fail2ban
```

Check the status:
```
sudo fail2ban-client status
```

---

