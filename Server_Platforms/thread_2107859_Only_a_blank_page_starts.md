---
title: "Only a blank page starts"
date: 2013-01-22
forum: Server Platforms
---

### Post by satimis on 2013-01-22
Hi all,

Ubuntu 12.04 desktop 64bit
Wordpress 3.3.1

I have WordPress installed locally. It was working and can be started on browser running /localhost/wordpress/wp-admin/

For unknown reason now it only starts a blank page.

I found some postings here on similar problem. Unfortunately none of them can help me out.

Please help. TIA

B.R.
satimis

---

### Post by volkswagner on 2013-01-23
It may be helpful to post any errors you see in apache2 logs.

In a terminal run:

```
tail -f /var/log/apache2/access.log
```

Then try to access the site, copy and paste the code ouput.

You can also do the same for error.log.

---

### Post by satimis on 2013-01-23
> **volkswagner said:**
> It may be helpful to post any errors you see in apache2 logs.

In a terminal run:

```
tail -f /var/log/apache2/access.log
```

Then try to access the site, copy and paste the code ouput.

You can also do the same for error.log.

$ tail /var/log/apache2/access.log```

127.0.0.1 - - [23/Jan/2013:17:23:22 +0800] "GET /wordpress/wp-admin/ HTTP/1.1" 500 275 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:18.0) Gecko/20100101 Firefox/18.0"
127.0.0.1 - - [23/Jan/2013:17:23:23 +0800] "GET /wordpress/wp-admin/ HTTP/1.1" 500 275 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:18.0) Gecko/20100101 Firefox/18.0"
127.0.0.1 - - [23/Jan/2013:17:23:24 +0800] "GET /wordpress/wp-admin/ HTTP/1.1" 500 275 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:18.0) Gecko/20100101 Firefox/18.0"
127.0.0.1 - - [23/Jan/2013:17:23:25 +0800] "GET /wordpress/wp-admin/ HTTP/1.1" 500 275 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:18.0) Gecko/20100101 Firefox/18.0"
127.0.0.1 - - [23/Jan/2013:17:23:28 +0800] "GET /wordpress/wp-admin/ HTTP/1.1" 500 275 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:18.0) Gecko/20100101 Firefox/18.0"
127.0.0.1 - - [23/Jan/2013:17:24:20 +0800] "GET /wordpress/ HTTP/1.1" 500 275 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:18.0) Gecko/20100101 Firefox/18.0"
127.0.0.1 - - [23/Jan/2013:21:08:54 +0800] "POST /wordpress/wp-cron.php?doing_wp_cron=1358946533 HTTP/1.0" 500 230 "-" "WordPress/3.3.1; http://localhost/wordpress"
127.0.0.1 - - [23/Jan/2013:21:08:53 +0800] "GET /wordpress/wp-admin/ HTTP/1.1" 500 275 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:18.0) Gecko/20100101 Firefox/18.0"
127.0.0.1 - - [23/Jan/2013:21:08:54 +0800] "GET /favicon.ico HTTP/1.1" 404 499 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:18.0) Gecko/20100101 Firefox/18.0"
127.0.0.1 - - [23/Jan/2013:21:08:56 +0800] "GET /wordpress/wp-admin/ HTTP/1.1" 500 275 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:18.0) Gecko/20100101 Firefox/18.0"

```

$ tail /var/log/apache2/error.log```

[Wed Jan 23 16:07:28 2013] [error] [client 127.0.0.1] script '/var/www/wordpress/wp-admin/html.php' not found or unable to stat
[Wed Jan 23 16:08:17 2013] [error] [client 127.0.0.1] File does not exist: /var/www/wordpress/wp-admin/index.htm
[Wed Jan 23 16:08:33 2013] [error] [client 127.0.0.1] File does not exist: /var/www/wordpress/wp-admin/index.html
[Wed Jan 23 17:20:13 2013] [notice] caught SIGTERM, shutting down
[Wed Jan 23 17:20:40 2013] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.5 with Suhosin-Patch configured -- resuming normal operations
[Wed Jan 23 17:20:57 2013] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Wed Jan 23 17:20:57 2013] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Wed Jan 23 17:28:10 2013] [notice] caught SIGTERM, shutting down
[Wed Jan 23 21:05:39 2013] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.5 with Suhosin-Patch configured -- resuming normal operations
[Wed Jan 23 21:08:54 2013] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico

```

Several hours ago it still worked without problem.  The nightmare started on installing the 'blackbird' plugin.  Then I couldn't start it.

---

### Post by volkswagner on 2013-01-23
This is more of a WordPress specific issue vs. Ubuntu Server.

Perhaps you may want to disable the plugin which likely broke WordPress.  Check out this link on how to [disable the plug without using the Dashboard]("http://wpdude.com/case-study-disabling-plugin-dashboard-fubar").  The example uses FTP but you can easily use ssh.

Pay close attention to creating a backup before you do more damage... you've been warned ;)

---

### Post by satimis on 2013-01-23
> **volkswagner said:**
> This is more of a WordPress specific issue vs. Ubuntu Server.

Perhaps you may want to disable the plugin which likely broke WordPress.  Check out this link on how to [disable the plug without using the Dashboard]("http://wpdude.com/case-study-disabling-plugin-dashboard-fubar").  The example uses FTP but you can easily use ssh.

Pay close attention to creating a backup before you do more damage... you've been warned ;)
Thanks for your advice.

This is a local installed WP.  I haven't created any page yet.  After installation I was playing around its features.  Just started creating page by installing the plugin-blackbird.  After finish it didn't showed the plugin on screen.  Neither I could click backforwards.  I started another page trying to login again and found a blank page resulted.

$ sudo find / -name plugins | grep blackbird
No output

$ sudo find / -name plugins | grep black
Also no out put.

$ sudo find / -name plugins
```

/home/satimis/.gconf/apps/compiz-1/plugins
/home/satimis/.gconf/apps/gedit-2/plugins
/usr/share/pyshared/twisted/plugins
/usr/share/apt-xapian-index/plugins
/usr/share/update-notifier/plugins
/usr/share/bluefish/plugins
/usr/share/gedit/plugins
/usr/share/tinymce/www/plugins
/usr/share/gwibber/plugins
/usr/share/computerjanitor/plugins
/usr/share/wordpress/wp-includes/js/tinymce/plugins
/usr/share/wordpress/wp-includes/js/swfupload/plugins
/usr/share/wordpress/wp-content/plugins
/usr/share/checkbox/plugins
/usr/share/hplip/ui4/plugins
/usr/share/rhythmbox/plugins
/usr/share/ubufox/plugins
/usr/lib/telepathy/salut-0/plugins
/usr/lib/telepathy/gabble-0/plugins
/usr/lib/gnome-bluetooth/plugins
/usr/lib/remmina/plugins
/usr/lib/unity-2d/plugins
/usr/lib/thunderbird-addons/plugins
/usr/share/wordpress/wp-includes/js/swfupload/plugins
/usr/share/wordpress/wp-content/plugins
/usr/share/checkbox/plugins
/usr/share/hplip/ui4/plugins
/usr/share/rhythmbox/plugins
/usr/share/ubufox/plugins
/usr/lib/telepathy/salut-0/plugins
/usr/lib/telepathy/gabble-0/plugins
/usr/lib/gnome-bluetooth/plugins
/usr/lib/remmina/plugins
/usr/lib/unity-2d/plugins
/usr/lib/thunderbird-addons/plugins
/usr/lib/totem/plugins
/usr/lib/brasero3-1/plugins
/usr/lib/thunderbird/plugins
/usr/lib/firefox/plugins
/usr/lib/shotwell/plugins
/usr/lib/gedit/plugins
/usr/lib/firefox-addons/plugins
/usr/lib/iceape/plugins
/usr/lib/eog/plugins
/usr/lib/x86_64-linux-gnu/qt4/plugins
/usr/lib/x86_64-linux-gnu/krb5/plugins
/usr/lib/nautilus-sendto/plugins
/usr/lib/python2.7/dist-packages/twisted/plugins
/usr/lib/mozilla/plugins
/usr/lib/xulrunner/plugins
/usr/lib/xulrunner-addons/plugins
/usr/lib/rhythmbox/plugins
/usr/lib/midbrowser/plugins
/usr/lib/iceweasel/plugins

```


Edit:
====

Performed following steps:

$ sudo nano /etc/php5/apache2/php.ini
Change;
html_errors = On

Restart Apache2
$ sudo service apache2 restart
```
     
     * Restarting web server apache2
     ... waiting    ...done.
    
```

Still a blank page. No error message displayed.

sudo find / -name blackbird -type d```

/usr/share/wordpress/wp-content/themes/blackbird

```

# ls /usr/share/wordpress/wp-content/themes/blackbird
```
     
    404.php         css               index.php       search.php
    archive.php     editor-style.css  js              sidebar-footer.php
    attachment.php  footer.php        languages       sidebar.php
    author.php      front-page.php    license.txt     single.php
    blog.php        functions         loop.php        style.css
    category.php    functions.php     page.php        tag.php
    changelog.txt   header.php        screenshot.png
    comments.php    images            searchform.php

``` 

# rm -r /usr/share/wordpress/wp-content/themes/blackbird

On browser;
/localhost/wordpress/wp-admin

WP login page comes back -> login -> starting Dashboard

Appearance -> Themes -> Install Themes
[blackbird] -> search
    BlackBird```

    Install | Preview
     
    Blackbird is a Uniquely Designed, Professional, Responsive and beautiful
    ......
    ......

```  

Before installing this theme again. Is there any way checking the server here to find out any other possible cause making the installation fail?  Thanks


Regards
satimis

---

### Post by volkswagner on 2013-01-24
One thing I should have mentioned was to check the permissions of the folder and files for the theme.

I'm not sure of any available precheck.  As you can see now, it's not difficult to remove the theme if it does not work.

Perhaps try again.  If it fails, check the permissions and make sure the files are readable by apache2.

---

### Post by satimis on 2013-01-24
> **volkswagner said:**
> - snip -

Perhaps try again.  If it fails, check the permissions and make sure the files are readable by apache2.
OK, I'll retry.

What should be the permission of the folder, blackbird?

www-data root ?  Thanks

satimis

---

### Post by volkswagner on 2013-01-24
Compare it to your other working plugins/themes.

Likely www-data:www-data or yourusename:www-data.

I say owner as your username because if you are uploading via ftp this may be helpful.

---

### Post by satimis on 2013-01-24
> **volkswagner said:**
> Compare it to your other working plugins/themes.

Likely www-data:www-data or yourusename:www-data.

I say owner as your username because if you are uploading via ftp this may be helpful.
Hi,

I wonder whether there is something wrong on the LAMP server here?


Performed following steps;

Download blackbird version 1.1.4 on;
[http://wordpress.org/extend/themes/blackbird](http://wordpress.org/extend/themes/blackbird)

# ls -ald /usr/share/wordpress/wp-content/themes/twentyeleven
drwxr-xr-x 7 www-data www-data 4096 Jan 23 17:19 /usr/share/wordpress/wp-content

(above confirms permission = www-data www-data)

unzip blackbird.1.1.4.zip

# mv /home/satimis/blackbird /usr/share/wordpress/wp-content/themes/

# chown -R www-data:www-data /usr/share/wordpress/wp-content/themes/blackbird
# ls -ald /usr/share/wordpress/wp-content/themes/blackbird```

drwxr-xr-x 7 www-data www-data 4096 Jan  2 22:24 /usr/share/wordpress/wp-content/themes/blackbird

```

login WP 

Appearance -> Themes
After playing around a while the screen became blank.  Then /localhost/wordpress/wp-admin popup only a blank screen without Login page but without warning message displayed.

# rm -r /usr/share/wordpress/wp-content/themes/blackbird

Login page comes back.


I'll install a new WP on a VM of Oracle VirtualBox to check what will happen.

I followed;
1)
How To Install WordPress in Ubuntu Server 12.04 LTS
[http://ubuntuserverguide.com/2012/05/how-to-install-latest-wordpress-in-ubuntu-server-12-04-lts.html](http://ubuntuserverguide.com/2012/05/how-to-install-latest-wordpress-in-ubuntu-server-12-04-lts.html)

and

2)
Ubuntu Server Guide
[http://ubuntuserverguide.com/2012/05/how-to-install-latest-wordpress-in-ubuntu-server-12-04-lts.html](http://ubuntuserverguide.com/2012/05/how-to-install-latest-wordpress-in-ubuntu-server-12-04-lts.html)

to install WP here.

I hesitate whether I made a mistake on Step 4 of 2) above;

$ sudo bash /usr/share/doc/wordpress/examples/setup-mysql -n wordpress_preciseserver blog.preciseserver.com

In order to ping blog.preciseserver.com I edited;
/etc/hosts```

127.0.0.1       blog.preciseserver.com  localhost
127.0.1.1       localhost.localdomain   localhost

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

on /etc/hostname```

localhost

```

therefore;
$ hostname
localhost

$ hostname -f
blog.preciseserver.com


I'll follow another document;
WordPress	installation
[https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress)

and

ApacheMySQLPHP
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

to install WP and LAMP server on Ubuntu 12.04 desktop 64bit

Any comment before start?  TIA

satimis

---

### Post by satimis on 2013-01-25
Hi all,

Made another round installing Wordpress on a VM also without luck.

host  Ubuntu 12.04 desktop 64bit
VM (guest)  Ubuntu 12.04 desktop 64bit
vituralizer  Oracle VirtualBox

Performe following steps;

Documents to follow;

1)
ApacheMySQLPHP
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

2)
WordPress	installation
[https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress)

(This is a local installation without pointing to mydomain on Godaddy)

Installation went through without much problem.

$ sudo apt-get install tasksel

$ sudo tasksel install lamp-server


2)
WordPress	installation
[https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress)

$ sudo bash /usr/share/doc/wordpress/examples/setup-mysql -n wordpress localhost```

PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_req=1 ttl=64 time=0.030 ms

--- localhost ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.030/0.030/0.030/0.000 ms
/etc/wordpress/config-localhost.php written
Trying to create upload directory: /srv/www/wp-uploads/localhost
Setting up permissions
Goto http://localhost to setup Wordpress

```

$ sudo bash /usr/share/doc/wordpress/examples/setup-mysql -n wordpress_mydomain_org wordpress.mydomain.org```

ping: unknown host wordpress.mydomain.org

```

$ sudo bash /usr/share/doc/wordpress/examples/setup-mysql -n localhost localhost```

PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_req=1 ttl=64 time=0.026 ms

--- localhost ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.026/0.026/0.026/0.000 ms
WARNING: /etc/wordpress/config-localhost.php exists!

```

$ sudo /etc/init.d/apache2 restart```

 * Restarting web server apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
   ...done.

```

On browser
[http://localhost/wordpress/wp-admin/install.php](http://localhost/wordpress/wp-admin/install.php)

Site Title	Testing
Username	admin
Password	mypassword
Your E-mail	[email]satimis@mydomain.com[/email]

Privacy 	(check)Allow my site to appear in search engines like Google and Technorati.

--> Install WordPress

Logout WP

$ sudo chown -R www-data /usr/share/wordpress

Relogin WP

-> Update
You have the latest version of WordPress.

-> update plugin	select all
-> update theme		select all

Appearance -> Themes -> Install Theme

blackbird -> Install
```

Downloading install package from http://wordpress.org/extend/themes/download/blackbird.1.1.4.zip&#8230;

Unpacking the package&#8230;
Installing the theme&#8230;
Successfully installed the theme BlackBird 1.1.4.

```

-> Activate

Only a blank page displayed

-> backwards
-> preview	also a blank page

-> Logout
Also only a blank page displayed

On browser;
[http://localhost/wordpress/wp-admin/](http://localhost/wordpress/wp-admin/)
Only a blank page displayed

On terminal:
ls -ald /usr/share/wordpress/wp-content/themes/blackbird```

drwxr-xr-x 7 www-data www-data 4096 Jan 25 17:07 /usr/share/wordpress/wp-content/themes/blackbird

```

# ls -al /usr/share/wordpress/wp-content/themes/blackbird/    ```
                   
total 304
drwxr-xr-x 7 www-data www-data  4096 Jan 25 17:07 .
drwxrwx--- 7 www-data www-data  4096 Jan 25 17:07 ..
-rw-r--r-- 1 www-data www-data  2127 Jan 25 17:07 404.php
-rw-r--r-- 1 www-data www-data  2283 Jan 25 17:07 archive.php
-rw-r--r-- 1 www-data www-data  5153 Jan 25 17:07 attachment.php
-rw-r--r-- 1 www-data www-data  3527 Jan 25 17:07 author.php
-rw-r--r-- 1 www-data www-data  4705 Jan 25 17:07 blog.php
-rw-r--r-- 1 www-data www-data  2138 Jan 25 17:07 category.php
-rw-r--r-- 1 www-data www-data   505 Jan 25 17:07 changelog.txt
-rw-r--r-- 1 www-data www-data  1699 Jan 25 17:07 comments.php
drwxr-xr-x 4 www-data www-data  4096 Jan 25 17:07 css
-rw-r--r-- 1 www-data www-data  5632 Jan 25 17:07 editor-style.css
-rw-r--r-- 1 www-data www-data  1393 Jan 25 17:07 footer.php
-rw-r--r-- 1 www-data www-data  8512 Jan 25 17:07 front-page.php
drwxr-xr-x 5 www-data www-data  4096 Jan 25 17:07 functions
-rw-r--r-- 1 www-data www-data  3989 Jan 25 17:07 functions.php
-rw-r--r-- 1 www-data www-data  3889 Jan 25 17:07 header.php
drwxr-xr-x 3 www-data www-data  4096 Jan 25 17:07 images
-rw-r--r-- 1 www-data www-data  1504 Jan 25 17:07 index.php
drwxr-xr-x 2 www-data www-data  4096 Jan 25 17:07 js
drwxr-xr-x 2 www-data www-data  4096 Jan 25 17:07 languages
-rw-r--r-- 1 www-data www-data 35155 Jan 25 17:07 license.txt
-rw-r--r-- 1 www-data www-data  2778 Jan 25 17:07 loop.php
-rw-r--r-- 1 www-data www-data  1338 Jan 25 17:07 page.php
-rw-r--r-- 1 www-data www-data 77367 Jan 25 17:07 screenshot.png
-rw-r--r-- 1 www-data www-data   399 Jan 25 17:07 searchform.php
-rw-r--r-- 1 www-data www-data  2217 Jan 25 17:07 search.php
-rw-r--r-- 1 www-data www-data  3175 Jan 25 17:07 sidebar-footer.php
-rw-r--r-- 1 www-data www-data   728 Jan 25 17:07 sidebar.php
-rw-r--r-- 1 www-data www-data  4590 Jan 25 17:07 single.php
-rw-r--r-- 1 www-data www-data 52503 Jan 25 17:07 style.css
-rw-r--r-- 1 www-data www-data  1522 Jan 25 17:07 tag.php

```

Advice would be appreciated.  TIA

Edit-1:
====

$ sudo nano /etc/apache2/apache2.conf
adding:
ServerName    localhost
                     
$ sudo service apache2 restart```

 * Restarting web server apache2
 ... waiting    ...done.

```

Now no complaint.  But WP is still a blank page

Edit-2
======

Blackbird has problem.

Deleted it to login WP

Installed and activated following themes without problem:
responsive
utility

---

### Post by volkswagner on 2013-01-25
Again, this is a Wordpress issue, more specifically related to the Blackbird theme.  It seems you are not alone, but there are no responses to [this similar issue]("http://wordpress.org/support/topic/blank-page-60").

I suggest reporting the issue to the theme developer, or try a different theme.

---

### Post by satimis on 2013-01-25
> **volkswagner said:**
> Again, this is a Wordpress issue, more specifically related to the Blackbird theme.  It seems you are not alone, but there are no responses to [this similar issue]("http://wordpress.org/support/topic/blank-page-60").

I suggest reporting the issue to the theme developer, or try a different theme.
This plugin is quite strange.  Once installed even after deleleting its directory/folder you can find it on;
Appearance -> Themes

but not working.  Don't try to delete it otherwise a blank screen will result on evoking WP on browser.  There is no way to restore it execept reinstalling WP.

I'm not prepared persuing this problem any further.  Thanks again for your help.

satimis

---

### Post by volkswagner on 2013-01-25
You should be able to backup your wordpress directory and database enabling you to restore to a non broken state without reinstalling wordpress from scratch.

---

### Post by satimis on 2013-01-25
> **volkswagner said:**
> You should be able to backup your wordpress directory and database enabling you to restore to a non broken state without reinstalling wordpress from scratch.
Thanks for your advice.

My local installed WP is for testing only current.  There is no important data stored. I just ran;

$ sudo apt-get install --reinstall wordpress

DONE

I install WP on VM of VirtualBox and clone several VMs.  In case the running WP doesn't work.  I start another VM and delete the problematic VM.

For website editing, currently I use the online installed WP on Godaddy site for its editing.

I'm prepared to use the local WP creating/editing website and upload the files to Godaddy website after finish.  It'll be more convenient to me.

Where is the index page of the website created with WP?  I have been googling around for it.  I expect doing some minor editing on it and other pages created, using my limited knowledge on html/xhtml/css/php/java scripts etc. learned in the past.  Although I haven't used them for sometimes.  I trust it won't be too difficult for me to remaster them.

Regards
satimis

---

### Post by volkswagner on 2013-01-26
The page templates are part of the theme.  Each theme will use a unique template.

For example I'm using daily-minefield theme, the index.php is located ~/wordpress/wp-content/themes/daily-minefield/.

You can navigate to this content from wordpress admin web dashboard: 
 [INDENT]Dashboard > Appearance > editor[/INDENT]
[INDENT]Once you are in the editor section, be sure to select the theme you want to edit from the dropdown at the top right of the page.[/INDENT]

---

### Post by satimis on 2013-01-27
> **volkswagner said:**
>  - snip -
You can navigate to this content from wordpress admin web dashboard: 
 [INDENT]Dashboard > Appearance > editor[/INDENT]
[INDENT]Once you are in the editor section, be sure to select the theme you want to edit from the dropdown at the top right of the page.[/INDENT]
Thanks for your advice.

I can find the coding on all added pages but NOT the home page/index page.

On building website with codes such as html/css/php etc. the first page is the html.index or home page. Would it be the theme where I start building website on WP? But it has been edited/modified. If YES, then where can I the find the edited/modified starting theme? Thanks

satimis

---

