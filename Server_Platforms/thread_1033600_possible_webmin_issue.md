---
title: "possible webmin issue"
date: 2009-01-07
forum: Server Platforms
---

### Post by anwoke8204 on 2009-01-07
Hi, when I create a virtual domain the first one works just fine, but the second one and the ones after that I get the following error:

Forbidden
You don't have permission to access / on this server.


--------------------------------------------------------------------------------

Apache/2.2.8 (Ubuntu) DAV/2 SVN/1.4.6 PHP/5.2.4-2ubuntu5.4 with Suhosin-Patch mod_ruby/1.2.6 Ruby/1.8.6(2007-09-24) mod_ssl/2.2.8 OpenSSL/0.9.8g Server at realdealcars.org Port 80

anyone know how I can correct this issue so they show up correctly, I have uploaded the site to the home directory for the site, and as far as I can tell, there are no restrictions on the site as well.  TIA

---

### Post by volkswagner on 2009-01-07
Check the file permissions for your directory.

```
ls -alt /home/webuserid/webdirectory
```

When do you get the error message, creating the site in Webmin or your browser when accessing the new site?

---

### Post by anwoke8204 on 2009-01-07
permissions appear to be ok, they are as follows

andrew@srv1:~$ ls -alt /home/realdealcars/public_html
total 204
drwxrws--- 11 realdealcars webadmin  4096 2009-01-07 11:53 .
drwxrws---  4 realdealcars webadmin  4096 2009-01-07 11:53 themes
drwxrws--- 31 realdealcars webadmin  4096 2009-01-07 11:53 modules
drwxrws---  6 realdealcars webadmin  4096 2009-01-07 11:53 language
drwxrws--- 15 realdealcars webadmin  4096 2009-01-07 11:53 includes
drwxrws---  3 realdealcars webadmin  4096 2009-01-07 11:53 install
drwxrws--- 19 realdealcars webadmin  4096 2009-01-07 11:53 images
drwxrws---  2 realdealcars webadmin  4096 2009-01-07 11:53 blocks
drwxrws---  6 realdealcars webadmin  4096 2009-01-07 11:53 admin
drwxrws---  2 realdealcars webadmin  4096 2009-01-07 11:49 stats
drwxrws---  9 realdealcars webadmin  4096 2009-01-07 11:49 ..
lrwxrwxrwx  1 root         root        23 2009-01-07 11:49 awstats-icon -> /usr/share/awstats/icon
lrwxrwxrwx  1 root         root        23 2009-01-07 11:49 icon -> /usr/share/awstats/icon
-rwxrwx---  1 realdealcars webadmin 46979 2008-06-11 11:06 mainfile.php
-rwxrwx---  1 realdealcars webadmin 10429 2008-06-02 09:24 footer.php
-rwxrwx---  1 realdealcars webadmin 16844 2008-05-26 14:45 admin.php
-rwxrwx---  1 realdealcars webadmin  8612 2008-05-26 14:45 config.php
-rwxrwx---  1 realdealcars webadmin  4622 2008-05-26 14:45 evo.htaccess
-rwxrwx---  1 realdealcars webadmin     0 2008-05-26 14:45 evo.sitemap.xml
-rwxrwx---  1 realdealcars webadmin   227 2008-05-26 14:45 evo.staccess
-rwxrwx---  1 realdealcars webadmin  8662 2008-05-26 14:45 header.php
-rwxrwx---  1 realdealcars webadmin  5012 2008-05-26 14:45 index.php
-rwxrwx---  1 realdealcars webadmin  9565 2008-05-26 14:45 install.php
-rwxrwx---  1 realdealcars webadmin  2283 2008-05-26 14:45 ips.php
-rwxrwx---  1 realdealcars webadmin  5005 2008-05-26 14:45 modules.php
-rwxrwx---  1 realdealcars webadmin   378 2008-05-26 14:45 robots.txt
-rwxrwx---  1 realdealcars webadmin  1553 2008-05-26 14:45 rss.php
-rwxrwx---  1 realdealcars webadmin     0 2008-05-26 14:45 sample.ftaccess
-rwxrwx---  1 realdealcars webadmin   704 2008-05-26 14:45 trap.php
-rwxrwx---  1 realdealcars webadmin     0 2008-05-26 14:45 ultramode.txt
andrew@srv1:~$

---

### Post by windependence on 2009-01-07
You need to disable the default host when you are doing virtual hosts.

-Tim

---

### Post by anwoke8204 on 2009-01-07
how do I disable the default host, I don't see an option to disable it, just delete

---

### Post by windependence on 2009-01-07
Where are you seeing any "options"? Apache is configured using a set of simple text files. If you are trying to use a GUI tool to configure your virtual hosts, this may be where your problem is.

>               Apache2 ships with a virtual-host-friendly default configuration.              That is, it is configured with a single default virtual host (using              the *VirtualHost* directive) which can modified or used as-is if you              have a single site, or used as a template for additional virtual hosts              if you have multiple sites.  If left alone, the default virtual host              will serve as your default site, or the site users will see if the              URL they enter does not match the *ServerName* directive of any of your               custom sites.  To modify the default virtual host, edit the file              /etc/apache2/sites-available/default.  If you              wish to configure a new virtual host or site, copy that file into the              same directory with a name you choose.  For example,              **sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/mynewsite**              Edit the new file to configure the new site using some of the directives              described below.[https://help.ubuntu.com/8.04/serverguide/C/httpd.html](https://help.ubuntu.com/8.04/serverguide/C/httpd.html)

Try:

```
 sudo a2dissite default
```

I'm not sure if you need the absolute path here. Most of my sites are Apache 1.3


-Tim

---

### Post by anwoke8204 on 2009-01-08
I have disabled the default site using the a2dissite command, but still the first virtual domain works, but the others do not go through, I just get:
The website cannot display the page 
 HTTP 500  
   Most likely causes:
The website is under maintenance. 
The website has a programming error. 
 
   What you can try: 
     Refresh the page. 
 
     Go back to the previous page. 
 
     More information 
 
when i try to run the install script for one of the scripts I use on this site, I get:
Access Denied  
This is a restricted area which you should not be trying to access!
Please return to the mainsite.  

any ideas.  if it helps the website in question is realdealcars.org  the one that is working (still have to upload the database backup) is rooksystems.com

TIA for your assistance

---

### Post by volkswagner on 2009-01-08
Not sure of your particular setup.  Generally web files need permission by www-data group.

Does webadmin belong to the www-data group.

To see if it a permission issue, grant the folder recursively rwx access for all temporarily.  Then restart apache2.

---

### Post by anwoke8204 on 2009-01-08
I gave all access to the folder, but it still wouldn't work, it look like virtualmin is setting them up to run under thier own user and group for each site.  the first site works fine with a user and group of rooksystems, but the second site with a user and group of realdealcars doesn't work.  any other ideas.  TIA

---

### Post by volkswagner on 2009-01-08
Is the first site, a working .php site?  Perhaps you have a .php issue..


Is it truly an issue of which site is added first?

IE: Can you remove all virtual hosts and add one of the non working sites first to verify?  Backing up config. files first...

---

### Post by anwoke8204 on 2009-01-08
yes, my first site is a php site, all of my sites on my server are php based as I need the database backend.  the phpinfo.php test works on all sites just fine though, so not sure if it is a php issue or if it is a virtual host issue.

 TIA for the help

---

### Post by volkswagner on 2009-01-08
I am not sure it you are having a similar issue I once had.  I remember having an issue after a new install of a Twiki site.

The problem was setting the correct root directory, I believe.

Although Twiki was installed to /home/user/Twiki.....I had to set the doc root to /home/user/Twiki/bin.

Shot in the dark here.

---

### Post by anwoke8204 on 2009-01-08
I have checked the directories, and all appear to be valid, as per virtualmin configuration, each site is under /home/(domain name)/Public_Html/  and I have the data for the sites taht are comming up as access denied under those directories.  could there be an issue with permissions somewhere, i have checked them, and they seem to be fine, virtualmin creates a user for each virtual domain, and assigns ownership of the publilc_html to that username, do I need to change it to the www_data user and group?

TIA

---

### Post by volkswagner on 2009-01-09
If modifying the permissions to read and execute for all did not work, I am certain changing the group and owner would still have no affect.

```
sudo chmod -R 777 /home/(domain name)/Public_Html
```

Notice the capital "R" sets it to  recursive.  This would be temporary to see if it is a permission issue.

I know you tried this earlier, but make sure you check the file properties to see if the files are readable and executable by all.

```
ls -alt /home/(domain name)/Public_Html/ 
```

---

### Post by anwoke8204 on 2009-01-09
I did the chmod, but issues remain, could it be I need to change a user setting in apache or something?
TIA

---

### Post by volkswagner on 2009-01-09
You can post the output of the following

```
ls -alt /home/sitenotworking.com/Public_Html
```

```
ls -alt /etc/apache2/sites-enabled
```
```

cat /etc/apache2/sites-enabled/sitenotworking.conf.vhost
```

I also sent you a  PM (private message)

---

### Post by anwoke8204 on 2009-01-09
results of ls-alt /home/rooksystems/public_html
total 12
drwxr-xr-x 2 rooksystems rooksystems 4096 2009-01-09 07:09 stats
drwxr-x--- 9 rooksystems rooksystems 4096 2009-01-09 07:09 ..
drwxr-x--- 3 rooksystems rooksystems 4096 2009-01-09 07:09 .
lrwxrwxrwx 1 root        root          23 2009-01-09 07:09 awstats-icon -> /usr/share/awstats/icon
lrwxrwxrwx 1 root        root          23 2009-01-09 07:09 icon -> /usr/share/awstats/icon

results of ls -alt /eta/apache2/sites-enabled
lrwxrwxrwx 1 root root   49 2009-01-09 07:09 rooksystems.com.conf -> /etc/apache2/sites-available/rooksystems.com.conf
lrwxrwxrwx 1 root root   56 2009-01-08 02:37 andrewsblog.no-ip.info.conf -> /etc/apache2/sites-available/andrewsblog.no-ip.info.conf
lrwxrwxrwx 1 root root   50 2009-01-08 01:32 realdealcars.org.conf -> /etc/apache2/sites-available/realdealcars.org.conf

results of cat /etc/apache2/sites-enabled/sitenotworking.conf.vhost

cat: /etc/apache2/sites-enabled/sitenotworking.conf.vhost: No such file or directory

---

### Post by anwoke8204 on 2009-01-09
here is the result of the rooksystems.com.conf file under the sites-enabled directory
<VirtualHost 192.168.1.13:80>
SuexecUserGroup "#1002" "#1003"
ServerName rooksystems.com
ServerAlias [www.rooksystems.com](www.rooksystems.com)
ServerAlias webmail.rooksystems.com
ServerAlias admin.rooksystems.com
ServerAlias lists.rooksystems.com
DocumentRoot /home/rooksystems/public_html
ErrorLog /home/rooksystems/logs/error_log
CustomLog /home/rooksystems/logs/access_log combined
ScriptAlias /cgi-bin/ /home/rooksystems/cgi-bin/
ScriptAlias /awstats /home/rooksystems/cgi-bin
DirectoryIndex index.html index.htm index.php index.php4 index.php5
<Directory /home/rooksystems/public_html>
Options -Indexes IncludesNOEXEC FollowSymLinks
allow from all
AllowOverride All
</Directory>
<Directory /home/rooksystems/cgi-bin>
allow from all
</Directory>
RewriteEngine on
RewriteCond %{HTTP_HOST} =webmail.rooksystems.com
RewriteRule ^(.*) [https://rooksystems.com:20000/](https://rooksystems.com:20000/) [R]
RewriteCond %{HTTP_HOST} =admin.rooksystems.com
RewriteRule ^(.*) [https://rooksystems.com:10000/](https://rooksystems.com:10000/) [R]
Alias /dav /home/rooksystems/public_html
Alias /pipermail /var/lib/mailman/archives/public
<Location /dav>
DAV On
AuthType Basic
AuthName rooksystems.com
AuthUserFile /home/rooksystems/etc/dav.digest.passwd
Require valid-user
ForceType text/plain
Satisfy All
</Location>
<Files awstats.pl>
AuthName "rooksystems.com statistics"
AuthType Basic
AuthUserFile /home/rooksystems/.awstats-htpasswd
require valid-user
</Files>
RedirectMatch /cgi-bin/mailman/([^/]*)(.*) https://rooksystems.com:10000/virtualmin-mailman/unauthenticated/$1.cgi$2
RedirectMatch /mailman/([^/]*)(.*) https://rooksystems.com:10000/virtualmin-mailman/unauthenticated/$1.cgi$2
</VirtualHost>
<VirtualHost 192.168.1.13:443>
SuexecUserGroup "#1002" "#1003"
ServerName rooksystems.com
ServerAlias [www.rooksystems.com](www.rooksystems.com)
ServerAlias webmail.rooksystems.com
ServerAlias admin.rooksystems.com
ServerAlias lists.rooksystems.com
DocumentRoot /home/rooksystems/public_html
ErrorLog /home/rooksystems/logs/error_log
CustomLog /home/rooksystems/logs/access_log combined
ScriptAlias /cgi-bin/ /home/rooksystems/cgi-bin/
ScriptAlias /awstats /home/rooksystems/cgi-bin
DirectoryIndex index.html index.htm index.php index.php4 index.php5
<Directory /home/rooksystems/public_html>
Options -Indexes IncludesNOEXEC FollowSymLinks
allow from all
AllowOverride All
</Directory>
<Directory /home/rooksystems/cgi-bin>
allow from all
</Directory>
RewriteEngine on
RewriteCond %{HTTP_HOST} =webmail.rooksystems.com
RewriteRule ^(.*) [https://rooksystems.com:20000/](https://rooksystems.com:20000/) [R]
RewriteCond %{HTTP_HOST} =admin.rooksystems.com
RewriteRule ^(.*) [https://rooksystems.com:10000/](https://rooksystems.com:10000/) [R]
SSLEngine on
SSLCertificateFile /home/rooksystems/ssl.cert
SSLCertificateKeyFile /home/rooksystems/ssl.key
Alias /dav /home/rooksystems/public_html
Alias /pipermail /var/lib/mailman/archives/public
<Location /dav>
DAV On
AuthType Basic
AuthName rooksystems.com
AuthUserFile /home/rooksystems/etc/dav.digest.passwd
Require valid-user
ForceType text/plain
Satisfy All
</Location>
<Files awstats.pl>
AuthName "rooksystems.com statistics"
AuthType Basic
AuthUserFile /home/rooksystems/.awstats-htpasswd
require valid-user
</Files>
RedirectMatch /cgi-bin/mailman/([^/]*)(.*) https://rooksystems.com:10000/virtualmin-mailman/unauthenticated/$1.cgi$2
RedirectMatch /mailman/([^/]*)(.*) https://rooksystems.com:10000/virtualmin-mailman/unauthenticated/$1.cgi$2
</VirtualHost>

---

### Post by anwoke8204 on 2009-01-09
here is the config file for the second site.
<VirtualHost 192.168.1.13:80>
SuexecUserGroup "#1003" "#1004"
ServerName realdealcars.org
ServerAlias [www.realdealcars.org](www.realdealcars.org)
ServerAlias webmail.realdealcars.org
ServerAlias admin.realdealcars.org
ServerAlias lists.realdealcars.org
DocumentRoot /home/realdealcars/public_html
ErrorLog /home/realdealcars/logs/error_log
CustomLog /home/realdealcars/logs/access_log combined
ScriptAlias /cgi-bin/ /home/realdealcars/cgi-bin/
ScriptAlias /awstats /home/realdealcars/cgi-bin
DirectoryIndex index.html index.htm index.php index.php4 index.php5
<Directory /home/realdealcars/public_html>
Options -Indexes IncludesNOEXEC FollowSymLinks
allow from all
AllowOverride All
</Directory>
<Directory /home/realdealcars/cgi-bin>
allow from all
</Directory>
RewriteEngine on
RewriteCond %{HTTP_HOST} =webmail.realdealcars.org
RewriteRule ^(.*) [https://realdealcars.org:20000/](https://realdealcars.org:20000/) [R]
RewriteCond %{HTTP_HOST} =admin.realdealcars.org
RewriteRule ^(.*) [https://realdealcars.org:10000/](https://realdealcars.org:10000/) [R]
Alias /dav /home/realdealcars/public_html
Alias /pipermail /var/lib/mailman/archives/public
<Location /dav>
DAV On
AuthType Basic
AuthName realdealcars.org
AuthUserFile /home/realdealcars/etc/dav.digest.passwd
Require valid-user
ForceType text/plain
Satisfy All
</Location>
<Files awstats.pl>
AuthName "realdealcars.org statistics"
AuthType Basic
AuthUserFile /home/realdealcars/.awstats-htpasswd
require valid-user
</Files>
RedirectMatch /cgi-bin/mailman/([^/]*)(.*) https://realdealcars.org:10000/virtualmin-mailman/unauthenticated/$1.cgi$2
RedirectMatch /mailman/([^/]*)(.*) https://realdealcars.org:10000/virtualmin-mailman/unauthenticated/$1.cgi$2
</VirtualHost>

---

### Post by anwoke8204 on 2009-01-09
here is the ls- alt listing

drwxr-xr-x  4 realdealcars realdealcars    4096 2009-01-09 07:50 old - Copy
drwxr-xr-x  4 realdealcars realdealcars    4096 2009-01-09 07:50 themes
drwxr-xr-x 18 realdealcars realdealcars    4096 2009-01-09 07:50 old
drwxr-xr-x 15 realdealcars realdealcars    4096 2009-01-09 07:50 includes
drwxr-xr-x  6 realdealcars realdealcars    4096 2009-01-09 07:50 language
drwxr-xr-x 10 realdealcars realdealcars    4096 2009-01-09 07:50 mail
drwxr-xr-x 31 realdealcars realdealcars    4096 2009-01-09 07:50 modules
drwxr-xr-x 19 realdealcars realdealcars    4096 2009-01-09 07:50 images
drwxr-xr-x 14 realdealcars realdealcars    4096 2009-01-09 07:50 chat
drwxr-xr-x  2 realdealcars realdealcars    4096 2009-01-09 07:50 blocks
drwxr-x--- 14 realdealcars realdealcars    4096 2009-01-09 07:50 .
drwxr-xr-x  6 realdealcars realdealcars    4096 2009-01-09 07:50 admin
drwxr-xr-x  2 realdealcars realdealcars    4096 2009-01-09 07:48 stats
drwxr-x---  9 realdealcars realdealcars    4096 2009-01-09 07:48 ..
lrwxrwxrwx  1 root         root              23 2009-01-09 07:48 awstats-icon -> /usr/share/awstats/icon
lrwxrwxrwx  1 root         root              23 2009-01-09 07:48 icon -> /usr/share/awstats/icon
-rw-r--r--  1 realdealcars realdealcars  139571 2008-12-21 16:18 error.log
-rw-r--r--  1 realdealcars realdealcars 1579876 2008-12-21 16:18 accesslog
-rw-r--r--  1 realdealcars realdealcars     866 2008-11-23 20:19 sitemap.xml
-rw-r--r--  1 realdealcars realdealcars    8625 2008-08-30 16:25 config.php
-rw-r--r--  1 realdealcars realdealcars       0 2008-08-30 16:21 .htaccess
-rw-r--r--  1 realdealcars realdealcars      51 2008-08-28 22:37 desktop.ini
-rw-r--r--  1 realdealcars realdealcars   46979 2008-06-11 10:06 mainfile.php
-rw-r--r--  1 realdealcars realdealcars   10429 2008-06-02 08:24 footer.php
-rw-r--r--  1 realdealcars realdealcars   16844 2008-05-26 13:45 admin.php
-rw-r--r--  1 realdealcars realdealcars    4622 2008-05-26 13:45 evo.htaccess
-rw-r--r--  1 realdealcars realdealcars       0 2008-05-26 13:45 evo.sitemap.xml
-rw-r--r--  1 realdealcars realdealcars     227 2008-05-26 13:45 evo.staccess
-rw-r--r--  1 realdealcars realdealcars    8662 2008-05-26 13:45 header.php
-rw-r--r--  1 realdealcars realdealcars    5012 2008-05-26 13:45 index.php
-rw-r--r--  1 realdealcars realdealcars    2283 2008-05-26 13:45 ips.php
-rw-r--r--  1 realdealcars realdealcars    5005 2008-05-26 13:45 modules.php
-rw-r--r--  1 realdealcars realdealcars     378 2008-05-26 13:45 robots.txt
-rw-r--r--  1 realdealcars realdealcars    1553 2008-05-26 13:45 rss.php
-rw-r--r--  1 realdealcars realdealcars       0 2008-05-26 13:45 sample.ftaccess
-rw-r--r--  1 realdealcars realdealcars     704 2008-05-26 13:45 trap.php
-rw-r--r--  1 realdealcars realdealcars       0 2008-05-26 13:45 ultramode.txt

---

