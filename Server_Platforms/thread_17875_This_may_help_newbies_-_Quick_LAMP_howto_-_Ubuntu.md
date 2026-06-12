---
title: "This may help newbies - Quick LAMP howto - Ubuntu"
date: 2005-03-03
forum: Server Platforms
---

### Post by machiner on 2005-03-03
A quick and painless LAMP install/config for Ubuntu.

I don't run Apache2 so this howto will focus on Apache 1.3. As well, I think Webmin makes setting LAMP up very easy, even though we don't really use it for much.  So this howto will include those instructions as well.

Considering the proliferation of Content Managers like Mambo and Drupal (et al) we will also make changes to allow for these scripts to run locally without impediment.
***********************
For Hoary users:
Open up your Synaptic and install the following:

ssleanet (sp) OPTIONAL
apache
apache-common
apache-utils
libapache-mod-perl
libapache-mod-php4
libapache-mod-ssl
*********
mysql-client
mysql-common
mysql-server
libmysqlclient12
libqt3c102-mt-mysql
libdbd-mysql-perl
php4-mysql
*********
php4
php4-pear
php4-imagick
php4-common
php4-gd2
*******************
Some of the applications already come pre-installed with Ubuntu, and some will include dependancies. As well, you may not want to install php4-imagick, or php4-gd2, but you will find that some scripts (SugarCRM) will want these and others.

For Warty users I found it necessary to add a Debian repository in order to install libapache-mod-php4. At the command prompt type:
sudo gedit /etc/apt/sources.list

add this line:
deb [ftp://ftp.debian.org/debian](ftp://ftp.debian.org/debian) sarge main contrib non-free #

You must then type: sudo apt-get update
 Or, you may just save the file, and open synaptic and update it there. Don't forget to comment out this line or remove it once you have installed the necessary php4 lib.

*******************

To make things a little easier we work with Webmin. Goto: 
[http://prdownloads.sourceforge.net/webadmin/webmin-1.180.tar.gz](http://prdownloads.sourceforge.net/webadmin/webmin-1.180.tar.gz)
and pick your mirror.  Once downloaded, extract webmin into a directory of your choice and open a terminal. Goto the extracted webmin directory land type the following:

sudo sh setup.sh /usr/local/webmin

From there follow the prompts, mostly just enter. You may choose your port, uname and password. You may also decide to run Webmin securely - always a good idea. You must have SSLeanet (SP) installed. It's in the repository, or - you can install it when you are in Webmin. As well, you may choose to have Webmin start at boot or no. I choose no. The command to start Webmin when you need it is the following:

sudo /etc/webmin/start   to stop it when your finished:  sudo /etc/webmin/stop

Everything installed? Good. Close everything. Shake it off.

***********************************

Open a terminal and type the following command as a regular user:
mysqladmin -u root password <password> (pick a password)

Now start Webmin. You can leave the terminal open.  Open your browser and point to: 127.0.0.1:10000   Of course, if you changed the port at installation you would choose that port instead of 10000. As well, if you had ssleanet installed already and webmin installed allowing secure browsing, you would point to this address:
[https://127.0.0.1:10000](https://127.0.0.1:10000)

*********************************

Navigate to the SERVERS aspect of Webmin. You will see Apache and 2 below it you will see MySQL. Click on Apache.  The first screen you see will "confirm" your modules. You should see "php4" and a few others.  Choose OK. If you don't see what you want, it might be installed with Apache anyway. This howto is limited.  Next screen you will see your Apache modules, at the top of your screen you will see commands to Apply Changes, Stop/Start Apache, etc. Stop Apache.

You will see an icon for "edit config files" Click that.  There are 4 or 5 things to change. I only change enough to run Mambo sites, and cgi scripts locally. I'm no Apache expert.

Scroll down in the config file until you come to this section:

# First, we configure the "default" to be a very restrictive set of 
# permissions.  
#
<Directory />
    Options SymLinksIfOwnerMatch
    AllowOverride None      <<<<<<<<<<change None to read: All
</Directory>


Goto this section next:
# This controls which options the .htaccess files in directories can
# override. Can also be "All", or any combination of "Options", "FileInfo", 
# "AuthConfig", and "Limit"
#
    AllowOverride None <<<<<<<<<<<<<<change None to All

next:

<IfModule mod_dir.c>
    DirectoryIndex index.php index.html index.htm index.shtml index.cgi
</IfModule>

Make sure that "index.php" is FIRST in the above line.

Next, if you want to run cgi-bin locally and you have your cgi-bin in your /var/www directory change the following to reflect that:

<IfModule mod_alias.c>
    ScriptAlias /cgi-bin/ /var/www/cgi-bin/   <<<<<<<<<<<<<<<<<<<<<<<<<<<

#
# "/usr/lib/cgi-bin" could be changed to whatever your ScriptAliased
# CGI directory exists, if you have that configured.
#
    <Directory /var/www/cgi-bin/>  <<<<<<<<<<<<<<<<<<<<<<<<<
        AllowOverride None
        Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>
</IfModule>

I think the default local for cgi-bin is : var/lib/cgi-bin  or something like that. 

Next goto the following section:

    # And for PHP 4.x, use:
    #
    #AddType application/x-httpd-php .php  <<<<<<<<<<<<<<<<<<<uncomment
    #AddType application/x-httpd-php-source .phps <<<<<<<<<<<<uncomment

That's all I ever do to change my config file. Click the SAVE button.

*********************

Next, you need to change php.ini to alloy running the mysql add-on. Alt-Tab to your terminal, start another session and type the following:
sudo gedit /etc/php4/apache/php.ini

ctrl+F to find : mysql.so   it will be in the Dynamic Extensions area. Looks like this:
; Example lines:

;extension=mysql.so
;extension=gd.so
;extension=udb.so

remove the semi-colon for mysql.so. Scripts like SugarCRM need to run the GD Graphics library that's why we installed the module originally and you can uncomment it now in your php.ini file. Save the file, close it.

*******************************

Alt-Tab back to Webmin. You may now Start Apache.  Click on the Servers icon in Webmin, click on MySQL.  You should be greeted with a uname/passwd login screen. Your password that you chose earlier is already in the field as stars. You may click login.  Now you may Start MySQL.

****************

You are finished. You may close everything out, run the STOP comand for Webmin and populate your /var/www folder with all your fancy websites and and cgi-scripts.

Typical Disclaimer:
I hope this solves many of the problems that crop up on the forum frequently.
You machine is different than mine. YMMV - I do this exact setup every time on my machine and others with good results.  If you want to run Apache2, more power to you but I could never figure out how to allow the modrewrite to work in Apache2 - this means that I couldn't setup Mambo for using "nice" URLS.  You may be able to do that -- Rock On.

---

### Post by az on 2005-03-03
" could never figure out how to allow the modrewrite to work in Apache2"

sudo a2enmod rewrite


How the f*ck do you set up postfix to send emails through gmail?  It can be done.  I have read every howto on the internet and I am still screwing it up.

How about just through any old mail provider (like from one's ISP...)

Thanks.

---

### Post by machiner on 2005-03-03
I'm not there yet. Still satisfied with the emails that come with my hosted websites.

When you know - tell me.

Thanks for the a2enmod tip.  I just upgraded to apache2 this morning -- no worries.

---

### Post by machiner on 2005-03-04
---> disreguard <---

---

### Post by Phosphoros on 2005-03-05
My system must hate me.  I've done everything just like you said and I've got error messages out the wazoo.

Thanks for the HOWTO though, I'm just cursed.  :cry:

I'm sort of giving up on MySQL.  Either I'm to dumb or I don't have the right PhD to make it work.  lol

---

### Post by machiner on 2005-03-06
Sorry it isn't working for you.

Did you have apache already installed? Or php4?

What's not working?  Would you rather compile it - there's a terrific tutorial I know of if you need it.

That write up is for a fresh LAMP install...lemme know where it's failing for you.

---

### Post by Phosphoros on 2005-03-06
Hi machiner,
Yep, sure was a fresh install of all components.  Nothing had been installed yet (LAMP related).

First I couldn't find ssleas (I believe that was the name of it, some file dependacy one of the programs needed) in any repository, I have all the ones enabled from the HOWTO here and at ubuntuguide.  
Also, MySQL kept giving me permission errors as well as not being able to find varies packages.

PHP had some issues as well and basically I kind of gave up.  I know thats not the Linux spirit but I had just won my dependancy hell fight with multimedia and had pretty much had it.
Also please forgive that I don't have the specifics of the errors.  I had fiddled with some optional components in the repository after I had given up on LAMP and pretty much ruined my install, hence forcing me to reinstall Ubuntu which I did no problem. Which is why I can't give you specifics. :(
Now that I'm up and running again, I'm sort of scared to try it again.   :-P 

If I try again I'll post what went wrong here because I just know I'm cursed and it'll all happen again.

BTW, would Phpmyadmin be something to isntall as well if I'm MySQL-challenged?

---

### Post by machiner on 2005-03-07
I don't know what to tell you -- this write up is based on a fresh hoary install with default repositories -- I enabled all of them except the ones (2) preceeded by:
"this is for updates after release" paraphrased.

When I do this (method, I guess) I search for: php4, mysql, and apache in synaptic -- I choose to install the components I wrote up, and BAM -- I sit and watch them install -- no problem.

Then I open a terminal and change the password for mysql admin...then I uncomment the "mysql.so" in my php.ini file.

Then I go into webmin - do what I described (really nothing, just click a configure button, and ok the uname password in mysql) and I see that I'm tight with LAMP.

THen I stop apache, change my httpd.conf file, restart apache and my sites load and all is well.

Again, sorry it didn't work for you -- If your install is stock hoary (even warty) than this quick tutorial should work like a charm.

The file to install enabling https:// with webmin is this:
**libnet-ssleay-perl**

---

### Post by adamkane on 2006-11-18
Webmin is unnecessary for a newbie.

Here's all you need to get LAMP to work with a CMS:

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

```Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```Reboot (or start mysql manually).

Open phpmyadmin:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Name: root
Pass: [blank]

-----------------------------------------------------------------------------

Apache2/PHP-latest/MySQL-latest, install XAMPP:
[http://www.ubuntuforums.org/showthread.php?t=223410](http://www.ubuntuforums.org/showthread.php?t=223410)

---

