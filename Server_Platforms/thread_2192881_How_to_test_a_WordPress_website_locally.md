---
title: "How to test a WordPress website locally?"
date: 2013-12-10
forum: Server Platforms
---

### Post by satimis on 2013-12-10
Hi all,

I have WP Version 3.5.1 running on Ubuntu 12.04 which is a VM of Oracle VirtualBox.  [http://localhost](http://localhost) can find it working.

I'm prepared testing a working website on it which is running on Godaddy Server but couldn't figure out how to do it.  The aforesaid website can be browsed on Internet with its URL

Please advise.
1) Where shall I copy following folders and files to which will be download on Godaddy server?```

index.php        wp-blog-header.php    wp-cron.php        wp-mail.php
license.txt      wp-comments-post.php  wp-includes        wp-settings.php
readme.html      wp-config.php         wp-links-opml.php  wp-signup.php
wp-activate.php  wp-config-sample.php  wp-load.php        wp-trackback.php
wp-admin         wp-content            wp-login.php       xmlrpc.php

```

WordPress is installed on;
/var/www/wordpress/
ls /var/www/wordpress/```

index.php        wp-blog-header.php    wp-cron.php        wp-mail.php
license.txt      wp-comments-post.php  wp-includes        wp-settings.php
readme.html      wp-config.php         wp-links-opml.php  wp-signup.php
wp-activate.php  wp-config-sample.php  wp-load.php        wp-trackback.php
wp-admin         wp-content            wp-login.php       xmlrpc.php

```

2)
How to test the website?  Evoking [http://localhost](http://localhost) ?

3)
What will be the easy way to upgrade Wordpress to the latest version?

Please advise.  TIA

Rgds
satimis

---

### Post by nerdtron on 2013-12-10
My short answers:
1. Copy them, as long as you use relative links, the folder in which they contain doesn't matter. Be careful that the permissions of files are preserved when you copy. And be sure to check the databases username/passwords on your config.
2. If [http://url_of_server_in_godaddy/](http://url_of_server_in_godaddy/) or on your local pc, http//:localhost or if it doesn't work, try adding /wordpress on the end of the URL.
3. no idea.

---

### Post by satimis on 2013-12-10
> **nerdtron said:**
> My short answers:
1. Copy them, as long as you use relative links, the folder in which they contain doesn't matter. Be careful that the permissions of files are preserved when you copy. And be sure to check the databases username/passwords on your config.
2. If [http://url_of_server_in_godaddy/](http://url_of_server_in_godaddy/) or on your local pc, http//:localhost or if it doesn't work, try adding /wordpress on the end of the URL.
3. no idea.
Hi,

Thanks for your advice.

What I can't resolve is whether create a new folder, say website_name, on my local server under /var/www/wordpress/website_name/ and copy all folders and files from Godaddy server on it?  If copy them on /var/www/wordpress/ all existing folders and files will be overwritten.

I'm prepared performing following test;

(1)
Duplicate the website on Godaddy server to local server

2)
After testing the duplicate website working, I'll edit the domain setting on Godaddy server, which is registered and hosted there, pointing to the IP address of my local server.  I'm subscribing static IP.  But I can't run my local server 24x7.  

3)
After having further tested the duplicate website working without problem I'll map the domain on Godaddy server so that the URL will point to my local server first.  If not working it will automatically point to Godaddy server.

Edit:
It is quite easy to copy the complete blog of the website on Godaddy with FileZilla to my local server.

Rgds
satimis

---

### Post by sandyd on 2013-12-11
> **satimis said:**
> Hi,

Thanks for your advice.

What I can't resolve is whether create a new folder, say website_name, on my local server under /var/www/wordpress/website_name/ and copy all folders and files from Godaddy server on it?  If copy them on /var/www/wordpress/ all existing folders and files will be overwritten.

I'm prepared performing following test;

(1)
Duplicate the website on Godaddy server to local server

2)
After testing the duplicate website working, I'll edit the domain setting on Godaddy server, which is registered and hosted there, pointing to the IP address of my local server.  I'm subscribing static IP.  But I can't run my local server 24x7.  

3)
After having further tested the duplicate website working without problem I'll map the domain on Godaddy server so that the URL will point to my local server first.  If not working it will automatically point to Godaddy server.

Edit:
It is quite easy to copy the complete blog of the website on Godaddy with FileZilla to my local server.

Rgds
satimis
3. 
Upload it to a subdirectory so you dont overwrite it (if you want instead, you can just setup virtual hosts, and map the domains to the server in /etc/hosts)
Check this out [http://codex.wordpress.org/Changing_The_Site_URL#Relocate_method](http://codex.wordpress.org/Changing_The_Site_URL#Relocate_method)

---

### Post by satimis on 2013-12-11
> **sandyd said:**
> 3. 
Upload it to a subdirectory so you dont overwrite it (if you want instead, you can just setup virtual hosts, and map the domains to the server in /etc/hosts)
Check this out [http://codex.wordpress.org/Changing_The_Site_URL#Relocate_method](http://codex.wordpress.org/Changing_The_Site_URL#Relocate_method)
Hi,

Thanks for your advice.

Performed following steps:
1)
Created a new folder;
/var/www/domain

$ sudo chown www-data:www-data /var/www/domain

2)
Copied the website to;
/var/www/domain/

$ cd /var/www/domain/
$ sudo chown www-data:www-data * -R
$ sudo usermod -a -G www-data user

3)
edited /etc/hosts

changed localhost to domain

4)
edited /var/www/domain/wp-config.php
adding following line on it```

define('RELOCATE',true);

```

5)
Reboot the VM
(performing this test on a VM of VirtualBox)

On browser
[http://domain](http://domain)```

IT WORKS

```

[http://domain/wp-config.php](http://domain/wp-config.php)
```

Error establishing a database connection

```

satimis

---

### Post by nerdtron on 2013-12-11
Edit your wordpress config for correct database username and password.

---

### Post by satimis on 2013-12-11
> **nerdtron said:**
> Edit your wordpress config for correct database username and password.
On wp-config.php```

// ** MySQL settings - You can get this info from your web host ** //
/** The name of the database for WordPress */
define('DB_NAME', 'domain');

/** MySQL database username */
define('DB_USER', 'domain_user');

/** MySQL database password */
define('DB_PASSWORD', 'password');

/** MySQL hostname */
define('DB_HOST', 'domain.hostedresource.com');

```
On installing Wordpress, the database created is for localhost.  Whether I have to create a new database for the new domain?

Thanks

satimis

---

### Post by Habitual on 2013-12-11
> **satimis said:**
> http://localhost[/URL] ?


```
sudo vi /etc/hosts
ipa.dd.re.ss domain.com

```

"poor man's DNS"

---

### Post by satimis on 2013-12-11
> **Habitual said:**
> ```
sudo vi /etc/hosts
ipa.dd.re.ss domain.com

```

"poor man's DNS"
Hi,

Thanks

I tried your suggestion before without result.  I have been searching hard on Internet.  There are many similar links but relating to Windows server.  The solution is on MySQL.  I'll try later.

satimis

---

### Post by Habitual on 2013-12-11
> **satimis said:**
> Hi,

Thanks

I tried your suggestion before without result.  I have been searching hard on Internet.  There are many similar links but relating to Windows server.  The solution is on MySQL.  I'll try later.

satimis
I've used this method for years.
Define "without result" exactly.

---

### Post by satimis on 2013-12-11
> **Habitual said:**
> I've used this method for years.
Define "without result" exactly.
Hi,

Add following line on /etc/hosts```

192.168.0.127  domain.com

```

On browser
192.168.0.127
It works

domain.com
Not found

192.168.0.127/domain.com
Not found

satimis

---

### Post by Habitual on 2013-12-11
Sometime the cheap dns takes a few minutes...
[http://domain.com](http://domain.com) should definitely work.
```
SELECT option_name, option_value  FROM db_name.wp_options where option_name = 'siteurl';
``` output please.
You may have to sanitize it.

does it show [http://domain.com](http://domain.com) or something else, or extra like [http://domain.com/more_stuff_here?](http://domain.com/more_stuff_here?)

---

### Post by nerdtron on 2013-12-11
When you edit the /etc/hosts sometimes you need to clear the cache of your browser.

---

### Post by satimis on 2013-12-12
> **Habitual said:**
> Sometime the cheap dns takes a few minutes...
[http://domain.com](http://domain.com) should definitely work.
```
SELECT option_name, option_value  FROM db_name.wp_options where option_name = 'siteurl';
``` output please.
You may have to sanitize it.

Hi,

I'm hosting on Godaddy.  I couldn't run MySQL commands on their server.  On their phpmyadmin I found
```

option_name	siteurl
option_value	http://kitchen.satimis.com

```

Just cleared history and cache memory on Chrome.

/192.168.0.127```

IT WORKS!

```

/192.168.0.127/kitchen.satimis.com```

NOT FOUND

```

/192.168.0.127/kitchen (folder name)```

Error establishing a database connection

```

Performed following test;
According to 
define('DB_NAME'            )
define('DB_PASSWORD'        )
define('DB_HOST'

on wp-config.php created a new database but still failed evoking the website locally.  I suppose I have to adding a new user with abovementioned data to the existing database created previously at installation of WordPress.

> 
does it show [http://domain.com](http://domain.com) or something else, or extra like [http://domain.com/more_stuff_here?](http://domain.com/more_stuff_here?)
Nothing displayed, just "NOT FOUND".

It the PC connected to Internet then it browses the website on Godaddy server.


Edit:
How to test WordPress has been installed correctly?  Because this is a newly installed copy and no website has been created yet.

Rgds
satimis

---

### Post by nerdtron on 2013-12-12
Just trying to clear something up. Skip if my assumptions are wrong.

So you are testing your website (which is in GoDaddy) on your local computer. You copy the files from the GoDaddy server to your computer?
If I'm correct did you also backup the mysql from GoDaddy and restored it to the mysql of your local computer?

---

### Post by satimis on 2013-12-12
> **nerdtron said:**
> Just trying to clear something up. Skip if my assumptions are wrong.

So you are testing your website (which is in GoDaddy) on your local computer. You copy the files from the GoDaddy server to your computer?

You're correct

> 
If I'm correct did you also backup the mysql from GoDaddy and restored it to the mysql of your local computer?
That is share hosting.  I have not idea how to export the database of this website under testing to my local PC.  Please help.  Thanks

Furthermore I wonder whether there is no mistake on installing WordPress.  During its installation there was no complaint

Rgds
satimis

---

### Post by nerdtron on 2013-12-12
Sorry no idea how to get a backup of database from godaddy, because we host our own wordpress sites. Maybe the other system admins from the forum may help.
All I know is that when I backup/transfer/migrate a website based on wordpress you should have a backup of the html files and the database it uses. Then restore them on the other machine.

---

### Post by sandyd on 2013-12-12
> **satimis said:**
> You're correct


That is share hosting.  I have not idea how to export the database of this website under testing to my local PC.  Please help.  Thanks

Furthermore I wonder whether there is no mistake on installing WordPress.  During its installation there was no complaint

Rgds
satimis

phpmyadmin -> right hand columnm click on the database name, and then go to the export tab. Export it from there and download it to computer

Go to your mysql server, and login
```

mysql -uroot -p

```
Create database
```

CREATE DATABASE wordpress_new;

```
Grant permissions on database
```

GRANT ALL PRIVILEGES ON wordpress_new.* TO wp_new@localhost IDENTIFIED BY 'passwordhere';
```
Flush privs and exit
```

flush privileges;
exit

```
Import database you exported
```

mysql -uwp_new -p < db_file_you_exported
```
use 'passwordhere' when it asks for password

---

### Post by daryl2 on 2013-12-12
First of all you need to read the documentation

Wordpress is a nuisance to move and edit simply because it stores URL's in its database.

There are two ways of approaching this.
1) you can setup a namevirtualhost with exactly the same name, and trick your computer into thinking that the localhost is your godaddy host. (which is the easiest way) the only problem with this is you cant browse the original website from that computer. But if you have a spare computer or a VM then i suppose its not really a problem too much.
2) you can change the URL to a localhost type one.

To do option 1, 
Firstly make a new VHOST file lets call it yoururl.com : something like this would be sufficient: pop it in /etc/apache2/sites-available/yoururl.com
<VirtualHost *:80>
                        ServerName yoururl.com
                        ServerAlias yoururl.com
                        ServerAdmin [email]your@email.com[/email]
                        DocumentRoot /var/www/yoursitesfiles/
                        <Directory /var/www/yoursitesfiles/ >
                                Options Indexes FollowSymLinks MultiViews
                                AllowOverride All
                                Order allow,deny
                                allow from all
                        </Directory>
                        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
                        <Directory "/usr/lib/cgi-bin">
                                AllowOverride None
                                Options +ExecCGI -MultiViews +SymLinksIfOwnerMat                                                                                        ch
                                Order allow,deny
                                Allow from all
                        </Directory>
                        ErrorLog /var/log/apache2/yoururl.com-error.log
                        LogLevel warn
                        CustomLog ${APACHE_LOG_DIR}/yoururl.com-access.log combined
                        Alias /doc/ "/usr/share/doc/"
</VirtualHost>

Then ensure you have NameVirtualHost enabled in your ports.conf usually /etc/apache2/ports.conf

NameVirtualHost *:80
Listen 80

then you want to copy ALL the files from your wordpress root to /var/www/yoursitesfiles/ 

then go and edit /etc/hosts and add this line:
127.0.0.1     yoururl.com

then run sudo a2ensite yoururl.com

The extract the wordpress database to a .sql file, and run it back into your local database. 

get the username and password out of the wp-config.php file. 

I generally log into mysql as root then run 
CREATE 'user'@'localhost' IDENTIFIED BY 'password';
CREATE DATABASE databasename;
GRANT ALL PRIVILEGES ON databasename.* TO 'user'@'localhost';

Then i exit mysql \q and then run mysql -u user -p databasename < /path/to/databasedumpfile.sql
then enter the password.

Then run 
sudo service apache2 restart

Then i would completely CLOSE my browser because it doesnt use the /etc/hosts lookup if it has been cached in the browser and re-open it again then browse to your URL and it should work.

---

### Post by satimis on 2013-12-12
Hi daryl2,

Lot of thanks for your detail advice.  Before start I expect clarifying following points;

1)
About option-2
> 
2) you can change the URL to a localhost type one.

What is "localhost type one"?

2)
> 
then you want to copy ALL the files from your wordpress root to /var/www/yoursitesfiles/ 

If the local copy of WordPress is on /var/www/wordpress/
then copy all folders and files from my live website on Godaddy to;
/var/www/wordpress/mydomain.com ?
Do I need adding .com ?

3)
> 
I generally log into mysql as root then run
CREATE 'user'@'localhost' IDENTIFIED BY 'password';
CREATE DATABASE databasename;
GRANT ALL PRIVILEGES ON databasename.* TO 'user'@'localhost';

I suppose running the commands on local PC retaining the databasename which was created at time of installing WordPress ?

4)
> 
Then i exit mysql \q and then run mysql -u user -p databasename < /path/to/databasedumpfile.sql

What is the file "databasedumpfile.sql" ?  Is it on the local WP copy OR the imported copy?


I am running VirtualBox here possible creating dozens of VMs for testing on my PC (AMD Core-8, 32G RAM, 3T WD Black lable HD).  I'll come back after fixing the problem in re evoking the local copy of WP first.  Thanks

Rgds
satimis

---

### Post by Habitual on 2013-12-13
Some references:
[http://support.godaddy.com/help/article/6117/moving-your-wordpress-site-to-us-from-another-host](http://support.godaddy.com/help/article/6117/moving-your-wordpress-site-to-us-from-another-host)
[http://support.godaddy.com/help/article/7572/fixing-broken-links-after-moving-your-wordpress-site](http://support.godaddy.com/help/article/7572/fixing-broken-links-after-moving-your-wordpress-site)
[http://support.godaddy.com/search/move+wordpress+to+godaddy/](http://support.godaddy.com/search/move+wordpress+to+godaddy/)

---

